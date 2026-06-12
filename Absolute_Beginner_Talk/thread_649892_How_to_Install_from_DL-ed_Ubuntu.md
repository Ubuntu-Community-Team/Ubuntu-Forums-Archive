---
title: "How to Install from DL-ed Ubuntu"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by Brothermoscow on 2007-12-25
So i downloaded Ubuntu 7.10 from the ubuntu website and it comes as an ISO. No problem, i open up Alcohol120, mount the ISO... and nothing. I open up the folders, I dont see any kind of install.exe or anything. I've never used Linux or Ubuntu before, but im well versed in XP, and am no new kid on the block to computers... but I'll admit i need sum help here... at the very first step: how do i install ubuntu?

Thanks for the help

---

### Post by forestpixie on 2007-12-25
burn it to a cd as an iso - slowly and then boot with it - make sure bios set to boot from cd

---

### Post by overdrank on 2007-12-25
> **Brothermoscow said:**
> So i downloaded Ubuntu 7.10 from the ubuntu website and it comes as an ISO. No problem, i open up Alcohol120, mount the ISO... and nothing. I open up the folders, I dont see any kind of install.exe or anything. I've never used Linux or Ubuntu before, but im well versed in XP, and am no new kid on the block to computers... but I'll admit i need sum help here... at the very first step: how do i install ubuntu?

Thanks for the help
Hi and maybe these links will help
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by LinuxIsInnovation on 2007-12-25
Alternatively, use daemon tools to mount your iso and install it. Its better if you burn it on a disk though, since ubuntu has a Live CD that comes handy in many cases :)

---

### Post by Brothermoscow on 2007-12-25
I burned it, and popped it in and set bios to boot from disk... i get message that says Invalid Boot Diskette... what now?

---

### Post by SeanHodges on 2007-12-25
The BIOS must be set to boot from CD-ROM, i'm not sure but it sounds like it's trying to boot from the floppy disk?

---

### Post by Brothermoscow on 2007-12-25
almost 100% sure its set to cd-rom...

---

### Post by LinuxIsInnovation on 2007-12-25
Looks like your burning was improper or the iso was damaged. Did you download the iso with correct architecture from the official website?

---

### Post by Brothermoscow on 2007-12-25
I believe so... I downloaded it from the Northeastern University mirror, from the official ubuntu site.

---

### Post by SeanHodges on 2007-12-25
Previous times I have seen this it turned out the ISO was not burned correctly onto the CD. If you open the CD in Windows does it just have one file in it with the file extension ".iso"?

---

### Post by LinuxIsInnovation on 2007-12-25
Its not an architecture problem. Insert the Ubuntu disk in Windows. Does a browser like thingy pop up with all software options like Firefox etc.? If no, then you cd image is corrupted or burning had been improper.

---

### Post by Brothermoscow on 2007-12-25
No, there are a few folders and some other files.

---

### Post by LinuxIsInnovation on 2007-12-25
What does the autorun come up with? Right-click on the CD icon and select Autorun option..

---

### Post by Brothermoscow on 2007-12-25
The auto-run jus asks if i want to open the folder inside... i guess there really isnt an autorun.

---

### Post by Brothermoscow on 2007-12-25
Bah.... WTF?! whats goin on wit this... i cant figure out where its going wrong

---

### Post by overdrank on 2007-12-25
> **Brothermoscow said:**
> Bah.... WTF?! whats goin on wit this... i cant figure out where its going wrong

HI and did you see my post
Hi and maybe these links will help
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by Brothermoscow on 2007-12-26
Yeah, I saw ur post and went to the links you recommended... my bios is set to boot from the disk first, the disk should be burned properly, i have more than just the ISO, i have folders and the ubuntu files... i dont have a start.exe or anything. I see the following:
Folders: 
_disk
boot
dists
doc
install
pics
pool
preseed
Files:
cdromupg
readme.dis
ubuntu
md5sum.txt

none of these are .exe and there's no autorun that gets it working... any ideas?

---

### Post by frup on 2007-12-26
I take it you are using a standard intel or amd architecture that is 32bits and trying to use a 32 bit cd? what is the file name of the iso you downloaded?

---

### Post by oldos2er on 2007-12-26
You won't find any *.exe files in Linux. 

 Try burning to a fresh cd-r at a slow speed; 4x or slower. Double-check your BIOS is set to boot from the cdrom drive. Once the cd boots to the first menu, choose 'check cd for defects.'

---

### Post by Brothermoscow on 2007-12-26
the ISO i downloaded is ubuntu-7.10-server-sparc

---

### Post by forestpixie on 2007-12-26
are you sure that's what you want

---

### Post by SeanHodges on 2007-12-26
As forestpixie said, are you sure you're using a Sun Sparc computer?

Usually, you want to download the default type: "Standard personal computer (x86 architecture, PentiumTM, CeleronTM, AthlonTM, SempronTM)"...

I'm a bit out of my league here if you're running a Sparc platform; and if you are, you might get responses from people who know the Sparc architecture better if you also post in this section: [http://ubuntuforums.org/forumdisplay.php?f=146](http://ubuntuforums.org/forumdisplay.php?f=146)

---

### Post by Brothermoscow on 2007-12-26
wait... I went to ubuntu and searched pc... and it gave me that ISO to download.. u sayin i dl-ed the wrong one?

---

### Post by PeterJS on 2007-12-26
Does the machine run windows? If so there's no way it's a sparc, and further almost guaranteed to be i386.

---

### Post by thenailedone on 2007-12-26
> **Brothermoscow said:**
> wait... I went to ubuntu and searched pc... and it gave me that ISO to download.. u sayin i dl-ed the wrong one?

Yup... you have the wrong version... did you go to [www.ubuntu.com](www.ubuntu.com) to find and download the right file... because then you should have been guided easily to the right version for you... check [http://ubuntu.mirror.ac.za/ubuntu-release/7.10/](http://ubuntu.mirror.ac.za/ubuntu-release/7.10/) to see what I mean...

---

### Post by Brothermoscow on 2007-12-29
OK... so im an idiot and still cant figure out how i managed to download the sparc version.... BUT i got the right one now, and i burned it successfully, and i popped it in my computer and booted from it successfully... and when i say install... my monitor gives me ****... "OUT OF RANGE" 

crap. 

anythin i can do bout that?

---

### Post by thenailedone on 2007-12-31
> **Brothermoscow said:**
> OK... so im an idiot and still cant figure out how i managed to download the sparc version.... BUT i got the right one now, and i burned it successfully, and i popped it in my computer and booted from it successfully... and when i say install... my monitor gives me ****... "OUT OF RANGE" 

crap. 

anythin i can do bout that?

Just some background info... when you boot from the CD into the live environment it is still fine?  (Or can't you get into it without this message)... What is your screen specs?

I know of an alternative install CD that is supposed to use a text base installer etc. which is often used when the GUI version is giving problems...

Lets see if we can fix your dilemma... (heck I'm here till Wednesday... even if I'm a noob at least I can also search for answers right :) )

---

