---
title: "Dual booting Ubuntu &amp; Vista (XP, Feisty) - How I did it with no Linux experience"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by wxnker on 2007-02-22
I see a lot of threads regarding dual booting issues and there's a lot of great help to find in these threads. I did my own setup with the help of this forum as I was a complete Linux newbie when I started out with Ubuntu Edgy.

Some of this information is probably mentioned in threads in this forum already, but still I will  post this information  to sum up "how I did it" in case new Linux users may find this solution helpful as it's an almost complete **GUI alternative** with no need of using terminal commands.

Don't get me wrong. I like using the terminal but as a Linux newbie (still am in many ways) I found all the command line instructions a bit "scary". 

I wrote an answer to a newbie user in another thread. He got "scared" of using Linux because of **Grub, dual boot, boot manager issues**. As I see it, dual booting isn't any harder to setup in Ubuntu than in Windows. 

[COLOR="Red"]First of all, check out Grub. Find out what it is and what it does.[/COLOR]

_Here's the answer from that thread:_
I installed **Ubuntu Edgy** and **Windows Vista** on the same harddisk with 3 partitions (Ubuntu, XP & Linux swap) with **dual booting** with no problems and without touching a command line (I had never used Linux before at the time so I used loads of information in this great forum).

_Installing Grub but not on the MBR:_
From my experience it can be a good idea NOT to install Grub on the MBR (Master Boot Record). This can normally be changed right after the "partition setup" during the install of Ubuntu by choosing the button "ADVANCED" just before the installation starts copying files.

I'm no expert but I use this method because of the possibility to install other OS's like Windows later on. As far as I know Windows will write it's boot information on the MBR and thereby overwrite the Ubuntu Grub file if it's installed on the MBR. This may be a minor (and fixable) detail but as I see it, a convenient one.

If I want to add an Windows OS I can do this without changing the Ubuntu Grub and when Windows is installed I just start Google and download a small free program (**EasyBCD**) that can change the boot up Grub settings from a GUI within Windows Vista.

I think this information may be convenient for the novice Linux user and not as scary as using a command line to edit the Grub menu.lst.

The only thing to remember is to know how Grub list disks. 
0 = first disk (hda) 
1= second disk (hdb) etc. 
0,0 first disk, first partition (hda1) etc. 
Correct me if I'm wrong. Anyway, there's plenty of information on this on the www.

e.g. I have Ubuntu Edgy on the first harddisk and the first partition so I installed grub to (0,0) and not the default choice (0) which would be the MBR.

I hope this could be a suggestion for new users.

_With Windows already installed:_
I have not tried to install Ubuntu on a system with Windows already installed, but I would think that by doing it this way, the Windows boot should be left intact and then it's pretty easy to boot into Windows, download the tool for Windows, do the grub settings without using any code and get the bootmanager on the next reboot.


_With an Empty system/harddisk:_
If you, like I did, want to setup an Ubuntu and Windows system from scratch with an empty harddisk, I have had success with doing it this way.

1. Install Ubuntu but choose not to install Grub on the MBR
2. Install Windows
3. Boot into Windows and download the tool for Windows.
4. Install the tool and show it your Linux partition where the Grub file is.
5. Reboot and choose which OS to boot.

This might be posted elsewhere and this is merely the way I did it, so it's just a suggestion on how to do it the "easy way".

[COLOR="Red"]The tool is called **EasyBSD**. I do not know if it works with other versions of Windows than Vista, but the name BSD indicates that it is merely a tool for Windows Vista (BSD being the "Boot Configuration Data" in Windows Vista), but If the tool does not work with XP (I don't know as I'm running a Windows FREE system "Free at last...") then I guess there are similar tools for Windows XP etc.[/COLOR]

