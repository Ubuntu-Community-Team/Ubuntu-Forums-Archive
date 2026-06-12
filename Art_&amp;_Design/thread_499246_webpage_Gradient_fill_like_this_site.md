---
title: "webpage Gradient fill like this site"
date: 2007-07-12
forum: Art &amp; Design
---

### Post by twistedtwig on 2007-07-12
Hi all,

this maybe the wrong place and possible a daft question... but does anyone know how to do a background image gradient fill like this site does please?  I understand I could create an image the size of the page and have that tile across but thats poop.. 

This site fades no matter how long the page is...

I have tried googling it but didn't find anything meaningful (could be BAD googler)!

Thank you for your help

---

### Post by Prefader on 2007-07-12
Looking at the stylesheet, it appears that they've done exactly what you proposed - create a 1px wide background image of the gradient ([http://ubuntuforums.org/imagesorig/ub2/bgrepeat.jpg](http://ubuntuforums.org/imagesorig/ub2/bgrepeat.jpg)) which is tiled across the top of the page, and set the background color of the page to match the bottom color in the gradient.   :)

---

### Post by digitalis_vulgaris on 2007-07-12
<html>
<head>
<style type="text/css">
body{background-color:#000000; background-image:url('a.jpg'); background-repeat:repeat-x}
</style>
</head>
<body>
blah, blah
</body>
</html>

This is exemple how I would do this with CSS. You can place CSS script in head section of page.

**background-color** define color of background in hex (in my case it's white color)

**background-image** define link to the image (in my case it's a.jpg in same directory like html page)

**background-repeat** define tipe of tiling (in this exemple it's horizontal)

**a.jpg** is picture compress on 40% (minimum for good looking web compression). Width is 1px and height is 800px.
If you need horizontal gradient you could use picture w:1024px, h:1px. Set **background-repeat:repeat-y**.

---

### Post by twistedtwig on 2007-07-13
wicked.. Thanks for the help :)

---

