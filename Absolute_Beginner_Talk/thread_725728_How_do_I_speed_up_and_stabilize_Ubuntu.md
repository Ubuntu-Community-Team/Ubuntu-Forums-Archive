---
title: "How do I speed up and stabilize Ubuntu?"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by kennster on 2008-03-16
ok i have switched from vista to this ubuntu and whell ever thang i do now i haft to force quit and its realy slow at first it was fine and dandy idk it might be something i did so i was wondering some metheds to help speed it back up and not have programs crash as much... any advice?

---

### Post by baddog144 on 2008-03-16
Hmm... strange problem... perhaps some basic specs? That would help alot 

Thanks alot :D

---

### Post by Laser Dude on 2008-03-16
It might help people if you posted something more specific.  What version of Ubuntu are you running?  Which programs are you trying to use?  What are your system specs?

---

### Post by DarinB on 2008-03-16
well, so far i have not heard complaints like this.
i wonder if there are more serious problems.
if the poster could be clearer it would be helpful, maybe then a solution can be found.
If that is not possible just reload windows and be happy.

---

### Post by leadhead on 2008-03-16
That is a pretty broad statement. I have worked on alot of operating systems Linux/Unix in small amounts but on alot of different types (Solaris, SCO, Redhat) a bit of os9 and every windows version ever made.

All of them have their strengths and weaknesses. I am a noob to with Ubuntu, but it is pretty fast, faster than our vista laptops at work which have enough hardware to run the latest video games. I am running Ubuntu on a 1.4ghz celeron deck...and it is faster.

---

### Post by kennster on 2008-03-16
> **DarinB said:**
> well, so far i have not heard complaints like this.
i wonder if there are more serious problems.
if the poster could be clearer it would be helpful, maybe then a solution can be found.
If that is not possible just reload windows and be happy.

sry for slow respons 

specs are:
OS =ubuntu  gusty
CPU =3.4gig amd dule core
Ram =2gig DDR2
HDD1 =WD raptor 10,000rpm 120gig
HDD2 =WesterDigtal 7200rpm 500gig

all in stata and Video card is a 7800 nvidia gforce

problem is when running lets say wow with wine 
if i go on like myspace it will eather not load the page till i x outta wow 
and firefox always crashes and has a Npviwer.bin or something that pops up after it and has to be force quit  and ill get a few of them running in System moitor any idea if u need more info ill be glad to try and provide

---

### Post by housam on 2008-03-16
Can you type in the terminal 
```
sudo fdisk -l
```
and post the result where -l is a small L

---

### Post by bumanie on 2008-03-16
I suspect you may not have installed all the codecs necessary and you will have to check that you've enabled the ubuntu repositories also. Go to  System --> Software Sources --> ensure the first 4 boxes are ticked then open third party software tab and tick anything that is there. Just out of interest are you being informed of updates (orange box with white star, top right of screen).

---

### Post by housam on 2008-03-16
Also look at [[COLOR="Red"]_this thread_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=712625") it may help.

---

### Post by drubin on 2008-03-16
I used to have a similar issue, Did you install the drivers for your Nvidia graphics card?? that might help

---

### Post by kennster on 2008-03-16
> **bumanie said:**
> I suspect you may not have installed all the codecs necessary and you will have to check that you've enabled the ubuntu repositories also. Go to  System --> Software Sources --> ensure the first 4 boxes are ticked then open third party software tab and tick anything that is there. Just out of interest are you being informed of updates (orange box with white star, top right of screen).

no im not for some reasion it stop showing up

---

### Post by kennster on 2008-03-16
> **housam said:**
> Can you type in the terminal 
```
sudo fdisk -l
```
and post the result where -l is a small L



Disk /dev/sda: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6a382358

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       17495   140528556   83  Linux
/dev/sda2           17496       18241     5992245    5  Extended
/dev/sda5           17496       18241     5992213+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00043c9a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

---

### Post by housam on 2008-03-17
I see that you have a very good partition table, no conflects . nothing wrong with your hard desk.

If you have compiz or beryl try to remove them . they sometimes do this problem.

---

### Post by Xiong Chiamiov on 2008-03-17
Be aware that WoW (or anything running through Wine) will most likely not run as fast as it would in Windows (depending on how much crap your Windows installation is running).  As far as Firefox goes, is it a default install, or have you installed extra plugins?  When people write extra code to add to it, you can lose a lot of performance if they don't know what they're doing.  Also try out Kazehakase and Opera if you don't need all the addon compatability that Firefox has.  Just because it's the most popular doesn't mean it's the best for you.
Of course, there most likely are other issues going on (like video card drivers), but I thought I'd touch this.

---

### Post by kennster on 2008-03-17
> **housam said:**
> I see that you have a very good partition table, no conflects . nothing wrong with your hard desk.

If you have compiz or beryl try to remove them . they sometimes do this problem.


TY i worked hard makeing shure they partition good :D

and also i do run compiz 

> Be aware that WoW (or anything running through Wine) will most likely not run as fast as it would in Windows (depending on how much crap your Windows installation is running). As far as Firefox goes, is it a default install, or have you installed extra plugins? When people write extra code to add to it, you can lose a lot of performance if they don't know what they're doing. Also try out Kazehakase and Opera if you don't need all the addon compatability that Firefox has. Just because it's the most popular doesn't mean it's the best for you.
Of course, there most likely are other issues going on (like video card drivers), but I thought I'd touch this.

i do know this and when i origanly ran it it wokred fine... whell didnt lag and looked as good as it can bein ran threw and emulater lol.. but yes FF was defalt good idea about Opera and Kazehakase ive been tryin to member the name of it cuz i like plane and simple less = more in my eyes but would . new themes cause this problem also? its just small little program crashes when runnning more then 1 program. and i was scard NPvider.bin was a virus i was like OMG WTFM8 so im guessin im good on that

---

### Post by Rmantingh on 2008-03-17
Following thread about npviewer.bin may be of interest although no solution is offered:-

[http://ubuntuforums.org/showthread.php?t=647961](http://ubuntuforums.org/showthread.php?t=647961)

Although I must say I'm running Xubuntu 7.10 64 bit and have had no problems with Flash and Firefox.

---

### Post by savagenator on 2008-03-17
here is my solution through much troubleshooting.

I have found that the computer slows down when running a lot of web pages that use heavy flash, especially in 64-bit ubuntu with nspluginwrapper. Please tell us if you are running 64-bit version of ubuntu.

Also, a solution might be to update your flashplugin-nonfree or run firefox through wine

AND if you are running a 7800GT nvidia card, then it may be very weird in ubuntu. Mine always is a (female dog) to setup and sometimes run.

---

### Post by handydan918 on 2008-03-17
Just wanted to second the motion made by a previous poster that you look at your video card drivers. Running an nvidia card with the vesa drivers not only deprives you of the video acceleration otherwise possible, it may also be taxing your system memory instead of using the video memory. Both of those things will slow the system down.

---

### Post by kennster on 2008-03-17
> **savagenator said:**
> here is my solution through much troubleshooting.

I have found that the computer slows down when running a lot of web pages that use heavy flash, especially in 64-bit ubuntu with nspluginwrapper. Please tell us if you are running 64-bit version of ubuntu.

Also, a solution might be to update your flashplugin-nonfree or run firefox through wine

AND if you are running a 7800GT nvidia card, then it may be very weird in ubuntu. Mine always is a (female dog) to setup and sometimes run.

drivers are fine it runs ever thang fine i think its fire fox its self maby. but yes i am running 64-bit ubuntu, ket me try what the outhers sed tho about the reinstalling and what not

---

