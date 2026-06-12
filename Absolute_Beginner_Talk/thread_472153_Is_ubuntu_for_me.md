---
title: "Is ubuntu for me?"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by ts51 on 2007-06-12
I am thinking about dual booting on my Dell with XP. Will this configuration work and will I be able to do the following? 


My Configuration:
2.63 GHz
512 MB of RAM
Belkin Wireless B/G card with broadcom chipset. 

I at least want to be able to 
[LIST]
[*]chat on aim
[*]network with xp machines
[*]print wirelessly
[*]use McAfee Wireless Internet Security (I don't know if this will work, but I need it in order to log onto my wireless network)[/LIST]
Let me know, as I don't need Ubuntu, but want to give it a 2nd try, and to be able to just about everything I already to on xp. 

Thanks,
TS51

---

### Post by icechen1 on 2007-06-12
Yes but i think broadcom chip set will not work "out of the box".You have to follow some guides in this forum.

---

### Post by ts51 on 2007-06-12
Ok. 

Now, should I decide to dual boot xp with ubuntu, do I just boot into the Ubuntu install CD and choose my 2nd hard drive partition to install to? 

And then, If I do this, can it easily be undone?

---

### Post by Hendrixski on 2007-06-12
yup.. the liveCD can partition the hard-drive for you... it can even unpartition it for you if you don't like it...

---

### Post by Hendrixski on 2007-06-12
By the way.. welcome to the community.  We know you'll looooooooooove Ubuntu, because we all did too which is why we recommend it to all of our friends and why we come by here and help out people who are interested and who are getting started.

There are some good videos to show you how to install Ubuntu at [http://screencasts.ubuntu.com](http://screencasts.ubuntu.com) as well as many other videos to get you started.  Also check out ubuntuvideo.com and ubuntuclips.org
There are plenty of fun manuals, and if you have questions you can Google it, or just ask here and we're more than happy to help.  You can also ask on IRC to chat with people in real time :-)

again, welcome

---

### Post by ts51 on 2007-06-12
ok-- now i just need to decide if i want to take the plunge :)

---

### Post by ts51 on 2007-06-12
Another thing-- 

does anyone have a belkin broadcom card, that is working with the most recent Ubuntu? If so, could you post (or direct me to) an easy to follow guide to installing it that won't take me over an hour to do?

---

### Post by Hobo Joe on 2007-06-12
I'd recommend that, as a new user, you should start with a dual boot.

Having said that, I'm pretty sure everything you just mentioned will work fine.

If you want to install, here is the easiest way to do it:
First, defrag Windows.
Then, when you boot into the live CD, start up Gparted, and resize the Windows partition to the desired size. Then add a partition for Linux, however big you want it, and format it to ext3. Then add a little one, about 1-2 GB, and format it to Linux swap.

Alternatively, and a little easier way to do, but less controlled, you can let the installer auto resize your Windows partition and make the linux ones.

---

### Post by ts51 on 2007-06-12
I already have 2 partitions- one of which i never use
so can i just use the unused one (its blank)

^^^ thats more important-- any ideas at all please post






also will this program work on ubuntu?: [http://us.mcafee.com/root/package.asp?pkgid=278](http://us.mcafee.com/root/package.asp?pkgid=278)

---

### Post by Hendrixski on 2007-06-12
> **ts51 said:**
> I already have 2 partitions- one of which i never use
so can i just use the unused one (its blank)

^^^ thats more important-- any ideas at all please post






also will this program work on ubuntu?: [http://us.mcafee.com/root/package.asp?pkgid=278](http://us.mcafee.com/root/package.asp?pkgid=278)

YES.  If you have a blank partition then you can install Ubnutu on it.. the liveCD will just do it... it'll ask you which partition to use, just select.... again, watch the video on screencasts.ubuntu.com it shows you how to do it very easily

As for the McAffee program, i don't know.  You may want to call them and ask if they have a linux version.  You're going to hear this a lot so I'll say it first;  you don't need a lot of security tools on Linux because it's built secure.  it's not full of bugs the way that Windows is.  Ubuntu comes with a built-in firewall... and you can install a virus-scanner from the repositories which will scan your emails for Windows viruses so that you don't pass them on.  Linux itself has never, not once in 15 years gotten a virus.  Ever.  just doesn't happen.

---

### Post by ts51 on 2007-06-12
> **Hendrixski said:**
> YES.  If you have a blank partition then you can install Ubnutu on it.. the liveCD will just do it... it'll ask you which partition to use, just select.... again, watch the video on screencasts.ubuntu.com it shows you how to do it very easily

As for the McAffee program, i don't know.  You may want to call them and ask if they have a linux version.  You're going to hear this a lot so I'll say it first;  you don't need a lot of security tools on Linux because it's built secure.  it's not full of bugs the way that Windows is.  Ubuntu comes with a built-in firewall... and you can install a virus-scanner from the repositories which will scan your emails for Windows viruses so that you don't pass them on.  Linux itself has never, not once in 15 years gotten a virus.  Ever.  just doesn't happen.

First, thanks for all the help. 

The only reason I use the McAffee program is because it help to encrypt my wireless network from others.

I think I'll try it. After all, if it doesn't work I'll just wipe out my linux partition and only use xp 

by the way: downloading ubuntu as of now

---

### Post by Swab on 2007-06-12
> **ts51 said:**
> First, thanks for all the help. 

The only reason I use the McAffee program is because it help to encrypt my wireless network from others.


 

You don't need McAffee to setup encryption, you can do it yourself, it's as simple as entering a key.. well it's simple if you can get that broadcom card working.

---

### Post by bone43 on 2007-06-12
You may want to read this page..

[http://ubuntuforums.org/showthread.php?t=232059](http://ubuntuforums.org/showthread.php?t=232059)


Have Fun :D

---

### Post by rusty4r on 2007-06-12
If you'll search the tips and tutorial forum there is a "how to" on broadcom cards

---

### Post by ts51 on 2007-06-12
> **Swab said:**
> You don't need McAffee to setup encryption, you can do it yourself, it's as simple as entering a key.. well it's simple if you can get that broadcom card working.


I know, but the thing that make McAffee "special" ,so to speak,  is that it rotates the WEP key every  2 hours (I think thats the time interval) to make your network more secure.

---

### Post by Hendrixski on 2007-06-12
> **ts51 said:**
> First, thanks for all the help. 

The only reason I use the McAffee program is because it help to encrypt my wireless network from others.

I think I'll try it. After all, if it doesn't work I'll just wipe out my linux partition and only use xp 

by the way: downloading ubuntu as of now

:-) hey, we're all here to help because we love Ubuntu.. and because someone else helped us when we were getting started because that person loved Ubuntu as well... and soon, you'll love Ubuntu and you'll be telling everyone you know about it and helping them out.  trust me.

As for macafee  they're a big enough company that they may have a Linux version.  if not, then one of their competitors may.  But then again... because Linux is just so damn secure very few people make security products for it.

---

### Post by Hendrixski on 2007-06-12
also

If you're downloading make sure that you have a way to create a .iso image... it's not the same as burning a regular CD on Windows... though, it SHOULD be, just some developer thought that they can make your life harder.  I would recommend the videos at [http://screencasts.ubuntu.com](http://screencasts.ubuntu.com).  they're free, and they're not like that bald guy on TV who's like "buy my expensive videos to teach you how to use Windows, and then I'll send you crap in the mail until forever"
no. none of that.  just good videos that help you get started

---

### Post by Swab on 2007-06-13
> **ts51 said:**
> I know, but the thing that make McAffee "special" ,so to speak,  is that it rotates the WEP key every  2 hours (I think thats the time interval) to make your network more secure.

Well WEP can be cracked in under 1 minute.  You should be using WPA to secure your wireless.

---

### Post by ts51 on 2007-06-13
Before I do any OS installing, I want to know how to set up the wireless. I need some tutorial that assumes you have no way of connecting to the internet in Ubuntu (meaning you have to download onto a flash drive or cd from, say a working, XP machine) that is easy to follow. If someone could point me to a tutorial, that would be great. I figure that if I understand Ubuntu, installing as a dual boot on a primary machine shouldn't be a problem. 

By the way: my wireless card is a "Belking F5d7000 version. 2000 802.11 b/g card"

The wireless aspect is the only thing stopping me from installing. 


-TS51

---

### Post by Zzl1xndd on 2007-06-13
> **Swab said:**
> Well WEP can be cracked in under 1 minute.  You should be using WPA to secure your wireless.

I was gonna mention that and its an important point just switch to WPA

---

### Post by Smeltn on 2007-06-13
well first time here. I am really excited to try out Ubuntu. I have been reading on it for a few weeks now and got the CD yesterday.  

I am not looking at replacing Windows completely yet, considering I play World of Warcraft ALOT. But I am extremely excited to get started using ubuntu and learning everything I can about it.


Great forums btw, you guys are extremely helpful from what I read to any noobies questions. 

I hope you will be the same to me, considering I know I will have a few questions myself.. :P

---

### Post by ts51 on 2007-06-13
> **tweakedenigma said:**
> I was gonna mention that and its an important point just switch to WPA


Ok. Thanks for the tip. 


-TS51

---

### Post by ts51 on 2007-06-13
> **Smeltn said:**
> well first time here. I am really excited to try out Ubuntu. I have been reading on it for a few weeks now and got the CD yesterday.  

I am not looking at replacing Windows completely yet, considering I play World of Warcraft ALOT. But I am extremely excited to get started using ubuntu and learning everything I can about it.


Great forums btw, you guys are extremely helpful from what I read to any noobies questions. 

I hope you will be the same to me, considering I know I will have a few questions myself.. :P

Just start a new thread under the begginer section as I did. Ask for help there, and it will come.

---

### Post by ts51 on 2007-06-13
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Ndiswrapper_for_Broadcom_43xx_wireless_chipset](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Ndiswrapper_for_Broadcom_43xx_wireless_chipset) 
I am probably going to use that guide to install my wireless card. 

Can some one verify:

1) That that guide is accurate for my 32bit system
2) That the Belkin F5D7000 version 2000 802.11b/g card is Broadcom 43xx 


I like that guide, and if it is accurate, and will work, I am going to install Ubuntu. 

Does anyone know if it is possible to test a guide like that using only the live cd? 

-TS51

---

### Post by Swab on 2007-06-13
> **ts51 said:**
> [http://ubuntuguide.org/wiki/Ubuntu:Feisty#Ndiswrapper_for_Broadcom_43xx_wireless_chipset](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Ndiswrapper_for_Broadcom_43xx_wireless_chipset) 
I am probably going to use that guide to install my wireless card. 

Can some one verify:

1) That that guide is accurate for my 32bit system
2) That the Belkin F5D7000 version 2000 802.11b/g card is Broadcom 43xx 


