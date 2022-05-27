`

>

# Sharp-Multer

Small Utilty to use with Multer as storage engine to optimise images on the fly It uses Sharp to optimise images to jpg, png, webp as well as resize them.

    var  multer  =  require("multer");
    var  SharpMulter  =  require("sharp-multer");
    var storage =  SharpMulter  ({
    				 destination:  (req, file, callback)  => {
    						 callback(null, "images");
    				 },
    				 imageOptions:{
    					 fileFormat: "jpg",
    					 quality: 80,
    					 resize: { width: 100, height: 100 },
    					 }
    				 });
    var  upload  =  multer({ storage });
    app.post("/upload", upload.single("avatar"), async  (req, res)  => {
    console.log(req.file);
    return  res.json("File Uploaded Successfully!");
    }


## Install

> `npm install sharp-multer`

## Image Options

SmartyPants converts ASCII punctuation characters into "smart" typographic punctuation HTML entities. For example:

| Key          | ASCII                        | HTML                                                            |
| ------------ | ---------------------------- | --------------------------------------------------------------- | ----------------------------------------------------- | ------------------- |
| fileFormat   | `jpg                         | png                                                             | webp 'Defaults:"jpg"'`                                | converts all Images |
| resize       | `{height:"", widht:"" } `    | Images will be resized before saving no resizin if not provided |
| quality      | `Number(0-100) defualts :80` | reduce the qulity for better performance                        |
| useTimestamp | `true                        | false defualt :false`                                           | will add suffice to file name "Images_1653679779.jpg" |
