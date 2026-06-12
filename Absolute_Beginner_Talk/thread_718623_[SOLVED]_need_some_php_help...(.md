---
title: "[SOLVED] need some php help...:("
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by RadiationHazard on 2008-03-08
i've tried many sites that are actually for coding help but no one actually helps me at any other site besides this one.
so i have a question for anyone who is reading this and knows php.
i have most of the script
all i want is for it to also print out the html code for the picture under the direct link
if anyone can do this please help!!

```

<html>

<head>

<title>Image Uploader</title>
<link rel="stylesheet" type="text/css" href="sitestyle.css" />
</head>

<body>
<table width="600px" border="0" align="center">
<tr>
   <td class="heading" align="center" colspan="3"><img src="http://localhost/imagebanner.gif"></td>
</tr>
<tr>
   <td align="center" class="links">
<a href="http://localhost/"><img border="0" src="http://localhost/images/home.gif" id="home" onmouseover="this.src='http://localhost/images/home2.gif';" onmouseout="this.src='http://localhost/images/home.gif';" /></a>
   <a href="http://localhost/image_uploader"><img border="0" src="http://localhost/images/imageuploader.gif" id="image uploader" onmouseover="this.src='http://localhost/images/imageuploader2.gif';" onmouseout="this.src='http://localhost/images/imageuploader.gif';" /></a>
   <a href="http://localhost/talk"><img border="0" src="http://localhost/images/talk.gif" id="Talk" onmouseover="this.src='http://localhost/images/talk2.gif';" onmouseout="this.src='http://local host/images/talk.gif';" /></a></td>
</tr>
<tr>
   <td align="center" colspan="4"><br/>
<?php
// The Temporary Directory where the file is uploaded too
// THIS DIRECTORY MUST EXIST!
$target_path = "temp/";

## SET YOUR WEBSITE URL PATH HERE.
### TO BE USED FOR THE TEXTAREA OUTPUT.
$siteurl = "http://localhost/image_uploader/";

$target_path = $target_path . basename( $_FILES['uploadedfile']['name']); 

if(move_uploaded_file($_FILES['uploadedfile']['tmp_name'], $target_path)) 
	{


// The Output page.
echo '
<img src="'.$target_path.'" />
<br />
<textarea COLS=60>'.$siteurl.$target_path.'</textarea>';


	}

	 else
	{
	// What to say if there is an error.
	echo "There was an error uploading the file.<br />Most likely, your file is too big.";
	}
?>
<br/>
</body>
</html>

```

---

### Post by RadiationHazard on 2008-03-08
i guess i'm not going to get any help from this site either now...:(

---

### Post by billgoldberg on 2008-03-08
You should post your question in the right section of the site.

[http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

It's more likely you'll get better help there.

---

### Post by RadiationHazard on 2008-03-08
ok thank you. and sorry

---

