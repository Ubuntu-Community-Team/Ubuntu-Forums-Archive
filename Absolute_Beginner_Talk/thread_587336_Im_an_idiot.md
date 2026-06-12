---
title: "Im an idiot"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by leonardoapt on 2007-10-22
.....or at least not to good at ubuntu.....

....well i was thinking of making my computer a dual.....

....and i had the long time problem with that i could not format the C:\ when i installed windows because it wouldnt let me since the installation files that where important for installing win xp was there.....

....but now that i was going to install UBUNTU i got a [lesser] great idea. I was going to install just UBUNTU and then windows.....so that everything would be formatted (?) [ntfs]...and then of course UBUNTU again but this time in to another partition. So what happened is UBUNTU works great.....unfortunatly i can't run the win xp cd since it is..... .EXE files......

....and i can't install wine because it says that libaudio2 can't be installed and that it needs it........

....so can anybody help me to install wine so that i can get back to windows so that i can have the dual??? Cause i dont know what to do....i followed the [www.winehq.org](www.winehq.org) instructions......but it just keeps saying that libaudio2 couldnt be installed....and that wine is dependent of it. (oh before it was binftm or something like that too.....but that one worked last time.....

well, i would appreciate some help since i dont really know how to work this OS and was hoping on learning it parallel while using win xp.

Mvh Leo

---

### Post by fjf314 on 2007-10-22
Wait, how are you installing Windows? If you're just using a Windows CD, then intead of running it from within Ubuntu, you should just boot to it. That will allow you to format your HDD as NTSF and install Windows. Once you've done that, you can then boot from the Ubuntu CD, create a partition, and then install Ubuntu onto that partition.

In order to boot from your Windows CD, you need to set your BIOS to read your CD drive before the HDD. Right when your machine starts, at the very first screen you should be able to press a key (on my machine it's Delete) and access the BIOS menu. Set your CD drive as the first item, insert your Windows CD, and reboot the machine. From there the Windows setup should begin.

---

### Post by leonardoapt on 2007-10-22
Well there is a password to my BIOS [im not sure i set it, one day it just said that the CMOS was changed and when i tried to enter to restore default settings i needed a password in never knew] :confused:
So booting from the CD is pretty difficult......i tried the same when i was going to install UBUNTU, fortunatly i could start the boot file that comes with the CD.....anyway....so thats NOT an alternative.

So i guess the only way for the CD to boot would be to first install wine and with it open the setup.exe from the windows cd.....so.....what do i do now?

---

### Post by Maestro23 on 2007-10-22
> **leonardoapt said:**
> Well there is a password to my BIOS [im not sure i set it, one day it just said that the CMOS was changed and when i tried to enter to restore default settings i needed a password in never knew] :confused:
So booting from the CD is pretty difficult......i tried the same when i was going to install UBUNTU, fortunatly i could start the boot file that comes with the CD.....anyway....so thats NOT an alternative.

So i guess the only way for the CD to boot would be to first install wine and with it open the setup.exe from the windows cd.....so.....what do i do now?

libaudio2 is in the repo's.

> sudo apt-get install libaudio2

---

### Post by Paul820 on 2007-10-22
You can reset a bios password, although you will have to find the make of your motherboard and have a bit of a read on google. Here is a link to get you started: [http://www.tech-faq.com/reset-bios-password.shtml]("http://www.tech-faq.com/reset-bios-password.shtml")

---

### Post by ed-koala on 2007-10-22
Well, here's something that might be a bit of an extreme solution, but should work fast for ya.  If you are PC savvy, open up your machine and take out your CMOS battery for a few mins, then put it back.  If I'm right, that should reset your bios.  Might want to google this to be safe before attempting, but assuming it works, you'll be able to change your boot order then and just reinstall Windows then Ubuntu.

Good Luck!

---

### Post by leonardoapt on 2007-10-22
yeah i tried that it just says error, something about that it hasnt got an installations candidate...?? im not sure what that means.....

hmm...looks like if wine is on the computer....i wonder if the setup can manage without the audio......ill try this.....if im not back soon...im succeding....

---

### Post by leonardoapt on 2007-10-22
nope it gets an error

---

### Post by Paul820 on 2007-10-22
> **ed-koala said:**
> Well, here's something that might be a bit of an extreme solution, but should work fast for ya.  If you are PC savvy, open up your machine and take out your CMOS battery for a few mins, then put it back.  If I'm right, that should reset your bios.  Might want to google this to be safe before attempting, but assuming it works, you'll be able to change your boot order then and just reinstall Windows then Ubuntu.

Good Luck!
Yeah, that can work, although you also need to put a jumper on two pins near the battery. Like ed-koala said, do a google to make sure you do it correctly otherwise you might put the jumper on the wrong pins. If you have the manual there is usually a picture of the motherboard in that and it will tell you the pins to set.

---

### Post by Jerry N on 2007-10-22
I don't think you can use Wine to install MS Windows - Wine has it's own version of part of the MS Windows environment so that some Windows programs can be run within Linux.  

Also if you have a password protecting your BIOS you should be able to clear it with a jumper or by removing the backup battery for several minutes.  You will need the motherboard manual to determine exactly how to do that.  

I don't dual boot Windows and Linux but my understanding is that you have partition the disk, install Windows in one partition, and then install Linux in the other partition.

Jerry

---

### Post by leonardoapt on 2007-10-22
Im going to read those 2 last ones.....i would need to do that anyway....my bios is mine.....dont want anyone that trojaned my *** being in controle....

---

### Post by leonardoapt on 2007-10-22
Im going to try some backdoor passwords be right back!

---

### Post by fjf314 on 2007-10-22
> **Jerry N said:**
> I don't dual boot Windows and Linux but my understanding is that you have partition the disk, install Windows in one partition, and then install Linux in the other partition.

Whenever I dual-booted back in the days of Dapper, you didn't even have to make your own partitions if you didn't want to. You could format the whole HDD as NTFS and install Windows on it. Then, during the Ubuntu installation, when it asked where it should be installed you could select "Guided Partition." From there you just moved a slider to select what percentage of the NTFS partition to format as EXT3 for Ubuntu and it handled the rest.

---

### Post by ed-koala on 2007-10-22
Another quick idea, that probably won't work but is fast also ... Assuming you have Windows installed somewhere, try hitting F8 as youtr machine boots to see if you get the windows boot choice screen.

Can't imagine that working, but with Windows I won't say anything is impossible lol.

---

### Post by leonardoapt on 2007-10-22
Dont have internet....UBUNTU formatted the HD before installing.....well the problem with the partition is that i want one for windows....one for UBUNTU and one for all other things....and if i made a partition with windows......and choose guided it would make just 2 partitions......or the crap i did.....and manually i didnt get it...i did everthing as i should but it kept saying something about a root being selected.

Well my moderkort is Phoenix - Award BIOS CMOS v6.  [and then either] 00PG [or] OOPG

MS9127C

does anybody want to help me look for passwords??

Mvh Leo

---

### Post by leonardoapt on 2007-10-22
Is there any software for UBUNTU that can get the password?

Mvh Leo

---

### Post by Paul820 on 2007-10-22
Try 'AWARD_SW' or 'j262' for the password, without the quotes

---

### Post by leonardoapt on 2007-10-22
i tried all on the recomended page.....xp that was award or phoenix

---

### Post by leonardoapt on 2007-10-22
OK, in the page it says that if i remove the battery...i los all CMOS setup....does this mean i have to install something before windows? or does it mean that everything jumps to default?

Mvh Leo

---

### Post by adamorjames on 2007-10-22
VirtualBox, not Wine to install MS Windows inside Linux.

---

### Post by bigboy_pdb on 2007-10-22
If you want to install WINE then you should look at this:
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Once you've followed those instructions, open Synaptic Package Manager (System -> Administration -> Synaptic Package Manager), search for "wine", right click it in the menu and select the option that marks it for installation, and then click the "Apply" button.

WINE most likely won't run all of your software so you might want to run a Windows under a virtual machine (such as vmware-server) for programs that aren't too demanding (such as a word processor).

Regarding your BIOS problem, I cannot really help you with that, but if you do fix it then you should create two partitions (one for Windows and one for Linux). Install Windows first and Linux following that (otherwise you'll need to re-install grub) if you're doing a fresh installation of both systems.

---

### Post by leonardoapt on 2007-10-22
Thanks all....ill try that battery thing and hope for the best.......wish me luck xp

but you should all read everything....because 1....i was at winehq.org

2nd the installation cd setup wont run with that...to demanding, gets errors

3rd i know i should install windows first......but since im a noob, i didnt know that this OS cant open exe files....

Mvh Leo

---

### Post by leonardoapt on 2007-10-23
Now everything works great.....almost....im going to post about how to make an nvidia geforce 4 mx work on this...so that i can watch tv shows from the computer.....

mvh Leo

---

