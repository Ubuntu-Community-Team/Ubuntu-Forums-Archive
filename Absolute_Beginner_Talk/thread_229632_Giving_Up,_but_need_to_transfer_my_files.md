---
title: "Giving Up, but need to transfer my files"
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by haze03 on 2006-08-04
I tried to set-up my old k6-2 500 box with ubuntu to use as a file/music server, but for me it just sucked.  The system was way slow and wireless just wouldn't work.  So, I picked up an old powermac g4 on craig's list to use instead, but need to transfer my files. I have an external usb drive, i started transferring, went to bed, woke up, and it froze about 6 files in.  Now I can't transfer files to the external drive because it says I don't have permission to write to the drive.  Which is funny because there is only one user on the system, I logged in as that user, and teh properties of the disk says the same user that i logged in as is the only one who can write to the desk.  Not to mention I wrote 6 files to it last night.  So, any suggestions?  The external drive is formatted hfs and I believe I am running 5.10.  These sogs have been on here for 6 months without me being to access because wireless won't work, so I would really appreciate the help.

---

### Post by stormblue on 2006-08-04
You could try FTP or maybe a SAMBA network.

---

### Post by aysiu on 2006-08-04
Have you tried installing *hfsplus* and *hfsutils*?

---

### Post by haze03 on 2006-08-04
I can't ftp/samba, I have no network connection.  I only have wireless switch/router access, I could never get it to work, and now the wireless card is now in the powermac.  

As for installing those tools, I don't see the purpose.  I already copied over two files, so teh support is there.  I just don't get why it says only user x has write permission and i am user x.  I can't change the permissions because it says only user x can and. once again, I am user x.

---

### Post by aysiu on 2006-08-04
Press Alt-F2 ```
gksudo nautilus
``` Then no permissions can be denied you.

---

### Post by OU812 on 2006-08-05
Could you burn the files to cds or dvds?

john

---

### Post by haze03 on 2006-08-05
Thanks aysiu I will try that.

As far as burning goes, I have 180 GB.  That would taker forever to burn.

---

### Post by haze03 on 2006-08-05
i tried gksudo nautilus from terminal and got the following error:

xlib: connection to ":0.0" refused by server
xlib: No protocol specified



(gksudo):7350): Gtk-WARNING **: cannot open display:

---

### Post by haze03 on 2006-08-06
alt+f2 was a no go.  the dialog box open, i typed in gksudo nautilus and the dialog box closed.  no programs opened and i still go the no permission to write error when i tried to copy files.  

so frustrating.  i have spent a good 20 hours on set-up, diagnosis, etc and not once have actually accessed the files over my network and listened to the music.  i even bought a rt250 chipset wireless card with linux drivers, but it would not cooperate with the network encryption, only when the encryption was turned off.  and i so wanted to use amarok.  i have been trying to compile/install amarok natively on my powerbook so that I don't always have to have my windows box running with foobar.  

now i get 1 1/2 folders copied, finally thinking i can get these backed up flac files to the powermac i picked up and stinking computer won't give me permission to write files anymore.  grrrrrrrrr.  having five computers running in my room right now you'd think i'd be able to cope with the frustration, but dang it "i just want my music!!!!"  it took forever to backup to flac.

---

### Post by kebes on 2006-08-06
Instead of using an external USB drive, why not just remove the hard drive with the data you want, and put it as a slave in the other computer (that you want to transfer onto). Transferring drive to drive will be very fast.

I don't know exactly what your hardware is... so this might not be an option, but if it is possible with the computer(s) you have at hand, I think this would be fairly straightforward.


If not, could you format the USB drive with Linux? (or is there other data you don't want to erase?) With a formatted drive I imagine there would be no problem copying files onto it.

---

### Post by haze03 on 2006-08-06
i am going to have to get the other data off and format in linux.  i tried popping it into my powermac, there is a cool util on sourceforge called extfsx, but it was uncooperative with the Tiger version of OSX.  i was excited when i came across the program because that would be the fastest and easiest way. 

on a side note, i liked ubuntu.  i remember the first time i gave linux a try, it was back in 1997 and it was such a pain.  i used for a week, but i only had 6.4 gb hdd space so it had to go.  anyhow, with different components ubuntu would be good, it just wasn't cooperative with my system.  mostly because i could add repositories and install from the universe because i only have a wireless connection where i am at and the wireless never managed to work right.  plus, i couldn't d/l drivers for teh video.  i have a 20.1 in dell lcd and ubuntu is running at 640x480.  it is so frustrating trying to do anything when you can't see all the windows.  i often can't click on open/close/save/etc.  it sucks.

---

### Post by haze03 on 2006-08-06
this isn't an ubuntu problem, but since it is a *nix problem maybe somebody can help.  i have once again tried to mount the linux drive in os x, but when i mount at the command line i get the error "mount: realpath /mnt: No such file or directory"  what does that mean?  the command i typed was sudo mount -t ext3 -w /dev/disk2s1 /mnt/ubuntu

---

### Post by kebes on 2006-08-07
Sounds strange. The only thing I can think of is that the directory doesn't exist. I presume you created the "ubuntu" directory in "/mnt/" on your OS X machine?

Do you still get the error if you "cd /mnt/" and then "mount -t ext3 -w /dev/disk2s1 ubuntu" ?

Probably you're not going to be able to read the Linux disk from OS X. Too bad, since that would have been the simplest.


Okay, there are two other "swapping hard drive" options I can think of:

1. If you can boot your Mac machine from a linux LiveCD (PPC version), then it will certainly be able to read the internal Linux HD with your data, and hopefully you can write the data to the Mac's internal HD.

2. You could create a fat32 partition on one of the disks, and use that to transfer the files (I believe OS X reads fat32 without trouble). So in your first computer you make a fat32 partition, copy the data into it. Then bring that disk over to the other computer and boot it as a slave under OS X. In OS X you then copy everything from the fat32 onto the Mac's HD.

(If you have an extra hard drive lying around, this would be even easier.)

I know this is getting really complicated, and must be frustrating you. It would have been much simpler if the USB hard drive just worked immediately! Anyways, best of luck.

---

### Post by haze03 on 2006-08-07
so i have tried another method.  i have ethernet card in the ubuntu box and the powermac has it built in, you'd think it would be as easy as turn on file sharing, connect the cable, transfer the files . . . not with linux.  i can't get either machine to recognize each other.  so i tested the powermac with my powerbook using the same method, worked great, could transfer files.  then tried powermac and windows, worked great, could transfer files.  tried ubuntu with anything, nada, take your ball and go home we don't play together.  i went and did gedit smb.config or whatever, says samba is installed and at the bottom it even showed the directory i wanted as being shared.  in file manager right click, says it is shared by SMB.  does it work?  no.  under network connections eth0 active, green light on the card.  what gives?  somebody help me before i kill myself.  it will be some time before i mess with linux again.  

also, how come stuff just stops opening?  says i mount my second disk and browse to the folder.  all works well.  then say i go back into places->network.  nothing opens.  say i go into system->admin->users (or whatever) nothing opens.  have to reboot to do anything.  what in the hell causes that?  kill me now.

---

