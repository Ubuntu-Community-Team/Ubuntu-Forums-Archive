---
title: "Triple boot Macbook Pro: OSX, Linux, Vista"
date: 2007-03-14
forum: Apple Intel Users
---

### Post by jimmydie on 2007-03-14
Hello All,

I keep searching for someone who has done a triple boot using OSX, Linux, and Vista, but I am not sure if this is being done. I'm currently running OSX Tiger, Ubuntu EdgyEft and Windows XP on a Macbook pro and it is working great. My ultimate goal is to run Leopard, Ubuntu Edgy or greater and Vista for support purposes. Is this being done?
I sometimes get great alternitive ideas when I post that answer differently from my question, such as: Why not get another machine, or What do you need all three for? Just remote into another machine, etc... Unfortunately I am stubborn and want to Triple boot like I described: OSX, Ubuntu, and Windows Vista :grin: .

What I would like to know is: 

Has this been done successfully using the OSX, Ubuntu, and Vista RC1 or greater?


Best,

---

### Post by silhouette on 2007-03-14
The problem is getting OS X to install without disturbing any of the other installations. Same problem with Windows. AFAIK it isn't possible to install either without wiping the whole drive. The other problem is which bootloader to use since I don't think GRUB can load OS X. Hmm, [here's a post](http://uneasysilence.com/archive/2005/08/3934/) that suggests maybe you can use chainloading to defer GRUB to the OS X bootloader, then load OS X (or Windows?) from there. So yeah, I think it's possible, it just might take a lot of experimentation.

---

### Post by cyberdork33 on 2007-03-14
you are going to have the most trouble in getting Vista not to mess things up. Maybe you can defer that install to a VM? Vista likes to control the Hard drive. Maybe in the final version of bootcamp, Vista will be supported, and that will give another option.

---

### Post by jimmydie on 2007-03-14
Thanks for the heads up. I've looked into the chainloading and it could be a possibility. That thread is talking about XP and I am talking about triple booting to Vista. Probably for the purposes of this thread it is best to specify Vista or XP when talking about Windows. Let's hope that someone who has had succuss triple booting VISTA, OSX and Linux is out there. 

Anybody?

---

### Post by nonpareilpearl on 2007-03-14
I tried asking for information, but didn't find anything:

[http://ubuntuforums.org/showthread.php?t=376109](http://ubuntuforums.org/showthread.php?t=376109)

I figured when I had enough money I'd do test it all out :: malicious laughter ::

---

### Post by jimmydie on 2007-03-14
Yes the VM is a possibility, but as I mentioned. I am stubborn and have tunnel vision so I'll need a good shrink or someone who maybe has been triple booting OSX, Linux, and Vista or some solid evidence that this is impossible.;)

---

### Post by mickinator on 2007-03-14
I was on the phone to good people at Apple as i plan on purchasing one soon, they said it was possible to dual boot vista and osx, but they werent sure about the linux, i need all 3 as im doing ze programming, so im presuming that if its ok to dual boot vista and osx, and some people here have installed linux, then it is possible to do all 3

---

### Post by cyberdork33 on 2007-03-14
I don't think the current bootcamp beta supports vista:
[http://www.apple.com/macosx/bootcamp/](http://www.apple.com/macosx/bootcamp/)

i think the final version is supposed to.

---

### Post by Chrisj303 on 2007-03-14
I have my macbook setup to TripleBoot OSX/XP/UBUNTU. To use Vista instead of XP, AFAIK is ,as of yet, a no-go.
You need to find a good guide to follow, the onmac.net triple boot guide is head and shoulders above the rest.
In a nutshell
1.install osx
2.install bootcamp (make drivers)
3.install refit (osx)
4.partiton hard drive (disk util)
5.install XP
6.Bootoff live cd (ubuntu)
7.install refit.deb
8.install ubuntu.
9.install LILO (GRUB dosen't work properly)

*like i said, you really need to follow a guide. There is a little more to it, but not much. My install is solid as a rock.

chrisj303

---

### Post by cyberdork33 on 2007-03-14
BTW, IDK where these "grub doesn't work" things are coming from it works fine for me...

---

### Post by jimmydie on 2007-03-14
I have found no reports of anyone triple booting OSX, Linux, and Vista. 

The triple boot with XP works nice, but the first time I did this I felt like I was walking through deep mud. I'll be willing to walk through mud again if i can get Vista on my machine.

---

### Post by redfox on 2007-03-14
The relevancy of my post is only partial.  Vista isn't supported, but it does run via Boot Camp.  I had RC1 running on mine (I still would, but not having proper drivers was making it not worth it).

You've done a lot more research on this than me, but it would seem that since you can run Vista with Boot Camp, there is a way.  I think some of the older guides would be more relevant, because they are less smooth, and this is a less smooth procedure.  (That makes sense to my fogged mind, but there might be more reasonable reasons that I am not thinking of right now.)

I foresee this thread or topic becoming very important.

---

### Post by Chrisj303 on 2007-03-15
> **cyberdork33 said:**
> BTW, IDK where these "grub doesn't work" things are coming from it works fine for me...

When using GRUB, it would only respond to my keyboard about 20% of the time - which is a nightmare as i need the keyboard to select which OS i want to boot.
As soon as an OS was booted however the keyboard worked perfectly.
And you don't have to look very hard at all to see that many,many people have lot's of issues with GRUB on the Macbook.
Also, with LILO, it will boot the OS i select via refit without any user interaction whatsoever - it boots straight into the windows 'loading' screen.
I have yet to see a triple boot guide that uses GRUB.

Cheers,
chrisj303

---

### Post by cyberdork33 on 2007-03-15
I have seen the many troubles people are having with grub, that is why i don't get it, it was NOT an issue for me.

---

### Post by chipm on 2007-03-15
I am typing this on a Macbook Pro that is reliably triple booting Mac OSX, Ubuntu, and Vista. It took me nearly a dozen install attempts to get (almost) everything to work. I say almost because the only thing that doesn't work at this point is the wireless card under Ubuntu. These are the key learnings:

1) There are several tutorials out there on how to do this install, but none of them work completely. I had to pick and choose bits and pieces from several to get something that worked and worked repeatedly.
2) I could not get GRUB to work reliably, no matter how many times I tried. Something about the keyboard driver prevented me from scrolling down the list (I could only scroll with a USB keyboard attached). I really wanted to use GRUB, but in the end went back to LILO, which has consistently worked fine.
3) Every time OSX or Ubuntu does a system or firmware level update it breaks my Vista boot capability. When this happens I insert the Vista disk, and select it from refit. The keyboard doesn't work at this point, so I have to use a USB keyboard to click Enter to get into setup on the Vista disk. Once there, just click Repair and Vista fixes the problem. After that it will boot normally into Vista, until the next update screws with the hardware/boot partition. This has happened about once a week or so the past month. It's a little annoying, but I just carry the Vista disk around with me and it hasn't been a problem.
4) The Atheros wifi card does not have a linux driver. Madwifi is coming out with one, but no date is known. Doing the ndiswrapper approach you'll read about on a bunch of blogs and forums only ends up locking up my system (if you use the DLink driver) or failing to install (if you use the newest Lenovo driver). I think it will work with an older Lenovo driver, but I don't have it and couldn't find it. When I want to use wireless I use OSX or Vista, and am living without wireless in Ubuntu until Feisty fixes this for me (the card is supposed to be supported).
5) I could not compile and install a new Kernel that LILO would boot into. It is probably my own ignorance, but I gave up after a few failed attempts and reinstalls.
6) You only need Bootcamp for the driver disk. Use Mac OSX diskutil to make the partitions and then install Refit. Refit is an amazing tool, and works very well. Once you have your partitions, you can try various install of Windows and Linux without messing up Refit or the OSX partition. OSX and Refit always worked throughout my attempts. It's comforting to see something work when nothing else does.
7) As you read through the instructions in various tutorials about how to chroot from the Ubuntu Live CD, hang on to them! You will end up doing that procedure several times to make changes to your Ubuntu install when you need to boot from the Live CD. Once I figured this out, it made life a lot easier during my attempts to get GRUB to work and to upgrade my Kernel. LILO has been reliable, but I understand that a kernel upgrade will require me to fix LILO as well (this hasn't happened yet, but knowing the chroot steps make it a trivial fix).
The chroot code I'm referring to looks something like this:
sudo su -
mkdir /mnt/ubuntu
mount /dev/sda2 /mnt/ubuntu
mount -t proc none /mnt/ubuntu/proc
mount -o bind /dev /mnt/ubuntu/dev
chroot /mnt/ubuntu /bin/bash
You'll need to type all that each time you want to access your Ubuntu partition from a Live CD boot
8 ) Be careful when using tutorials that are for Macbooks. They have different hardware, and several ideas (like right clicking, wifi, and so on) didn't work with my Macbook Pro. Same goes for comments on forums and blogs. I tried a lot of things that didn't work because I didn't pay attention to this.
9) I couldn't get Feisty Herd 5 to work, so I am using Edgy. Hopefully the final release of Feisty will work, because it has some nice hardware support for the Atheros wifi card, and the mac keyboard and touchpad.
10) If you are used to Windows, you will find the lack of right click annoying. There are a bunch of solutions, but the only one I could get to work reliably was:
xmodmap -e 'keycode 116 = Pointer_Button2'
xmodmap -e 'keycode 108 = Pointer_Button3'
xkbset m
This sets you little enter key to be the right click, and the right Apple key to be the middle click. You have to install xkbset for this to work. I use it in a shell script that runs at startup (add it under Preferences->Sessions->Startup).
11) In addition to external USB keyboard, I can't recommend a USB mouse highly enough. I never had the mouse lock up, but being able to easily right click when setting up Vista and Ubuntu made life a lot easier. You can get by without one, but if you have one, use it. I used a wireless Microsoft Notebook Mouse and it worked flawlessly in all 3 OSes throughout all of my attempts. Pretty amazing, that.

