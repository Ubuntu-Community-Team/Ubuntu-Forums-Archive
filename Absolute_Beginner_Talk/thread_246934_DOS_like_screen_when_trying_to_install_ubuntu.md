---
title: "DOS like screen when trying to install ubuntu"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by eldar on 2006-08-30
Got an older laptop. gateway 5300. 256 ram, 850P3, 8meg vid (I think). 8gb hdd.

I downloaded ubuntu from one of the mirror sites listed on this site. None of them boot in anyway. Finally burned one at 8X and it got me into some goofy DOS looking setup. I was able to fdisk my drive and wipe out my win98 install and repartion but I am unable to get the cd to boot into the ubuntu install. Now I have a standard cd-rom. Does it require a dvd-rom? If not is there some command I can type in to start the install? I can find anything that really helps. All the sites I find that talk about installing refer to the GUI interface. Thats fine...if you get one. Anything special I should try, or should I download kubuntu and try that instead?](*,)

---

### Post by hopstah on 2006-08-30
you may have not downloaded what is called the "live cd".  the live cd differs from the cd which i assume you have by including the GUI interface you have read about.  try and redownload one of the livecd downloads and see if that's the case.  I highly suspect that it is.  you can install it from the cd that you have, but it's much less convenient.

---

### Post by goatflyer on 2006-08-30
Your machine is plenty good enough for Ubuntu, its almost my specs exactly.

The 6.06 desktop cd is the one you want.  It boots into a graphical installer.

You are burning the iso file as an image, right?  Not as a regular data file?

The CD will boot when you power up if your BIOS is set to boot from CD first.

Can you be more specific about the kinds of DOS-looking messages you see?  It will help diagnose your situation.

---

### Post by deadgobby on 2006-08-30
> **eldar said:**
> Got an older laptop. gateway 5300. 256 ram, 850P3, 8meg vid (I think). 8gb hdd.

I downloaded ubuntu from one of the mirror sites listed on this site. None of them boot in anyway. Finally burned one at 8X and it got me into some goofy DOS looking setup. I was able to fdisk my drive and wipe out my win98 install and repartion but I am unable to get the cd to boot into the ubuntu install. Now I have a standard cd-rom. Does it require a dvd-rom? If not is there some command I can type in to start the install? I can find anything that really helps. All the sites I find that talk about installing refer to the GUI interface. Thats fine...if you get one. Anything special I should try, or should I download kubuntu and try that instead?](*,)
 Do you have the 5300 with a pIII or Celeron, If a pIII you will most likly need to use Ubie's Alternative ISO. Try Kubie and see what happens. 
GUI tool for setting up / configuring SAMBA shares on Ubuntu.
 I guess at the DOS looking screen type in ls ( LS ) in lower caps. See if you get a listing of files. 
 I think if you type in install it will go. 
Gobby

---

### Post by eldar on 2006-08-30
Comes up with starting Caldera DR-DOS

Then loads cd-rom drivers and other drivers.

Says "no ntfs volumes found, exiting"

Then comes to

Caldera DR-DOS 7.03
some copyright stuff then and ends with
[DR-DOS] a:\

I will see if I can set to ntfs since it looks like thats what it wants.

Otherwise, how would I get the "live" download?

---

### Post by jISh on 2006-08-31
How on earth would you end up with Caldera DR-DOS coming up with a blank hard drive and an Ubuntu CD? Really..what did you do! Heh. Are you sure you don't have a floppy in your drive? A DR-DOS boot floppy, perhaps?

'Cause, ya know, it can't find an NTFS partition since you wiped it out. And seems you didn't repartition properly, not to mention it'd be useless since it would create FAT16 or FAT32 which you don't want for Linux.

And it seems to kick you back to the A:\ prompt, which further ignites my suspicions of a floppy disk in there. You're on a laptop you say? You have a  CD-ROM and floppy drive both in there at once?

And no, the Ubuntu install is a CD, not a DVD.

After checking for a floppy disk, when you reboot, pop into your BIOS for a moment and make sure it's set to boot from CD-ROM FIRST.

So you're probably at a DOS-looking screen because you're in DOS.

And for the record, DOS is what looks like UNIX. :P

---

### Post by eldar on 2006-08-31
Nope no floppy drive. Cant have both floppy and cd in my laptop. They both use the same port.

The dr-dos does not have an option for ntfs. Nope this dos things comes from the cd I made after I had to burn it a 8X to get anything from the disk. Got it from a mirror site link, on this very site.

So I will put in my winXP disk and format to ntfs then, and try my disk again....tomorrow anyways. Unless there is a tool that will do this that I can download.

---

### Post by Carbonfish on 2006-08-31
eldar,

