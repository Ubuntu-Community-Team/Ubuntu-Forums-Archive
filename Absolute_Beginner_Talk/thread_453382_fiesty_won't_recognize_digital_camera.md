---
title: "fiesty won't recognize digital camera"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by norcal on 2007-05-24
I have a casio exilim digital camera and am using 7.04. On the last version of ubuntu  the camera was instantly recognized and a folder was placed on the desktop. Now i get no satisfaction. any help appreciated.

---

### Post by Sparkster185 on 2007-05-24
Does any message pop up when you plug in the camera?  Are you able to use other USB devices in that slot without problems?

Can you find the device in /media ?  If you open up a camera management program (DigiKam, or something), can you connect to it that way?

---

### Post by norcal on 2007-05-24
nothing shows up in the media folder and nothing shows up on the desktop. i did run a command that i saw from another posting and the camera is recognized.

---

### Post by hakan69 on 2007-05-24
Hi
I have got the same problem with a Fujifilm S304. everything worked out of the box in Edgy, but not with Feisty. I can mount it manually, but automount doesn't work. 
Memory stick, USB scanner, USB-HDD automounts.
Regards Hakan

---

### Post by norcal on 2007-05-25
here is the output i get when running lsusb in terminal

Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 07cf:1001 Casio Computer Co., Ltd QV-8000SX/5700/3000EX Digicam
Bus 001 Device 001: ID 0000:0000  

so it looks like the camera is recognized i just can't figure out how to get the pictures.

---

### Post by Atomic Dog on 2007-05-25
If your camera setup mode will allow you to select the USB mode setting make sure you set it to "PTP." Ubuntu will suddenly see the camera and will start gthumb to pull down the photos.

---

### Post by norcal on 2007-05-25
thanks atomic dog. that did it. damn i am stoked.

---

### Post by Atomic Dog on 2007-05-25
> **norcal said:**
> thanks atomic dog. that did it. damn i am stoked.

2 for 2 today with help.  This is a record for me.  Usually you guys are helping me with problems!  You have no idea how long it took me to get my digital camera (a Sony) working.  Took me a long time to find this little setup trick, and it works.  So glad I was able to share this.  Giving back & stuff.

Now post some pics!

---

### Post by oxidas on 2007-05-30
Power in simplicity. Damn, I have been scanning the forums for some days, trying to find a solution, was even considering a kernel update. But all the time all I needed to do is change it to "PTP". Thanks Atomic dog!

---

### Post by misfitpierce on 2007-05-30
Yep a mode on cam does it sometimes... luckly for me my Casio just plugged and played... :)

---

### Post by .bashrc on 2007-05-30
Works like a charm on my Macbook as well. Thanks!

Search and ye shall find, as they say.

---

### Post by juretto on 2007-06-21
Hi,
I have the same problem with my Casio Exilim and my new Ubuntu 7.04.
I also tryed to set the USB mode to "PTP", but it doesn't work.
"lsusb" doesn't recognize any device, and also "tail -f /var/log/messages" doesn't show any output about the camera.
USB sticks work properly, and in the last 6.10 the camera worked fine.

The USB cable is OK, because it works on Win.
Help me please...
THX,
J.

---

### Post by juretto on 2007-06-22
Any other idea than the "PTP" setting?
I'm worry about the "lsusb" output... it doesn't recognize any device!

:(

THX,
J.

---

### Post by juretto on 2007-06-22
I guess could be the kernel version.
According to the latest Feisty upgrade, I have currently installed the **2.6.20-16-386**.

@norcal, 
@oxidas,
@Atomic Dog

May I know what kernel version do you have?
PLEASE HELP ME!

THX,
J.

---

### Post by juretto on 2007-06-22
Hi,

I have found a solution... a not so technical solution...
In the Italian Forum people suggest to me this possible procedure to resolve: [http://forum.ubuntu-it.org/index.php?topic=46197.msg402923#msg402923](http://forum.ubuntu-it.org/index.php?topic=46197.msg402923#msg402923)

When I was trying to start, the camera started to work properly...!!!

The only thing I did today was to connect my camera to a PC with Windows 2000 installed and downloaded some pictures.
After that... LSUSB recognize the camera properly.

So, I'm happy, even if I spoken by myself.. 

But... wich problem could be? The memory-card filesystem?
Thank You,
J.

---

### Post by LegoAddict on 2007-07-06
Ok, so I have a Casio Exilim that I just bought a few days ago.  It's been automounting in Linux just fine ever since I've gotten it.

So I have a bunch of pictures and I go to dump them onto my laptop (which runs a fully updates as of July 6th Feisty under GNOME).  I plug, it mounts.  Nothing special.  I drag a few files over, and as I'm going to get some more, I get one of the messages like my camera has been unplugged without unmounting it first.  Ok, so I check the cords, nothing went.  I plug it back in.


Nothing.  The little dock says the USB is connected, but when I plug in the charge cord, it doesn't recognize the battery.  So I eject the battery and reinstert it.  It's charging now.


But it's still not mounting.  It will turn on fine, and it will take pictures fine, but Linux refuses to recognize it.  I ran lsusb, and it would just hang there with no output.  I can't find where to mount it, and I'm starting to panic.


Costco gave me a 30 any reason return policy for a full refund thing, but if the problem is if the memory chip (which I guess it shouldn't be because the file system has to be on the internal HD of the camera) is the problem, I've just lost all my pictures.

I'm going to test it on WindowsXP.  Please Help! (ps, I can't read Italian, but if someone could translate that page, it would be great).


EDIT:  Rebooted Ubuntu.  Works fine.  Must not have had the camera turned on or something >.<

*quietly edges off to avoid embarrasment*

---

### Post by carusoswi on 2007-07-12
Sorry to say my Minolta Dimage S414, while it shows up in terminal after running lsusb, is unrecognized by Fspot (no camera connected) and will not show if I click places and navigate to where all media should show up.

Any more suggestions?  The cam has no menu to adjust USB that I coudl find.

Hope you can help.  Otherwise, I have to continue using XP to move my pics onto the 'puter.

Caruso

---

### Post by awilkin on 2007-08-23
Is the cam Pictbridge enabled? Got 3 options on mine when plugging in the USB lead, PC, PictBridge and PC Cam. PC doesn't work but PictBridge does a treat!

Issue with the PC option seems to be SCSI errors whilst trying to read the SD card in the Camera, USB is fine. Get icon for camera under Computer in browser but can't mount it, says "probably no media in drive".  Camera automounts without SD card in and SD card automounts in Card reader so looks like the camera is not allowing full access to the SD card?

Andrew

---

