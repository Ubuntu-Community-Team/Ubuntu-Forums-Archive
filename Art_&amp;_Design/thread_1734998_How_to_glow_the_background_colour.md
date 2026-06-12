---
title: "How to glow the background colour?"
date: 2011-04-20
forum: Art &amp; Design
---

### Post by satimis on 2011-04-20
Hi folks,

Ubuntu 1010 desktop 64bit

Web design
==========

The background image is a little bid small covering about 95% of the webpage leaving a small border on both sides (left and right).  

Is there an easy way to fill the fluid areas with gradients that blend seamlessly into the background image without doing it on graphic editing software such as GIMP etc.?  TIA

B.R.
satimis

---

### Post by LarsKongo on 2011-04-21
CSS3 should be able to stretch the background. Won't work on older browsers though. All modern browsers should support it.

```
body {
    background-image:url('background.png');
    background-repeat:no-repeat;
    background-size:cover; /* This is what will stretch the image */
    background-position:center;
}
```

---

### Post by satimis on 2011-04-21
> **LarsKongo said:**
> CSS3 should be able to stretch the background. Won't work on older browsers though. All modern browsers should support it.

```
body {
    background-image:url('background.png');
    background-repeat:no-repeat;
    background-size:cover; /* This is what will stretch the image */
    background-position:center;
}
```

Hi,

Thanks for your advice.

```

      <style type="text/css" title="Default-Style">
        body {
        background-image: url("Hibiskus.jpg");
        background-size:cover;
        background-position: center center;
        background-repeat: no-repeat;
        background-attachment: fixed;
        margin: 12em 5em;
        padding: 0;
        font-family: "tahoma", Arial, Helvetica, sans-serif;
        font-size: 25px;
        }
....

```

The command doesn't work here.

Firefox 3.6.16

B.R.
satimis

---

### Post by LarsKongo on 2011-04-21
> **satimis said:**
> Hi,
Firefox 3.6.16

Try to add this too:
*-moz-background-size:cover;*
*-webkit-background-size:cover;*
*-o-background-size:cover;*
*-khtml-background-size:cover;*

That should make it work on some older browsers with the exception of Internet Explorer and any older version of Firefox than 3.6 (1.9.2). IE9 supports background-size, but not the older versions.

For older versions of IE this may work: (Not sure though.)
```
filter: progid:DXImageTransform.Microsoft.AlphaImageLoader(src='.myBackground.jpg', sizingMethod='scale'); -ms-filter: "progid:DXImageTransform.Microsoft.AlphaImageLoader(src='myBackground.jpg', sizingMethod='scale')";
```

---

### Post by satimis on 2011-04-21
> **LarsKongo said:**
> Try to add this too:
*-moz-background-size:cover;*
*-webkit-background-size:cover;*
*-o-background-size:cover;*
*-khtml-background-size:cover;*

That should make it work on some older browsers with the exception of Internet Explorer and any older version of Firefox than 3.6 (1.9.2). IE9 supports background-size, but not the older versions.

For older versions of IE this may work: (Not sure though.)
```
filter: progid:DXImageTransform.Microsoft.AlphaImageLoader(src='.myBackground.jpg', sizingMethod='scale'); -ms-filter: "progid:DXImageTransform.Microsoft.AlphaImageLoader(src='myBackground.jpg', sizingMethod='scale')";
```

Hi,

Your advice works here.  Thanks.

```

     <style type="text/css" title="Default-Style">
        body {
        background-image: url("Hibiskus.jpg");
        background-size: cover;
        background-position: center center;
        background-repeat: no-repeat;
        background-attachment: fixed;
        -moz-background-size:cover;
        -webkit-background-size:cover;
        -o-background-size:cover;
        -khtml-background-size:cover;
        margin: 12em 5em;
        padding: 0;
        font-family: "tahoma", Arial, Helvetica, sans-serif;
        font-size: 25px;
        }
...

```

Any entry (considered repeated) can be removed?

Furthermore if the image is too big to fill in the webpage what syntax shall I apply?  TIA

B.R.
satimis

---

