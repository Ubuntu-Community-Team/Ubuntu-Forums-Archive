---
title: "having major troubles!! Help!"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by celticparadox on 2006-09-01
OK so i had this thought, "maybe ill try running linux and see what happens" Heh....well where to start, I guess I'll outline the problems i'm having and hope for some feedback. Please keep in mind this is my first ever brush with Linux...

1. I can't use the arrow keys in the boot manager....I have the options to boot linux or windows, however the arrow keys do not work, and for some reason i can't access the bios.

2. When trying to utilize the add/remove programs feature i get this handy error 
"This is a major failure of your software management system. Check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information: 'sudo apt-get update'." But when i run the sudo update thingy it prompts me for a password and then promptly does not work. 

3. Installing anything is a nightmare hahahah when i run synaptic i get this happy little message 
'E: Type '$' is not known on line 32 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem."

Needless to say I can't install anything and am kinda put off at the moment but im willing to keep chugging away and learning about the Linux OS...

Worst of all I can't play WOW cuz i can't boot into windows....but i digress. I really want to experience this OS but so far its been nothing but trouble. I know this is likely because im a noob and know nothing about linux 

I'd love some help if it is available

---

### Post by Bachstelze on 2006-09-01
Hi and welcome to Ubuntu :)

For your "software installation" problem, the must be an error in your sources.list. Open a terminal (Alt+F2, gnome-terminal), and type

```
gksudo gedit /etc/apt/sources.list
```

You will be prompted for your password, ignore the few error messages that will appear, you will have gedit (a text editor, much like Windows' Notepad) opened with a file in it. Please copy/paste the contents of the file.

---

### Post by toasted on 2006-09-01
And for the keyboard... it sounds like its usb eh? Try a 'regular' keyboard and see if it works

---

### Post by celticparadox on 2006-09-01
here are the results of the sources list
as for the keyboard, i tried a regular one to no avail....

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
 $ dpkg -i /PATH_TO PACKAGE/PACKAGE_NAME.deb


I appreciate the help, 
Celticparadox

---

### Post by celticparadox on 2006-09-02
Ok, slight update, I managed to crack into the bios and get the USB drivers working for the dual boot so I can now boot into my windows OS. However the insrtalling problem continues to confuse me. Hopefully someone out there will  have the answer for me.

The eventual goal is to get the Cedega installed (already purchased) and get wow running properly, If you have an7y info please see the result of the sources list query posted above.

Ola and thanx
Celt

---

### Post by jpkotta on 2006-09-02
If the "$ dpkg -i /PATH_TO PACKAGE/PACKAGE_NAME.deb" line is in /etc/apt/sources.list, get rid of it.  It shouldn't be there.  Either that, or put a '#' at the beginning of the line.

---

### Post by celticparadox on 2006-09-02
hmmmm....now when i enter that into the terminal i get this message bash: /etc/apt/sources.list: Permission denied

I get the feeling that something is waaaaaay wrong here but i can't put my thumb on  it....

Celt

---

### Post by celticparadox on 2006-09-02
oh yeah  and im still getting this alot "E: Type '$' is not known on line 32 in source list /etc/apt/sources.list"

any clues?

---

### Post by eternalis on 2006-09-02
> **celticparadox said:**
> hmmmm....now when i enter that into the terminal i get this message bash: /etc/apt/sources.list: Permission denied

I get the feeling that something is waaaaaay wrong here but i can't put my thumb on  it....

Celt
You have to type sudo nano /etc/apt/sources.list and then enter your password to be able to modify it.

---

### Post by celticparadox on 2006-09-02
sweet ok.....think im making some headway here...i zapped that annoying line out of there and that appears to have helped. My main concern now in the installation of things like the necessary Nvidia drivers etc, i have the NVIDIA-FreeBSD-x86-1.0-8774 hopefully thyat is right....its currently sitting on the desktop and i really have no clue how to install stuff but anyone new to command lines and package managers can likely feel my pain. When I get to the package manager (synaptic) i really have no clue what to look for or what to do with it if I find it.....<if me = id10t then whine on forums>

DO i need the same sort of network drivers/java runtime stuff that is required in XP? 

FYI the system specs run like this
AMD Athlon 2500+
1 g DDR
ATI RAdeon 9550 (slightly tweaked) and yes I know radeon ain't happy in Linux or so I have heard
250 g hd running 3 partitions XP/Ubuntu/swap

BTW the response to questions is awesome here. Makes me glad i chose to try this out, despite the unfamiliarity, complete lack of Linux knowledge whatsoever and the unfortunate dependance on Redmond washington....

---

### Post by bodhi.zazen on 2006-09-02
First, for the nvidia drivers follow the instructions on the nvidia site. You need to install this from the command line after killing (exiting) you X server. This drops you to a CLI (no gui).

What do you need Java for?

---

### Post by celticparadox on 2006-09-02
if i dont need java then thats just fine by me......here is the latest error message 

W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_universe_binary-i386_Packages)

---

### Post by celticparadox on 2006-09-02
oh, and it's actually the command line stuff that is giving me headaches (surprise surprise) I have installed easy ubuntu in an attempt to make my life easier....not sure if t6hat realy means anything

essentially i need some coaching on the command line and what to enter therein

Call me the uber noob lol

---

### Post by bodhi.zazen on 2006-09-02
It gets easier. You are a recovering windows'aholic after all. Withdrawal symptoms such as these are common. They go away in time.

Linux addiction, however, is worse....

---

