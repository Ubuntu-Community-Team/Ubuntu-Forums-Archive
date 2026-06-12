---
title: "Help installing nvidia driver"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by mrdlr on 2007-06-14
I am new to linux, trying to find my way and get my system working smoothly.

I downloaded the appropriate driver from nvidia and tried to run the installer.

STEP 3: Install
Type "sh NVIDIA-Linux-x86-100.14.09-pkg1.run" to install the driver.

When I do this I get the following error message

david@mrdlr:~$ sh NVIDIA-Linux-x86-100.14.09-pkg1.run
sh: Can't open NVIDIA-Linux-x86-100.14.09-pkg1.run

How can I open the driver?

---

### Post by dannyboy79 on 2007-06-14
how do you know you need that driver? that's the latest UNSTABLE driver. If you think you need it, than just make sure that you're in the location in which you downloaded the file to. you can find out your current dir by typing in pwd. then just (cd) to the directory you downloaded it to. I am geussing that it's stored on your desktop, so you would type
cd Desktop
then issue the above command again. (note: I didn't have to designate /home/<username>/Desktop because when you're going up 1 directory, you can just use the name of the folder)\
OR
if you're not sure what driver you need, than show me hte output of this command

lspci -v

or, if you have a pretty recent card, anything later than a 5700, you can just install the nvidia-glx-new driver from synaptic.

---

### Post by Kobalt on 2007-06-14
If you're new to Ubuntu, I'd recommend you to install your nvidia drivers using System > Admin. > Restricted drivers manager.
You'll avoid many possible problems, and it will be just as efficient.

---

### Post by dannyboy79 on 2007-06-14
the reason I sugegsted what I did was because the restricted modules manager didn't chose the correct driver for my card. and I don't see how that's any easier than using synaptic

---

### Post by mrdlr on 2007-06-14
Hey guys, thanks for the replies.

I guess I shouldn't be installing a driver manually. I have a restricted driver that is working fine. My problem is that I have two monitors and only one will work at a time. Is there some way to get to an options page within the driver utility?

---

### Post by dannyboy79 on 2007-06-15
do you have nvidia-settings installed? if not do,
sudo aptitude install nvidia-settings
this will most likely tell you that it's going to remove your restricted module nvidia driver (i think that's what happened to me), just go ahead with that, then just reinstall the nvidia driver.

After that, you can envoke the nvidia-settings gui by just entering 
sudo nvidia-settings
into the box that arises after hitting alt-F2 at the same time. Then yuo can enable dual monitor support. It's pretty awesome, don't forget to save your new xorg.conf. IF you want, you can also add a new menu item for nvidia-settings, menu editing is located within System, Admin or System, Prefs I believe. then just enter the same thing for the command as what you entered in the terminal, you can pick whatever icon you want, and you can give whatever description you want. Doing this works for all commands I am pretty sure because sometimes when you install something, it doesn't add a menu entry for clicking.

---

### Post by whftom on 2007-06-16
mrdlr--
           I'm trying to install the these drivers as well.  Once in the directory where the drivers are you must install from root.  When I sh the file it unpacks and then stops--with the message "no precompiled kernel interface".  I'm such a rookie that I can't figure out just what or which precompiled kernel is correct for my installed version.  I have version 2.6.20.16.28--I believe.  There are several versions listed as installed by the Synaptic Package Manager (including 2.6.20.15.27 and ....16.29) as well as several variations.  There is only one package listed as "linux-llibc-dev" and it is installed. I don't know at this point where to find "the" precompiled kernel interface for my installed version.  Perhaps you or someone else would have a suggestion or two that I might look into.

Regards,
               Tom

---

### Post by dannyboy79 on 2007-06-18
you need the kernel headers I believe, but again, why are you trying to install the Nvidia Driver tha tyou downloaded frmo the their site?????? Just use synaptic and install either the nvidia-glx-legacy, nvidia-glx, or the newest one which is nvidia-glx-new. That will download the correct headers and do everything for you. Just make sure you gogle which nvidia driver you need from synaptic.

