---
title: "php script doesn't run"
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by linux-beginner on 2006-10-25
Hello

If the followed script runs:
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

I get the next error message:
> The image "http://localhost/***" cannot be displayed,because it contians errors

I work with Ubuntu 6.06, php5 and Apache2. I've also installed DG-package.
Could you help me, please?

---

### Post by Bachstelze on 2006-10-25
You might find the example script in [there](http://fr2.php.net/manual/en/function.imagettftext.php) helpful ;) Make sure you have the FreeType library as well.

---

### Post by linux-beginner on 2006-10-25
What is the name of the package of freetype library?

---

### Post by Bachstelze on 2006-10-25
I don't know if it's available as a package, you'll have to go through the fun of reinstalling PHP from source :p Don't worry though, there aren't much dependencies so it's pretty straightforward. There's a page on the Wiki qabout it if I remember well.

---

