---
title: "Live CD errors"
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by YamNivek on 2006-08-17
Hi,

Ive downloaded the x64 version of Ubuntu but when I boot from the cd error messages appear.


hdb:ide_intr: huh? expected NULL handler on exit
hdb:ide_intr: huh? expected NULL handler on exit
Buffer I/O error on device hdb, logical block 357298

this repeats for about 25-30 mins and then seems to load up the next part. After that the screen loses its signal. I hear the sound I assume is the startup sound but theres no picture.

My pc is Athlon64 3500+, 1Gb Ram, Ati x800xl, 80Gb Hdd.

Ive searched all over these forums but cannot find a definitive answer. Ive heard good things about linux and this distro and wanted to try the live cd to see if its worth acomplete switch from windows.

---

### Post by PriceChild on 2006-08-17
Have you checked the md5 checksum of the image you burnt to cd against the checksum posted on the site next to the download link?

---

### Post by kostkon on 2006-08-17
Yes, just download the md5 checksums file from where you found the iso, and you can use [md5summer]("http://www.md5summer.org/") to do the check in Windows.

Also, have you burnt the iso at a low speed. Try burning the iso again at 4x speed.

You have, first, to be sure that is not a CD problem in order to start thinking about other possible causes.

---

### Post by taurus on 2006-08-17
It sounds to me like you are experiencing a minor problem with Ubuntu regarding your graphic card!  If you plan to install it on your machine, try the alternate CD then because it uses text base instead of GUI...

---

### Post by YamNivek on 2006-08-17
The MD5 checksums were fine.

The thing is I dont really want to install it at the moment. This is the first time ive tried to use linux and I really just wanna try the live cd to see if I like the way it works. Is there a way around this problem?

---

### Post by taurus on 2006-08-17
Get into another console, <Ctrl><Atl>F2, and either configure your X again or edit /etc/X11/xorg.conf and replace whatever "Driver" for it now to "vesa"...

```

sudo dpkg-reconfigure xserver-xorg <-- to configure your X
sudo nano /etc/X11/xorg.conf <-- to edit X

```

---

### Post by YamNivek on 2006-08-17
Cheers for the help but still nothing.

At what point exactly do I have to press <ctrl><alt>F" to get to th e console. I tried it on the screen before it boots (where it gives the options start, start in graphics safe mdoe etc.). That didnt work, so I waitied until the screen turned off and tried it then and still nothing.

---

### Post by w_duggleby on 2006-08-17
> **kostkon said:**
> Yes, just download the md5 checksums file from where you found the iso, and you can use [md5summer]("http://www.md5summer.org/") to do the check in Windows.

Also, have you burnt the iso at a low speed. Try burning the iso again at 4x speed.

You have, first, to be sure that is not a CD problem in order to start thinking about other possible causes.

Hi

     Just downloaded the ISO from Wayne State (slow, but the Indiana download, though much faster on ADSL, stalled out at 58% three times!)  Also downloaded MD5summer as indicated.  The problem is how to "download the md5 checksum file from where you found the iso". Is a puzzlement.

Dugg

---

### Post by taurus on 2006-08-17
> **YamNivek said:**
> Cheers for the help but still nothing.

At what point exactly do I have to press <ctrl><alt>F" to get to th e console. I tried it on the screen before it boots (where it gives the options start, start in graphics safe mdoe etc.). That didnt work, so I waitied until the screen turned off and tried it then and still nothing.
Just wait for it to finish booting and after you hear the drum beats, then press <Ctrl><Atl>F2 (three of them at the same time)...

---

### Post by YamNivek on 2006-08-17
OK just tried it an nothing happened. I think im gonna give up on this linux lark as it just wasnt meant to be. I only wanted to test it out quickly and its turned into 3 days of looking at a black screen and looking on forums and it still doesnt startup. Cheers for your help guys.

---

### Post by taurus on 2006-08-17
Sorry that it doesn't work for you.  I am sure I would probably figure out heads and tails if I sit in front of your computer...  ;)

---

### Post by YamNivek on 2006-08-17
im in no doubt you would!!!! Never mind. I just tried a mandriva distro and although that booted up, i couldnt move the mouse!!!! Talk about bad luck!!

---

### Post by taurus on 2006-08-17
Maybe you want to try out the Fedora Core 5!!!

---

### Post by kostkon on 2006-08-17
> **w_duggleby said:**
> Hi

     Just downloaded the ISO from Wayne State (slow, but the Indiana download, though much faster on ADSL, stalled out at 58% three times!)  Also downloaded MD5summer as indicated.  The problem is how to "download the md5 checksum file from where you found the iso". Is a puzzlement.

Dugg

Hi Dugg,

There must be a file called *md5sums* or something similar in the file list, where you found your iso. 

Just download this file in the same folder you have your iso, and then open it with *md5summer*. If you get a green light for this life, then it's OK.

---

### Post by billylilly on 2006-08-17
This problem is occurring for me also except the error messages refer to hdc rather than hdb.  I too want to see what the operating system is like before installing but am falling down at the first hurdle.

Users like me have no experience of Linux so most of the replies I have seen here go over our heads.

The point is that the Live CD is spewing out error messages when it should simply load up.  The problem is not unique to one user and raises unanswered questions about the product's readiness for implementation.  Is there any way this can be fed back to the Development Team and for the question raised at the outset of this thread to be answered in the form of a revised Live CD?

---

### Post by taurus on 2006-08-17
If you want to file a bug report, you should do that directly instead of here because I doubt if they have time browsing around here...  ;)

---

### Post by Max1130 on 2006-08-17
can anyone help me out with my live cd problem? I'm using dyne : bolic

---

### Post by billylilly on 2006-08-18
I really do believe this is a bug but have no idea how to report it.  Any assistance would be greatly appreciated.

---

### Post by GaryR on 2006-08-20
I had this error when booting from the CD.  My system has three hard drives, and the error occurred on hdd.  Im a noob, but I think that hdd doesn't exist (4th hard drive?) and that it's somehow getting the error on the CD and calling it hdd.  After about twenty such messgaes, the boot succeeded and I was able to install without problems.

---

