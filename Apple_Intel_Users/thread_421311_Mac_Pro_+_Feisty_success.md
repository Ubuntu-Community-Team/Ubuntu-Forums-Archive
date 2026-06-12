---
title: "Mac Pro + Feisty: success"
date: 2007-04-24
forum: Apple Intel Users
---

### Post by jdemesse on 2007-04-24
I've managed to install Feisty 64 bit on my Mac Pro. I had some serious issues with rEFIt (GFT and MBR out of sync) so Bootcamp was used in the end to create a triple boot system (possible since my mac has two disks). 

I didn't knew enough about the Compiz/Beryl differences to make a choice so after reading some posts in this forum, I decided to go with Beryl. It worked, but produced a lot of visual artifacts (my video card is an ATI X1900XT). I was able to configure BigDesktop but that wasn't what I wanted. I ended up removing Beryl and using the "Preferences - Desktop Effects" functionality. It just worked (tm) ... After removing Beryl, I was able to configure Xinerama (two LCD's, different resolutions). The second monitor showed a big ugly box instead of a mouse cursor and I was able to solve that problem by installing the latest ATI drivers with Envy.

NetBeans, and all Swing applications, don't work with Compiz/Beryl. I'm still unable to enable Xinerama when using desktop effects. Nothing big, just minor annoyances. 

Sound/video works but some video formats are having playback problems (eg DivX ...). When that happens, sound playback crashes. I'm not sure what the problem is but I suspect it must be a codec problem.

I'm still investigating how to solve some of the remaining problems and will report back if I know more. If somebody wants more information, just ask and I will try to answer it.

---

### Post by ronocdh on 2007-04-24
Thanks a lot for posting! Regarding your video playback issues, have you given VLC a spin? (**sudo apt-get install vlc** if not.) It comes with pretty much every codec one could ever need. Also, out of curiosity, which build of Ubuntu are you using, i386 or 64-bit? I never miss a change to plug the benefits of the AMD64 build. ;)

The rEFIt trouble is a shame; I've only ever used it to multiboot on a single harddrive, so perhaps my experience doesn't apply here, but I think the "partitioning tool" on the rEFIt boot screen should take care of any MBR/GFT issues. By just selecting it it will poll both tables and determine whether they are out of sync; if they are, it'll ask for permission to match them up. Sorry if I'm preaching to the choir here...

Hopefully we'll see progress on the drivers front someday soon.

Have you searched this forum for more issue on sound? I thought I saw a popular one a week or so ago, though it may have been for an iMac rather than a Mac Pro. Good luck!

---

### Post by jdemesse on 2007-04-24
I use the 64 bit edition. I tried the 32-bit edition live CD but only 2 GB RAM was detected, the 64 bit Feisty detects the full 4 GB of RAM.

Yes, I know about the rEFIt "Partitioning tool". My GFT and MBR were out of sync but the Partitioning tool didn't saw any differences and never asked to sync the two. I have searched for a tool that tries to do a MBR to GFT sync but I couldn't find any.

I have installed a new set of ALSA drivers like described on [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/89980](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/89980) . One difference though, i didn't use the --with-cards=hda-intel configure flag because I have an additional USB headphone attached to my Apple keyboard. This headphone works when I build and install the complete package (yeah, I don't care which driver it is).

I had to turn off the Headphone switch in the Gnome Volume Control to use the HDA digital output. I've discovered this painfully late, but apparently, it's switched on on default :P

Music playback now works on the Mac Pro analog/digital channels and on my headphones.

I still have that video problem though. Some videos stop sound playback after 2/3 seconds. I still suspect that this is a codec problem. An example codec for which all sound playback fails is "DivX MS-MPEG-4 Version 3". A codec that works without problem is the "XVID MPEG-4" codec. 