---

### Post by whftom on 2007-06-19
dannyboy-
                   I appreciate your reply.  I'm installing these drivers because the Nvidia card (XFX 6200A AGP) seems to require these drivers.  The legacy drivers are for 4 series and below (according to NVNEWS).  I have read about difficulties installing the legacy drivers and the subseqent problems getting functionality and difficulties removing them.  I am a total rookie here so I'm not so sure of anything I'm doing.  I have been reading and cautiously moving slowly.  The driver version that seems appropriate is not yet in the repositories---which means they are probablly unstable--but I guess I'm willing to take that chance.  Can you tell me if "compiled kernel interface" means the "headers" for the installed version or is there an "interface"  i.e. installer or something that  "interface" refers to?   Again thanks for your attention.

Regards,
                Tom

---

### Post by dannyboy79 on 2007-06-19
you only need to use the nvidia-glx-new driver NOT the unstable but that's up to you. yes, you need to the kernel headers if you want bleeding edge unstable nvidia driver because it has to compile the kernel and you always need to the kernel headers to compie stuff which will only work for that kernel (so if you ever update your kernel thru synaptic, you'll have to reinstall your nvidia driver again) 

I have the same card and the nvidia-glx-new (which is the 9755 driver) works great!!! i have used nvidia-settings to set up 2 totally seperate screen and 1 is my 17" HDTV (VGA in using the vga from the card) which has mythtv running on it and the other is my 17" Flat Panel Monitor

---

### Post by whftom on 2007-06-19
dannyboy-
                    Thank-you.  I am particularly interested in using  DVI-out to my rear-projection (DVI-in) tv for viewing HD video.  I'm relieved to hear this card works so well for you.  I will take your advice and install the 9755 drivers.  I currently have an ATI card on the machine and wonder if I can use the GUI to get the Nvidia drivers installed and then swap the cards?  So far I have swapped the cards and, of course, get no GUI once the Nvidia card in place.  I am trying to learn to use the command line and I'm making some progress but I am fairly lame in this area. Again, thank-you for your help.  I will post my results.
  
Regards,
                  Tom

---

### Post by whftom on 2007-06-19
dannyboy-
                    MythTV is next for me.  I have a 10' sat dish and access to nealy 40 sats and 400+ channels and I am looking forward to getting more from the sky onto my TV.  

Regards
              Tom

---

### Post by dannyboy79 on 2007-06-19
> **whftom said:**
> dannyboy-
                    Thank-you.  I am particularly interested in using  DVI-out to my rear-projection (DVI-in) tv for viewing HD video.  I'm relieved to hear this card works so well for you.  I will take your advice and install the 9755 drivers.  I currently have an ATI card on the machine and wonder if I can use the GUI to get the Nvidia drivers installed and then swap the cards?  So far I have swapped the cards and, of course, get no GUI once the Nvidia card in place.  I am trying to learn to use the command line and I'm making some progress but I am fairly lame in this area. Again, thank-you for your help.  I will post my results.
  
Regards,
                  Tom
when you install the 9755 driver, make sure that you purge anythign and everything related to nvidia-glx, the most common issue is people trying out the restricted modules manager and then that one will install the nvidia-glx driver, then they realize that they can use synaptic and then they try to install the nvidia-glx-new driver and then their x will never start even after they remove the restricted modules manager check mark. so make sure you purge and remove anything with nvidia-glx*, then change your driver to use vesa temporarily, then restart your machine, make sure that the vesa driver is being used, then install the nvidia-glx-new driver, then you should be set. Here's my xorg.conf BUT just so you are aware I live in the US so my keyboard will be different and also I have 2 displayes don't forget. they are both hooked via VGA so notice the CRT settings, sometimes you have to choose different settings for DVI I beleive. What I am saying, is don't juse copyt and paste the entire thing, just get ideas of what to do by looking at mine BUT I can tell that mine was totally setup by me using the nvidia-settings GUI, it's awesome. it's just like you're in winbloz after you right click on the desktop and you want to adjust the resolution or use 2 displays or use twinview. good luck. Mythtv and Feisty is the simplest it's ever been with Ubuntu EVER. it's a matter of installing it and if you have a Haugpauge Card 150, 250, or 350, the IVTV drivers are installed automagically.

