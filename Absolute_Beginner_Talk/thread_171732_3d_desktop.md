---
title: "3d desktop?"
date: 2006-05-07
forum: Absolute Beginner Talk
---

### Post by shutupimpoor on 2006-05-07
i downloaded the 3ddesktop from synaptic package manager, and I don't get what it is supposed to do

---

### Post by Dr Von Bon Bon on 2006-05-07
type 3ddesk in terminal


you can see your desktops
its quite cool

---

### Post by shutupimpoor on 2006-05-07
I don't think I have openGL installed, can anybody help?

root@ubuntu:~# 3ddesk
Attempting to start 3ddesktop server.
Daemon started.  Run 3ddesk to activate.
3ddeskd: glXIsDirect failed, no Direct Rendering possible!
3ddeskd: Please configure hardware acceleration.  Exiting.
Server not found after waiting 5 seconds.
Could not find server.
Try starting manually (3ddeskd)

---

### Post by aimislame15 on 2006-05-07
When I tried this, my screen just went blank instead of showing anything (pressed return and it got me back out). No errors at command prompt either.

---

### Post by Teroedni on 2006-05-07
To  shutupimpoor and aimislame15
What graphics card do you got?

Open terminal and paste this command into it
```
sudo lshw -class display

```

Paste the result here

---

### Post by shutupimpoor on 2006-05-07
hahaha wow i spent a good 20 minutes looking up how to determine your video card and then Terodni gives the command on my post. anyway:

```
 *-display:0
       description: VGA compatible controller
       product: RV350 AP [Radeon 9600]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@01:00.0
       version: 00
       size: 128MB
       width: 32 bits
       clock: 66MHz
       capabilities: vga bus_master cap_list
       resources: iomemory:e8000000-efffffff ioport:8000-80ff iomemory:f8020000-f802ffff irq:10
  *-display:1 UNCLAIMED
       description: Display controller
       product: RV350 AP [Radeon 9600] (Secondary)
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@01:00.1
       version: 00
       size: 128MB
       width: 32 bits
       clock: 66MHz
       capabilities: cap_list
       resources: iomemory:f0000000-f7ffffff iomemory:f8030000-f803ffff

```
I read that ATI is hard to get to work with Linux, I also have a nVidia GeForce 5500 FX, but when I tried to attach it I couldn't load Linux, the screen turned blue and there were a bunch of characters, but it worked fine when I switched back to my Radeon 9600 SE (I think thats what I have now anyway).

---

### Post by Teroedni on 2006-05-07
> I also have a nVidia GeForce 5500 FX, but when I tried to attach it I couldn't load Linux, the screen turned blue and there were a bunch of characters

The reason that happend is that Ubuntu tries to load either ati or something driver module. In order to make the fx 5500 load you need either the nv driver or the propiery nvidia driver(3d)



So my question to you are
[COLOR="Red"]Which card do you wanna use?[/COLOR]
It is possible to get booth to work , but i think it will be easier to get the nvidia one to work correctly.
So the choice is yours;)

---

### Post by shutupimpoor on 2006-05-07
i choose the green! (nvidia)
make my life complete!

---

### Post by Teroedni on 2006-05-07
all right:D


You need to edit your xorg file

```
sudo gedit /etc/X11/xorg.conf
```


scroll down to device in the text file

Replace driver  "xxx" with driver  "nv"

---

### Post by Merlintrix on 2006-05-07
i get exactly the same error when i try to run 3ddesk


and this is the output of  lshw -class display
*-display
       description: VGA compatible controller
       product: VT8378 [S3 UniChrome] Integrated Video
       vendor: VIA Technologies, Inc.
       physical id: 0
       bus info: pci@01:00.0
       version: 01
       size: 64MB
       width: 32 bits
       clock: 66MHz
       capabilities: vga bus_master cap_list
       resources: iomemory:e4000000-e7ffffff iomemory:e8000000-e8ffffff irq:10

can u help me?

---

### Post by n3tfury on 2006-05-07
i'm going to guess that your integrated vid is not going to cut it for the 3D desktop.

---

### Post by shutupimpoor on 2006-05-07
scratch that, i'm keeping the ATI. i still get the same error when i try to start with my nvidia. i changed the thing too, but i guess it doesn't work (my ati still works even tho it says nv weirdly)

anyway i can get the thing i need for ati radeon 9600 se?

---

