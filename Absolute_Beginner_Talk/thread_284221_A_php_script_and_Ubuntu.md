---
title: "A php script and Ubuntu"
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by linux-beginner on 2006-10-25
Hello,

I'm user of Ubuntu 6.06, Apache2, php5. I've also got dg-package.
If I run the followed script:
```
<?php
header("Content-type: image/png");

$image=imagecreate(400,200);
$red=imagecolorallocate($image,255,0,0);
$blue=imagecolorallocate($image,0,0,255);
$font="verdana.ttf";

imageTTFtext($image, 50,0,20, 100, $blue,$font, "Test!");
imagepng($image);
?>
```
then I get this message:
> The image "http://localhost/MY/PATH" cannot be displayed, because it contains errors

The script runs in a windows system!
Could you help me please?

Thanks,

---

### Post by Bachstelze on 2006-10-25
Do you have the FreeType library installed ? Try running an image script not using test to see if that's the problem.

---

### Post by linux-beginner on 2006-10-25
This script runs wel:
```
<?php
header("Content-type: image/png");
$image=imagecreate(200,200);
$red=imagecolorallocate($image,255,0,0);
$blue=imagecolorallocate($image,0,0,255);

for($x=1; $x<5; $x++){
 imageString($image, $x, (20*$x), (20*$x), "Welkom!", $blue);
}
imagepng($image);
?>
```

---

### Post by Bachstelze on 2006-10-25
Then the problem is obviously the TTF font. Install the Freetype library (no, I don't know how to do that).

---

### Post by linux-beginner on 2006-10-25
I've installed Freetype library.
:(

---

### Post by Bachstelze on 2006-10-25
Hmm, weird... Make sure it's properly installed with phpinfo()

---

### Post by linux-beginner on 2006-10-25
gd
GD Support 	enabled
GD Version 	2.0 or higher
FreeType Support 	enabled
FreeType Linkage 	with freetype
FreeType Version 	2.1.10
T1Lib Support 	enabled
GIF Read Support 	enabled
GIF Create Support 	enabled
JPG Support 	enabled
PNG Support 	enabled
WBMP Support 	enabled

---

### Post by linux-beginner on 2006-10-25
This is the result of phpinfo():

> 
          [CENTER]**[SIZE="4"][SIZE="5"] gd[/SIZE][/SIZE]**[/CENTER]

GD Support  [CENTER]enabled[/CENTER]
GD Version[CENTER]2.0 or higher[/CENTER]
FreeType Support     [CENTER]enabled[/CENTER]
FreeType Linkage     [CENTER]with freetype[/CENTER]
FreeType Version     [CENTER]2.1.10[/CENTER]
T1Lib Support 	     [CENTER]enabled[/CENTER]
GIF Read Support     [CENTER]enabled[/CENTER]
GIF Create Support   [CENTER]enabled[/CENTER]
JPG Support         [CENTER] enabled[/CENTER]
PNG Support 	     [CENTER]enabled[/CENTER]
WBMP Support 	     [CENTER]enabled[/CENTER]


---

### Post by Bachstelze on 2006-10-25
Then sorry but I can't help you any further, wait for someone else I guess or ask your question in another forum, this isn't exactly a newbie question ;)

---

### Post by UnknownVariable on 2006-10-25
Make sure in your PHP script that the font you're pointing to is a direct location. For instance, you have $font="verdana.ttf"; Is the verdana.ttf file residing in that direct level folder? If not, copy and paste the file from your fonts folder over to your web folder. :)

---

### Post by Ben Sprinkle on 2006-10-25
Advice:
Install everything that has the word 'php' in it.

---

### Post by linux-beginner on 2006-10-25
:-D :p :) 
To UnknownVariable: Thank you. It's solved. You're right. Now the $font is pathed to directory where the font is.
:-D :-D 

To HymnToLife: Thank you for your usefull information.

---

### Post by Ben Sprinkle on 2006-10-25
Guess I am worthless. * Kills thy self.

Just kidding, glad you solved your digital nightmare.

---