I like that guide, and if it is accurate, and will work, I am going to install Ubuntu. 

Does anyone know if it is possible to test a guide like that using only the live cd? 

-TS51

I just installed today on a machine with a Broadcom 43xx.  I used the fwcutter method and it worked with no problem.  Of course I did have a wired connection to download the needed package.

The instructions there tell you how to check if you have a Broadcom 43xx.   You can boot the live CD and test from there.

---

### Post by ts51 on 2007-06-13
> **Swab said:**
> I just installed today on a machine with a Broadcom 43xx.  I used the fwcutter method and it worked with no problem.  Of course I did have a wired connection to download the needed package.

The instructions there tell you how to check if you have a Broadcom 43xx.   You can boot the live CD and test from there.


I'll do that. If I get the wireless working in the Live CD, then I'm installing.


-TS51

---

### Post by ts51 on 2007-06-13
[B]Alright. Tried to get wireless working in the Live CD. Didn't happen. Process worked but I couldn't connect (card never powered on). I am assuming that's because I was trying this in the Live CD and not on an actual OS. 

This is what happened in the terminal:[/B] 

[COLOR=Red] To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ cd ~/Desktop
ubuntu@ubuntu:~/Desktop$ tar -xf bcm4318.all.tar.gz
ubuntu@ubuntu:~/Desktop$ sudo ./ndiswrapper_setup
Starting ndiswrapper install...
If you have any package managers open (i.e. Adept or Synaptic or apt-get),
Please close them now.
Pausing for 10 seconds - please read the message.
Feisty release detected.
Installing ndiswrapper-1.9...
Done...
ndiswrapper: No such file or directory
ndiswrapper died with exit status 1
ndiswrapper: No such file or directory
ndiswrapper died with exit status 1
You appear to have an i386 system...installing the i386 drivers...
Done...
Adding drivers to ndiswrapper...
Done...
Gathering wireless card information...
Done...


