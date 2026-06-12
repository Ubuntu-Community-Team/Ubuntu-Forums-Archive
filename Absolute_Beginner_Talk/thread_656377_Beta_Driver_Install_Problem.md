---
title: "Beta Driver Install Problem"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by wasing on 2008-01-02
im installing the beta driver for the HVR-1600 TV Tuner so i went to these support articles on how to do it

[http://www.hauppauge.com/pages/faq/support_faq_hvr1600.html#3a]("http://www.hauppauge.com/pages/faq/support_faq_hvr1600.html#3a")

anyway it was fine up to the point were it said make install (Root)

so i typed make install and i got this

make -C /home/wasing/BETADRIVER/cx18-1a65fdfd182d/v4l install
make[1]: Entering directory `/home/wasing/BETADRIVER/cx18-1a65fdfd182d/v4l'
Stripping debug info from files
-e
Removing obsolete files from /lib/modules/2.6.22-14-generic/kernel/drivers/media/video:
video-buf.ko rm: remove write-protected regular file `/lib/modules/2.6.22-14-generic/kernel/drivers/media/video/video-buf.ko'?

can anyone help me plz. thx in advance

---

### Post by wasing on 2008-01-02
haha figured it out i had to sudo make and then enter my root password

thx for help ubuntu community. now how am i suppose to test to make sure this worked?

ok well i think i got it to work?... not sure but on the website it says totake the fireware from the windows file and put it into the linux driver file but there is no such file.. if anyoe else has succesfully installed this beta driver please help me.

---

### Post by rmills on 2008-01-04
How'd this work out for you?  I'll give it a shot tonight and let you know what I find.

---

### Post by dphirschler on 2008-03-17
I am very interested in this thread.  I have been trying to install the beta driver too and so far have failed.  I am still new to Linux, but I am confident that I can figure it out.  In the mean time, I would like to see people's progress installing this driver.


Darryl

---

