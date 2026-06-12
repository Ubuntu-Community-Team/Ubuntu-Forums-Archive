---
title: "Troubles Installing Ubuntu"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by IkickPigeons on 2007-03-11
Hello,

First I'd like to say that I'm a total noob with Linux but I'm  looking forward to getting into it. (I'm super pissed at Vista and microsoft in general. Next laptop I buy will be a mac.)

But anyways. 

I downloaded the 32 bit 6.10 Ubuntu for desktops. I boot from the CD and get to the home menu. Whenever I try to start or install Ubuntu i simply get a black screen at the end. It finishes loading, with the Linux kernel loading and the part with the bar bouncing back and forth goes for a while. Then I get a black screen. It's either two things, my video card (ATI X1900XTX 512 mb) or my monitor (Hanns-G 19" LCD 16:10 native resolution 1440x900)

_My Specs:_
[B]Gigabyte DS-3 Mobo
E6400 OC'd 3.2 ghz Core 2 Duo
ATI X1900XTX 512mb 
2 gb of patriot ram PC3200
2 SATA drives 250gb and 320 gb
Creative Audigy 2zs gamer edition sound card[/B]

So whats wrong here? How do I fix it? I haven't even installed the OS yet. I did manage to load the Live CD on a different computer. It manage to run perfectly fine. The only problem I found was the resolution. It was running at 1280x768 when the monitor was 1280x1024.

Specs for other computer:
MSI K8N Plat 2 Mobo
AMD 3200+
Nvidia 6800 ultra
1 gb of corsair value select
80 gb SATA drive
Viewsonic LCD 1280x1024 

One other question.

If I do get Ubuntu to work, whats the best way to install it on my system? Should I install Ubuntu on my other hard drive that is used for archives? I would like to keep XP Pro for my games and Photoshop. Should I keep the two OS'es on different drives or can i combine them on the same drive? 


thanks for reading this far.

---

### Post by matburton on 2007-03-11
Is it still loading when you get a black screen?
Is the CD still spinning and do you get the sounds related to the gnome login?

---

### Post by dRock1286 on 2007-03-11
> **IkickPigeons said:**
> 

One other question.

If I do get Ubuntu to work, whats the best way to install it on my system? Should I install Ubuntu on my other hard drive that is used for archives? I would like to keep XP Pro for my games and Photoshop. Should I keep the two OS'es on different drives or can i combine them on the same drive? 


thanks for reading this far.

I used a second drive for Ubuntu and like how it works very well.  I automatically get the choice to load between the two OS's at the boot screen and I like it.

---

### Post by IkickPigeons on 2007-03-11
I don't know if It does makes the sounds. (Speakers were off) But what does happen is that my monitor says that "there is no video connection please check video signal or cable." And the live CD probably spent around 20 minutes loading on the splash screen. 

My guess, is that its my video card. I read somewhere that Ubuntu doesn't like ATI cards. Plus my other computer ran it fine and it has an Nvidia card in it.

Also, which version should I use? 32 bit or 64? Which is more stable and which currently has more features?


Thanks all for the help.

---

### Post by IkickPigeons on 2007-03-12
sorry to do this, but...

BUMP

---

### Post by ravis_31 on 2007-03-12
i have the exact same problem.I posted it [here]("http://ubuntuforums.org/showthread.php?t=382973")
Mine is a Acer ferrari 4005WLMi AMD Turion64,
ATI Radeon X700,
100GB HDD 
and Matshita DVD drive

travis

EDIT:I just tried it on my dell and it works fine,it has onboard 256 MB shared graphics while my acer has 128 MB dedicated graphics.How do i get it to work on my acer?

---

### Post by IkickPigeons on 2007-03-13
What kind of card does your Dell have? Is it an nvidia card? I tried on a different computer that was running an Nvidia based GPU and it ran perfectly fine.

---

### Post by ravis_31 on 2007-03-13
i think its a nvidia card.the live session and the install worked perfectly fine on the dell but my acer stops exactly at the same place.Any idea how do i resolve this?

travis

---

### Post by hyper_ch on 2007-03-13
You could try the alternate install cd... however you won't have a live-cd then... but install normally works better on the alternate...

---

### Post by ravis_31 on 2007-03-13
i downloaded the image from the site,i don't have a separate install cd.Is there a documented problem of ubuntu not working with ATi cards?
ikick..its the inbuilt Intel GMA 950