That's pretty much it. Vista looks great and runs very well on this machine. I haven't installed Beryl/Compiz (after all the work it took to get this up and running, I'm sticking to using it for now, I've had a lot of problems with Beryl on my other PC, and don't want to mess this up), but have read that it can be installed and works well. Please post your experiences if you try it.

In my next post I'll post a tutorial of the things that worked for me.

Hope this helps someone!

---

### Post by oskarloko on 2007-03-15
Just only on point ( 4 )

You used the last xp D-LINK driver on ndiswrapper or the first version of it ?

On this web [http://www.dlink.com/products/support.asp?pid=489&sec=0](http://www.dlink.com/products/support.asp?pid=489&sec=0)
Firstly I used 1.02 and linux hangs

Then I switched to 1.01 and worked fine...

But that was on Egdy

---

### Post by chipm on 2007-03-15
Thanks for the tip.

I indeed tried the DLink 1.0.2 driver, which consistently locked the machine as soon as I enabled wireless. I haven't tried 1.0.1, but read elsewhere also that it does work. Ndiswrapper, while excellent, didn't work with 1.0.2, and I tried compiling several versions before learning that apparently the newest versions are the most problematic with this driver. After all the hassle of trying to uninstalling ndiswrapper (even after a lot of manual editing of config files it still gives LILO errors on startup) I think I'm going to just wait for an actual  linux driver. Having wireless in OSX and Vista ought to hold me until April and Feisty.

---

### Post by jimmydie on 2007-03-16
It sound like there is a information gap trying to triple boot with Mac OSX Tiger, Linux Ubuntu (or other) and Vista. On the other hand there could be lack of interist in this setup.

---

### Post by strogon14 on 2007-03-16
In reply to point 4) of chipm:

I got wireless to work under Ubuntu Feisty on an Intel Mac mini 1.8 Hhz with the latest SVN version of madwifi (as of 15/03/2007). This Mac mini version uses an Atheros chip too. This is the respective output of [FONT="Courier New"]lspci[/FONT]:

[FONT="Courier New"]02:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)[/FONT]

