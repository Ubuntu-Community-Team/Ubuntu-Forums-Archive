---
title: "Accessing Windows Share - Default Program for File Types"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by Cat.Food on 2007-04-30
Hi!

I've got all the PCs in my home network connected to a Linksys BEFSR81 router.  Everything works great!

One of my PCs acts as a file and print server.  It runs Windows 2000 Pro SP4.  I know, I know... I should probably use Linux on my file and print server, but I'm not quite that proficient with Linux yet...  I'm also too cheap to buy a copy of Windows server.  Since I'm the only one who uses this network, the limitations of Win2K Pro as a server don't really bother me... I just need it to store my files and print my documents.

So anyways, I have this Win2K box sharing out a few directories to my network.  The filesystem on the Win2K box is NTFS.  Using Ubuntu, I can connect to it just fine.  I can read files, write files, and execute them without any problems whatsoever.

On my Ubuntu box, I have it set to use GQView by default for opening pictures, *.jpg, *.gif, etc etc etc.  As long as the files are located on my Ubuntu box's hard drive, this works just fine.  If I access any jpegs or gifs on my Windows share,  Ubuntu attempts to open them with GIMP by default.  Is there any way to fix this so that Ubuntu will use GQView by default when accessing pictures on my windows share?

I've already tried going into properties and changing the "open with" to GQView.  It doesn't matter... If the file is on the same hard drive as Ubuntu, it opens just fine with GQView.  If the same file type is on the Windows share, it opens with GIMP.

I would like to set Ubuntu to use GQView by default for any type of *.jpg or *.gif file, no matter where it is located.  How can I do this?

Ubuntu 6.06.1 Dapper Drake
AMD Athlon 1400
768MB RAM
ABIT KT7A Mainboard
NVIDIA GeForce 3 Ti500 Video Card
SoundBlaster AWE64 Value Sound Card

---

### Post by rmt on 2007-04-30
I would like to see this one answered, very interesting, sorry I can't help :( , but I will keep an eye on it :)

---

### Post by Cat.Food on 2007-05-01
RMT,

Thank you for the interest!  I've found an answer by myself!  Most satisfying...

A bit of a note first though... further investigation revealed that I was unable to view *.jpg, *.gif or any other type of picture file using any of the programs I have installed in Ubuntu when connecting to the windows share.

So, here's the deal.  It isn't a problem with Ubuntu.  The problem lies with the programs I'm attempting to use to view pictures on my windows share.  GQView and the others are unable to access/process/view files that aren't a part of the linux filesystem.  When I'm using PLACES->CONNECT TO SERVER or any of the other options under PLACES, it allows me to access those shares, but it does not mount them into the Linux filesystem.  This is key!  It explains why I could view pictures stored on my hard drive just fine, but couldn't view the pictures on my windows share.

To get around this problem, I had to mount my windows share into the Linux filesystem.  I found a great page with info on how to do this here:

[How To Mount Windows Share into Linux Filesystem]("http://blog.abmas.biz/2007/04/28/hwto-mount-windows-share-into-linux-filesystem-using-smbfs-in-ubuntu-linux-or-any-other-linux-distro/")

Now, typing the command every time I want to mount or umount that share is gonna be a hassle.  I was hoping to write something like a DOS batch file to handle this for me.  The goal would be to just create the Ubuntu equivalent of a shortcut linking to the batch file so I could mount or unmount the share with a click of the mouse.  Ubuntu and Linux don't use DOS batch files (doh!), but they do use shell scripts.  I found info here on how to write simple shell scripts and make shortcuts to them:

[How To Create Batch Type Files]("http://ubuntuforums.org/showthread.php?t=412206&highlight=batch+file")

Note that writing these scripts for the mount and umount commands will make your passwords vulnerable to anybody with root access to the PC.  I think this also includes the possibility of somebody booting with the Live CD.  As such, this method should be considered EXTREMELY insecure!  But it should work!  ;)

I haven't tried it yet... I'll experiment more with writing simple shell scripts later....

---

### Post by Cat.Food on 2007-05-02
A bit of clarification, just in case somebody else stumbles across this thread looking for similar answers:

In Ubuntu, connecting to a windows share using PLACES->CONNECT TO SERVER is the windows equivalent of clicking START->RUN and typing in the name of a network resource such as "\\winserver\sharedfolder".

In windows, programs like IrfanView don't have a problem opening or viewing picture files using that method.  In Ubuntu (and probably all flavors of Linux), most programs will have a problem.  To get around this problem, you need to do the Linux equivalent of "Map a Network Drive" in windows.

To "map a network drive" in Linux, you need to mount the windows share into the Linux filesystem.  In the world of windows, you would simply pick an unused drive letter and map the share to that drive letter.  In Linux, you need to create an empty directory someplace and mount the windows share to that empty directory.  You can then access the windows share because it is now a part of the Linux filesystem!  Just don't forget to umount it when you're done!

I hope this makes sense...

---