travis

---

### Post by hyper_ch on 2007-03-13
Well, you have a choice of several downloads... one is the LiveCD which you have downloaded and one is the alternate install cd... :)

---

### Post by ravis_31 on 2007-03-13
ok..you mean the one mentioned [here]("http://releases.ubuntu.com/edgy/")
but is there any way i could get this to work?
this cd already works perfectly fine with the dell with on-board graphics but with dedicated graphics on the acer it doesn't show up anything?

travis

---

### Post by hyper_ch on 2007-03-13
yes, on that site look for:  Alternate install CD

The problems is the graphic drivers...ATI is badly supported and with the alternate install cd you will have a "text-based" install (it's also simple...) but it does not require the full graphics driver and it will use vesa...
Then once it's installed you can go ahead and get the ATI card to run properly... there are a few howtos with regard to ATI... you'll have to search the forums for it.

---

### Post by buuntuu! on 2007-03-13
hi ikick, welcome to ubuntu
try looking up your hardware in the compatibility list of the[ document storage facility]("http://doc.gwos.org/index.php/Main_Page")
youmight get an answer to your ATI-issue there...

> 
If I do get Ubuntu to work, whats the best way to install it on my system? Should I install Ubuntu on my other hard drive that is used for archives? I would like to keep XP Pro for my games and Photoshop. Should I keep the two OS'es on different drives or can i combine them on the same drive? 

keeping xp does not prevent you from installing on the sam hd, no problem there
many games run fine under WINE or DOSBOX, but you'll have to check.
instead of photoshop there is the GIMP, or GIMPSHOP for a more photoshopish feel and touch, so you won't have to reboot constantly ;)
hope you'll get your install right!

---

### Post by ravis_31 on 2007-03-13
ok,will i still be able to get my second partition repartitioned using the text based installer?i just looked up the hardware compatibility guide [link ]("http://doc.gwos.org/index.php/IncompatVideoCard")provided by buuntuu(thanx buuntuu)and looks like the x700 is not supported?
As mentioned by the guy there,can i use the same open source ati drivers for my x700 and get it to work?

travis

---

### Post by hyper_ch on 2007-03-13
well, the alternate cd also has a partitioner :)
No clue about the ATI cards... I use nVidia and it works out of the box :(

---

### Post by ravis_31 on 2007-03-13
will this options mentioned in this [link]("http://ubuntuforums.org/showthread.php?t=190133&page=7") work with my existing disk?Please confirm

travis

---

### Post by buuntuu! on 2007-03-13
> **ravis_31 said:**
> will this options mentioned in this [link]("http://ubuntuforums.org/showthread.php?t=190133&page=7") work with my existing disk?Please confirm

travis

no idea about the post you linked, but you could try [envy]("http://albertomilone.com/nvidia_scripts1.html")
which is said to be a good help setting up nvidia and ati-cards

---

### Post by ravis_31 on 2007-03-13
few more things to confirm..after i finish my text based install,will i be able to work on the GUI to actually use envy?
or can envy be used from cli itself?

travis

---

### Post by buuntuu! on 2007-03-13
yes, as it says on the envy-page ;)

---

### Post by ravis_31 on 2007-03-13
sorry i missed that part.uhh...how do i run envy from the cli? :neutral: 

travis

---

### Post by buuntuu! on 2007-03-13
no idea, never used it, ```
envy
```probably.
the forum will have your answer ;)

---

### Post by ravis_31 on 2007-03-13
thanx a lot buuntuu :)

---

### Post by ravis_31 on 2007-03-14
I have a Broadcom's 802.11G wireless which i'll be using as primary connection,how do i configure that?
also during the initial startup,the part where the keyboard detect takes place mine is giving as "bg" is it right or should it be showing something else?
Mine is a UK keyboard.

travis

---

### Post by ravis_31 on 2007-03-15
Ok,this is what i did
i used norton partition magic to repartition an existing logical drive(D: )of size 45GB to two drives D: (35GB,FAT32,logical) and F: (10GB,NTFS,primary).
In the ubuntu partitioner,i tried to resize 10GB(9.9..GB) primary partition to create two 4GB ext2 filesystem and a 1GB swapspace but ended up with 8GB of NTFS drive and 1GB of unallocated space.I don't get any free space as mentioned [here]("http://users.bigpond.net.au/hermanzone/p3.htm")
What am i doing wrong?Could someone help me out?

