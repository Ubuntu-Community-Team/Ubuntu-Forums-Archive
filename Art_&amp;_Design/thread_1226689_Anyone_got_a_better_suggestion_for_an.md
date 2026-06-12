---
title: "Anyone got a better suggestion for an"
date: 2009-07-29
forum: Art &amp; Design
---

### Post by Lavaeagle on 2009-07-29
This is what you go to.
theform.html

<html>
<head>
<title>File Upload Form</title>
</head>
<body>
This form allows you to upload a file to the server.<br>
<form action="getfile.php" method="get"><br>
Type (or select) Filename: <input type="file" name="uploadFile">
<input type="submit" value="Upload File">
</form>
</body>
</html>

The php
getfile.php

<html>
<head>
<title>Process Uploaded File</title>
</head>
<body>
<?php

move_uploaded_file ($_FILES['uploadFile'] ['tmp_name'],
       "../uploads/{$_FILES['uploadFile'] ['name']}")
if ( move_uploaded_file ($_FILES['uploadFile'] ['tmp_name'],
       "../uploads/{$_FILES['uploadFile'] ['name']}")  )
      {  print '<p> The file has been successfully uploaded </p>';
       }
else
      {   switch ($_FILES['uploadFile'] ['error'])
 {  case 1:
           print '<p> The file is bigger than this PHP installation allows</p>';
           break;
    case 2:
           print '<p> The file is bigger than this form allows</p>';
           break;
    case 3:
           print '<p> Only part of the file was uploaded</p>';
           break;
    case 4:
           print '<p> No file was uploaded</p>';
           break;
 }
       }
?>
</body>
</html>

[http://www.lavaeagle.com/theform.html](http://www.lavaeagle.com/theform.html)

But anyways i keep getting this error:
**Parse error**:  syntax error, unexpected T_IF in **/home/yoursty1/public_html/getfile.php** on line [B]10

A[/B]nyone have a better suggestion of a lite upload client?
Sorry mates :P

---

### Post by enz1m3 on 2009-07-30
can you show us getfile.php contents?

You seem to have posted the same as theform.html

---

### Post by Lavaeagle on 2009-08-01
Sorry there i changed it up there for you

---

### Post by alex.rayu on 2009-08-01
It seems to be the syntax baby. Check out your brackets and semi-colons,

---

### Post by Lavaeagle on 2009-08-02
The syntax can't be that hard to learn in a few minutes. :popcorn:

---

### Post by Lavaeagle on 2009-08-02
I got it to work once!!!!
Then i think i changed to the permission levels.  anyone know the level it needs to be ??

---

### Post by enz1m3 on 2009-08-07
Ideally, if you're using something like apache + mod_fcgid + suexec, it should be just 644, but if you're running mod_php, it probably needs to be 666 (for files and 755 or 777 for directories)

---

### Post by howlingmadhowie on 2009-08-07
> **Lavaeagle said:**
> This is what you go to.
theform.html

<html>
<head>
<title>File Upload Form</title>
</head>
<body>
This form allows you to upload a file to the server.<br>
<form action="getfile.php" method="get"><br>
Type (or select) Filename: <input type="file" name="uploadFile">
<input type="submit" value="Upload File">
</form>
</body>
</html>

The php
getfile.php

<html>
<head>
<title>Process Uploaded File</title>
</head>
<body>
<?php

move_uploaded_file ($_FILES['uploadFile'] ['tmp_name'],
       "../uploads/{$_FILES['uploadFile'] ['name']}")


you're missing a semi-colon here. just as a matter of interest. why are you moving the file twice? the second call (the next line) will fail.
> 
if ( move_uploaded_file ($_FILES['uploadFile'] ['tmp_name'],
       "../uploads/{$_FILES['uploadFile'] ['name']}")  )
      {  print '<p> The file has been successfully uploaded </p>';
       }
else
      {   switch ($_FILES['uploadFile'] ['error'])
 {  case 1:
           print '<p> The file is bigger than this PHP installation allows</p>';
           break;
    case 2:
           print '<p> The file is bigger than this form allows</p>';
           break;
    case 3:
           print '<p> Only part of the file was uploaded</p>';
           break;
    case 4:
           print '<p> No file was uploaded</p>';
           break;
 }
       }
?>
</body>
</html>

[http://www.lavaeagle.com/theform.html](http://www.lavaeagle.com/theform.html)

But anyways i keep getting this error:
**Parse error**:  syntax error, unexpected T_IF in **/home/yoursty1/public_html/getfile.php** on line [B]10

A[/B]nyone have a better suggestion of a lite upload client?
Sorry mates :P

---

