---
title: "Xorg working on a 9500 and ATI MACH64 GX?"
date: 2008-09-23
forum: Apple Hardware Users
---

### Post by Bikerbob on 2008-09-23
Hi,

I have posted several other threads beating my head to a pulp trying to get this to work.

I have successfully installed Kubuntu 804 and Ubuntu 804 on a 9500 with 387mb of ram... to the command line.

I have managed to get the odd x session working on ubuntu 804 using No driver on the boot and FBDEV as the driver.

Its only 640 x 480 8bit - not very usable at all and I am not able to adjust the resolution either by X or by direct editing of .conf

Now from what I understand the video card ATI Mach64 GX - uses a ramdac that was never coded for linux. So I have to use FBdev.

Are there limits to FBdev? what can I run? 

Is it possible to get this configuration to work? I have other video cards but the monitor I am using is apple so I need to get an apple monitor to vga converter.. but this is looking like it might be the best thing.

if I try and run sudo dpkg-reconfigure xserver-xorg it starts get s just past the keyboard entries and errors out with 

FATAL: Module battery not found.

Thanks
James

---

### Post by Bikerbob on 2008-09-24
OK, I managed to get a session yesterday running 1024 x 768 15/16 depth?

that looked great, but was SLOW.. I assume because the FB uses the procoessor to do all the imaging??

On reboot I was right back into 640 x 480 8 bit. Now I notice that the dmesg and the Xorg.0.log were different. One found a default of 15/16 the other 8 bit. but both were puzzling.

The uploaded files are, my xorg.conf - as best as I can get it to this point. Would love tips on how to get it working better, streamline it.. etc.


The logs - 2 Dmesg and xorg log - 2 of each.. one before the rootboot that I got the 1024 x 768 (note also in Dmesg how it detected the hardware different each time) and the one after that I  returned to 640 x 480.

James

---

### Post by abtabt on 2008-09-24
hello
 it can be tricky to get it work but 
lets try
 
first post your xorg file
 
 (if you let the system do the xorg file  it will damage your xorg file on 8.04 not work on OLD WOLD MACS with old graficcard )

---

### Post by Bikerbob on 2008-09-24
any help would be fantastic :)

---

### Post by abtabt on 2008-09-24
all screen conf is hash out ????

then the vesa driver goes on 

the fbdev driver use 15 depth

change like this

and hash 

#  BusID		"PCI:0:14:0"

 is the HorizSync  VertRefresh right for our monitor ???




 Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
        DefaultDepth 	15 
	SubSection "Display"
		Depth		15
		Modes	"1024x768"	"800x600"	"640x480"
	EndSubSection

try and come back 

the slow thing is the computer model and the fbdev driver

and use 1024x768 in mac os before you start linux

---

### Post by Bikerbob on 2008-09-24
So you knew that abtabt? about using BootX with nodriver and it using the resolution of where you were??? THats weird. If I use it from splash which is only 640 x 480 linux detects a video card that will do only 640 x 480.

ok.. so you want me to put vesa in place of fbdev for driver. use default depth of 15.
You want me to hash out the bus ID???

yes the values there were correct for the 20" monitor I have(Apple Display)

and use your screen section?

I am still using no driver option on Bootx?

Finally I wondered, what about not using no driver, but blacklisting the ATI driver and using  vesa or atyfb?

I tried vesa once already and it said it was trying to load a 64k bios.. could not find.. and errored out.


YEP! did same thing (EE) VESA(0) Cannot read V_BIOS (5)

James

---

### Post by Bikerbob on 2008-09-24
I have been reading about the atyfb.

Is support for this built into 8.04? 

Can I compile support and run it that way? From what I understand Atyfb should work with my card.

If I add video=atyfb at start it crashes.

James

---

### Post by abtabt on 2008-09-25
> **Bikerbob said:**
> I have been reading about the atyfb.

Is support for this built into 8.04? 

i use it on a 4400 old world but you need to upgrade the system if you have not done it 

Can I compile support and run it that way? From what I understand Atyfb should work with my card. 

If I add video=atyfb at start it crashes.
 
some combination will messup the boot (remember bootx is a good old switcher knife to boot a new system and get it work can be diffecult spec the old graficcard)

i use only mark no video in bootx and only kernel arg like root=/dev/hdax or sdax
 
and the 1024x768 must be on the macos and tusend colurs not 256 colurs when fbdev use in xorg fbdev use  Depth 15,  framebuffer bpp 16

James

to hash busid in xorg for the card can solve some problem for some card

if you look in the log it detect the memory on the video board
diffrent

(II) FBDEV(0): hardware: OFfb ATY,mach64 (video memory: 300kB)
get 640

(II) FBDEV(0): hardware: OFfb ATY,mach64 (video memory: 1536kB)
get 1024x768

good luck

---

