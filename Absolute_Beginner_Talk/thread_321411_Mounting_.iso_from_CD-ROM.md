---
title: "Mounting .iso from CD-ROM"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by SnowFire72 on 2006-12-18
I am very new to Ubuntu and do not know much at all! I have an .iso on a CD and I want to mount it. But whenever I try mounting it I get this message... 

"mount: special device /dev/hdc does not exist"

??? I'm so confused... 

-SnowFire72

---

### Post by SnowFire72 on 2006-12-18
bump?

---

### Post by freebeer on 2006-12-18
Did you burn it as an .iso?  If so, then it should boot automatically - at least when you restart your machine.  The BIOS needs to be told to boot from CD-ROM perhaps?

---

### Post by balloons on 2006-12-18
what are you specifically trying to do? Be more descriptive please. Perhaps this will help

Open a terminal and type the following lines:

To mount Image (ISO) file 
```
sudo mkdir /media/iso
sudo modprobe loop
sudo mount file.iso /media/iso/ -t iso9660 -o loop
```

To unmount Image (ISO) file 
```
sudo umount /media/iso/
```

your iso will be mounted at /media/iso. You can then browse it using nautilus.

to view, or browse to in nautilus
```
sudo nautilus /media/iso
```

this may help as well
[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper) or
[http://ubuntuguide.org/wiki/Edgy](http://ubuntuguide.org/wiki/Edgy)

---

### Post by SnowFire72 on 2006-12-19
> **freebeer said:**
> Did you burn it as an .iso?  If so, then it should boot automatically - at least when you restart your machine.  The BIOS needs to be told to boot from CD-ROM perhaps?

That is exactly what I tried. In fact, thats how I installed Ubuntu. But it's a weird thing? Because I can't set my CD drive as priority boot now? It doesn't even list that I have a CD drive. I trouble shooted over and over with that and it just wouldn't show up. 

What I am trying to do is dual boot Ubuntu and Windows using partitions? So far I love what Ubuntu offers, but of course windows would be nice to have for things that ubuntu can't or has trouble with doing. Also the simplicity for me with windows is a huge plus. 

Guitara, can you be more specific with what to do using terminal? That is something that I am very very unfamiliar with. My mother can't even access the internet without my help, I feel like I can somewhat relate to her now. lol 

-SnowFire72

---

### Post by marx2k on 2006-12-19
> **guitara said:**
> 
To mount Image (ISO) file 

sudo mkdir /media/iso
sudo modprobe loop
sudo mount file.iso /media/iso/ -t iso9660 -o loop[/CODE]


Can you give me a little information on what the loop module does? This is excellent information regarding mounting an ISO file, btw - I was wondering about this myself.

---

### Post by compwiz18 on 2006-12-19
@**marx2k**: The loop module allows you to mount a file on the disk as a drive...but I'm not sure why modprobe loop cause I've never had to do that before...but whatever works I guess.

@**SnowFire72**...
How to get to the terminal: [http://psychocats.net/ubuntu/terminal](http://psychocats.net/ubuntu/terminal)
But before you run anything, can you answer this for me: do you have an actual physical CD that you want to use, or just a CD image?

---

### Post by SnowFire72 on 2006-12-19
I had the .iso file that I then burned to a cd using a .iso burning program.

---

### Post by SnowFire72 on 2006-12-19
So what do I do from here?

---

### Post by ciscosurfer on 2006-12-19
> **marx2k said:**
> Can you give me a little information on what the loop module does? This is excellent information regarding mounting an ISO file, btw - I was wondering about this myself.You only need to **sudo** **modprobe loop** if loop hasn't been compiled in-kernel (most of us using the stock kernel from Ubuntu do not have this problem...in other words, you probably *don't need to issue* modprobe loop). :D

And generally speaking, when you try to use **mount** to mount an ISO, you don't typically need to specify the filesystem type (i.e., iso9660) because mount will recognize you are trying to mount an ISO file and will do the "leg work" for you.  Just some food for thought.  You can read more about using mount and the switches it uses by issuing **man mount** from within a terminal.

@SnowFire72,
You can learn more about using the Terminal here:
[http://psychocats.net/ubuntu/terminal](http://psychocats.net/ubuntu/terminal)
[https://help.ubuntu.com/community/BasicCommands](https://help.ubuntu.com/community/BasicCommands)
[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/terminals.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/terminals.html)

Then follow **guitara**'s instructions above. :-)

---

### Post by SnowFire72 on 2006-12-19
When I do the mounting code from guitara, I get this message. 

"No such file or directory." 

I'm mounting from my CD in my CD-DRIVE. So, maybe it isn't including looking through the CD-DRIVE for the file?? 

-SnowFire

---

### Post by SnowFire72 on 2006-12-19
Can anyone help me?

---

### Post by compwiz18 on 2006-12-19
Oh probably...

run ```
ls /media
``` in the terminal please?

just copy and paste that command into your terminal, and then post what the terminal says after you press enter.

this will help us figure out what the problem is.

---

### Post by balloons on 2006-12-19
well you need to replace file.iso with the filename of what your trying to mount. If your trying to mount the cd in the cdrom drive, ubuntu should do it for you. Just browse in nautilus to the cd.

---

### Post by SnowFire72 on 2006-12-19
This is what it said...

[COLOR="Cyan"]cdrom[/COLOR]  [COLOR="DarkOrchid"]cdrom0[/COLOR]  [COLOR="Cyan"]floppy[/COLOR]  [COLOR="DarkOrchid"]floppy0  iso  ISO  windows[/COLOR]

And I did replace file.iso with the files name.iso.

---

### Post by compwiz18 on 2006-12-20
Put the cd in the drive and do **ls /media/cdrom** . and post the output.

---

### Post by SnowFire72 on 2006-12-20
I got nothing?

---

### Post by ciscosurfer on 2006-12-20
> **SnowFire72 said:**
> I got nothing?Is this a question?  If it is, my response is, "I don't know, did you?"

Or did you mean, "I got nothing" ???  <<like: what gives?

---

### Post by compwiz18 on 2006-12-20
> **ciscosurfer said:**
> Is this a question?  If it is, my response is, "I don't know, did you?"

Or did you mean, "I got nothing" ???  <<like: what gives?
I think what is meant is that **ls /media/cdrom** turned up nothing.  Which is what was supposed to happen.  So we can now offically confirm that the cd is, in fact, not mounted.  So try **sudo mount /dev/hdc /media/cdrom**

---

### Post by SnowFire72 on 2006-12-20
Okay, now I get this message... 

mount: special device /dev/hdc does not exist

By the way, you are the most patient group of people I have ever met. lol 

Kudos!

---

### Post by compwiz18 on 2006-12-20
Can you run **lspci** and post the output?

---

### Post by SnowFire72 on 2006-12-20
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:06.0 Communication controller: Conexant Unknown device 2702 (rev 01)
01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)

---

### Post by compwiz18 on 2006-12-20
I don't see your CD drive listed in there...can you tell me which one it is?

---

### Post by SnowFire72 on 2006-12-20
Do you want my cd drive brand and info? 

[Memorex]("http://reviews.cnet.com/Memorex_16X_double_layer_drive/4505-3212_7-31109465.html") 

But yeah, ever since I installed ubuntu, I haven't been able to locate my cd drive in the bios to put it on priority boot.

---

### Post by compwiz18 on 2006-12-20
Really?  Ubuntu shouldn't touch the BIOS...are you sure it is plugged into the motherboard?  You haven't opened the case or anything since you installed Ubuntu have you?

---

### Post by SnowFire72 on 2006-12-20
Ubuntu didn't touch the bios. Before I had ubuntu, I had windows, but it was my dads employee's old computer and it was password protected. So I installed Ubuntu. To do that, I had to set the bios to boot my cd drive as priority. So now I have ubuntu, but I would like to partition the hard drive with both ubuntu and windows. After sticking in the cd and what not and seeing that it wasn't working and would give me that error message, I went into the bios once again to see if it has changed my boot sequence, when I got there, my cd drive wasn't listed as an option to boot from.

---

### Post by balloons on 2006-12-20
if your bios doesn't see the cd rom drive, nothing else will.. so start there and get it listed in the bios again. perhaps you unplugged the data cable by accident? check and see. eitheir way, the drive needs to be present in the bios for any OS to use it.

---

### Post by SnowFire72 on 2006-12-21
Any troubleshooting idea's?

---

### Post by compwiz18 on 2006-12-21
Make sure the thing is connected to the motherboard.  And the power supply.  And anything else it might need to be plugged into.  Other then that - someone else can help you can hardware isn't my best point.

also, check and make sure you didn't accidentally disable it in the bios.

---

### Post by SnowFire72 on 2006-12-21
okay, I disconnected EVERYTHING (playing it safe) and then reconnected it everything. My bios now says I have a CD-ROM Drive. Woot. I have it on priority boot, but the CD I am using must not work on priority boot. Anways, skipping ahead, I go to check my CD-Drive under where it has always been in the Home Folder... and now it says I have a floppy and floppy 1 drive. Where as before I had a floppy and a CD-ROM 1 drive. I also connected the CD-RW drive it came with so I have two optical drives and a floppy now.

---

### Post by SnowFire72 on 2006-12-21
I also tried **sudo mount /dev/hdc /media/cdrom** again, but this time I got this message...

mount: No medium found

Then I typed in **lspci** and got this... 

00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:06.0 Communication controller: Conexant Unknown device 2702 (rev 01)
01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)

---

### Post by LookTJ on 2006-12-21
The cdrom should automatically mount if there's a cd in it

---

