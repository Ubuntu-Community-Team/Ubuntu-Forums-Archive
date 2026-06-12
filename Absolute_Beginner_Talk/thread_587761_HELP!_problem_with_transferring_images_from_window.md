---
title: "HELP! problem with transferring images from windows to ubuntu"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by gschoppe on 2007-10-23
hi guys, bit of a MASSIVE problem with my ubuntu system (feisty 64bit), proFTPd, and my windows system.

I've been trying to get some graphics for a website from my windows box to my Ubuntu box via FTP.  However, whenever I try to send an image file (tried .gif & .jpg) that is of any reasonable size (larger than 16x16 pixels, for example) the transfer times out after about a third of the file has transferred.

not only that, but when i attempted to move the same files to the ubuntu box via my samba share, explorer froze.

in addition, when I transferred the images manually via thumbdrive, although the thumbnails showed, Firefox (on both the windows and linux box) refused to open said images until they were opened in GIMP and saved as a different file format.  It wouldn't work when I re-saved them to the same format.

WHAT THE HECK IS GOING ON??

on the windows side of things, the images are made in Corel Paintshop Pro 10, saved as both jpg and gif and transfer was attempted via FileZilla in Binary mode.


Help?

---

### Post by Jorn.jambers on 2007-10-23
Can't you just move them with a usb thumb drive?

---

### Post by hyper_ch on 2007-10-23
Are they in the same network?

---

### Post by gschoppe on 2007-10-23
same network... html and similar ascii files transfer fine... its only image files that i'v seen the problem with.


as for using a thumb drive, i mentioned in the original post, that although i could copy the file over via thumb drive, and it would show thumbnail and open properly, when it was referenced in an html file, it would not display in firefox or ie on either machine intil i changed file types using gimp. (.jpg to .gif or vice versa... obviously i also had to change the html to match)

I need this to work, as FTP is necessary for reasonable remote file  control on my network.

---

### Post by irish_flu on 2007-10-23
OK, let me make sure I've got this.  The FTP server is on the Ubuntu box, and the client is on the Windows box, right?

What client are you using for FTP transfer on the Windows box? I have found the (built-in) command-line client to be very robust.  On the other hand, Internet Explorer is a very bad FTP client.

Do you get any errors when the files stop copying?  You might try a different client; I like "Core FTP".  It's not free as in speech, but it's free as in beer.

---

### Post by gschoppe on 2007-10-23
I'm using fileZilla, so its a lot better than i.e.  The error is a timeout, but it always occurs about 1/3rd of the way through the image.  Also tried transfer via i.e's ftp... no dice (no error message, it just locks up).  The same issue, however, is seen when trying to copy the image to my samba share (on the same ubuntu box).

for debugging purposes, here's one of the simplest images that will not transfer: [http://www.send-file.com/1CB3E7E71CAD22B4]("http://www.send-file.com/1CB3E7E71CAD22B4")

---

### Post by irish_flu on 2007-10-23
That's weird.  You're not by any chance dealing with a full disk partition, are you?

---

### Post by hyper_ch on 2007-10-23
Tried SSH/SCP?

(1) install ssh server
```

sudo apt-get install openssh-server

```

(2) download winscp
[http://www.winscp.com](http://www.winscp.com)

(3) connect
-> use your ubuntu login/pwd

(4) transfer files ;)

---

### Post by gschoppe on 2007-10-23
irish flu : not full partition, got 400gb left

hyper_ch: Thanks for the suggestion, but FTP is a sticking point with me... I absolutely need FTP access to work properly.

any more ideas... It seems to me that rather than an FTP issue, this must be an issue with Ubuntu reading my picture files, due to the problem showing in Samba too.

can anyone try the file I uploaded and see if it opens normally on ubuntu, or if you can recreate the issue?

---

### Post by hyper_ch on 2007-10-24
SSH/SCP is the same as FTP... just with encryption (sort of)

No need to configure a server...

---