### Post by djsroknrol on 2006-05-07
Well, I'm running a Radeon 9200 SE with the radeon driver, and 3ddesk works fine for me..check out my xorg [here]("http://ubuntuforums.org/showthread.php?t=160499")..and search the posts for eye candy..the tutorial I followed worked fine for me...make the on / off switch twords the end of the post..it's very helpful in case of a crash...

---

### Post by djsroknrol on 2006-05-07
thought I'd make it easier for ya...here's the link to the [tutorial]("http://ubuntuforums.org/showthread.php?t=100167&highlight=3ddesktop")...

---

### Post by shutupimpoor on 2006-05-07
PS, anyone who is trying to switch video cards or is having the problem where its a blue screen with a bunch of characters saying "Failed to start Xserver (Your Graphical Interface), its a lot easier than I thought, the newb way of doing it is as follows:

restart
when you chose your OS, chose recovery mode
at the end of the loading screen enter your root password
type ```
 sudo dpkg-reconfigure xserver-xorg 
```
enable autodetect settings and keep pressing enter - or customize as you see fit


(i'm a linux n00b so these directions may do something bad and I just haven't noticed on my computer yet)

---

### Post by shutupimpoor on 2006-05-07
ok i still have this error, but now i have a nvidia geforce 5500 FX video card, so atleast its a nvidia and not an ATI video card. 

the error i get is

```
Attempting to start 3ddesktop server.
3ddeskd: glXIsDirect failed, no Direct Rendering possible!
3ddeskd: Please configure hardware acceleration.  Exiting.
Daemon started.  Run 3ddesk to activate.
Server not found after waiting 5 seconds.
Could not find server.
Try starting manually (3ddeskd)

```
what do i do?

---

### Post by Omnios on 2006-05-07
[QUOTE=shutupimpoor]PS, anyone who is trying to switch video cards or is having the problem where its a blue screen with a bunch of characters saying "Failed to start Xserver (Your Graphical Interface), its a lot easier than I thought, the newb way of doing it is as follows:

restart
when you chose your OS, chose recovery mode
at the end of the loading screen enter your root password
type ```
 sudo dpkg-reconfigure xserver-xorg 
```
enable autodetect settings and keep pressing enter - or customize as you see fit


(i'm a linux n00b so these directions may do something bad and I just haven't noticed on my computer yet)[/QUOTE]


 If I remember correctly when you have a onboard card and seperate graphics card there is reconfig setting in the card area that poits to your card and I think you have to point it to the card you want to use, PCI whatever or so. If you can get in with versa or if its working I think you can go MENU /System / Administration / Device Magnager where you should be able to get where your video card is connected.

---

### Post by tennvols_69 on 2006-05-07
i also have a problem with running this.  this is what i get when i try.
~$ 3ddesk
Attempting to start 3ddesktop server.
Daemon started.  Run 3ddesk to activate.
3ddeskd: glXIsDirect failed, no Direct Rendering possible!
3ddeskd: Please configure hardware acceleration.  Exiting.
Server not found after waiting 5 seconds.
Could not find server.
Try starting manually (3ddeskd)

i also cannot run glxgears so i think its all related.

---

### Post by guitarman on 2006-05-07
[QUOTE=Teroedni]The reason that happend is that Ubuntu tries to load either ati or something driver module. In order to make the fx 5500 load you need either the nv driver or the propiery nvidia driver(3d)



So my question to you are
[COLOR="Red"]Which card do you wanna use?[/COLOR]
It is possible to get booth to work , but i think it will be easier to get the nvidia one to work correctly.
So the choice is yours;)[/QUOTE]
I have an S3 card. Can I run the 3D desktop too?

Here is my video config......

 *-display
       description: VGA compatible controller
       product: VT8375 [ProSavage8 KM266/KL266]
       vendor: S3 Inc.
       physical id: 0
       bus info: pci@01:00.0
       version: 00
       size: 128MB
       width: 32 bits
       clock: 66MHz
       capabilities: vga bus_master cap_list
       resources: iomemory:dfe80000-dfefffff iomemory:d0000000-d7ffffff irq:11

Thanks

---

### Post by Papa-san on 2006-05-07
My card is:
```
 *-display
       description: VGA compatible controller
       product: Radeon Mobility M6 LY
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@01:00.0
       version: 00
       size: 128MB
       width: 32 bits
       clock: 66MHz
       capabilities: vga bus_master vga_palette cap_list
       resources: iomemory:e0000000-e7ffffff ioport:c000-c0ff iomemory:fcff0000-fcffffff irq:11

```
and I'm not even sure it will support this feature. I do think it would be cool tho!

