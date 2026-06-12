---
title: "My CD fails to mount. Please help. Anyone"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by CCNA_student on 2007-12-09
I am having trouble getting Ubuntu 7.10 to read some of my discs. I can stick in a DVD and it plays, or I can put in the Ubuntu disc. But if I try to put in other discs that I know work
(They worked on Windows XP and Ubuntu 7.04) I receive the error message in the picture I attached. Can anyone explain how to fix this or at least why this is happening?

---

### Post by Orestes on 2007-12-09
Are they music "discs"? DVD "discs"? discs with data on?

---

### Post by CCNA_student on 2007-12-09
The discs that refuse to mount are data discs. Some I even burned using Ubuntu 7.04.

---

### Post by CCNA_student on 2007-12-09
Please help.

---

### Post by Orestes on 2007-12-09
Have you tried to mount them manually?

sudo mkdir /media/cdtmp
sudo mount /dev/hdc /media/cdtmp

Where /dev/hdc is the device corresponding to your CD-ROM drive. To find out what the device is called, type:

dmesg | grep [Cc][Dd]\-[Rr]



**BE VERY CAREFUL USING SUDO!!!** You can break your system! You have been warned.

---

### Post by CCNA_student on 2007-12-09
I tried your command and it said  "cannot create directory `/media/cdtmp': File exists". Is there another way?

---

### Post by Orestes on 2007-12-09
that means that you've done it once, then tried to do it again. If you've created the directory, you don't need to do it again. go on to the next line now.

---

### Post by CCNA_student on 2007-12-09
I then get the message "mount: No medium found". I do have the disc in the system.

---

### Post by Orestes on 2007-12-09
Heh. You have two cdrom drives then, yeah?

---

### Post by CCNA_student on 2007-12-09
I tried again, here is what I got.

---

### Post by CCNA_student on 2007-12-09
I do have two drives, but I do not use the DVD writer because it no longer functions.

---

### Post by Orestes on 2007-12-09
You've a typo. You typed /de**b**/hdc instead of /de**v**/hdc

Did you do the dmesg command like I asked before? *This is important*. It might turn out that your drive is called /dev/hdd or similar.

---

### Post by CCNA_student on 2007-12-09
I did the dmseg thing and typed dev instead of dvb, no change.

---

### Post by Orestes on 2007-12-09
Hmm. You are quite sure the disc is in the right drive? (I don't mean to be patronising)

---

### Post by CCNA_student on 2007-12-09
Here is what I get.

---

### Post by CCNA_student on 2007-12-09
The disc is in the right drive. Only one of them opens up at all.

---

