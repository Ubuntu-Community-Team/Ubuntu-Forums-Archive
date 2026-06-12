---
title: "Internet Explorer Replacement"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by chrisf79 on 2007-04-09
Greetings,

I am a Realtor and our local MLS system forces us to use Internet Explorer.  Basically, when you go to log in, your system checks to make sure you have Adobe Acrobat installed, checks your browser version, etc.  If any test fails, it will not allow you to log on.  Every test passes except for when it says I'm using Firefox on Linux and won't allow me to log in.

Is there a way to run Internet Explorer in Linux?  I tried using Wine but couldn't get it to work.

Any help would be GREATLY appreciated!

---

### Post by machoo02 on 2007-04-09
You could use [ies4linux]("http://www.tatanka.com.br/ies4linux/page/Main_Page"), which is script that will help you install IE through WINE.

---

### Post by dwblas on 2007-04-09
Try Firefox's user agent switcher.  Install and click on Tools, select and change to IE
[https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

---

### Post by x-ray vision on 2007-04-09
Maybe by spoofing the user agent string?:
[http://johnbokma.com/mexit/2004/04/24/changinguseragent.html](http://johnbokma.com/mexit/2004/04/24/changinguseragent.html)

See also PrefBar toolbar:
[http://prefbar.mozdev.org](http://prefbar.mozdev.org)

---

### Post by Aurora Borealis on 2007-04-09
> **chrisf79 said:**
> Greetings,

I am a Realtor and our local MLS system forces us to use Internet Explorer.  Basically, when you go to log in, your system checks to make sure you have Adobe Acrobat installed, checks your browser version, etc.  If any test fails, it will not allow you to log on.  Every test passes except for when it says I'm using Firefox on Linux and won't allow me to log in.

Is there a way to run Internet Explorer in Linux?  I tried using Wine but couldn't get it to work.

Any help would be GREATLY appreciated!

Depending on the Ubuntu version you're running, you may already have ies4 ies4linux available.

---

### Post by aysiu on 2007-04-09
> **Aurora Borealis said:**
> Depending on the Ubuntu version you're running, you may already have ies4 ies4linux available.
Do you have a link that backs that up? I've never heard of such a thing, and there's no *ies4linux* on [http://packages.ubuntu.com](http://packages.ubuntu.com)

---

### Post by chrisf79 on 2007-04-09
The IEs4Linux thing worked!  Only bad thing is that it doesn't see Adobe Acrobat installed.  ANy way of getting around this?

The Mozilla User Agent Switcher almost works.  It allows me to log in but the submit button (javascript button) just clicks and doesn't go anywhere.

---

### Post by Wiebelhaus on 2007-04-09
If all plugin's for fire fox fail , try codeweavers crossover linux which is pay for or wine which is free.


wait.......

Wine supports IE right?

---

### Post by Aurora Borealis on 2007-04-09
> **aysiu said:**
> Do you have a link that backs that up? I've never heard of such a thing, and there's no *ies4linux* on [http://packages.ubuntu.com](http://packages.ubuntu.com)

Yes-thank you for asking. I should have posted it in the first place. It's the second-to-last paragraph.

[http://www.whatwouldjesusdownload.com/christianubuntu/news/2007/03/ubuntu-ce-v22-edgy-released-march-15.html](http://www.whatwouldjesusdownload.com/christianubuntu/news/2007/03/ubuntu-ce-v22-edgy-released-march-15.html)

---

### Post by aysiu on 2007-04-09
> **Aurora Borealis said:**
> Yes-thank you for asking. I should have posted it in the first place. It's the second-to-last paragraph.

[http://www.whatwouldjesusdownload.com/christianubuntu/news/2007/03/ubuntu-ce-v22-edgy-released-march-15.html](http://www.whatwouldjesusdownload.com/christianubuntu/news/2007/03/ubuntu-ce-v22-edgy-released-march-15.html)
Ah, that makes sense. FYI: Christian Edition isn't an official Ubuntu release, even though it uses the word *Ubuntu* as part of its name.

---

### Post by Aurora Borealis on 2007-04-09
> **aysiu said:**
> Ah, that makes sense. FYI: Christian Edition isn't an official Ubuntu release, even though it uses the word *Ubuntu* as part of its name.

Oh, I didn't know that; that would explain why the package wasn't listed on the Ubuntu page.

---

