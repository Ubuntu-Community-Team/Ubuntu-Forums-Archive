---
title: "TrueType Library"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by linux-beginner on 2006-10-23
Hello,

My followed script doesn't run.
```
<?php
header("Content-type: image/png");

$image=imagecreate(400,200);
$red=imagecolorallocate($image,255,0,0);
$blue=imagecolorallocate($image,0,0,255);
$font="luxisri.ttf";

imageTTFtext($image, 50,0,20, 100, $blue,$font, "Test!");
imagepng($image);
?>
```

I think there is a problem with TrueType suport.:-k 
Could you guide me how I can tell PHP about TrueType library?

Thanks,

---

