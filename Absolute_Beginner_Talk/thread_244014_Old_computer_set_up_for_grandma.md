---
title: "Old computer set up for grandma"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by SpiffyChee on 2006-08-25
My grandma has an old computer dell 500mhz and its got windows 98 on it.
I deleted everything so it is ready to be reformatted with either windows 98 or linux. 

My goal is to set up the computer with kubuntu for my little cousins to play games and  browse the net. My grandma has a few games like 'freddie the fish' and 'arthurs interactive' for windows.
Am i able to run those few games on linux with wine or something, i am clueless on wine?

should i be looking at a different linux that is easier for kids. if so which should i use. Does linux crash? i wont be there to fix it. It will take a plane to get here. my grandma has a main comp to use, so this one will just be for games and internet, nothing else.


will there be a difference in speed with kubuntu than windows 98?

can i dual boot? what are the options there?



thanks. 
ps i have never installed linux before, just used a few live cds like this one (i am on the kubuntu live cd)

---

### Post by Kilz on 2006-08-25
> **SpiffyChee said:**
> My grandma has an old computer dell 500mhz and its got windows 98 on it.
I deleted everything so it is ready to be reformatted with either windows 98 or linux. 

My goal is to set up the computer with kubuntu for my little cousins to play games and  browse the net. My grandma has a few games like 'freddie the fish' and 'arthurs interactive' for windows.
Am i able to run those few games on linux with wine or something, i am clueless on wine?

should i be looking at a different linux that is easier for kids. if so which should i use. Does linux crash? i wont be there to fix it. It will take a plane to get here. my grandma has a main comp to use, so this one will just be for games and internet, nothing else.


will there be a difference in speed with kubuntu than windows 98?

can i dual boot? what are the options there?



thanks. 
ps i have never installed linux before, just used a few live cds like this one (i am on the kubuntu live cd)

With that older computer I would recomment Xubuntu for the lightweight xfce desktop. I also think fluxbox is avaiable in the repo's once its installed thats even lighter. Kubuntu with kde might run to slow for that old hardware.
Linux is rock solid, crashes are rare once its setup and running. There are lots of native games included, wine will run windows games but only some of them.

---

### Post by djsroknrol on 2006-08-25
I would stick with a dual boot setup so the kiddies can still play Freddie and the Arthur stuff...Grandma would probably be more at home with the Linux side for Internet, etc....Gee.I remember getting Freddie the fish for my kids. Glad to know they're still popular as they were good titles...How time flies...

---

### Post by SoloSalsa on 2006-08-25
I'll say there will be a difference!
   First thing first:  how much RAM is there?  You *must* have at least 256MiB to use the (main) Ubuntu familly.
   Even if you have sufficient memory, with that processor, I would not suggest Kubuntu.  KDE is kinda power hungry.  Gnome is okay, XFCE is much better.  You can use KDE if you do a server install, but that takes a bit more work.  There are plenty of other distro's, but Ubuntu is pretty nice and easy.  Really, for its intended use, Win98 is okay.
   I'm using Linux on my laptop.  It had the same 500Mhz.  I tried Ubuntu, then Xubuntu.  Xubuntu is a wee bit less friendly, but faster, for sure.

---

### Post by SpiffyChee on 2006-08-25
thanks guys, im just about to install xubuntu.
how do you dual boot windows 98 and xubuntu, i found a tutorial for xp but not 98. i dont know. 

and if i did get it to dual boot, would it go into an ugly selection for os everytime i turn on the computer that kids wont understand?

---

### Post by msak007 on 2006-08-25
> **SpiffyChee said:**
> and if i did get it to dual boot, would it go into an ugly selection for os everytime i turn on the computer that kids wont understand?

For that, you can try using "gfxboot" per [this thread]("http://www.ubuntuforums.org/showthread.php?t=208855"). I've gotten it working and it looks great for the OS selection.

---

### Post by confused57 on 2006-08-25
> **SpiffyChee said:**
> thanks guys, im just about to install xubuntu.
how do you dual boot windows 98 and xubuntu, i found a tutorial for xp but not 98. i dont know. 

and if i did get it to dual boot, would it go into an ugly selection for os everytime i turn on the computer that kids wont understand?

Before you do anything, I recommend that you make a Win98SE boot floppy so that you can restore the Windows mbr if something goes wrong during the Xubuntu installation, as described here:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)
Basically, you would go to:
[http://www.bootdisk.com/](http://www.bootdisk.com/)
Download the Win98SE OEM boot disk, format a floppy, double-click on the .exe & you'll have your boot floppy...to restore the mbr, boot up with the floppy, enter **fdisk /mbr** to restore your Windows mbr.

You might need to defragment Windows before beginning the Xubuntu installation, makes it easier to resize the Windows partition.
Might want to read over this guide before installing: 
[http://psychocats.net/ubuntu/installing.html](http://psychocats.net/ubuntu/installing.html)

---

### Post by Jerome36 on 2006-08-25
I don't know how big your hard drive is, but you might want to defrag it, before you partition... if you're putting both Operating Systems on the same hard drive.

---

### Post by Sef on 2006-08-25
Xubuntu would be best with your computer if it has 128 mb ram. It can run on 64 mb ram, but 128 is recommended.  

Before you dual boot, [read this.]("http://www.users.bigpond.net.au/hermanzone/")

---

### Post by SpiffyChee on 2006-08-26
Ok i wish i read that post about making a floppy disk before i did it, but i found a site with bootdisks so i think that should work too.


I tried installing xubuntu linux, but it stopped installing hlaf way through. so i turned the computer off. now i cant do anything with the hard drive. i cant install windows, i cant install linux, its messed.

i dont have another hard drive, so is there some way i could take that hard drive and bring it to the other windows comp and format it while its hooked up to that?I dont know how to format hard drives. I tried the boot disk thing, but i couldnt figure out what letter my cd drive was.


please i need help. thanks

---

### Post by confused57 on 2006-08-26
> **SpiffyChee said:**
> Ok i wish i read that post about making a floppy disk before i did it, but i found a site with bootdisks so i think that should work too.


I tried installing xubuntu linux, but it stopped installing hlaf way through. so i turned the computer off. now i cant do anything with the hard drive. i cant install windows, i cant install linux, its messed.

i dont have another hard drive, so is there some way i could take that hard drive and bring it to the other windows comp and format it while its hooked up to that?I dont know how to format hard drives. I tried the boot disk thing, but i couldnt figure out what letter my cd drive was.


please i need help. thanks
Can you make the Win98SE OEM boot floppy on the 2nd Windows computer?  Does your grandma possibly have any disks or floppies that came with the computer?

---

### Post by SoloSalsa on 2006-08-26
Ah! You're in a pickle if you needed any data...  Actually, you're not.  There are plenty of things you can do.  I'm online like 18 hours daily, so respond whenever.
Okay.  Here's what you do.  If you **do not** need anything presently on the drive, then just reformat it.  How?  With [this.  Gnome Partition Editor]("http://gparted.sourceforge.net/") is the same editor that the Xubuntu installation uses.  To get it, you will need a cd burner, assuming your other computer has one.  If not, then you'll need to follow your own plan: hook it up to a different computer.
Again, contact me whenever, as soon as you need help!  To do that, click on my name, and then 'send SoloSalsa a private message'.  Or just follow-up on this forum.

---

