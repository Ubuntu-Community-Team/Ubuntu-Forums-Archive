---
title: "absolute n00b: Can't Load 7.10 after first install, just black screen"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by ni ni on 2008-03-13
Hello,
I really thought today was a great day - i was about to say goodbye to windows forever! But no...

I installed 7.10 with Wubi and I get as far as the first splash screen then all i get is just a black screen.

One of my problems is I dont know what the GRUB is, or how i edit the command line or any of that.

What is sudo and where/when do i type it?

is it back to yucky windows for me???

or can someone help?

Intel Celeron M processor 1.60GHz
1.59GHz, 448 MB RAM
VIA/S3G UniChrome Pro IGP
X86-based


I want ubuntuuuu!!

---

### Post by mikesignguy on 2008-03-13
1. Did the live cd work?
2. What graphics card do you have
3. Ctlr -Alt F1 will get you to a terminal ( that is where you sudo)
  What does it say?
4. If you don't know what GRUB is, why are you trying to edit it?
5. Don't panic you will be windows free soon!

---

### Post by Hospadar on 2008-03-13
you may want to dump the wubi install and do a regular install.

it's not really that tough or dangerous, and it's easy to undo with a little guidance (which you can find here). so get rid of wubi through windows and then:

First: back up any critical data you have in windows

Second: Defrag your windows machine (several times if possible, on fresh bootups)

Third: using the livecd, start gparted (Alt-F2, type in "sudo gparted") and shrink down the windows partition to a resonable size (if you are just trying things out, you only need a couple gigs for ubuntu)

Fourth: start the installer, and when you get to the partitioner, install ubuntu into the free space you just created on the drive.

Ubuntu will take care of the dual booting for you as long as you don't wipe out your windows partition.  just read the installer options carefully and you will be fine.  Also you should probably google around for some more ubuntu dual boot tutorials until you are more comfortable with the process.

---

### Post by SteveHillier on 2008-03-13
> **ni ni said:**
> is it back to yucky windows for me???
or can someone help?

Intel Celeron M processor 1.60GHz
1.59GHz, 448 MB RAM
VIA/S3G UniChrome Pro IGP
X86-based

I want ubuntuuuu!!
If you want Ubuntu - go get it.  Do not fall at the first hurdle.  Once you get there I am sure you will catch the bug and stay with it.
I admit, I had a similar problem today - Gutsy install (over a previous install of Dapper I think).
The hardware I was using was Core 2 Duo E6550, 2Gb RAM, and stuff but more importantly ATI Radeon Graphics card and 19" widescreen monitor.  [The Dapper install I refer to was not on this hardware]   The live CD version worked OK, it displayed a graphical screen and so on, but on reboot after install an initial splash screen then black screen.  I tried VGA and not DVI connectioon, no change.
I have read in this forum that there are some issues with Ati cards and this install a) was not my first and b) not the most important.
I suspect it is the graphics card that is messing things up.  The live CD uses the VESA driver and the install probably installs a different driver.
I have Gusty installed on one of my machines at work, on a machine I am setting up as a web server, I am installing it onto a laptop as I type, but all of these are using 3 x 4 screens not the 16 x 9 format.
From your spec you are installing onto a laptop and I assume it is wide screen.
There will be lots of clever peole on this forum who will help you with the detail, but it might mean getting your hands a bit dirty in the process.
Please keep the faith and work through it, the reward will be worth the wait.
Good luck

---

### Post by ni ni on 2008-03-13
thanks everyone for having faith in me: i won't give up.

---

### Post by ni ni on 2008-03-14
> **mikesignguy said:**
> 
3. Ctlr -Alt F1 will get you to a terminal ( that is where you sudo)
  What does it say?


when do i press Ctlr -Alt F1 ???  when it's loading up?

---

### Post by Therion on 2008-03-14
No problem... I'm a bit of an old hand at this problem.  Here&#8217;s how to fix the booting to a black screen issue.  

You&#8217;re going to have to edit a file called menu.lst a few times to make the fix permanent.  

Boot from the LiveCD.
At the Menu you get hit &#8220;F6&#8221;.
Using the arrow keys, find and delete the the words **splash** and **quiet**.
Hit &#8220;Enter&#8221; twice.  This will get you to the desktop so you can do a full install.
Once Ubuntu is installed, reboot your machine and get ready to hit the ESCape key.
When you see GRUB (it&#8217;s the countdown timer) hit the ESCape key.
Keep your selection on the first line of the menu and hit "E" to enter Edit mode.
Using the arrow keys, go to the second line of text and and hit "E" again to edit this line.
Delete the words **splash** and **quiet**.
Hit &#8220;Enter&#8221;, then "B" to continue booting.
Once you're in Ubuntu, open up the Terminal and enter:

```
gksudo gedit /boot/grub/menu.lst
```
Find and delete the words **quiet** and **splash** from the line that starts with Kernel  one more time.
Save the file, Exit&#8230; And you&#8217;re done.

Now do all your updates and THEN installl the Restricted Driver for your video card in needed. 
Let me repeat that: Updates first, THEN your video driver.  NOT the other way around.

---

### Post by ni ni on 2008-03-14
Therion thanks for the help - and the edit to make it easier.  But when i downloaded ubuntu there was no file in the winrar archive that was .iso, so i turned to wubi for help.

I'm downloading again from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download), to burn a cd, but i've no idea where the iso is!!!! god i shouldn't be allowed own a computer!!!

---

### Post by Therion on 2008-03-14
Well, nothing wrong with wubi as far as I know, though I've never used it personally.

When you dowload Ubuntu you're going to have a .iso file saved to wherever your dowloaded files go.  There will be no WinRAR archive file, just an .iso file; that's all you get.  :)

