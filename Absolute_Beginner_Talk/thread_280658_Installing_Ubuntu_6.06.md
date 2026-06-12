---
title: "Installing Ubuntu 6.06"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by jlfutari on 2006-10-19
Hello all,
I have downloaded ubuntu-6.06-desktop-amd64 iso , burnt to it to disc and attempted to install it. Upon re-boot the disc is recognised and window comes up , were I select install..... . Ununtu then starts a install process..... a scrolling list of what it is doing with 'OK' at the end of the line. My screen then goes blank, and all I have is a flashing cursor......
So were have I gone wrong?
My system - AMD62x2 CPU, 7600GS video, and Sata hard drve and 1GB memory.

Thanks for any help provided!
:)

James

---

### Post by Sef on 2006-10-19
Did you either download it via bittorrent or do an md5sum to make sure it downloaded right?

How to [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM").

---

### Post by jlfutari on 2006-10-19
I downloaed the iso straight from my ISP....

James

---

### Post by Sef on 2006-10-19
> I downloaed the iso straight from my ISP....


You should an md5sum to make sure it donwload correctly and that the isp copy is good and corrupted.

---

### Post by jlfutari on 2006-10-19
Sef,
Do you have any suggestion for a MD5sum program for windows.

What is the diference between "ubuntu-6.06-alternate-amd64.iso" version "ubuntu-6.06-desktop-amd64" . As a beginner, should I stick to one in prefernece to another?

Thanks for your help!
:)

James

---

### Post by Paul133 on 2006-10-19
The alternate is a text install, while the desktop is a graphical. I'd advise you to use the desktop if you can. If it hangs, use the alternate. Good luck!

---

### Post by jlfutari on 2006-10-19
Ok, I will download the alternate and see what happens
Thanks
:)

James

---

### Post by Bartender on 2006-10-19
I found MD5Summer to be pretty easy and understandable.  Still takes a little scratching around to figure out what to do, but after screwing with it for a while I'm now able to compare the .iso to the original md5 on the website, and compare CD's.  The only twist with checking CD's is you either have to have a known-good one to verify against or have someone send you their results in a .txt file.  Take a look at the website for some basic instruction.
One thing that I don't understand (but it worked anyway) is I asked it to check the md5's on a finished boot CD.  It found about 47 files (I think that's what it was) and checked all the md5's.  I saved the resulting md5 file to the Desktop.  Then I asked md5Summer to "verify" a second burned CD.  This time it found hundreds of files, but it still successfully compared to the original saved files and verified the second CD was OK.
If you end up doing all the above PM me and I'll send you the md5 .txt file from an Ubuntu CD.  The md5 for the .iso, as you know, is on the download website.
EDIT: Whoops, I don't have the results from an AMD download.  Sorry.

---