The procedure was very simple:

[FONT="Courier New"]
sudo apt-get install build-essential
# I dont know if the next step is really necessary
sudo apt-get install madwifi-tools
svn checkout [http://svn.madwifi.org/trunk](http://svn.madwifi.org/trunk) madwifi
cd madwifi
make
sudo make install
sudo modprobe ath_pci
[/FONT]

and then use the network-manager to configure the wireless network. The module gets loaded automatically after the next boot.

I have only tried WEP encryption so far, not WPA.

Hope that helps somebody!

Chris

---

### Post by ZERO_SHIFT on 2007-03-17
Have anyone thought of running both vista and os x on Virtual box on Ubuntu?

---

### Post by jimmydie on 2007-03-17
That is some good info Chipm, I must have skipped past your lessons of war the last time I posted. I look forward to your Tutorial. I bet that when Leopard, comes out there will be nice way to get them all to boot more seemlessly. And It sounds like Fiesty will be around that time also.

---

### Post by Movi on 2007-03-19
I'm just gonna give out some tips, because just 2 days ago i did wrestle with OSX Linux and Vista. So here's the deal:

-Vista doesn't play nice with GRUB. It WILL refuse to install if it sees Ubuntu.
-Vista brakes after you install Linux, although just do what it says (boot from CD, click some repairing stuff) and it will work fine.
-NTFS-3G DOESN'T work with Vista (yet). 

And one more thing. I found having a double bootlader painfull with refit around. So after i installed Ubuntu, i actuall told Vista to overwrite grub. Then i booted from the Ubuntu CD, did the chroot stuff, modified /boot/grub/menu.lst so that instead of writing GRUB to the MBR, it will write GRUB to your Linux partition. This makes stuff much better considering that the keyboard doesnt ALWAYS work with GRUB, hence you wouldnt be always able to select vista and/or Ubuntu, and within refit selecting windows will kick you to grub anyway (in such a setup refit is actually useless after syncing MBR with GPT). Although refit wll be kinda confused on where your Linux is (it will say "Boot Linux from " instead of "Boot Linux from partition 3") it will work just as great. 

Hope this helps a lot, as to the drivers for vista - i think this isn't the place for that ;]

Oh, and after i learned that Psychonauts are barely playable because of the DX9 emulation, i killed it and installed XP in that space. XP didn't complain about Linux. But it looks so ugly. And Vista looks bareable but wont do what i want it to do.... Damn!

---

### Post by jimmydie on 2007-03-20
How much ram did you have when you are trying to triple boot with OSX, Ubuntu and Vista?

---

### Post by stickboy3k on 2007-04-18
> **Movi said:**
> 
And one more thing. I found having a double bootlader painfull with refit around. So after i installed Ubuntu, i actuall told Vista to overwrite grub. Then i booted from the Ubuntu CD, did the chroot stuff, modified /boot/grub/menu.lst so that instead of writing GRUB to the MBR, it will write GRUB to your Linux partition. This makes stuff much better considering that the keyboard doesnt ALWAYS work with GRUB, hence you wouldnt be always able to select vista and/or Ubuntu, and within refit selecting windows will kick you to grub anyway (in such a setup refit is actually useless after syncing MBR with GPT). Although refit wll be kinda confused on where your Linux is (it will say "Boot Linux from " instead of "Boot Linux from partition 3") it will work just as great. 


I was wondering if that was possible, really annoying having both bootloaders, refit is great. Any chance you could post a little how to on the grub stuff? Is it possible to remove grub from the mbr and reinstall it on the linux partition or will I need to wipe linux and vista, then reinstall?

Thanks :)
Ron

