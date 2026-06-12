---
title: "Good Bye windows? Installation Help"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by sda80 on 2006-10-16
Hello,
I want to dump windows and give ubuntu a try. There is a small problem though. My laptop does not have a dvd/cd or floppy drive (thinkpad x31). I do however, have a 499MB flash drive and my laptop supports booting from USB.

Can I find a minimal ubuntu image that will fit on my flash drive to boot from? maybe then I can run apt and install other packages like a desktop environment.

Any help would be greatly appreciated.

---

### Post by K.Mandla on 2006-10-16
The server install image is only ~430Mb. That might work for you.

[http://releases.ubuntu.com/dapper/](http://releases.ubuntu.com/dapper/)

Once it's installed you can build a graphical desktop with the *sudo aptitude install ubuntu-desktop * and similar commands. :mrgreen:

---

### Post by daou on 2006-10-16
I guess you could try installing the server version. The iso image is about 430 MB. I haven't done this myself, so I'm not sure what pieces you would have to get with apt afterwards.

---

### Post by sda80 on 2006-10-16
Great! I am dowloading as we speak. DO I simply copy the image over to the USB flash stick? Or do I need to do anything special?

thank you again!

---

### Post by K.Mandla on 2006-10-16
I knew you were going to ask that. :) Things get a little complicated after that. You have to convince the USB stick that it's bootable, and that it should boot the ISO that's on it. 

I have to be honest at this point: I've never had much luck with this. But here are a few pages that might give you some ideas.

[http://www.ubuntuforums.org/showthread.php?t=28948](http://www.ubuntuforums.org/showthread.php?t=28948)
[http://dirk.eddelbuettel.com/quantian/howto_lilogrub.html](http://dirk.eddelbuettel.com/quantian/howto_lilogrub.html)
[http://www.knoppix.net/wiki/Poor-mans_install%2C_grub%2C_PDI](http://www.knoppix.net/wiki/Poor-mans_install%2C_grub%2C_PDI)

Also check out [http://pendrivelinux.com/](http://pendrivelinux.com/) which is more or less dedicated to the idea.

Good luck! ;)

---