Burn that .iso file to a CD using [these instructions](https://help.ubuntu.com/community/BurningIsoHowto#head-5f36c46dbbdd2bd773ae1f5d361be66c6553babf).  Then leave the CD in the drive and reboot your computer.  That's really all there is to it.

---

### Post by 3rdalbum on 2008-03-14
> **ni ni said:**
> Therion thanks for the help - and the edit to make it easier.  But when i downloaded ubuntu there was no file in the winrar archive that was .iso, so i turned to wubi for help.

On Windows, turn off "Hide filename extensions for known filetypes" or whatever it's called, so it will display the filename extensions. You'll see that the file you are downloading is actually a .iso.

---

### Post by ni ni on 2008-03-15
> **Therion said:**
> 
Boot from the LiveCD.
At the Menu you get hit “F6”.
Using the arrow keys, find and delete the the words **splash** and **quiet**.
Hit “Enter” twice.  This will get you to the desktop so you can do a full install.



This doesn't get me to the desktop it just gets me to my old friend the black screen :(:(:(:(:(:(
(not a black screen where one might enter text, but a black screen when no input at all is possible )

---

### Post by ni ni on 2008-03-15
My graphics card is Via/S3g UniChrome Pro IGP, could that be part of the problem?

Do i need to install a driver for that? How might i do that?

I just want to get on to that lovely desktop!!!

---

### Post by PmDematagoda on 2008-03-15
Did you try having a look at this [guide]("https://help.ubuntu.com/community/OpenChrome")?

---

### Post by ni ni on 2008-03-15
> **PmDematagoda said:**
> Did you try having a look at this [guide]("https://help.ubuntu.com/community/OpenChrome")?


Thanks PmDematagoda,
I get Failed to process build dependancies



hmmmm

---

### Post by PmDematagoda on 2008-03-15
Can you post the output of:-
```
cat /etc/apt/sources.list
```

---

### Post by ni ni on 2008-03-16
> **PmDematagoda said:**
> Can you post the output of:-
```
cat /etc/apt/sources.list
```

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy main restricted

## uncomment the following two lines to add software from the 'universe'
## repository
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence.  please satisfy yourself as to 
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy universe
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted

---

### Post by ni ni on 2008-03-16
I had to write it all by hand but i am just mad to get Ubuntu!

---

### Post by TLDigital on 2008-03-16
> **SteveHillier said:**
> If you want Ubuntu - go get it.  Do not fall at the first hurdle.  Once you get there I am sure you will catch the bug and stay with it.
I admit, I had a similar problem today - Gutsy install (over a previous install of Dapper I think).
The hardware I was using was Core 2 Duo E6550, 2Gb RAM, and stuff but more importantly ATI Radeon Graphics card and 19" widescreen monitor.  [The Dapper install I refer to was not on this hardware]   The live CD version worked OK, it displayed a graphical screen and so on, but on reboot after install an initial splash screen then black screen.  I tried VGA and not DVI connectioon, no change.
I have read in this forum that there are some issues with Ati cards and this install a) was not my first and b) not the most important.
I suspect it is the graphics card that is messing things up.  The live CD uses the VESA driver and the install probably installs a different driver.
I have Gusty installed on one of my machines at work, on a machine I am setting up as a web server, I am installing it onto a laptop as I type, but all of these are using 3 x 4 screens not the 16 x 9 format.
From your spec you are installing onto a laptop and I assume it is wide screen.
There will be lots of clever peole on this forum who will help you with the detail, but it might mean getting your hands a bit dirty in the process.
Please keep the faith and work through it, the reward will be worth the wait.
Good luck



I love Ubuntu........I am a complete noob, but because of the forums I have been able to install linux ubuntu  successfully on my HP dv6000t laptop.  I need to get my networked BrotherMFC420CN printer working and I will be happy.  I don't think there are drivers for my HP Express Go  card yet, but I am sure it will be around soon.  I am in love with Linux/Ubuntu.  I am currently dual booting until support for my Video card becomes available then it is good buy to MS.

---

### Post by ni ni on 2008-03-16
I can't wait to say bye to MS"!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by ni ni on 2008-03-17
What do you guys think the problem is? Is it the graphics card?

---

### Post by PmDematagoda on 2008-03-17
You did not read the guide properly, because if you had then you may have noticed the lines instructing that the Universe and Multiverse repositories are to be enabled:-
>     *

      You must have administrative privileges.
    *

      [B]Make sure you have enabled the Universe and Multiverse repositories.
      See Managing Repositories in Ubuntu or Kubuntu for help with this[/B].
They are at the top of the guide, please read them and then try again.

---

### Post by TLDigital on 2008-03-27
> **TLDigital said:**
> I love Ubuntu........I am a complete noob, but because of the forums I have been able to install linux ubuntu  successfully on my HP dv6000t laptop.  I need to get my networked BrotherMFC420CN printer working and I will be happy.  I don't think there are drivers for my HP Express Go  card yet, but I am sure it will be around soon.  I am in love with Linux/Ubuntu.  I am currently dual booting until support for my Video card becomes available then it is good buy to MS.


Got my Printer Working now:):D:p):P;)

---