---

### Post by whftom on 2007-06-19
dannyboy-
                      Didn't work.  I get a screen  half full of white lines and two Ubuntu logos and words --tried Mr. Eliots Envy--took about two hours to go through that and near what I think is the end of the build process it stops.  Thanks for your time.  Back to the old ATI card---at least I get something I can read.

Regards,
                Tom

---

### Post by dannyboy79 on 2007-06-19
> **whftom said:**
> dannyboy-
                      Didn't work.  I get a screen with half full of white lines and two Ubuntu logos and words --tried Mr. Eliots Envy--took about two hours to go through that and near what I think is the end of the build process it stiops.  Thanks for your time.  Back to the old ATI card---at least I get something I can read.

Regards,
                Tom

if you are getting white lines, it because your xorg.conf file is incorrect, try to do 
sudo dpkg-reconfigure xserver-xorg
then chose the nvidia driver, then choose your resolutions that you want, then for anythign you don't know, just let the defaults be and this should make it work. OR if you want to go back to ATI go ahead but NVIDIA has far superior linux driver support than ATI at the current time. (and for a long time I might add)

---

### Post by nalinde on 2007-06-19
@mrdlr i suggest that you give alberto milones nifty little app, Envy, a try.
Get it att [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by dannyboy79 on 2007-06-19
> **nalinde said:**
> @mrdlr i suggest that you give alberto milones nifty little app, Envy, a try.
Get it att [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

you must not have read his post, he did try Envy. and by the way, Envy is NOT needed when synaptic will install the driver twice as easy. The only time you would need Envy is if you have a GeForce 8800GTX or something that's not supported by the repositories OR when you want bleeding edge but then you're just asking for more problems IF you're a newbie.

---

### Post by whftom on 2007-06-19
dannyboy-
                   Thanks for hangin in with me.  I am trying to configure the xorg conf package.  It keeps not seeing the AGP port and thus not the card.  It asks for:  PCI:00:01:0_______________ and I don't know what to enter.  I ran  "lspci" to get a location and I found nothing forthe AGP--just PCI/AGP bridge location of :00:01:0 so I entered that.........not.  I am supposed to enter the video card's bus ID and I don't know what it is.   The VGA controller ID is 01:00:0 I tried that too.....no joy. Upon looking at the log file I see a number of Nvidia modules installed , Nvidia chipset found etc...........then EE NVIDIA(0) faliled to load NVIDIA kernel module!,  EE aborting............

---

### Post by dannyboy79 on 2007-06-20
as I said, when you run the sudo dpkg-reconfigure xserver-xorg and you don't know something, than just accept the default. if the default is blank, than so be it.

I also need to know what else it says about failed to load NVIDIA kernel module. does it say which one is failing to load? does it say something about an API Mismatch?

---

### Post by whftom on 2007-06-20
dannyboy--
                   Good day to you.
               I have to confess,.... I  have run  NVIDIA-Linux-x86-100.14.09-pkg.run.  I followed instructions by Alberto from one of his install how-to's.  I ran uname -r, opened synaptic and searched for: header, linux-source, and build-essential for matching my version and installed.  I then made sure "nvidia-glx"  was not installed (ran rm) and made sure gcc was installed.  Stopped gdm.  From the console as root I : sudo sh NVIDIA-Linux-x86-100.14.09-pkg.run.  I started to get excited.....but to no avail I got the errors I mentioned in my last post.  I have, however, managed to copy the Nvidia log file to my home directory and I will attach a copy----if you would be so kind as to have a look?  It looks to my uneducated eye like there is a problem with either the kernal headers, gcc (gcc/436) or there is no Nvidia kernel module installed (for some reason).  This machine is a (not the one I'm writing this on) custion (circa 1999) box with a Gigabyte GA-5AX(rev 4) mobo, AMD k6-2 500 cpu, 256k ram, 20 hdd.  I have scoured the bios, cmos, and all the chipset stuff looking for some change that might make a difference--but I'm not that informed about what I'm looking at in there.  I believe this box is an i386, with 3-step ACPI (I can set temps for the cpu but not fan stuff).  That's all I know just now.  Thanks for your help.  I guess I don't know how to include the log file!  I have it but it apparently doesn't have a valid extension.

Regards,
                Tom

---

### Post by dannyboy79 on 2007-06-20
i can try to help but I've never looked at a nvidia install log. I would rather see the dmesg file. towards the end it will say what happened with the nvidia module trying to be loaded. if you want to post your dmesg than do this

dmesg > dmesg.log

then open the file and select all and copy it to your clipboard (meaning just copy by hitting ctrl-c) then paste it at [www.pastebin.com](www.pastebin.com)
make sure you select the choice for more than 1 day, I think it'll host the contents for 1 month. then paste the link that it ends up being after you palsted it into pastebin and you hit, send, it'll be the pastebin.com plus a number

so are you saying that the nvidia installer acts like it worked but your xserver doesn't start? if so, what does the error say when you tell it that you do want to read the xserver errror? if nvidia installer fails to even install, then you'll have to go to nvnews.com forums for help as  i wouldn't be able to help.

---

### Post by whftom on 2007-06-21
dannyboy---
                      Eureka!!!  Nvidia installed and lookin' gooood.  In the bios: changed graphics aperture from 64 to 32,  disabled video shadow,  installed linux headers for i386, ran Nvidia installer for 100.14.09 and bang!  I will revisit the bios and tinker some more (one thing at a time) because those settings (I believe) can give me some slight speed adavantages and because I want to know exactly which change enabled success.  I want to thank you for your attention and help--I might have given up there at one point had you not gotten envolved.  I really appreciate it!  When I can I will pass it on.

Regards,
               Tom

---

### Post by dannyboy79 on 2007-06-21
the only thing that allowed it to work, is because you installed the headers for i386. Nothing in the bios would stop it from working. At least it shouldn't. Let us know.

---

### Post by samuraiCat on 2007-06-21
> **dannyboy79 said:**
> the only thing that allowed it to work, is because you installed the headers for i386. Nothing in the bios would stop it from working. At least it shouldn't. Let us know.

How do you "install the headers for i386" and why would this work? I'm having similar problems, and I haven't heard this one before.

---

### Post by whftom on 2007-06-21
samuraiCat--

                     Good day to you.
I have an old (some would say ancient) machine I have resurrected and installed Fiesty 7.04.  After looking at the Nvidia installer log (mostly I know not what I see) I did notice ...gcc/486...I have read in several places (nvnews) that gcc must be installed to allow Nvidia instalers to compile a kernel for your distro.  In this effort to get the drivers installed I realized this box had  i386 architecture.  I made the connection (I thought)---maybe the newer gcc from my recent upgraded Fiesty install was too new for my architecture together with the Nvidia card and using Synaptic I installed linux-headers for i386.  The rest you know.  ( I left everything else, including all the other headers, just the way it was).

Regards,
                 Tom

---

### Post by whftom on 2007-06-21
dannyboy--

               Good day to you.
Well, I changed the bios --Graphic Aperature Size from 32 to 64-----Nvidia driver failure!  I thought this setting pertained to the Vid card.........not!  It must refer to the architecture-i.e. 32bit, 64bit etc.  Changed it back to 32.....all is good.  Changed video bios shadow to enable........all is good.  I don't have any time with this new card so this last bios change is indeterminate as far performance, but over time I will see if it makes any difference.  Thanks for your attention dude!  Later..............

Regards,
              Tom

---

### Post by dannyboy79 on 2007-06-22
> **samuraiCat said:**
> How do you "install the headers for i386" and why would this work? I'm having similar problems, and I haven't heard this one before.

well this is only if you're using the nvidia driver install package from their site, it's because the nvidia module has to be compiled and it can't be compiled if the kernel headers aren't there. so you would either open synaptic and do a search for "linux" than you should see the headers for your kernel, then install them. you can find out your kernel by issueing 
uname -r

you'll get something like:
2.6.20-16-generic
so in my case I would need to install the linux-headers for the 2.6.20-16-generic kernel.

---

### Post by dannyboy79 on 2007-06-22
> **whftom said:**
> dannyboy--

               Good day to you.
Well, I changed the bios --Graphic Aperature Size from 32 to 64-----Nvidia driver failure!  I thought this setting pertained to the Vid card.........not!  It must refer to the architecture-i.e. 32bit, 64bit etc.  Changed it back to 32.....all is good.  Changed video bios shadow to enable........all is good.  I don't have any time with this new card so this last bios change is indeterminate as far performance, but over time I will see if it makes any difference.  Thanks for your attention dude!  Later..............

Regards,
              Tom


AGP Aperture Size

Common Options : 4, 8, 16, 32, 64, 128, 256

Quick Review

This BIOS feature does two things. It selects the size of the AGP aperture and it determines the size of the GART (Graphics Address Relocation Table).

The aperture is a portion of the PCI memory address range that is dedicated for use as AGP memory address space while the GART is a translation table that translates AGP memory addresses into actual memory addresses which are often fragmented. The GART allows the graphics card to see the memory region available to it as a contiguous piece of memory range.

Host cycles that hit the aperture range are forwarded to the AGP bus without need for translation. The aperture size also determines the maximum amount of system memory that can be allocated to the AGP graphics card for texture storage.

Please note that the AGP aperture is merely address space, not actual physical memory in use. Although it is very common to hear people recommending that the AGP aperture size should be half the size of system memory, that is wrong!

The requirement for AGP memory space shrinks as the graphics card's local memory increases in size. This is because the graphics card will have more local memory to dedicate to texture storage. So, if you upgrade to a graphics card with more memory, you shouldn't be "deceived" into thinking that you will need even more AGP memory! On the contrary, a smaller AGP memory space will be required.

It is recommended that you keep the AGP aperture around 64MB to 128MB in size, even if your graphics card has a lot of onboard memory. This allows flexibility in the event that you actually need extra memory for texture storage. It will also keep the GART (Graphics Address Relocation Table) within a reasonable size.


Enlight of this information, I can't speculate why your X server won't work with 64 versus 32 but I can assure you this is not why despite this being the only setting that will allow it to work or not. I can't explain why?

---

### Post by Jammerdelray on 2007-06-24
Hi, I just installed Ubuntu 7.04. I am trying to install Nvidia Linux Driver which I just downloaded, I went in to terminal and typed ""sh NVIDIA-Linux-x86-100.14.11-pkg1.run" from Desktop where it was downloaded to. I get a error, "Nvidia installer must be run as root". Not sure what root means. 

Thanks

---

### Post by Vodkayum on 2007-06-24
if using ubuntu use envy 
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
if kubuntu use automatix
[http://www.getautomatix.com/](http://www.getautomatix.com/)

these will automatically install nvdia drivers

---

### Post by Jammerdelray on 2007-06-24
Ok, looks promising, gonna give envy a try, thanks for the quick reply :P

---

### Post by Jammerdelray on 2007-06-24
Envy worked like a charm, thank you!! I reccomend it to anyone that is new to Ubuntu and wants to 
install the latest Nvidia drivers.

---

