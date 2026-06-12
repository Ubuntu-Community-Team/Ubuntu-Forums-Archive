---
title: "*I'm Confused about Shell?***"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by Luthy on 2006-08-31
Went on this site:
[http://jalbum.net/download3.jsp#linux](http://jalbum.net/download3.jsp#linux)

I downloaded the .bin file to my desktop. And here are the instruction dowloadload it i guess:

Instructions

    * After downloading open a shell and,  cd to the directory where you downloaded the installer.
    * At the prompt type:  sh ./JAlbuminstall.bin 

But im stupida and am confused. Can someone give me a step by step of this? ive never had to do this before. Thanks.

---

### Post by aysiu on 2006-08-31
1. Make sure you have extra repositories enabled--you'll need those to install Java:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

2. Install Java by pasting this command in the terminal: ```
sudo aptitude update && sudo aptitude install j2re1.4
```

3. Now, you can install your JAlbum thing: ```
wget -c http://www4.jalbum.net/download/6.5/Linux/NoVM/JAlbuminstall.bin
chmod +x JAlbuminstall.bin
sh ./JAlbuminstall.bin
```

P.S. Have you thought about just using F-Spot and an FTP program?

---

### Post by Luthy on 2006-08-31
Tried the code stuff & doesnt seem to work. Am Using F-Spot now. Thanks!

---

### Post by andlinux21 on 2006-09-02
If you installed java then open up an xterm window
cd /home/<your name here>/Desktop
then excute the sh ./JAlbuminstall.bin

that should work for you to run the program when its completed with the install go to the JAlbum folder in an xterm window and 
type sh JAlbum:D

---

