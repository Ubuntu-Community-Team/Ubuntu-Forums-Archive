---
title: "Perplexing Ubuntu installation issues"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by TygerTung on 2007-07-18
G'day,

I installed Ubuntu 6.06 as I couldn't manage to get 7.04 to work.

I downloaded both image files and when I made the disk of 7.04 nero was a bit concerned about somthing.

This is what it said:

Forign Image file: The entered block size does not correspond to the image length. The block size may be wrong. Do you want to correct the value or ignore the problem? Correct, or Ignore were the two options.

I just clicked ignore because when I went into correct it had all these funny options and you had to enter numbers and I didn't know what I was doing!!!

So I made up that boot disc and when I restarted the computer the ubuntu 7.04 screen came up no worries, except when you click the top option, load and install linux or somthing like that it just goes:

I/O error:

Error reading boot CD.

Reboot was the box you could click.

Up at the top it said: Loading Isolinux:[COLOR="Lime"]Disk errpr 32, AX=4200, drive 9F[/COLOR]

I had no idea what that was about but I thought that maybe there was an error with the disc because I burned it so fast so I tried burning it at 8 speed but it made no difference.

So I installed 6.06 and that installed without any issues:guitar: except it has me a bit stumped on a few things.

Whenever I try to go on the internet it will let me go to google and no other site apart from google. It will search on google and come up with results and everything, whenever it trys to go on any other site it just keeps looking and looking but will not find it.

Also I can't get any acess to my other hard drive with windows on it, I think it is because it is the NTFS file system? Also I have the same problem when on windows (XP Pro) I can't get into the drive with Ubuntu on it!!!!! Is there anyway of acessing each other drive? I want to transfer music and pictures and what have you across!!!!

Also on ubuntu, if I make the resolution any higher than 1152x684 I can't have any higher refresh rate than 60Hz, is that normal?

On ubuntu will I need to install drivers for all my hardware like the graphics card, motherboard etc?

Any help would be appreciated!

Cheers,

Sam

---

### Post by testube_babies on 2007-07-18
In Windows, you can install an ext driver to read the Ubuntu drive:
[http://fs-driver.org](http://fs-driver.org)

In Ubuntu, you need to install ntfs-3g.  I'm not sure this is available for Dapper.  I'd highly advise going with 7.04; not only does it have ntfs-3g available, but it makes networking a lot easier.  It also comes with a GUI manager for drivers.  But since you're having burning issues you can order it for free here (although I think you just need to re-download the image and try again):
[http://shipit.ubuntu.com](http://shipit.ubuntu.com)

Also, refresh rates tend to cause problems.  If it bothers you, searching the forums will yield plenty of different solutions.

---

### Post by TygerTung on 2007-07-18
Any idea why the internet might not work?

---

### Post by testube_babies on 2007-07-18
No, sorry.  Maybe someone else could help you out with that.

But ntfs-3g can be installed on Dapper as per this site...unfortunately you need the internet for the instructions to work:
[http://lunapark6.com/?p=1710](http://lunapark6.com/?p=1710)

---

### Post by TygerTung on 2007-07-19
I set 7.04 downloading before I went to work, will have to see if it works better when I get home.

Does anyone know anything else about these issues I am having?

---

### Post by davidjmayo on 2007-07-19
Try this
1 check your download is ok with md5sum 
2 follow this burning guide

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)  md5sum link in here too
[http://releases.ubuntu.com/feisty/MD5SUMS](http://releases.ubuntu.com/feisty/MD5SUMS) the md5sum number you need in here

---

