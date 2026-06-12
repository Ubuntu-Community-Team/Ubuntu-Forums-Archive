---
title: "Going round in circles"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by ububaba on 2007-04-11
Murphy's Law must be the most applicable one all the time. I have recently re-installed
[COLOR="Red"]Edgy[/COLOR]. After **login** and feeding the password the screen changes back to **login**. It is a
loop I cannot get out of. I cannot find the reason by just looking at the[COLOR="Red"] Grub[/COLOR]. 
Reasons are incomprehensible to me.  ](*,)

---

### Post by apjone on 2007-04-11
Have you tried login in to a terminal? You can not by default (if i remember correctly) log in to a gui as root.

---

### Post by ububaba on 2007-04-11
> **apjone said:**
> Have you tried login in to a terminal? You can not by default (if i remember correctly) log in to a gui as root.
Once I am not able to get out of this loop **login name / password** and back again. It is
not possible for me to reach the [B]Terminal
[/B] Perhaps I don't follow you.

---

### Post by apjone on 2007-04-11
if you press ctrl+alt+F1 @ the log on screen it will allow you to reach a terminal where you should be able to log in

---

### Post by ComplexNumber on 2007-04-11
> **ububaba said:**
> Murphy's Law must be the most applicable one all the time. I have recently re-installed
[COLOR=Red]Edgy[/COLOR]. After **login** and feeding the password the screen changes back to **login**. It is a
loop I cannot get out of. I cannot find the reason by just looking at the[COLOR=Red] Grub[/COLOR]. 
Reasons are incomprehensible to me.  ](*,)
soi guess ytou're saying that after you've entered your username and password, it sends you back to the login screen screen again, right? 
does it give you any error messages at all?

during the last time you were logged in successfully, did you do anything significant do the system?

btw you can login to the terminal by switching the session to failsafe terminal.

---

### Post by ububaba on 2007-04-11
> **ComplexNumber said:**
> soi guess ytou're saying that after you've entered your username and password, it sends you back to the login screen screen again, right? 
does it give you any error messages at all?

during the last time you were logged in successfully, did you do anything significant do the system?

btw you can login to the terminal by switching the session to failsafe terminal.

You are right it is username/password loop I cannot get out of, no possibility of getting
any error messages either. Silly as it may sound I cannot recall having sinned against 
anything specific. I did change xorg.conf from generic to conform to Nvidia. While on 
the other hand my Evolution mail started protesting that there was not enough of space
there. Which meant I had no possibility of downloading mail to inbox. Evolution sort of 
freezes.

I am using another HDD for this correspondence.

---

### Post by ComplexNumber on 2007-04-11
> **ububaba said:**
> You are right it is username/password loop I cannot get out of, no possibility of getting
any error messages either. Silly as it may sound I cannot recall having sinned against 
anything specific. I did change xorg.conf from generic to conform to Nvidia. While on 
the other hand my Evolution mail started protesting that there was [B]not enough of space
there.[/B] Which meant I had no possibility of downloading mail to inbox. Evolution sort of 
freezes.

I am using another HDD for this correspondence.
there's your problem. the login screen will kick you out if there is is a space shortage on the home and/or root partition.
you need to login via failsafe(if you can, through the login screen screen. if not, choose failsafe from the boot menu) and clear out some space. maybe delete trash items. 

do you have your home directory on a separate partition? and do you know if it is your home directory or root directory which is short of space? usually when you are down to your last few megabytes, then it will complain.

---

### Post by ububaba on 2007-04-11
> **ComplexNumber said:**
> there's your problem. the login screen will kick you out if there is is a space shortage on the home and/or root partition.
you need to login via failsafe(if you can, through the login screen screen. if not, choose failsafe from the boot menu) and clear out some space. maybe delete trash items. 

do you have your home directory on a separate partition? and do you know if it is your home directory or root directory which is short of space? usually when you are down to your last few megabytes, then it will complain.

Probably the best thing for me to do would be to go back to the complaining HD and try
to login via failsafe as you suggested and try to figure out the partition failure in gparted,
in the worst case mail the screen shot from gparted to ask for your helpfulness. This will
take another hour or so I am dying of hunger. Thanks for all.

---

### Post by ComplexNumber on 2007-04-11
if its your home directory thats short of space, you can login via failsafe at the boot menu. then when you've logged in, you can type in 'startx'. your will be in your root account then. if its your home directory thats short of space, you will be able to log in to your root account (thats assuming that your root partition isn't short of space too). 
i get the impression that you prefer working with GUI tools. you can delete stuff in the command line by typing in 'rm -R <name-of-directory>'


