---
title: "Insane, Sound Card"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by Gazz777 on 2007-12-07
Hi Guys, ripping my hair out here, sound card C-Media CM6501 sound card

works great in Windows, not a peep from it in Ubuntu

I will persevere, I am tempted to re-boot and goto windows with all it's flaws, but nae I say, there will be ups and downs but hells bells a simple fech-n play my mp3, after all it's the Tabernacle Choir and it's Christmas Time.

I am an addict to windows and will be for a long time, this is only my second day without my windows experience, so I must expect mood swings and tears, 

Ubuntu isn't seeing my spare hard-drive it isn't playing my music, and I keep getting errors in my mail config
I see this however as a challenge, and all the time Windows is whispering "reboot" my hands begin to shake and my heart races, but nae and nae some-more.

so can some very kind person point me to a possible solution regarding my sound card, I must add here, I have zero zilchoe nickty knowledge of this new and possibly wonderful OS system, and commands are what my wife gives me, and will increase in volume if I don't get this music playing, it does calm the wild beast,

 " and there more truth to that than what you may relies"

I bid you all 
Kind Regards
Gary
:KS

---

### Post by ronmarley1 on 2007-12-07
As far as the sound issue, it looks like this thread had a solution for a user:
[http://ubuntuforums.org/showthread.php?t=379429](http://ubuntuforums.org/showthread.php?t=379429)

EDIT: see post #4

---

### Post by Gazz777 on 2007-12-07
> **ronmarley1 said:**
> As far as the sound issue, it looks like this thread had a solution for a user:
[http://ubuntuforums.org/showthread.php?t=379429](http://ubuntuforums.org/showthread.php?t=379429)

EDIT: see post #4

gary@Linuk-DeskTop:~$ lsusb
Bus 001 Device 003: ID 06a3:8000 Saitek PLC 
Bus 001 Device 004: ID 12cf:0308  
Bus 001 Device 005: ID 0d8c:0201 C-Media Electronics, Inc. 
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
gary@Linuk-DeskTop:~$ 


I don't know what this is, but I hope it might guide someone to an answer, 

Thanx in advance
Gary

---

### Post by Gazz777 on 2007-12-07
Guys you's are good, I mean very good, went to the thread and bingo I now have sound.

Err my hard drive is seen ?

Any Way 
Cheers 
Happy Wife Means happy Life

:guitar:

---

### Post by ronmarley1 on 2007-12-07
Could you maybe give a few more details about the secondary hard drive issue?  Were you able to access it using Windows?  Is there an entry for it on the Places menu (on your top panel)?  How is the hard dive connected to your PC?  Is it internal, external, USB, firewire, etc...?  Are you seeing the second hard drive in BIOS?

---

### Post by ronmarley1 on 2007-12-07
> **Gazz777 said:**
> 
Happy Wife Means happy Life

:guitar:

Amen to that!

---

### Post by ronmarley1 on 2007-12-07
Does this site help?  [http://www.smorgasbord.net/2007/06/29/how-to-install-second-hard-drive-in-ubuntu-linux/](http://www.smorgasbord.net/2007/06/29/how-to-install-second-hard-drive-in-ubuntu-linux/)

Unfortunately, it's not that "beginner friendly" but it is very step-by-step.

---

### Post by Gazz777 on 2007-12-07
> **ronmarley1 said:**
> Could you maybe give a few more details about the secondary hard drive issue?  Were you able to access it using Windows?  Is there an entry for it on the Places menu (on your top panel)?  How is the hard dive connected to your PC?  Is it internal, external, USB, firewire, etc...?  Are you seeing the second hard drive in BIOS?


Hi there, I have a 320gig h/d in this I keep music and video's it's a separate drive no partitions nothing like that.
Ubuntu see's the drive that it's in as well as the partitions I created, but not the separate drive.

Windows I have no problem accessing the drive, however I will add, the drive that I am running Ubuntu and windows is a Sata Drive 300 gig, the 320gig that is invisible to Ubuntu is a normal drive ie not sata.
It is an internal drive, and I do see the second drive in the Bios.

any Idea's  :confused:

Thanx for your time :popcorn:

---

### Post by ronmarley1 on 2007-12-08
> **Gazz777 said:**
> Hi there, I have a 320gig h/d in this I keep music and video's it's a separate drive no partitions nothing like that.
Ubuntu see's the drive that it's in as well as the partitions I created, but not the separate drive.

Windows I have no problem accessing the drive, however I will add, the drive that I am running Ubuntu and windows is a Sata Drive 300 gig, the 320gig that is invisible to Ubuntu is a normal drive ie not sata.
It is an internal drive, and I do see the second drive in the Bios.

any Idea's  :confused:

Thanx for your time :popcorn:

Hmmmm.  Well, it's good that Windows sees the drive, and it shows up in BIOS.  So, we definitely know it's something with Ubuntu.  I've never had a PC using Ubuntu with a second hard drive, but I'll give a few suggestions.  My first guess is that it's just not mounted.

1.  Did the link I gave above provide any insight?  It's really good as far as I can see.  As the link mentions, run ```
sudo fdisk -l
``` and that should list all the hard drives on your PC.  If it does not, I'm not sure what to do at that point.

2.  As I mentioned, it may be just not mounted.  You can manually mount it, using the mnt command, and see if you can access it.  If so, then you can edit the fstab file and then Ubuntu will mount it automatically and give you rights to it while booting.  The link above describes how to do all of  this, with one change.  You will need to be root to edit and save the fstab file.  So when the link tells you to run ```
gedit /etc/fstab
```run ```
gksudo gedit /etc/fstab
``` instead.

---

