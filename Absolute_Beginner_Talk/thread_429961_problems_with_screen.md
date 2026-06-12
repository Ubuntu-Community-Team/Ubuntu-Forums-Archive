---
title: "problems with screen"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by Paul Barnett on 2007-05-01
I just upgraded to FF and am using nvida drivers. When I restarted my computer today everything on the screen 
was about 4 times a large as it should be. I have tried adjusting in settings but nothing I do seems to work. Please help.file:///home/paul/snapshot1.jpg

---

### Post by teddybairs1 on 2007-05-01
Paul, your snapshot didn't upload.

My wife had the same problem with her computer at one time. Are you using the video drivers which came with Feisty or are you using the restricted drivers? If you can, go to System -->Restricted Drivers Manager and see if you can't download and install the proprietary drivers for your Nvidia card. I suspect this should fix your problem.

---

### Post by Paul Barnett on 2007-05-01
I am using restricted drivers. I used automatixs to download invidia.

---

### Post by Paul Barnett on 2007-05-01
Here is a screen shot of the problem.

---

### Post by teddybairs1 on 2007-05-01
Ok, you're running Kubuntu. The KDE desktop.
Is it just the desktop that does this or is everything out of proportion? Is it usable or no?

---

### Post by bobplano on 2007-05-01
check the resolution. you could try editing your xorg.conf or typing in
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Paul Barnett on 2007-05-01
Thanks to Bobplano. It worked.

---

