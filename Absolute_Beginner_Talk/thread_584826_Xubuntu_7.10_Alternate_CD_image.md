---
title: "Xubuntu 7.10 Alternate CD image"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by scofff on 2007-10-21
Very weird, I can download and burn "good" image from any other image file (like xubuntu desktop or kubuntu), but when downloading and burning xubuntu 7.10 alternate dist image file all the sudden it finds itself corrupted. Tried to download again and checked MD5 - everything seems to be ok, and still corrupted CD. 

Downloaded from [http://cdimage.ubuntu.com/xubuntu/releases/gutsy/release/](http://cdimage.ubuntu.com/xubuntu/releases/gutsy/release/) about 36 to 24 hours ago.

It must sound as stupid question, but can you confirm that the image file is good?

...
Sco

---

### Post by Sef on 2007-10-21
Sometimes it takes a few times before you get a good image.   Once I had to download about 6 times before I got a good image.

---

### Post by scofff on 2007-10-21
MD5 is matching

...
Sco

---

### Post by spylvas on 2007-10-21
I have same problem. image it self seems to be fine, but once I burned it is broken. I used slowest possible speed for burning.

---

### Post by bodhi.zazen on 2007-10-21
I have had this problem before, and sometime I can solve it by changing burning software.

IMO K3B is the most reliable (although you will install kde libs as dependencies).

---

### Post by 70phr3 on 2007-10-25
I have not been able to burn a successful gutsy image since gutsy started.  I have tried several burning programs and checked the MD5s and nothing seems to work.  This is really getting to be frustrating.

---

### Post by dptxp on 2007-10-25
Use Bittorrent.
Download and install bittorrent in Windows.
Download the corresponding torrent file from Ubuntu
download page.
Open the torrent file in bittorrent.
Point the new iso file to old iso if you have already downloaded, or else just save anywhere.
Corrupt iso shall get corrected.
And if are getting new iso it is unlikely to be corrupt.

---

### Post by 70phr3 on 2007-10-25
The iso is perfect.  The iso works fine when installing onto a virtual machine in Virtualbox.  When the iso is burned, I can't get it to install anywhere.  Whether its a real pc or a virtual machine it doesn't matter.  A burned Gutsy image just will not work.

---

### Post by dptxp on 2007-10-26
> **70phr3 said:**
> The iso is perfect.  The iso works fine when installing onto a virtual machine in Virtualbox.  When the iso is burned, I can't get it to install anywhere.  Whether its a real pc or a virtual machine it doesn't matter.  A burned Gutsy image just will not work.

Are you burning using 'burn image' command ? Many destroy CDs by either unzipping the iso or burning iso as Data CD.

---

### Post by 70phr3 on 2007-10-26
I have tried right clicking and "Write to disk", using Gnome Baker, K3B, Nero (Windows) and even just plain cdrecord.  Nothing works.  Also, I have tried on my desktop at home, at work AND my laptop.

---

### Post by dptxp on 2007-10-26
> **70phr3 said:**
> I have tried right clicking and "Write to disk", using Gnome Baker, K3B, Nero (Windows) and even just plain cdrecord.  Nothing works.  Also, I have tried on my desktop at home, at work AND my laptop.

Use 'BURN IMAGE' command only. Select the iso file when prompted.
This is important, this is the only way top burn iso images to CD.
You can download and use Infrarecorder in Windows. K3B is fine in Linux.

---

### Post by 70phr3 on 2007-10-26
Maybe you don't understand.  I am burning the image.  It boots fine, but doesn't pass the cd check.  Also ms5sum fails on the cdrom every time.  Md5sum on the iso is perfect.

---

### Post by dptxp on 2007-10-26
> **70phr3 said:**
> Maybe you don't understand.  I am burning the image.  It boots fine, but doesn't pass the cd check.  Also ms5sum fails on the cdrom every time.  Md5sum on the iso is perfect.

If the iso is OK and CD check fails, it obviously is a CD burning problem.
Bad CD, bad CD burner, or wrong command for burning.

---

### Post by geomorillo on 2008-04-17
Well your logic is not totally correct


"the iso is OK and CD check fails, it obviously is a CD burning problem.
Bad CD, bad CD burner, or wrong command for burning."


Couldnt be that one file in the iso is corrupted


Obviously, the iso is ok but the cd chek fails because one file or more inside the iso are corrupted

ive tested this and i think that the iso alternate xubuntu 7.10 inside the servers, downloads ok but it contains corrupted files

---