travis

---

### Post by ravis_31 on 2007-03-15
could some one please help me out?

travis

---

### Post by hyper_ch on 2007-03-16
Hmmm, that 10GB partition that you made (which ended up as 8 & 1) --> you can just delete that partition... and then create new ones... it's not resizing that is needed here.

---

### Post by ravis_31 on 2007-03-16
i alredy cleaned up my 45 GB logical partition for installation.But when i try to cnvert to primary it says "If you do not install the OS ASAP you may not be able to boot properly" b'coz there are two primary partitions.
Its been three days i'm trying to install,everytime i do it the 8GBbecomes primary and 1GB becomes unusable(unallocated).Is there any place where there is a step by step guide or can you direct me.
The user in the psychocats link installs ubuntu first and then later windows but mine is vice versa..

travis

---

### Post by hyper_ch on 2007-03-16
You don't need a primary partition to install ubuntu... an logical partition in an extended one is just fine...

---

### Post by ravis_31 on 2007-03-16
ok,but will i be able to boot by setting the bootable flag to on in the logical drive?
also,when i tried to partition for ext3 and swap spaces i didn't get any free space,it was just one ext3 drive.How do i go about that?

travis

---

### Post by hyper_ch on 2007-03-16
You don't need to alter the bootable flag... grub will take care of that...

Just delete that partition and then create a swap partition and then one or more ext3 partition according to your liking...

---

### Post by ravis_31 on 2007-03-16
ok,i will try it out in the evening and post the results again.
thanx you very much for the help hyper.

travis

---

### Post by ravis_31 on 2007-03-16
ok,i'm installing now,my logical dirve d: is fat32,now how do i go ahead?
could someone help me out here?
i'm using the alternate cd to install.

travis

---

### Post by daradib on 2007-03-16
> I downloaded the 32 bit 6.10 Ubuntu for desktops. I boot from the CD and get to the home menu. Whenever I try to start or install Ubuntu i simply get a black screen at the end. It finishes loading, with the Linux kernel loading and the part with the bar bouncing back and forth goes for a while. Then I get a black screen. It's either two things, my video card (ATI X1900XTX 512 mb) or my monitor (Hanns-G 19" LCD 16:10 native resolution 1440x900)

I have an ATI card (ATI Radeon X800) and I had a similar issue in Kubuntu which I solved

You have several options. You can either install using alternate install CD and then fix your problem by booting in rescue mode or by using the live CD and try pressing Ctrl-Alt-F1 (or any key from F2-F6) when your screen is black (If you are using DVI output to monitor, switch to VGA.). You basically want to get to a terminal, where you can install the fglrx driver for ATI Radeon graphics cards. If you use the Ctrl-Alt-F1 method, then you will have to fix the method twice, once for  getting the live installer environment running and the second in rescue mode after Ubuntu is installed.

Install the fglrx drivers for Ubuntu via terminal.

```
sudo apt-get update
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
```

ATI are well known not to be able to provide correct drivers for their hardware so you will have to deactivate the composite extension in */etc/X11/xorg.conf *, otherwise you will get a jerky video display: ```
sudo nano /etc/X11/xorg.conf
``` and add the following lines at the end of the file:

[I]Section "Extensions"
        Option      "Composite" "0"
EndSection[/I]

Then type ```
startx
```.

You might want to try to reboot your machine if that doesn't work.

Confirm it worked, by issuing the "fglrxinfo" command:
```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9700 Generic
OpenGL version string: 2.0.5755 (8.24
```
If so, then everything is working nicely and you have 3D support.

If fglrxinfo gives you the following, your installation is not completed correctly:
```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
```

If so. these two commands might fix your installation, try this, reboot, and run fglrxinfo again:
```
mkdir -p /usr/X11R6/lib/modules/dri 
ln -s /usr/lib/dri/fglrx_dri.so /usr/X11R6/lib/modules/dri
```

Cheers

---

### Post by ravis_31 on 2007-03-16
i got into the kernel and checked the /usr/lib/dri and i see i don't have the fglrx_dri.so itself.Without having my network configured can't do sudo apt-get update?
Could you please let me know how do i configure my network from the kernel itself?

travis

---