---

### Post by Ken T on 2007-04-18
Thanks to all posters on this thread.

This may or may not be of interest to some: I've tackled the issue of having multiple OS's (Mac, Ubuntu AND Windows) running on my Macbook in a slightly different way. A pal of mine who owns a Mac store put me onto Virtual Machine software for Mac called Parallels, and while I did have to pay US$79 for the priviledge (sob), I can now run all three seamlessly, simultaneously. On rare occasions, Ubuntu has had an abortive bootup, but a simple reboot has fixed it. I like being able to skip between OS's without need of rebooting. Anyways, I know it's not a direct answer to the question, but perhaps it's of help. K

---

### Post by armware on 2007-06-24
I've spent this weekend trying to setup a triple boot between Vista, OS X and Kubuntu Fiesty on an HP Pavilion dv8000 (dv8230us).
I've been able to install all the os's, but can't seem to get the boot loader setup to properly launch into OS X. I can still boot into linux and vista.

Any ideas to get grub going properly?

OSx86 is installed on the second partition of the first drive (hd0, 1), yet that doesn't work.

More details:
I had OSx86 installed and running, including the proper video drivers. I decided to wipe the OSx86 partition and create two in its place, one for Vista and one for OSx86, leaving Kubuntu installed and untouched.
I have dual booted Kubuntu and Vista, and Kubuntu and OSx86, but combining them into the bootloader seems to be the only issue.

