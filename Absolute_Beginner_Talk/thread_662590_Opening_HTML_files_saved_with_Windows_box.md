---
title: "Opening HTML files saved with Windows box"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by HuBaghdadi on 2008-01-09
Hi.
I have some HTML files that I saved them on a Windows box with IE and FireFox.
When trying to open these HTML files under Ubuntu, No images, JavaScript files, CSS files and other dependencies
are being used by those HTML files.
Any ideas how to fix this?
Thanks.

---

### Post by Pevichaey5 on 2008-01-09
you need to have the pictures to display them in a html file in a web browser

a website uploads all pictures, text css,  things to your computer

---

### Post by talsemgeest on 2008-01-09
In other words, you need to have the folder that was created with the html file to view the saved web page.

---

### Post by HuBaghdadi on 2008-01-09
I have HTML files and their related folder side by side...

---

### Post by frup on 2008-01-09
open the html file and find an <img src="" /> tag and see what the path to the images is.

---

### Post by Paqman on 2008-01-09
How are you opening the html file? With Firefox? A text editor? An html editor?

---

### Post by Pevichaey5 on 2008-01-09
the important bit you need is the pictures that the index file was displaying, and make sure that they are where the index html file says they are

---

### Post by HuBaghdadi on 2008-01-09
I use FireFox

---

### Post by HuBaghdadi on 2008-01-09
src attribute of img tag includes folder name.

---

### Post by frup on 2008-01-09
and is that still the correct path?

---

### Post by HuBaghdadi on 2008-01-09
Please note that I have [NoScript]("https://addons.mozilla.org/en-US/firefox/addon/722") FireFox plugin installed.
I allowed scripts to run on these HTML pages, but the same thing.
AFAIK, NoScript doesn't blocks images and CSS files.

---

### Post by rkd on 2008-01-09
It might help if you could copy the whole src attribute of the img tag and paste it here so we can look at it. Or maybe the whole img tag.

---

### Post by Paqman on 2008-01-09
> **HuBaghdadi said:**
> 
AFAIK, NoScript doesn't blocks images and CSS files.

It doesn't. I'd put money on the paths being incorrect. Open your html file in a text/html editor and check the paths manually. 

Chances are this problem is due to how the designer wrote the page, not anything to do with the OS.

---

### Post by HuBaghdadi on 2008-01-09
Sadly, my laptop isn't next to me :(
But do you know?
I tried to open those saved HTML files on Windows with IE and I got the same result!
Yep, it seems there is some thing wrong with those HTML files.

---