----------------------------------



You should probably install an wireless connection manager
(if you er using Feisty, network-manager is already installed
The best choices are
                        network-manager OR wifi-radar
Strengths/weaknesses of network-manager:
+ Is able to use WPA, WEP, or any other kind of standard encryption
+ Easy to change networks
- Asks for keyring password on boot to connect to encrypted networks
- No network profiles, or at least you are unable to see them
- Is impossible to connect to a wired and wireless network at the same time
- No static IPs
- Network strength does not work

Strengths/weakness of wifi-radar:
+ Works 99% of the time
+ Static IPs or DHCP
+ Supports WEP
+ Network strength sort of works
+ Doesn't need password at boot
+ Able to connect to wired and wireless at the same time
- No WPA

After you have connected to the internet,
I would recommend installing one of these programs.
To install network-manager, open Synaptic (Ubuntu) or Adept (Kubuntu)
and find the package network-manager-gnome, and install it.
To install wifi-radar, open Synaptic (Ubuntu) or Adept (Kubuntu)
and find the package wifi-radar, and install it.


----------------------------------


Script completed.
If your wireless light is on, give your internet a shot.
If you are interested in install a connection manager, please
scroll up and read the pros and cons of a couple.
You will have to connect to use the internet now.
In Feisty just right-click on the network-manager icon in the top right of the screen,
you should see your wireless access point now.
If your are using an earlier distro, this can be accomplished (in GNOME) by
going to System / Administration / Networking,
and configuring the wireless card by selecting the network name.
If something is not working, please try rebooting.
If you need more help, please post ~/Desktop/bcm4318-setup.log on
the forum thread where you downloaded it from for help.[/COLOR]            

[B]
Now, if I go ahead install ubuntu, will this work? Or will I have the same outcome? If I can't get it working quickly, then I won't have time to use Ubuntu.[/B]

---

### Post by Nekiruhs on 2007-06-13
Post deleted by poster

---

### Post by ts51 on 2007-06-13
Any Ideas??

---

### Post by Sethalos on 2007-06-13
> **ts51 said:**
> Ok. 

Now, should I decide to dual boot xp with ubuntu, do I just boot into the Ubuntu install CD and choose my 2nd hard drive partition to install to? 

And then, If I do this, can it easily be undone?

I initially did the Dual Boot thing, but found that running Win XP through VirtualBox using the following instructions: [http://ubuntuforums.org/showthread.php?t=433359](http://ubuntuforums.org/showthread.php?t=433359)

I find this much easier and more eye pleasing, and it realllly freaks out my Windows Buddies when I do the cube rotation from the Windows Desktop.

Good luck

---

### Post by ts51 on 2007-06-13
> **Sethalos said:**
> I initially did the Dual Boot thing, but found that running Win XP through VirtualBox using the following instructions: [http://ubuntuforums.org/showthread.php?t=433359](http://ubuntuforums.org/showthread.php?t=433359)

I find this much easier and more eye pleasing, and it realllly freaks out my Windows Buddies when I do the cube rotation from the Windows Desktop.

Good luck


OK. 

Are you also that my method for installing my wireless card will work?

---

### Post by ts51 on 2007-06-13
hmmm....

---

### Post by Swab on 2007-06-13
Like I said, I used the fwcutter method.  It was straight forward. 

Did you check if your card is bcw43xx ?

---

### Post by ts51 on 2007-06-13
No, I am unsure how as every time I try it, nothing happens. Pretty sure though.......

---

### Post by Mazza558 on 2007-06-13
ts51, I'm afraid you'll need to install Ubuntu to do this, but it will enable wireless.

Download the file attached, put it on a flash drive and when you've installed Ubuntu run that file. It will ask if you want to install it, as well as your password. Install, then just reboot and you should be good to go.

You won't be able to get this working in the LiveCD, by the way.

---

### Post by ts51 on 2007-06-13
> **Mazza558 said:**
> ts51, I'm afraid you'll need to install Ubuntu to do this, but it will enable wireless.

Download the file attached, put it on a flash drive and when you've installed Ubuntu run that file. It will ask if you want to install it, as well as your password. Install, then just reboot and you should be good to go.

You won't be able to get this working in the LiveCD, by the way.


Thank you so much. I've been waiting for a program like this. Makes life easy, you know? 

This should be included with Ubuntu.

---

### Post by ts51 on 2007-06-13
One last note: I just double click it and it does everything for me?

---

### Post by Mazza558 on 2007-06-13
> **ts51 said:**
> One last note: I just double click it and it does everything for me?

A window will come up asking if you want to install it. One click and reboot. It's not a program, rather a package. It was supposed to be included with Feisty.

---

### Post by Billy_McBong on 2007-06-13
[COLOR="Blue"].debs will install by just double clicking and then click the install button[/COLOR]

---

### Post by ts51 on 2007-06-13
> **Billy_McBong said:**
> [COLOR=Blue].debs will install by just double clicking and then click the install button[/COLOR]

Ok. Looks like I might be installing Ubuntu sometime tonight or tomorrow. 

For me the Live CD is very snappy and quick-- I'd love to see how much faster it is when it's actually installed...

---

### Post by ts51 on 2007-06-13
Alright-- 

Went to install, and to my surprise, for once, wireless was not the issue. 

I was informed I needed at least 1 2gb partition and then 1 256mb linux swap partition. 

OK, I thought to myself. I'll just make another partition. I tried, but couldn't. Why? According to GPartition, you can't have more than 4 partitions. Unfortunately,  2 are Dell Backup Partitions and 1 is my xp partition. I can't part with these, so what should I do? 

Like I said before, I don't want to install without first learning all I can about Ubuntu/linux, which I did, but I never expected this. 

-ts51

---

### Post by ts51 on 2007-06-15
Just to let you know-- have ubuntu all up and working.

---

### Post by Swab on 2007-06-16
> **ts51 said:**
> Just to let you know-- have ubuntu all up and working.

Fantastic!

---