I could use some tips.
Thanks.

---

### Post by Chrisj303 on 2007-06-26
> **Ken T said:**
> Thanks to all posters on this thread.

This may or may not be of interest to some: I've tackled the issue of having multiple OS's (Mac, Ubuntu AND Windows) running on my Macbook in a slightly different way. A pal of mine who owns a Mac store put me onto Virtual Machine software for Mac called Parallels, and while I did have to pay US$79 for the priviledge (sob), I can now run all three seamlessly, simultaneously. On rare occasions, Ubuntu has had an abortive bootup, but a simple reboot has fixed it. I like being able to skip between OS's without need of rebooting. Anyways, I know it's not a direct answer to the question, but perhaps it's of help. K

I'm sure most people on these forums are aware of parallels/vmware, but it's just not the same as running the OS natively. 

I do however use VMware to boot my windows partition while in ubuntu ( i tripleboot osx/ubuntu/xp) on a mac.

I'm going to setup a tripleboot this weekend with osx/ubuntu/vista - i'll approach it in exactly the same manner as i did my current setup, using LILO. GRUB has always made things difficult for me.

I'll post back when sucsessfull  !

---

### Post by armware on 2007-06-26
Turns out, everything works as planned - something just f'd up my OS X. Every time I'd try to boot it by selecting it in the grub menu, it'd flash something on the screen and go back to the grub menu.
I booted into the OS X installer again, ran a scan on the partition, it found errors (and fixed them) but I still had the same problem, so I reinstalled OS X all together.
All three OS's work now, side by side.

I like the idea of booting the actual install within a virtual machine when needed, can it be setup to go back and forth (between selecting in the grub menu and in a virtual machine)?
Where can I find how to do that? THAT would be a handy (as well as nifty) trick.

As far as how I got all three to play nice, they just sort of cooperated for me.

---

### Post by Chrisj303 on 2007-06-26
> **armware said:**
> 

I like the idea of booting the actual install within a virtual machine when needed, can it be setup to go back and forth (between selecting in the grub menu and in a virtual machine)?
Where can I find how to do that? THAT would be a handy (as well as nifty) trick.

As far as how I got all three to play nice, they just sort of cooperated for me.


The grub bootloader won't be seen by the VM. It will boot just as any vm would.
To boot my windows install, while in ubuntu (on a mac!) i followed this guide:
[http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html]("http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html")

*Beware though, that this can apparantly cause WGA/Activation issues - i use a 'corporate' version to avoid this.

---

### Post by Tab on 2007-06-26
Easily done. Just partition your disk with Boot Camp, install Vista, and then install Ubuntu. Bam. It just works since Fesity included GRUB with EFI support. But really, you're much better off doing virtualization. I triple-booted for a while and then was forced to go the VM route, and haven't looked back.

---

### Post by Chrisj303 on 2007-06-27
How are you better off with virtualization?

I was using parallels and vmware fusion before i was triple booting, and found the limitations horrible.

---

### Post by Chrisj303 on 2007-07-01
> **Chrisj303 said:**
> I'm sure most people on these forums are aware of parallels/vmware, but it's just not the same as running the OS natively. 

I do however use VMware to boot my windows partition while in ubuntu ( i tripleboot osx/ubuntu/xp) on a mac.

I'm going to setup a tripleboot this weekend with osx/ubuntu/vista - i'll approach it in exactly the same manner as i did my current setup, using LILO. GRUB has always made things difficult for me.

I'll post back when sucsessfull  !


Well that was easy enough!!

I just booted from the Vista disc, reformatted my XP partition to ntfs, then installed Vista over it! - bootcamp 1.3 drivers and Bobs your uncle.!

*All* partitions boot and function fine.

I'm using LILO as my linux bootloader - i have a strong suspicion that Grub is whats giving people trouble.

I used 'V - Lite' to chop down an ultimate edition to fit on a CD - it works out as a 3GB install.

