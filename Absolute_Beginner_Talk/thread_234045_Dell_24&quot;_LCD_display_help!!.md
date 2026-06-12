---
title: "Dell 24&quot; LCD display help!!"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by matchboxlord on 2006-08-10
I have just installed ubuntu 6.06 and I have a 24in dell LCD.  My question is how to change the default resolution to 1920x1200 under ubuntu? Do I have to install the Nvidia driver first? I have a Nvidia 7800GT by the way.  Googled this a little bit, haven't found a solution yet.  Any help is greatly appreciated! Thanks.

---

### Post by Indras on 2006-08-10
You need to gooogle the model of your LCD and get the exact specs... there's usually a pdf file somewhere with your horizontal and vertical refresh rates.  Put those values into your /etc/X11/xorg.conf file under the Section "Monitor".  Your HorizSync and VertRefresh start with default, generic monitor settings, which don't usually support resolutions over 1024x768.

This will make higher resolution settings available.  If 1920x1200 still isn't available, I would try installing the NVidia drivers.

---

### Post by matchboxlord on 2006-08-10
thanks, I will try this out.

---

### Post by spiral777 on 2006-08-11
Try this page:

[Dell 24' Monitors Manual Page]("http://support.dell.com/support/systemsinfo/documentation.aspx?c=us&l=en&s=gen&~cat=3&~subcat=101")

Just select which one you have, pick your language and you should be able to find any info you need! :D

---

### Post by Hubris2 on 2006-11-10
I've installed the Nvidia X-server....it correctly detects my video and monitor, however it won't offer me anything higher than 1600x1200 although I know 1920x1200 is the actual limit.  I've tried manually editing the xorg.conf and my available options don't change.  Any more suggestions?

---

### Post by digby on 2006-11-11
If you run 'sudo dpkg-reconfigure xserver-xorg' it will give you the option to add that resolution at some point.  If it asks you any questions that you don't know the answer to (and it asks some obscure things) just hit enter to take the default answer.

It will get to a point where it gives you a list of resolutions.  Select 1920x1200 and unselect the rest. Finish the process, restart X, and you should be good to go.

---

### Post by Hubris2 on 2006-11-11
There are so many helpful folks around here....that's exactly the advice that I was given in another thread...and it worked great.  Thanks!

---

