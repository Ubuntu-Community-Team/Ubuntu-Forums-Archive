---
title: "Gtkpod not reading songs off of ipod shuffle"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by seaworthy4life on 2007-06-05
This is a new installation.  Rhythmbox sees the songs.  It seems to be mounted properly.  When I try to load ipod in gtkpod, I get this message:

> Could not find iPod directory structure at '/media/ipod'.  If you are sure that the iPod is properly mounted at '/media/ipod', gtkpod can create the directory structure for you.

Do you want to create the directory structure now?'

So I try to create new directory structure with ubuntu-gtkpod.  iPod mountpoint: /media/ipod, check.  Then, when it asks for model #, it shows all of these different generations of models, and inside all of these different fields, I only find one model that is 512 MB Shuffle, but it's not the same model no. as the one I bought at megastore Target.  So I try the one model that almost fits. 

Then, I get this error message.

> Error initialising iPod: Problem creating iPod directory or file: '/media/ipod/iPod_Control'.

Before I changed distros, it seems that I may have had this type of problem with suse10.0-gtkpod, even though Rhythmbox reads it just fine.

Do I simply need to go to the Apple store and reformat it with vfat?  I am going to try that and see what happens.

I did one of these to see if it helps, though everything probably looks alright to you, as well.

> justin@justin-desktop:~$ sudo tail -f /var/log/messages
Jun  5 16:24:50 justin-desktop kernel: [186838.383663] usb 4-1: configuration #1 chosen from 2 choices
Jun  5 16:24:50 justin-desktop kernel: [186838.384709] scsi5 : SCSI emulation for USB Mass Storage devices
Jun  5 16:24:54 justin-desktop kernel: [186843.380914] scsi 5:0:0:0: Direct-Access     Apple    iPod             2.70 PQ: 0 ANSI: 4
Jun  5 16:24:54 justin-desktop kernel: [186843.387986] SCSI device sda: 1015040 512-byte hdwr sectors (520 MB)
Jun  5 16:24:54 justin-desktop kernel: [186843.389480] sda: Write Protect is off
Jun  5 16:24:54 justin-desktop kernel: [186843.393298] SCSI device sda: 1015040 512-byte hdwr sectors (520 MB)
Jun  5 16:24:54 justin-desktop kernel: [186843.394297] sda: Write Protect is off
Jun  5 16:24:54 justin-desktop kernel: [186843.394330]  sda: sda1
Jun  5 16:24:54 justin-desktop kernel: [186843.398993] sd 5:0:0:0: Attached scsi removable disk sda
Jun  5 16:24:54 justin-desktop kernel: [186843.400592] sd 5:0:0:0: Attached scsi generic sg0 type 0
Jun  5 16:51:48 justin-desktop -- MARK --

---

### Post by seaworthy4life on 2007-06-05
As I expected, after I reformatted it at the Apple Store, gtkpod is still not reading the directory structure that is already on it.  When I try to redo the directory structure using gtkpod, it gives me the same error.

---

### Post by seaworthy4life on 2007-06-05
This is definitely the best deal for ipod shuffles.


[http://sourceforge.net/project/showfiles.php?group_id=136446](http://sourceforge.net/project/showfiles.php?group_id=136446)


> 
someusernoob's Avatar 	
someusernoob someusernoob is offline
A Carafe of Ubuntu
	  	
Join Date: Feb 2006
Location: The Netherlands
Beans: 216
Send a message via ICQ to someusernoob
Re: Problems with iPOD shuffle??
The iPod Shuffle works different then the normal iPod models (and the Nano), I couldn't get mine to work with any iPod 'application' on Linux. Therefor I use this little script: [http://shuffle-db.sourceforge.net/](http://shuffle-db.sourceforge.net/)

Just plug your iPod in its dock and mount it as a normal USB Mass Storage Device (the default behavior here). Fill it with music (with Nautilus/Konqueror like any other normal mp3-player), place the script from the link above in the root dir of your iPod (/media/iPod for example, depends on where you mount it/it has been mounted) and run it by double-clicking the file (it needs to be opened/executed by python). The database on the iPod will be regenerated and it will see the music you've copied to it.

Good thing is that you only need this script, no other application is needed anymore, bad thing is that you need to execute the script every time you change the music on the iPod.

Oh, and make sure when you unplug the iPod, you unmount it first by right-clicking on the icon on your desktop (I assume it is there). Copying files might be slow sometimes (when its memory is getting full), so the copy-process needs to finish first before you unplug it (sometimes it is still running while the copy-progress-bar is already done- when you unplug it at that moment you'll find your music to be incomplete).

---

### Post by NeoLithium on 2007-06-05
When rhythmbox scans the ipod, what directory is it mounting on?  It might be automatically mounting on something else other than /media/ipod.  Perhaps you just need to tell GTKPod to look in another mount point?

---

### Post by hkahwaji on 2007-06-06
Hi

I have a shuffle and I had the same issue with gtkpod. Rythmbox is mounting the ipod on /media/ADMINISTRAT_/iPod_Control

I just think that gtkpod is not handling the mounting properly.

---

### Post by hkahwaji on 2007-06-06
Guys

gtkpod thinks that the ipod is mounted to /media/ipod and that is not the case. I used Rythmbox and verified that it is mounted to /media/ADMINISTRAT_

I fixed the problem by telling gtkpod where the ipod is mounted to. Launch gtkpod and go to -> Edit -> Edit Repository/Ipod-Options and from there browse to the proper mounting point.

I hope this helps. It worked for me

---

### Post by hkahwaji on 2007-06-06
Now, gtkpod does see and populate all the songs in iPod, but I can not copy the songs to the filesystem. I get an error. Not suppoted file type.

Any idea

---

### Post by smilesleepy on 2007-06-06
I was having the same problem. It said it couldn't find my /media/ipod - 
so i opened in terminal 

sudo gktpod

low and behold, it loaded up all my songs.

---