I have used 'ext2 IFS ' and this guide
[http://ubuntuforums.org/showthread.php?t=358241]("http://ubuntuforums.org/showthread.php?t=358241")

...to Read/Write to my ubuntu partition.

---

### Post by Chrisj303 on 2007-07-02
Just an update,

I've just re-installed ubuntu - i just reformatted the partition and installed over the previous ubuntu. 

EVERYTHING WORKS FINE

Before i installed LILO (to the partition), i rebooted using GRUB - and again, everything was fine. I think the trick with the OSX/UBUNTU/VISTA tripleboot, is to install the bootloader to the actual partition, not hd0.

I also forgot to say, that rEFIt did not need re-syncing throughout the install of both OS' - everything just worked.

---

### Post by cyberdork33 on 2007-07-02
ubuntu installer was fixed for 7.04. No need to sync tables.

---

### Post by IrunwindowsjustoforACAD on 2007-07-02
has anyone tried to tri boot XP OSX and the Ubuntu live CD on a 2.16GHz macbook using boot camp?
I;m running XP and mac OSX on boot camp and i want to try out the Ubuntu live CD but for some reason, after I downloaded the software, burned the image to a CD and a DVD, boot camp does not recognize it when I start up the computer and press the option key with either the CD vesion or the DVD version... I tried it with rEFIt and the osx, xp and the live cd showed up in the menu as i booted the computer but when i chose the cd option it loaded windows! i tried choosing windows and it loaded windows also, and osx option ran osx...so what am i missing?!?! I ordered a copy of the ubuntu live cd just to see if it was the way i burned the cd so i' waiting for that to arrive.

---

### Post by linkx on 2007-07-03
I have triple-boot OS X, UbuntuStudio, and Vista Ultimate on my MacBook Pro right now. It's been runing like this for five months. Everything works great. I will post a how-to when I have time (next few days). Contact me with specific questions.

---

### Post by IrunwindowsjustoforACAD on 2007-07-06
Is it possible to run the Live CD of ubuntu while i have two other OS's running on my computer via bootcamp?

Processor: 2.16 Ghz intel COre 2 Duo
Memory: 1 GB 667 MHz DDR2 SDRAM
Startup Disk: Macintosh HD
Dual Booting with Boot Camp WIndows XP
   #:                   type name               size      identifier
   0:  GUID_partition_scheme                    *111.8 GB disk0
   1:                    EFI                    200.0 MB  disk0s1
   2:              Apple_HFS Macintosh HD       91.0 GB   disk0s2
   3:   Microsoft Basic Data Untitled           20.5 GB   disk0s3

---

### Post by IrunwindowsjustoforACAD on 2007-07-06
Aparently something's wrong with doing so because my Live CD won't show up in my boot Menu...unless I have refit, but it only loads windows if I click on the live CD option!!

---

### Post by cyberdork33 on 2007-07-06
I am confused. You have Windows and OSX... and want to boot the Ubuntu CD? There shouldn't be an issue with that.

---

### Post by IrunwindowsjustoforACAD on 2007-07-07
Ya I know. I fixed the problem, what it was is that my live CD, which I burned several times in my macbook, for some reason was not burned right! I don't know why my macbook is not copying the image to the cd correctly... I burned it in like two dvds and 3 cds and it dowsn't work...
what i did was i downloaded the live cd form my pc and used ISO to burn the cd, now it works fine on my mac...
Should I be worried about my macbooks impotency of burning an image to the cd??:(

---

### Post by Chrisj303 on 2007-07-10
> **IrunwindowsjustoforACAD said:**
> Ya I know. I fixed the problem, what it was is that my live CD, which I burned several times in my macbook, for some reason was not burned right! I don't know why my macbook is not copying the image to the cd correctly... I burned it in like two dvds and 3 cds and it dowsn't work...
what i did was i downloaded the live cd form my pc and used ISO to burn the cd, now it works fine on my mac...
Should I be worried about my macbooks impotency of burning an image to the cd??:(


I use TOAST.

In toast i do :

CD COPY>IMAGE FILE>(POINT TO IMAGE)>MOUNT>BURN.

This should work everytime, if it dosen't then it would suggest a problem.

---

### Post by cyberdork33 on 2007-07-10
> **Chrisj303 said:**
> I use TOAST.

In toast i do :

CD COPY>IMAGE FILE>(POINT TO IMAGE)>MOUNT>BURN.

This should work everytime, if it dosen't then it would suggest a problem.

Pretty much any burning app should be capable of burning an image file. You shouldn't have to buy toast. 

There is a free app called Burn that you might want to try. You never said what you used to burn the ISO though.

---

### Post by thefockinfury on 2007-07-12
-bump-

if anyone out there has come across a guide for setting up a triple boot (osx/ubuntu/vista) on a macbook, or one of the successful users here would be so kind as to write one, it would be MUCH appreciated. 

i had a working triple boot with osx/ubuntu/xp but ultimately had to scrap it because the partition sizes weren't what i needed. i went to parallels briefly but abandoned it for two reasons:

1) it has great 3d acceleration and the performance surprised me, but it's still not compatible with a good number of windows games
2) as a computer science student, a studio engineer and a musician, ubuntu studio is just about the greatest thing to ever happen to me... but the limits of virtualization make it impossible to work with midi or have direct access to my audio hardware.

i don't NEED to install vista (i know its bulky and intrusive) but i'm a real sucker for eye candy and i'm looking for a challenge. if i hate it i can always go back to XP anyway. i really just want to experience vista running natively. 

anyway, that was just a rambling for anyone who cared. the bottom line is: i'm about to go back to the triple boot setup. if there have been any developments in this topic please do tell! i'm not even looking for a step-by-step tutorial; i would really just like to know the fundamental differences (if any) between installing XP and Vista in a triple-boot environment.

thanks to anyone who can help. sorry to thread-jack but my query is pretty much the same as the original post and it wouldn't have made sense to start a new thread.

---

### Post by thefockinfury on 2007-07-13
update:
i just went ahead and installed vista. it went completely without a hitch... didn't throw any errors or anything. i have NOT yet reinstalled ubuntu. so right now i have a working dual boot with OSX and vista, with an empty linux partition in between them. 
when starting up, vista yells at me about an unsupported volume or something, and asks me to repair it, but boots past it anyway. i'm not going to mess with that until after ubuntu is installed. 
i gotta say that vista looks pretty cool. although i do find the start menu even more counterintuitive than XP's and i can definitely see that vista's security and DRM controls are going to start annoying me very soon. but aero is a cool interface, and it satisfies my soft spot for fancy GUI's. i'll take it. 
i'll let yall know when i'm finished installing ubuntu and i have my triple boot working. after that i would be happy to contribute my limited knowledge to anybody else's effort to write a triple boot guide.

---

### Post by thefockinfury on 2007-07-15
success! i'm writing this post from my newly reinstalled ubuntu feisty. it was probably the smoothest linux install i've ever done, and getting vista to play nice with ubuntu and OSX was no more difficult than it was with XP (save for one small hitch, which i'm about to discuss)

the guide i followed for this install was here:
[http://www.cs.helsinki.fi/u/jzshen/install_feisty.html]("http://www.cs.helsinki.fi/u/jzshen/install_feisty.html")

linux boots using GRUB installed to the linux partition as opposed to the MBR. the one problem seems to be with vista's bootloader. when booting up it repeatedly displays an error that reads something like "Warning: Unrecognized partition table for drive 80. Please rebuild it using a Microsoft-compatible FDISK tool (err=4)." it displays this message several times but boots past it in the end without a problem. i'm not entirely sure what to do about this, but rather than thread-jack, i'll make another post asking for help on this issue.

if anyone has some questions about what i did i'd be happy to explain what i did in my limited noob capacity.

cheers

EDIT: here is the link to my new thread if anyone has any info:
[http://ubuntuforums.org/showthread.php?t=501408]("http://ubuntuforums.org/showthread.php?t=501408")

---

### Post by RMSe17 on 2007-07-18
> **Movi said:**
> 
-NTFS-3G DOESN'T work with Vista (yet). 


Don't need it if you install Vista on FAT32.  Thats what I did, runs fine. (I used Vista Enterprise)

By the way, BootCamp doesn't do anything but let you partition the drive (and creating the correct partition tables) without losing data and create a drivers cd.  That is all it does.

---

### Post by michael_cowan on 2008-05-19
Hi,

Not sure if this is still of any use to you but I recently blogged my method for triple booting Vista, Linux and OSX:

[http://blog.reloadsystems.net/2008/05/18/triple-boot-vista-linux-and-osx/](http://blog.reloadsystems.net/2008/05/18/triple-boot-vista-linux-and-osx/)

Hope this helps.

---