### Post by Bikerbob on 2008-09-25
> **abtabt said:**
> to hash busid in xorg for the card can solve some problem for some card

if you look in the log it detect the memory on the video board
diffrent

(II) FBDEV(0): hardware: OFfb ATY,mach64 (video memory: 300kB)
get 640

(II) FBDEV(0): hardware: OFfb ATY,mach64 (video memory: 1536kB)
get 1024x768

good luck

yes, I saw that, and that is related to what mode I drop into linux from (640 or 1024) and use the nodriver option.

This is why I thought if I could NOT use the nodriver.. allow it to detect the Hardware correct.. black list the ATI driver so it does not try and load it - use either FBdev or atyfb, that I would get it to work.. with the correct memory detected.

James

---

### Post by abtabt on 2008-09-25
first you have a display but only 640 thats good



1. reset your mac (PRAM IT )

2. let MAC OS boot up

3. change display 1024x768 tusend colurs

4. chose BOOTX

5. mark no videodriver 

6. put your kernel arg  like root=/dev/hdax or sdax (dont forget to save this )

7. click on option and select force video and select your image

8. start linux (and a lot off stuff will d isplay)

9. the first part is the no video driver active 
then will the xorg (X) take action

10. do a reconfigure of the xorg 

11. then edit the xorg file 
if the driver is missing must be fbdev 

12. restart x 

if you have some issue with bootx trash the pef file for bootx in macos

this is my note for install on oldworld macs

i have use it on two oldworld and it works with 8.04 
with fbdev driver

both use 2.6.24.19 kernel

i have use the alternativ cd for install

and this note is for 8.04 (7.10 etc can be diffrent)

---

### Post by Bikerbob on 2008-09-25
> **abtabt said:**
> first you have a display but only 640 thats good


1. reset your mac (PRAM IT )

2. let MAC OS boot up

3. change display 1024x768 tusend colurs

4. chose BOOTX

5. mark no videodriver 

6. put your kernel arg  like root=/dev/hdax or sdax (dont forget to save this )

7. click on option and select force video and select your image

8. start linux (and a lot off stuff will d isplay)

9. the first part is the no video driver active 
then will the xorg (X) take action

Everything up to this point works great. Always has, but it will still detect the hardware wrong ie (memory low) 


> 10. do a reconfigure of the xorg 

If you read the last note in the very first post of this thread you will see I have never been able to reconfigure.


> 
11. then edit the xorg file 
if the driver is missing must be fbdev 

12. restart x 


Yes the way you are describing I can get a desktop of 1024 x 768 in 16 bit colour I think.. but it is VERY SLOW.. much slower than this machine should be. I have been told that fbdev does slow things down.. and even though this works.. the Hor and VERt is totally wrong and there are no sceens to change to etc.

If this is the best I can do with this card then I will pull it and put in another.. I have a Rage128 I can put in.. I just need an adapter for the monitor cable.

James

---

### Post by abtabt on 2008-09-26
[QUOTE=Bikerbob;5855295]Everything up to this point works great. Always has, but it will still detect the hardware wrong ie (memory low)

maybe not hmm  maybe it shows how much memory its take 1024 take more 640 take less 

buy my experienc the ati driver stopp support after 6.8.2-77,1
for old ati card and mac have a cuple of diffrenets ati cards


the only ati card on old world that i now is in a beige G3 how works 
with this ati driver but its not much faster then fbdev driver

i use glxgears to see that  

If you read the last note in the very first post of this thread you will see I have never been able to reconfigure.

I use this comands

sudo dpkg-reconfigure -phigh xserver-xorg       is one way

sudo dpkg-reconfigure xserver-xorg               is the second

but in 8.04 
 its goes wrong sometimes and the driver missing in the xorg file i have to edit the file manuelly i have see it in the old world with old card and a imac 333
and some time i can use a xorg from a older xorg file (7.04 etc)



Yes the way you are describing I can get a desktop of 1024 x 768 in 16 bit colour I think.. but it is VERY SLOW.. much slower than this machine should be. I have been told that fbdev does slow things down.. and even though this works.. the Hor and VERt is totally wrong and there are no sceens to change to etc.

yes its true its slow thing with fbdev but i can change 1024x768 to lower
i think you can to but you must use mac os to doit if chose a lower it can speed up tings
 
BUT if you use GNOME or KDE this slows dowm to mutch

TRY a less thing like icewm its verry god .if you can edit some.
you dont need to do that but you can get it like you want and use things
that includes in GNOME or KDE or XFCE4 with less power 
dont forget you have 604 ???mhz but you have plenty of ram
if you compere to OSX on your coputer and ubuntu i think ubuntu win ??? 



If this is the best I can do with this card then I will pull it and put in another.. I have a Rage128 I can put in.. I just need an adapter for the monitor cable.

---