---

### Post by Teroedni on 2006-05-09
[QUOTE=Papa-san]My card is:
```
 *-display
       description: VGA compatible controller
       product: Radeon Mobility M6 LY
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@01:00.0
       version: 00
       size: 128MB
       width: 32 bits
       clock: 66MHz
       capabilities: vga bus_master vga_palette cap_list
       resources: iomemory:e0000000-e7ffffff ioport:c000-c0ff iomemory:fcff0000-fcffffff irq:11

```
and I'm not even sure it will support this feature. I do think it would be cool tho![/QUOTE]


from man Radeon
```
SUPPORTED HARDWARE
       The radeon driver supports PCI and AGP video cards based on the follow&#8208;
       ing ATI chips

       R100        Radeon 7200

       RV100       Radeon 7000(VE), M6

```
**[COLOR="Red"]Solution 1[/COLOR]**
It seems your card is supported by the 3d radeon driver , but im not sure.
You Yust have to try and see if it gives you 3d;)
Go into your xorg.conf file and change driver "xxx" to Driver Radeon 
Hopefully it works


[COLOR="Red"]*Solution 2*[/COLOR]
It may also be that you can use Atis binary drivers(fglrx)
They exsist both in Synaptic and on Atis homepage.

No matter which solution you choose i wish your Luck:)

---

### Post by Teroedni on 2006-05-09
[QUOTE=guitarman] i have an S3 card. Can I run the 3D desktop too?

Here is my video config......

*-display
description: VGA compatible controller
product: VT8375 [ProSavage8 KM266/KL266]
vendor: S3 Inc.
physical id: 0
bus info: pci@01:00.0
version: 00
size: 128MB
width: 32 bits
clock: 66MHz
capabilities: vga bus_master cap_list
resources: iomemory:dfe80000-dfefffff iomemory:d0000000-d7ffffff irq:11


Thanks[/QUOTE]

Your need to edit your xorg.conf file so driver= "via"
That should give you 3d. Please tell me if you need help to do this.


[QUOTE=Merlintrix]i get exactly the same error when i try to run 3ddesk


and this is the output of  lshw -class display
*-display
       description: VGA compatible controller
       product: VT8378 [S3 UniChrome] Integrated Video
       vendor: VIA Technologies, Inc.
       physical id: 0
       bus info: pci@01:00.0
       version: 01
       size: 64MB
       width: 32 bits
       clock: 66MHz
       capabilities: vga bus_master cap_list
       resources: iomemory:e4000000-e7ffffff iomemory:e8000000-e8ffffff irq:10

can u help me?[/QUOTE]

Hello Merlintrix
Im sorry to have to give you bad news:
[QUOTE=man via]
The via driver supports the VIA CLE266, KM400/KN400 chipsets, including
       2D acceleration and the Xv video overlay extensions. Flat panel, TV and
       VGA outputs are supported.

       K8M800/K8N800, PM8X0 and CN400 support is still under development.

 Direct rendering 3D is available using experimental  drivers  in  Mesa,
       [www.mesa3d.org](www.mesa3d.org).   Also  there  is  an  XvMC client library for hardware
       MPEG1 /  MPEG2  decoding  acceleration  available  on  the  CLE266  and
       K8M/N800  chipsets  that uses the Direct Rendering Infrastructure, DRI.
       The XvMC client library implements a nonstandard "VLD" extension to the
       XvMC standard. The current Direct Rendering Manager Linux kernel module
       is available at dri.sourceforge.net.
[/QUOTE]

That means you have to compile a driver from Mesa tree.
I have no idea how to do this so i recommend you create a new post in the Hardware or Absolute Beginners section where you ask for help to compile a 3d driver for unichrome graphics. 
Hopefully some of the knowlegde there will help you:)

---

### Post by n3tfury on 2006-05-09
don't you need a pretty "hefty" card to run this?

---

### Post by Rinzwind on 2006-05-09
[QUOTE=n3tfury]don't you need a pretty "hefty" card to run this?[/QUOTE]
Define hefty?

It works perfectly on my X300 (Dell Inspiron 9300 notebook),

ONLY thing I don't like is the small wait after I push the Super-L-key.
Does anyone know if I can speed this up?

---

### Post by n3tfury on 2006-05-09
what size in MB are you using for your vid chip/card? i was thinking this will choke with anything less than 128mb

---

### Post by n3tfury on 2006-05-09
*edited because i don't know what happened*

---