[COLOR="Red"]For more information and to download the tool:[/COLOR]
[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

--------------
--------------

This is how I ended up doing it. Now I do not use Windows any more and I know a bit more on how to deal with Linux but if this method is not that good, then please let me know. :D
 
[COLOR="Red"]Of course if I format "hda1" partition 0,0 then I will loose my Grub menu, but I can always back it up before formatting and then use copy/paste if I need any information from it, in a new Grub menu.lst later on. By then I will have used Linux for some time and know how to boot from a CD and alter boot settings.[/COLOR]

I also found it quite easy to install Ubuntu Feisty this way, with Grub on the Feisty partition, hda2 (0,1) and not on the MBR. Then I could just boot into Ubuntu Edgy and copy the Grub info from feisty to the Grub menu.lst used by Edgy.

---

### Post by aktiwers on 2007-02-22
You should have made this post in the HOWTO's part of the forum though.. 
Great post, though I never dual booted before, so cant tell if there is an easier way.:)

I thought a duel boot went on automatically if you install ubuntu as the lost os.

---

### Post by wxnker on 2007-02-22
Perhaps if Ubuntu is installed as the last OS, you might be right but as I recall I tried this and then I could not boot into Windows, only Ubuntu with no NTFS write access. Back then I didn't really know how to change the Grub menu.lst in Ubuntu so I did a clean install the way mentioned in this post to avoid command lines etc.

Yeah I probably should have posted this in the "how to" forum, but if people find it useful and there's a need for it, then I guess someone can move it there for me.

Regards Wxnker

---

### Post by xpod on 2007-02-22
I tried a dualboot of Edgy & Vista myself the other day although i would have opted for the Vista vm option had i had  enough memory...according to the hype/criticism i dont even have enough to run it normally but regardless of that i had to see for myself what i might just have ended up with  for good had i not discovered Ubuntu four months into my computer journey last year:) 

No more complicated than a normal dualboot of any type i`ve ever done although i always use 2 hd`s now so things are always kept apart ....kinda.Straightforwared though an no problems at all.

Of course i would`nt even waste my breath explaining how bad I thought Vista was compared to my wonderful Ubuntu and that cheeky bugger even had the audacity to TELL me to piss of and get a better video card for it`s poxy DVD maker.......not to mention it never even bothered listing the aero options on this pc...lol

Of course, just as i wont waste my breath (too much) on the comparisons i also was`nt wasting the HD space for tooo long.....I just had to see this thing i might well have ended up with if my journey had not took the road it did:) 

PHEW!!!!!!

---

### Post by wxnker on 2007-02-22
Ha ha :D

I have to agree. I ditched Vista pretty quick. I'm so tired of MS constantly forcing me to upgrade my hardware to run their programs decently. Besides, after a short while I didn't even use Aero. Does it make using Windows better? I don't think so. It's merely something that looks "good".
The word "bloated" gets on ones mind, doesn't it?

1 month after discovering Ubuntu I had a Windows free system and I don't see any reason to go back. I was already using programs like "Open office" and "Firefox" in Windows so the change wasn't really hard. I only wish that hardware producers like Logitech would make Linux drivers. 

With Feisty coming up, Ubuntu will get even better. It looks better and has some great new features e.g. a control panel, automatic codec suggestion/install etc. I'm using "herd 4" and it runs great.

:biggrin:

---

### Post by xpod on 2007-02-22
I discovered FF 2 weeks into my pc adventure thankfully and  then discovered Ubuntu 4 months after turning that pc on for the first time.It was installed the next day i think and although i had a dualboot calamity 2 weeks later which actually caused me to re-install xp i got through the whole process just to realise i did`nt really need OR want the thing and off it came again in place of a dapper/edgy  dualboot which was much more fun and informative....as well an easy recovery method if the inevitable Ubu calamity happened......which never really did:(  

That ultimate Vista just aint for this here ultimate noob so all`s well that ends well:)

---

### Post by Computer Guru on 2007-03-06
Excellent guide, just like to clear up the EasyBCD thing.
 
EasyBCD only works if you have Windows Vista installed on the same PC. It runs from Windows 98+, and technically, you don't actually need Vista installed, just it's bootloader.
 
Unfortunately, there are no other tools that do the same thing for Windows XP and below.
EasyBCD 1.6 should work on computers without Windows Vista installed at all - but that's not out yet :)

---