If you go in to your BIOS and change the boot order so that your machine boots to the CD-ROM drive first, you shouldn't have to use your XP disk to format the HDD. Ubuntu will do that for you on install. If you aren't sure how to change the boot order, just restart the computer and hold down either the F1 key, or the "escape" key (it's been a few years since I've used a Windows machine except under duress) while it is booting, it should take you to the BIOS set-up menu. Just find out where the boot order is set, and use your arrow keys to move the CD-ROM drive to the top of the list. Then insert the Live-CD and restart the machine.

Ubuntu will do the rest. Since you are not trying to dual-boot, just let the installer do its thing.

You should be fine.

KC

---

### Post by mssever on 2006-08-31
It's likely that the DR-DOS business comes from a rescue partition in the hard disk. Which means that your BIOS is set to boot from the hard disk before the CD.

---

### Post by msandersen on 2006-08-31
I'm with msserver, if you don't have a DOS floppy or downloaded a completely wrong CD image, then it would have to be a hidden rescue partition. The messages have nothing to do with Linux.
There are a lot of different BOISes and ways of getting into them on startup. On an old Gateway desktop I have, I think it's the **DEL** key (ironic I know; no Gateway key) you hold down on startup. It should say which key explicitly somewhere during startup, even if it's only flashed briefly.
Since there are different BIOS versions, I can't tell you exactly where the boot order is set in yours, but it should tell you somewhere how to change the setting; ie it may be by using the Page Up/Page Down keys, or by hitting Enter and changing it in a popup. You'd want the CD-ROM to be first, *then* the hard drive.
Then you'd want to go to Save on Exit, or whatever the option is called, as long as the changes are saved before exiting.

Personally I installed Dapper using the Alternate CD, because I read some people having problems with the Graphical version, and because I preferred to upgrade rather than doing a clean install.

---

### Post by 3rdalbum on 2006-08-31
Congratulations, you've just had your first important lesson in Linux: If you're unfamiliar with something, read the instructions first.

Let me explain what's happened. You've gone into Nero and chosen to create a "bootable CD". This setting creates a CD with a DR-DOS installation. This is not the correct way to create a CD from an ISO. What's happened is that you've now got a CD which contains DR-DOS and an Ubuntu ISO file.

Start up another computer into Windows, put your munted CD in, and copy the ISO file back off it. Now, in Nero or another CD burning program, use the "Burn Disc Image" function to burn the image to disc the correct way.

Before you go through the install, I suggest you read the documentation on the disc to make sure you understand the technical terms and procedures which will be used.

---

### Post by msandersen on 2006-08-31
Never used Nero to make a bootable CD, so never thought of that. I suppose DR-DOS must be Nero's default boot image. A quick Google comes up with this post of the exact same problem:
[http://ubuntuforums.org/archive/index.php/t-10681.html](http://ubuntuforums.org/archive/index.php/t-10681.html)
which confirms it.
Rather ironic getting Caldera DR-DOS when trying to install Linux :) (I assume it's the same Caldera which changed its name to Sco).
So not so much a Linux lesson as a general computing lesson, though I generally don't read the manual either if I can discover it myself, except if it's a partitioning tool or something dangerous.
3rdalbum's tone is more than a little condescending, it's not obvious to even experienced users, especially to people not familiar with Nero boot CDs.
You could also say it's a lesson in searching first. though results vary depending on what you search for.

---

### Post by eldar on 2006-08-31
I did do a boot disk in nero. It has actually been the only disk to do anything. Bios is set to cd-rom which is how the caldera is coming up. I am not that much of a pc noob. 

I can whip up a good machine and know my way relatively well on XP and 98. I never used nero though to make a boot disk or had any prior exp with any linux.

SO I will try one more disk at as slow a speed as I can burn cause I have read that can be an issue. Otherwise, I might just order the disk. What image should I be downloading?

---

### Post by confused57 on 2006-08-31
There is an option in Nero to burn cd "as an image", which is what you want...look for the keyword "image".  As you already know, burn at a slow speed.

You probably want the  ubuntu-6.06.1-desktop-i386.iso, which is the live cd and installation cd also.

An excellent guide for burning an iso:
[http://www.psychocats.net/ubuntu/iso.html](http://www.psychocats.net/ubuntu/iso.html)

---

### Post by eldar on 2006-08-31
Thats how I tried to burn it the first 3 times, speed may have been the issue.

Otherwise, I think that is the image I downloaded. Not home right now to check though.

---

### Post by oliverb on 2006-08-31
Just a long shot but...could it be that the bios doesn't fully implement bootable CDs but only boots CDs with a FAT-based floppy image. If so it might require some kind of chain-load to get it running first time.

---

### Post by msandersen on 2006-08-31
Just so we're perfectly clear... ***don't*** burn the ISO image as a *Bootable Data Image*. This is where Nero adds the DR-DOS stuff.
If you're using Nero Express, choose ***Disc Image or Saved Project***.
If using the full version of Nero, cancel the *New Compilation* window you get and go to the top menu:
***Recorder -> Burn Image...***
Find the downloaded ISO image you downloaded and open it, set any parameter you want like the burn speed, and Burn it. 
That's it.

---

