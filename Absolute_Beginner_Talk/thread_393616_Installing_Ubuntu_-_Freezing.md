---
title: "Installing Ubuntu - Freezing"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by w0lf42 on 2007-03-25
Greetings, I'm fairly new to Linux and very new to Ubuntu.

I am currently running Windows XP SP2 and I decided to dual-boot Ubuntu.  I followed [Mathew's Miller's HOWTOs: Dual Booting Windows and Ubuntu]("http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/") to give me an idea of what to do.

He suggested that I use [Linux System Rescue CD]("http://www.sysresccd.org/") to partition my drives prior to using the Ubuntu installation CD.

Hard Drive Partition:
Primary A: NTFS (Windows XP) - 55 GB
Primary B: ext3 (Linux) - 8 GB
Extended 1: ext3 (Swap) - 2 GB
Extended 2: Fat32 (OS Share) - 3 GB

Note: I'm not sure if this is related - while running GParted, my USB mouse froze up quite often, preventing from doing my partitioning.  I ended up plugging in 3 x USB mice - using a spare as soon as each one froze.

Verification:
[LIST]
[*]Defraged the HD in Windows XP prior to partitioning
[*]Verified the ISO
[*]Verified the RAM (MemTest ver. 1.65)
[*]Verified the CD
[/LIST]

Problem:
Upon the loading of the beige screen, a graphic appears which has the Ubuntu logo, but it's scrambled a bit.  I can't read any text except for the logo.

The computer will hang, preventing me from installing Ubuntu.

I also noticed that the black load screen before it has some graphic oddities - the right 1/3 displays some white pixels which don't look like they belong.

I have attempted to change the graphics settings to a range of different options (including 640 x 480 x 16) as well as used the "Safe Graphics Mode".

Vitals:
Ubuntu ver. 6.10
CPU: AMD 64 X2 3800+
MB: eVGA K8 NF41 Socket 939 nForce4
HD: WD Raptor 74GB
Graphics: eVGA GeForce 7800 GT

---

### Post by lamalex on 2007-03-25
i would give the alternate install cd a try, you can download from the get ubuntu page on ubuntu.com. its the link at the very bottom when you're chosing your mirror. it almost always installs successfully.

---

### Post by w0lf42 on 2007-03-31
Iamalex,

I obtained the alternative install and everything seemed to go well until I booted into Ubuntu.  It froze at the same loading screen that the previous installation process froze on.

Note: I selected the "64bit AMD and Intel computers" version to install.  I will try the "Ubuntu 6.10 - Supported to 2008 Desktop Version".

---

### Post by w0lf42 on 2007-04-05
I tried the "Ubuntu 6.10 - Supported to 2008 Desktop Version" and got the same odd graphical problems with my other attempts.

Any suggestions?

---

### Post by karamba_kid on 2007-04-05
Did you download the ISO's via bittorrent or the mirrors in which case did you check the md5sums.  There is also a md5sum on the alternative cd.  I have had problems with the install cd's which I burned at too high of a speed.  Now I try to make sure I burn every ISO image at the lowest speed.  If you think that could be a problem try making another CD.

**Edit** oh it looks like you said it did install but X.org seems to freeze?  Is that it?  Have you been able to run a liveCD session on this machine successfully?

---

### Post by w0lf42 on 2007-04-05
I downloaded via mirror, checked the md5 and used the option on the initial boot screen to verify the CD.

I attempted to use the option from the initial boot screen to 'boot via safe mode'.  I was greeted with the same problem that I have had with all previous boot/install options with Ubuntu.

I am downloading Knoppix (as I didn't see an Ubuntu liveCD).  I attempt to try this later and report back.

---

### Post by mikeyphi on 2007-04-05
I note you are trying the 64bit version - quite a few previous posts have indicated problems installing that and the advice given was to use the 32bit version.

---

### Post by Roelski on 2007-04-05
I don't want to set you back, but try the 6.06 LTS version once.  Worked fine for me.  I then upgraded to 6.10 without probs.

Fyi: 6.06 Dapper is a LiveCD.

I must admit I had some problems setting Dapper up, but these were mainly related to the quality of / errors on my HDD.

Good luck,


Roelski

---

### Post by w0lf42 on 2007-04-05
**mikeyphi** - I tried both the 64bit and 32bit with the same result.

**Roelski** - Thanks, I'll try the version that you recommended and post my results.

---

### Post by w0lf42 on 2007-04-06
I tried Ubuntu 6.06 with the same result as my attempts with 6.10

---

### Post by Kedma on 2007-04-06
I was having the same problem..  and from the looks of it.. we have the same system for the most part..

AMD 64 X2 3800 ( socket 939 )
Gigabte K8 GMF-9
Sata 3.0 drives
7800 GT 256meg DDR3

I was also have the lock ups as soon as it would get to the desktop on the live cd..  both 64bit, and 32 bit.. so I used the alternate disk in 32bit mode.. and got it installed.. even have the dual boot working.. ( dual booting with win xp pro x64 edition ) yeah me..  but thats were the fun stops..  

it still locks up on me at the desktop..  I get the log in name, and pw.. then orange background.. a pixeld logo ( I can read the logo its pretty ugly with all the pixels missing ) and thats it.. system freezes..  no num lock key nothing.. just sits there..  

and ideas how to fix this??:confused:

---

### Post by w0lf42 on 2007-04-17
Kedma

I was able to resolve the problem after searching the forums.

1 - Boot Up Ubuntu
2 - When you are prompted to login, CTRL-ALT-F1
3 - sudo nano /etc/X11/xorg.conf
4 - find:
Driver          "NV"
replace with:
Driver          "vesa"

5 - restart X

Assuming this works, you'll be running non-nvidia drivers, but you can install an updated version once you get to your desktop.

---

### Post by w0lf42 on 2007-04-17
[Here is the post that had the solution that worked for me]("http://ubuntuforums.org/showthread.php?t=379807")

---

