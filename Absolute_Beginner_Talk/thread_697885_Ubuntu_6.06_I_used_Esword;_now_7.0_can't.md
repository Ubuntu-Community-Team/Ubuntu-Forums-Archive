---
title: "Ubuntu 6.06 I used Esword; now 7.0 can't?"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by samcrees on 2008-02-15
Hello; like I said:  On an older machine I installed Ubuntu 6.06 live CD and then started downloading stuff and mostly wanted my books and ESWORD to work.  I was new to Linux more or less a fried in the dept. of ED. told me Unbuntu was the best and most user friendly. Well, for some reason all of it worked well; even all of my music worked without error.  Of course I had to find the right player to get the most out of the music.

But, I still have the other machine and it was old, slow, and small HD so when my main machine Win XP decided to crash, and I added a drive and installed Ubuntu CE, which I ordered to get the best of the best in Linux Christian, and low and behold ESWORD did not work.  I tried some of the things I saw on the various forums,I got WINE to work and downloaded Esword but no words just GUI frontend,  and I even went as far as completely starting over with my original Unbuntu 6.06 live CD and nothing seems to change anything. So I am at a loss, why work just once and never again, unless ESWORD itself has changed some way.

I am getting ready to email Rick Myers and see if he made any changes.  He has emailed me before on questions, sometimes it may be a week or so before he answers, but he answers.    I was told he really does not like FREE Open Source; but folks that is a rumor and not a known fact.  I know he is good at what he has done, and to get my Esword I will ("If I must") go back and re-bild or add another WINDOWS "VIRUS" OS drive and start over just to get it.  I did try the Gnome Sword and sorry but it is not even close to what I can do with Esword.   Esword also worked flawlessly with my Open Office as well, both on the Linux machine and in Win XP.  

But, alas; now I am without my studies.   I also use LOGOS software and have not any idea if they (very expensive, and hardly ever updated)  have entered the wonderful world of Linux.

well, need to go , and I hope others have an idea of why it worked once and not now.

---

### Post by dcstar on 2008-02-15
> **samcrees said:**
> Hello; like I said:  On an older machine I installed Ubuntu 6.06 live CD and then started downloading stuff and mostly wanted my books and ESWORD to work.  I was new to Linux more or less a fried in the dept. of ED. told me Unbuntu was the best and most user friendly. Well, for some reason all of it worked well; even all of my music worked without error.  Of course I had to find the right player to get the most out of the music.

But, I still have the other machine and it was old, slow, and small HD so when my main machine Win XP decided to crash, and I added a drive and installed Ubuntu CE, which I ordered to get the best of the best in Linux Christian, and low and behold ESWORD did not work.  I tried some of the things I saw on the various forums,I got WINE to work and downloaded Esword but no words just GUI frontend,  and I even went as far as completely starting over with my original Unbuntu 6.06 live CD and nothing seems to change anything. So I am at a loss, why work just once and never again, unless ESWORD itself has changed some way.

I am getting ready to email Rick Myers and see if he made any changes.  He has emailed me before on questions, sometimes it may be a week or so before he answers, but he answers.    I was told he really does not like FREE Open Source; but folks that is a rumor and not a known fact.  I know he is good at what he has done, and to get my Esword I will ("If I must") go back and re-bild or add another WINDOWS "VIRUS" OS drive and start over just to get it.  I did try the Gnome Sword and sorry but it is not even close to what I can do with Esword.   Esword also worked flawlessly with my Open Office as well, both on the Linux machine and in Win XP.  

But, alas; now I am without my studies.   I also use LOGOS software and have not any idea if they (very expensive, and hardly ever updated)  have entered the wonderful world of Linux.

well, need to go , and I hope others have an idea of why it worked once and not now.

I presume this is the package you actually want:

**gnomesword**

---

### Post by darinh on 2008-02-17
Hi,

The GUI front-end with no words is a result of not overriding the riched20.dll in step 4, but go thru all the steps to get your dictionaries working too.  I'm still fairly inexperienced with linux, but I got e-sword version 7.9.5 to work on ubuntu 7.10 about 10 minutes ago following instructions from this link.  I don't know much about CE, but expect that these instructions will help you.

[http://ubuntuforums.org/archive/index.php/t-151708.html](http://ubuntuforums.org/archive/index.php/t-151708.html)

(I've updated his instructions a bit according to my recent experience with the newer version of esword... view the link for original instructions.)

1) Make sure that you have your wine updated.
2) You need to download the newest version of esword (which right now it is setup795.exe) and save it or move it to your desktop
3) Type in your Terminal "wine "/home/accountname/Desktop/setup795.exe""
*put your account name where it says accountname
4) You need to override the riched20.dll so in your Terminal type "winecfg" and go to the library tab. Type in riched20.dll under "New override for Library" and press apply.
5) Now that riched20.dll is listed, edit it and select "native" only.
6) You'll need a windows machine and a thumb drive or some other means for transferring a directory from one computer to another for this.  Go to a windows computer that has e-sword installed with all of the Bibles and commentaries you want.  Copy the e-sword directory from "c:\program files\" and put it on your thumb drive.
7) If you copy the e-sword directory in place now, you will get all of your Bibles and commentaries loaded, but the dictionaries still won't work, so you'll have to copy a dll from "c:\windows\system32" called msls31.dll to your thumb drive as well (does not go in e-sword directory).
8) Copy the e-sword directory from your thumb drive to "/home/accountname/.wine/drive_c/Program Files/". Replace all.
*put your account name where it says account name
9) Copy msls31.dll to "/home/accountname/.wine/drive_c/windows/system32/". (If dictionaries still don't work, you might have to override msls31.dll with winecfg just like riched20.dll)
*put your account name where it says account name

I hope that helps. ^_^  I really can't provide support for this advice... I, honestly, got really lucky with this install.  So if it doesn't work, you can send me pm's and I'll check them out, but I'll probably respond with, "dude, i have no idea."

---

### Post by Faud on 2008-02-17
also as a heads up the guy that designed the CE flavor had to skip the gusty release and go straight to hardy heron. They are going to have a E-sword installer built into the hardy heron version of Ubuntu CE though.

---

### Post by david_kt on 2008-02-18
> **samcrees said:**
>  well, need to go , and I hope others have an idea of why it worked once and not now.

Most likely it is due to wine version upgrade. You need to install the old wine you ever used before, not the current one. But I have made an instruction to install esword, complete with addons. Please try it and let me know if you face problem:

[http://ubuntuforums.org/showthread.php?t=404042]("http://ubuntuforums.org/showthread.php?t=404042") 

DK

---