I have installed the w64codecs package and all gstreamer-plugin packages that I could find (minus the -dev and -doc's). I tried with VLC too but the problem remains. VLC recovers a lot better from these errors then Totem though...

---

### Post by tosehee on 2007-04-25
I am planning to install Feisty on mac pro also. can you elaborate the steps you took to install with boot camp?

Thanks a lot in advance.

---

### Post by jdemesse on 2007-04-25
[LIST]
[*]Create new partition with bootcamp
[*]Reboot and start the Ubuntu Live CD
[*]Follow the installation and use the bootcamp partition (in my case /dev/sda3). This partition should be used as / .
[*]Install Ubuntu.
[*]Reboot, press ALT during machine bootup and select Ubuntu partition
[/LIST]

A few remarks though: 

[LIST]
[*]Don't use a separate swap partition, use a swap file.
[*]The last page of the Ubuntu install wizard allows you to define where GRUB or lilo should be installed. It's default on (hd0). Change this value to the Ubuntu partition. For example: /dev/sda3 -> (hd0,2).
[/LIST]

Good luck.

---

### Post by tosehee on 2007-04-25
Hrm. What's the reasoning for not using the swap partition?

---

### Post by jdemesse on 2007-04-25
Well, I personally learned that the hard way.

At first, I deleted the bootcamp partition in the Ubuntu Installer. I then created two partitions, a ext3 partition for / and a separate swap partition. Ubuntu installed properly but the GFT and MBR tables were out of sync. From then, Bootcamp and rEFIt would behave wierd:

[LIST=1]
[*]Ubuntu partition doesn't show up in the "Startup disk" OS X applet
[*]rEFIt would show partitions that couldn't boot. I suspect that this happened because of the GFT/MBR out-of-sync differences.
[/LIST]

In the end, I booted into OS X again, deleted the linux partitions, and recreated the single linux partition with bootcamp. Installation was smooth from then on.

My GFT/MBR tables are still out of sync and rEFIt still won't play nice with them but selecting the boot partition with Bootcamp works flawlessly.

---

### Post by tosehee on 2007-04-25
I see.

Thanks for the prompt and detailed explanation. So, if I use the bootcamp and single partition, do I still need to install rEfit and such? It seems that all I gotta do is create partition with bootcamp, then reboot to CD and install. Is this correct?

---

### Post by jdemesse on 2007-04-25
rEFIt won't be needed. I only decided to install rEFIt because 

[LIST=1]
[*]Better graphics in the bootmanager (Linux & windows logos instead of the standard Bootcamp HD image)
[*]Bootcamp tags the Ubuntu partition 'Windows' :) 
[/LIST]
You see, rEFIt was only used to try to create a good looking bootmanager :lolflag:

---

### Post by tosehee on 2007-04-25
Exactly what I wanted to know. Thanks a lot. I will give it a shot when I get home.

Thanks.

---

### Post by evilempire on 2007-04-25
You actually don't need Boot Camp or rEFIt. I installed on my office Mac Pro as follows:

1) I had a 80 gig drive lying around - I installed it in an empty drive bay. 
2) Pulled my other drive - you most likely didn't need to do this, I'm just paranoid.
3) Boot to the Ubuntu CD - you will need to choose Start in Reduced Graphics mode (or some such - I forget the exact option name but it is on the front menu)
4) Took all the defaults - except that I told Ubuntu to take the entire drive.
5) It pretty much just works. Since it installs the bootloader on the spare drive, once you put the other drives back in you will have to manually select the Ubuntu drive via booting with the Option key held down if you want to boot to Linux. It shows up in the boot menu as "Windows". 

I would suggest the first thing you do is go into the restricted driver menu and enable the driver for the NVIDIA graphics card. It makes a big difference, and is required to run Desktop Effects or Beryl.

---

### Post by ronocdh on 2007-04-25
> **evilempire said:**
> You actually don't need Boot Camp or rEFIt. I installed on my office Mac Pro as follows:

1) I had a 80 gig drive lying around - I installed it in an empty drive bay. 
2) Pulled my other drive - you most likely didn't need to do this, I'm just paranoid.
3) Boot to the Ubuntu CD - you will need to choose Start in Reduced Graphics mode (or some such - I forget the exact option name but it is on the front menu)
4) Took all the defaults - except that I told Ubuntu to take the entire drive.
5) It pretty much just works. Since it installs the bootloader on the spare drive, once you put the other drives back in you will have to manually select the Ubuntu drive via booting with the Option key held down if you want to boot to Linux. It shows up in the boot menu as "Windows". 

