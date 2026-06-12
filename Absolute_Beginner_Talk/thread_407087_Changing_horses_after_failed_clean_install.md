---
title: "Changing horses after failed clean install"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by jimmj43 on 2007-04-11
I have a Compaq Presario desktop, 900MHz, 256M, 30G and had reformatted it so I could do a clean install of Ubuntu (disk mailed from Ubuntu). No joy. Too many hours & not enough sleep. Decided to try a different approach and thought I'd ask about feasibility. I just finished installing W98se. What next? Is the partitioning process a totally separate step or will Ubuntu do that on its own on the install? Or am I just fulla beans?

I just had a brainstorm(?). I have an extra HD or 2 laying around. Is there a means by which I can install a 2nd HD and load/run some version of Windows (I'm partial to W2Kpro) on one and load/run Ubuntu on the other?
What would be entailed (assuming I'm not fulla beans again/still)?

---

### Post by theonlyrealperson on 2007-04-11
I do that too, with FreeBSD and Ubuntu. What you need is to reconfigure the boot sector to tell it to load the operating system you choose. 

I use the GAG bootloader, it allows me to choose which harddrive to boot off of even if it's on the "slave" drive. The thing to remember though is you still need to install grub, just make sure it's on the "root" of your Ubuntu harddrive (hd0,1 probably) and not on the bootsector (hd0,0 for instance).

You can get GAG here:
[http://gag.sourceforge.net/]("http://gag.sourceforge.net/")

You don't need to do anything special with the Windows install. Just install Windows first, then install GAG.

---

### Post by igknighted on 2007-04-11
> **theonlyrealperson said:**
> I do that too, with FreeBSD and Ubuntu. What you need is to reconfigure the boot sector to tell it to load the operating system you choose. 

I use the GAG bootloader, it allows me to choose which harddrive to boot off of even if it's on the "slave" drive. The thing to remember though is you still need to install grub, just make sure it's on the "root" of your Ubuntu harddrive (hd0,1 probably) and not on the bootsector (hd0,0 for instance).

You can get GAG here:
[http://gag.sourceforge.net/]("http://gag.sourceforge.net/")

You don't need to do anything special with the Windows install. Just install Windows first, then install GAG.

Can't you just either (a) install windows on one drive and linux on the other, then use grub to boot both, or (b) use the bios to select which drive to boot from (F8 on my comp)?  I wasn't aware there was an issue booting from "slave" drives, I do it all the time (including on a machine like the OP's).

---

### Post by theonlyrealperson on 2007-04-11
Really? I always thought there was a problem with booting from a slave drive. Oh well... But this way you don't have to change settings in your BIOs every time.

I'm sure you can do it in Grub - but I'm still a little green with Linux. GAG is extremely easy to set up - and it's graphical.

---

### Post by jimmj43 on 2007-04-11
OKAY, the GAG utility looks very promising. I like that it includes an option to uninstall an entire OS without disturbing whatever other OSs are resident.

But I have a total ROOKIE question: I wanna burn it to a disk, am clueless. I D/L'd the zip file, then unzipped it, then opened that file to have a look. Here's what I'm faced with:

[IMG]http://img394.imageshack.us/img394/4687/gagjx4.jpg[/IMG]

I've got Nero, but....... Up top in the image there are 3 unopened folders. Do I just select all as shown in the image or am I gonna hafta open each of those folders, etc, etc..? Alternatively, can I just burn an image of that single folder that emerged on my desktop upon unzipping?


Sidenote question: Can anyone give me step-by-step instructions (in newbie terms) describing how to install a 2nd HD. I have an open bay and a sharply limited budget.

---

### Post by IndyBob on 2007-04-11
I have Ubuntu Edgy on one drive as master and Windows XP or second drive as slave and edited Grub Menu as listed in the link below and it works like a charm.

[http://ubuntuforums.org/showthread.php?p=677880#post677880](http://ubuntuforums.org/showthread.php?p=677880#post677880)

---

### Post by theonlyrealperson on 2007-04-12
> **jimmj43 said:**
> 
But I have a total ROOKIE question: I wanna burn it to a disk, am clueless. I D/L'd the zip file, then unzipped it, then opened that file to have a look. Here's what I'm faced with:

I've got Nero, but....... Up top in the image there are 3 unopened folders. Do I just select all as shown in the image or am I gonna hafta open each of those folders, etc, etc..? Alternatively, can I just burn an image of that single folder that emerged on my desktop upon unzipping?


If you are going to use a CD instead of a floppy, the only thing you want to burn to a disk is the .iso file. Now, I noticed by the looks of the icons that Windows isn't picking up .iso files for what they are. So, I'd guess that Nero can't burn an iso properly. 

.iso's are really archives that need to be burned differently than a normal file for them to work correctly.

I don't know if anyone has any better Win programs for burning .iso's, but I used to use DeepBurner. It's freeware, and you can get it from [http://www.filehippo.com]("http://www.filehippo.com")

If it isn't on the front page, do a search for it on the site. Follow the direction in DeepBurner to burn the .iso to disk.

Good luck!

---

### Post by IndyBob on 2007-04-12
That's correct, you need the .iso file.  Search on these forums and somewhere it gives the link for a Windows program called InfraRecorder or you could try to "Google" InfraRecorder.  I downloaded that and burnt my Ubuntu CD's with that in Windows.  One word of caution, burn the CD at a slow rate of around 4 as they seem to fail if burnt at high speeds.  Also be sure you burn an "Image" of the file and don't make a copy of it.

---

### Post by jimmj43 on 2007-04-12
hmmmm....... I'm still unclear. If you can take a 2nd look at ^that^ image, you'll see 3 unopened files at the top of the list, then the 1st opened file is an ISO. I'm guessing I'll need to burn the whole ball of wax rather than that single ISO file, correct?

Thanks, guys.

---

### Post by theonlyrealperson on 2007-04-12
> **jimmj43 said:**
> hmmmm....... I'm still unclear. If you can take a 2nd look at ^that^ image, you'll see 3 unopened files at the top of the list, then the 1st opened file is an ISO. I'm guessing I'll need to burn the whole ball of wax rather than that single ISO file, correct?

Thanks, guys.

The first three files in that image are folders with stuff you don't need (unless you want to read the documentation, it comes in handy.) The .iso on there isn't actually "opened". Once you get on Linux you'll see what I mean. .iso's are archives like a folder (there are actually files inside that .iso file - THAT is what is burned to the CD), but Windows doesn't know how to handle them without having special programs. (Most Linux Distro's can read them naturally.) You are seeing the file, but you aren't seeing it opened.

99% of those files are for development and for putting GAG on a floppy disk.

The file you want for your CD is "cdrom.iso". You don't need any of the other files or folders.

Get InfraRecorder or DeepBurner or another .iso burner and just burn "cdrom.iso" to that disk. 

Don't just burn cdrom.iso to CD as-is - you have to do it specially or else it won't work.

As for your harddrive, just make sure that you have a power plugged in, the tape-like wire plugged in, and the "jumper" set right. The "jumper" is a little piece of metal and plastic on stuck on some metal pins on the back of your harddrive. Underneath it, there should be some letters like "M**, S**, C**" you want it set to the one beginning with "S". If you are still confused or don't see any letters underneath, Google the exact name of the harddrive and "jumper settings".

---

### Post by jimmj43 on 2007-04-12
Am I making this too difficult? I COULD copy that file to a floppy, but if I do, should I expect it to unload and install properly? BTW, the machine I'd be loading it into currently only has W98se installed.

---

### Post by theonlyrealperson on 2007-04-12
> **jimmj43 said:**
> Am I making this too difficult? I COULD copy that file to a floppy, but if I do, should I expect it to unload and install properly? BTW, the machine I'd be loading it into currently only has W98se installed.

No! Not at all! I couldn't help you with the floppy disk one anyway - I don't even have a floppy disk anymore. 

If you do copy it to a floppy disk, you have to follow their directions, you couldn't just copy all the files to floppy. You have to make the floppy "bootable", which I remember is explained in all their directions.

Or, you could just skip GAG for now and follow IndyBob's directions in setting up Grub. Then all you have to worry about is getting that second harddrive in and loading Ubuntu on it...

---

### Post by forkart on 2007-04-29
> **jimmj43 said:**
> OKAY, the GAG utility looks very promising. I like that it includes an option to uninstall an entire OS without disturbing whatever other OSs are resident.

But I have a total ROOKIE question: I wanna burn it to a disk, am clueless. I D/L'd the zip file, then unzipped it, then opened that file to have a look. Here's what I'm faced with:

[IMG]http://img394.imageshack.us/img394/4687/gagjx4.jpg[/IMG]

I've got Nero, but....... Up top in the image there are 3 unopened folders. Do I just select all as shown in the image or am I gonna hafta open each of those folders, etc, etc..? Alternatively, can I just burn an image of that single folder that emerged on my desktop upon unzipping?


Sidenote question: Can anyone give me step-by-step instructions (in newbie terms) describing how to install a 2nd HD. I have an open bay and a sharply limited budget.

You can try using magiciso to burn iso file to cd and dvd. It works fine.
[http://www.magiciso.com/tutorials/miso-burnwin.htm](http://www.magiciso.com/tutorials/miso-burnwin.htm)

---