btw i'm not sure as to why you say that its a partition failure what do you mean by that anyway? all im saying above is that you are short of space on either your home and/or root partition. its nothing serious at all.

---

### Post by ububaba on 2007-04-11
> **ComplexNumber said:**
> if its your home directory thats short of space, you can login via failsafe at the boot menu. then when you've logged in, you can type in 'startx'. your will be in your root account then. if its your home directory thats short of space, you will be able to log in to your root account (thats assuming that your root partition isn't short of space too). 
i get the impression that you prefer working with GUI tools. you can delete stuff in the command line by typing in 'rm -R <name-of-directory>'


btw i'm not sure as to why you say that its a partition failure what do you mean by that anyway? all im saying above is that you are short of space on either your home and/or root partition. its nothing serious at all.

Sorry, I formulated badly. A more honest statement ought to be that despite using Ubuntu
for over a year, I can't partition the disks properly and have only a fuzzy idea of what root 
and home partitions are. It takes all kind.

---

### Post by ComplexNumber on 2007-04-11
> **ububaba said:**
> Sorry, I formulated badly. A more honest statement ought to be that despite using Ubuntu
for over a year, I can't partition the disks properly and have only a fuzzy idea of what root 
and home partitions are. It takes all kind.
ok. so i guess you intend to start afresh and do a clean install, and resize partitions whilst you're at it, right?
if you tell me how much hard disk space you have, and how much RAM you have, then i can recommend how much space to set aside for each partition. i will also give you an explanation for my choice.

also, do you tend to store a lot of videos and/or mp3's?

---

### Post by Bachstelze on 2007-04-11
You can view the filesystem in Linux and other UNIX-like systems as a tree. The root folder is the root of the tree, which contains everything else. "So, you ask, why do I need to make several partition if one partition contains everything ?" Technically, making several partitions is not an absolute requirement, but it is strongly recommended. Why ? Because if your Linux system has a problem of any kind and you need to reinstall it, you will have to format the root partition and say goodbye to all data that's on it.

Fortunately, Linux (and UNIX-likes generally speaking) keep all the users' personnal files and settings in a subfolder called "home" of the root folder. That's why a common partitioning scheme is to put /home on a different partition than the root filesystem. That way, the root folder will go on one partition, as well as everything it contains : /bin, /usr, /var, etc. Everything *except* the /home folder, which will be on it's separate, dedicated partition. The use of doing that is simple : if a reinstall of the OS is needed, only the root partition will need to be formatted and all of the users' files and settings will remain untouched, ready to be used with the freshly reinstalled OS.

---

### Post by ububaba on 2007-04-11
> **ComplexNumber said:**
> ok. so i guess you intend to start afresh and do a clean install, and resize partitions whilst you're at it, right?
if you tell me how much hard disk space you have, and how much RAM you have, then i can recommend how much space to set aside for each partition. i will also give you an explanation for my choice.

also, do you tend to store a lot of videos and/or mp3's?

I was intending to use gparted for defining the function (for lack of a better term) to 
reallocate if possible different drives, once I'm there, according to your recommendations.
I have 320 GBs+1GB RAM. I intend to store books, world music and videos/documentaries etc. 
GUI is the only world I am at ease with. 

Hymn thanks, it all is trickling down one day I will find my salvation.

---

### Post by ComplexNumber on 2007-04-11
i would allocate the following:
-1GB swap space
-15GB for root partiton (more than enough. i have everything installed, and it still only takes up 7-8GB)

-304GB home partiton.


as HymnToLife recommends, its best to have lots of space on your home partiton because it acts as a permanent storage area. if and when you ever decide to do a clean install in the future, it means that all your desktop settings, documents, videos, music files, etc are untouched  install after install.

---

### Post by ububaba on 2007-04-11
I don't know couldn't find failsafe possibility of logging in. Here I am attempting to install
Edgy on HHD which is 320 GB and looks like this. Now I can get recommendations on
how to proceed further. I promise I will follow orders.

The latest situation is in the lower figure which I believe and hope would be satiftying to
you too.

---

### Post by ComplexNumber on 2007-04-11
post back to let us know how you get on.

---

### Post by ububaba on 2007-04-11
> **ComplexNumber said:**
> post back to let us know how you get on.

Keeping my fingers crossed. Everything seems to work perfectly till now. However, I am 
still a tad hesitant connecting and mounting another HDD which too has Edgy as the OS. 
It has stuff, which I would like to transfer to the bigger disk. Thanks for the help. \\:D/
Hopefully, I have learnt something.

---