I would suggest the first thing you do is go into the restricted driver menu and enable the driver for the NVIDIA graphics card. It makes a big difference, and is required to run Desktop Effects or Beryl.
I completely agree this is the best method if you have a separate hard drive to use. If rEFIt supports multiple drive installations--and I should think it does!--I still recommend using it, but as evilempire states, it's totally unnecessary. It is prettier, though. ;)

---

### Post by bstovall on 2007-04-25
I have a Mac Pro and am downloading this file. ubuntu-7.04-desktop-amd64.iso

Is that the one I want or another?
Some say to install the regular i386 (32bit) and then someone else said there is a i386 (64bit) to use.

Am I getting the right file?
Thanks

---

### Post by ronocdh on 2007-04-25
> **bstovall said:**
> I have a Mac Pro and am downloading this file. ubuntu-7.04-desktop-amd64.iso

Is that the one I want or another?
Some say to install the regular i386 (32bit) and then someone else said there is a i386 (64bit) to use.

Am I getting the right file?
Thanks
I recommend you get the AMD64, yes. That should let you use your hardware more extensively (access to more RAM, certainly better multicore handling). You could, however, run the i386 build, you'd just take a performance hit.

The biggest argument against 64-bit right now IMO is lack of solid wireless support for certain chipsets. On a Mac Pro, though, I don't think that'll be a big deal. ;) Make sure you check out the x86 forums, too, as there are some helpful chaps there.

One last thing: you might also want to grab the AMD64 alternate CD. Definitely get it if you have an ATI card in your machine, but if you have Nvidia, you should be alright. [See here]("http://ubuntuforums.org/showthread.php?t=414194") about that.

---

### Post by bstovall on 2007-04-25
I already installed the regular AMD64 (Not the Alternate) I have dual displays and I enabled the Restricted Drivers for my ATI card. I see no option for Dual displays though. Should be in System/Admin right?

Is it possible to get my wi/fi working? My wife will kill me for having a cable accross our dinner table! ;-)

Thanks

---

### Post by ronocdh on 2007-04-26
> **bstovall said:**
> I already installed the regular AMD64 (Not the Alternate) I have dual displays and I enabled the Restricted Drivers for my ATI card. I see no option for Dual displays though. Should be in System/Admin right?

Is it possible to get my wi/fi working? My wife will kill me for having a cable accross our dinner table! ;-)

Thanks
I have thus far had no luck with wifi on 64-bit, but that's with the Atheros 5416/8 chipset. Perhaps in a Mac Pro you have a Broadcomm? I think I've seen more luck with those, but I've never tinkered with one myself. I know the iMacs have 'em, so coast around here a bit and get a feel, or ask straight up about your hardware in the wireless and/or x86 forums.

(Use **lspci** to get your specific chipset; if it's unknown, then **update-pciids** I think is the command.)

I'm confident wireless will be less of a pain for you in i386, but you will notice a performance hit for number-crunching processes. =/ As I said, the **moment** I hear of testable Atheros drivers from Madwifi in 64-bit, I will be all over them! Tonight though, well... I'm burning the alternate for i386 right now. =/

---

### Post by bstovall on 2007-04-26
Well it says it is a Broadcom. Maybe I might be in luck then.
Thanks

---

### Post by The General on 2007-05-02
I just installed Ubuntu on my Mac Pro, but I have a weird problem...

I can't type and move my mouse at the same time. :confused: 

Makes it very hard to play games. :(

Can somebody help me?

---

### Post by The General on 2007-05-02
Nevermind, killall mouseemu fixes it. :)

---

### Post by thejam on 2007-06-12
> **evilempire said:**
> You actually don't need Boot Camp or rEFIt. I installed on my office Mac Pro as follows:[...snip...]
I would suggest the first thing you do is go into the restricted driver menu and enable the driver for the NVIDIA graphics card. It makes a big difference, and is required to run Desktop Effects or Beryl.

Did you use the amd64 version of feisty with the Nvidia driver?

---

