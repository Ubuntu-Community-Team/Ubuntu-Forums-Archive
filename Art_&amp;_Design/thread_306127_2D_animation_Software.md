---
title: "2D animation Software"
date: 2006-11-24
forum: Art &amp; Design
---

### Post by Rodneyck on 2006-11-24
Hi everyone,

I was wondering what everyone recommends for 2D cartooning and/or animation software on linux (running gnome Ubuntu here), either open source, pay or windows running through a Wine port that actually works?

I tried installing Toon Boom studio under Wine and it installed but when I tried to run the software, it replied with a bunch of errors.

Thanks in advance.

---

### Post by smartalecks on 2006-11-24
[Synfig]("http://www.synfig.com/") is pretty good and well developed.
There is also [Ktoon]("http://ktoon.toonka.com/"), which is also very good.

---

### Post by Rodneyck on 2006-11-25
Thanks for the suggestions. 

I have Synfig on my system and will play around with it. Odd though, some of the icons, such as "draw", are not shown on the buttons.  

I installed Ktoon and kept getting an error message and then it just shut down. It appears a lot of people on the boards are having trouble installing this one.

---

### Post by HanZo on 2006-11-27
> I have Synfig on my system and will play around with it. Odd though, some of the icons, such as "draw", are not shown on the buttons.
same problem here. If anyone knows what's causing this... It's pretty akward like this... half the icons are missing, that makes the learning curve much steeper!

---

### Post by ivomans on 2006-11-27
> **HanZo said:**
> same problem here. If anyone knows what's causing this... It's pretty akward like this... half the icons are missing, that makes the learning curve much steeper!

I had the same problem, this message in another thread solved the issue for me: [http://www.ubuntuforums.org/showpost.php?p=1768470&postcount=7](http://www.ubuntuforums.org/showpost.php?p=1768470&postcount=7)

---

### Post by Rodneyck on 2006-11-28
Thanks for the icon post. It will make the learning curve a little shorter. 

Can't wait to see the changes in the Feisty development.

---

### Post by -Phi- on 2006-11-28
The Feisty version of synfig is going through the process to get backported to Edgy. If anyone else can confirm it works with prevu then it might get processed faster.

[https://launchpad.net/products/edgy-backports/+bug/72795](https://launchpad.net/products/edgy-backports/+bug/72795)

- Phi

---

### Post by ivomans on 2006-11-29
I've played somewhat with synfig now but experience several severe bugs. Is it just me that is doing something wrong or do others recognize this as well?

1. When I save a file and open it later on all drawn elements are positioned in the center at x=0,y=0.

2. When I try to render to ffmpeg file the complete synfigstudio crashes.

This on a Kubuntu Edgy system.
When others recognize this behaviour I'll file a bugreport.

---

### Post by -Phi- on 2006-11-29
I also get that behaviour in the Edgy version of synfigstudio and the bug is known to the developer (it has to do with the way the source code was compiled). The Feisty version fixes most of the major bugs (ie. it doesn't crash so much and vectors remember where they're put) but has four fewer tools (don't know why).

The backport from Feisty is now marked "in progress" so I'm not sure a bug report is necessary. If you want the Feisty version now you can use prevu to backport it for your own use until it makes it into the backport repository.

- Phi (on Xubuntu Edgy)

---

### Post by Rodneyck on 2006-11-29
Four fewer tools?  Oh my, there aren't that many to begin with...  :)

---

### Post by -Phi- on 2006-11-29
It is odd. I think "draw", "sketch", "polygon", and "width" are missing. Technically all of those can be managed with the bline tool I guess.

[Screenshot of the Feisty version]("http://phispace.net/lj/Synfig.png")

- Phi

---

