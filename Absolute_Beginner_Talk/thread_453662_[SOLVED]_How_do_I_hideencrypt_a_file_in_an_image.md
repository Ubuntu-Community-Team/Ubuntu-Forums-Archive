---
title: "[SOLVED] How do I hide/encrypt a file in an image?"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by rouge568 on 2007-05-24
How would I go about hiding a file in an image. I first heard about it in *Ender's Game* and want to know how to do this as my final transfer from Windows to Ubuntu.
e.g. get secretfile.txt to name as prettypicture.jpg, and display otherprettypicture.jpg  with an encryption, so none's the wiser while I hide my passwords in plain sight as my backgrounhd.

---

### Post by vtel57 on 2007-05-24
[http://www.brunolinux.com/10-General_Info/Hidden_Messages.html](http://www.brunolinux.com/10-General_Info/Hidden_Messages.html)

Have FUN! :)

---

### Post by starcraft.man on 2007-05-24
Ah, I just happened across this last week, was wondering how to do it myself. I believe this is the command ya want, pretty simple in the terminal.

```
cat picturefile.jpg rarfile.rar > newfilethatisNOTtherarfileorpicturefile.jpg
```

The first object (the jpg in my example) is what your hiding inside the second object (in my case the rar) and the third object is the new one created after, you can name it anything. Then just reverse to get it out. I hope thats right... haven't actually done much hiding, no one else comes on my comp >.>.

Edit: there ya go, vtel gave ya a bit more detail. Mines just a basic one step process :).

---

### Post by ArieT on 2007-05-24
This kind of encryption is called steganography. Steghide is able to do this. You can install it with:
apt-get install steghide
and use it with
steghide embed -cf picture.jpg -ef secret.txt
and read the [documentation](http://steghide.sourceforge.net/documentation.php).

---

### Post by starcraft.man on 2007-05-24
> **ArieT said:**
> This kind of encryption is called steganography. Steghide is able to do this. You can install it with:
apt-get install steghide
and use it with
steghide embed -cf picture.jpg -ef secret.txt
and read the [documentation](http://steghide.sourceforge.net/documentation.php).

Cool, I didn't know it was on Ubuntu... used that a bit in windows. I go and get now :D. And yes your right, thats the big fancy pants word :p.

---

### Post by Jussi Kukkonen on 2007-05-24
starcraft.man, the point of steganography (hiding data in other dat, often in an image) is to **a)** encrypt data **b)** hide any signs of encryption. Your method fails both points. :)

apt-cache shows that Ubuntu has these steganography tools available:
> outguess - Universal Steganographic tool
samhain - Data integrity and host intrusion alert system
snowdrop - plain text watermarking and watermark recovery
stegdetect - Detect and extract steganography messages inside JPEG
steghide - A steganography hiding tool
xsteg - Graphical frontend to stegdetect


---

