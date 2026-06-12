---
title: "ubuntu studio porting"
date: 2007-05-12
forum: Apple PPC Users
---

### Post by StaticX on 2007-05-12
Hello everyone, I was hoping this is the correct place to post, I was wondering what steps would be necessary to "port" (not sure if this would be a correct term for a debian GNU/linux-based distro)  Ubuntu-studio to powerPC architecture.  I don't have a TON of programing experience, but would love to add this contribution to the community of which I have become so fond.  I am using Xubuntu feisty and with a 350Mhz ppc (powermac b&w) w/448 MB ram, and 2 swap drives (512 mb each, which weirdly enough gives my box a bit more breathing room, and at least speeds up a couple graphics programs and GCC) 

any suggestions would be appreciated....Thanx in advance

---

### Post by mrbugspray on 2007-05-16
Well the only way I can think of is to install ubuntu ppc, and install all the ubustu packages with synaptic. it should work as long as they support powerpc. For the packages that don't, you could probably install them from other repos. Then you can use linux mint, or reconstructor. (Don't know if they are for ppc.) If you get it to work, please share it. it's the way of the ubuntu.

---

### Post by stmiller on 2007-05-16
For audio and video work in Linux, a low-latency kernel with a higher kernel timing setting is required. Ubuntu studio is built on this kernel. 
Ubuntu also provides these kernels for x86 and x86_64, but not ppc. So to make the most of a ppc audio distro you would need to recompile your own kernel with these settings.

I could make a how-to, if anyone is interested. But other than the kernel, just using synaptic to install all the audio apps would get your system up to par with the programs in ubuntustudio.

---

### Post by jaboit on 2007-05-16
> **stmiller said:**
> For audio and video work in Linux, a low-latency kernel with a higher kernel timing setting is required. Ubuntu studio is built on this kernel. 
Ubuntu also provides these kernels for x86 and x86_64, but not ppc. So to make the most of a ppc audio distro you would need to recompile your own kernel with these settings.

I could make a how-to, if anyone is interested. But other than the kernel, just using synaptic to install all the audio apps would get your system up to par with the programs in ubuntustudio.

Such a how-to would be amazing and most appreciated. Perhaps I'm not the only one?

:)

---

### Post by stmiller on 2007-05-17
Okay let me try to get something together and I'll perhaps put a posting on the PowerPCFAQ page.

---

### Post by stmiller on 2007-05-17
Okay I posted a quick and dirty how to:

[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

Enjoy! I use a low-latency kernel with higher timing and find that everything from DVD playback, video playback, and audio playback is 100% better. Faster and smoother. I wish ubuntu would enable these options by default.

---

### Post by jaboit on 2007-05-18
> **stmiller said:**
> Okay I posted a quick and dirty how to:

[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

Enjoy! I use a low-latency kernel with higher timing and find that everything from DVD playback, video playback, and audio playback is 100% better. Faster and smoother. I wish ubuntu would enable these options by default.

Wow! This looks amazing, I can't wait to try it out. Thanks again.   :grin:

---

### Post by Piuro on 2007-05-18
I'm also interested in doing this, but am fairly new to linux (I have someone who knows what they're doing helping me). Which portion of the above link do I want to be looking at?

---

### Post by stmiller on 2007-05-18
Hey- sorry I should have mentioned where I put the info. It's the section:

How can I configure and compile my own kernel under PowerPC Linux?


When I have more time I will try to make debs of a low-latency kernel. I've tried a few different ways following the x86 how-tos to create kernel debs and it never quite works right for ppc. So for the time being, you'll have to compile your own kernel if you want extra options.

---

### Post by Piuro on 2007-05-18
Well, like I said, I'm new to linux. With my Ubuntu machine as a backup though, if I screw up I can always format :D. Best way to learn to swim and all that...

---

### Post by Piuro on 2007-05-18
Okay, as absolutely stupid as is it for someone as new as me to be doing this... I've compiled the kernel, now what do I do, if you don't mind guiding me a bit on this.

---

### Post by mrbugspray on 2007-05-18
> **stmiller said:**
> Okay I posted a quick and dirty how to:

[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

Enjoy! I use a low-latency kernel with higher timing and find that everything from DVD playback, video playback, and audio playback is 100% better. Faster and smoother. I wish ubuntu would enable these options by default.


Thanks... You convinced me to use ubuntu as my primary operating system. :) Thanks Again.

---

### Post by stmiller on 2007-05-19
> **mrbugspray said:**
> Thanks... You convinced me to use ubuntu as my primary operating system. :) Thanks Again.

Ha! Well that is not exactly my purpose. :) But glad I could help.

PS: Piuro: my yahoo or jabber id is on my profile. Feel free to add me to your buddy list.

---

### Post by johng4 on 2007-05-21
I'm sucky with WIKIs but I'll try to add this in the WIKI as well, but there's a step that will further dimplify the process of configuring the kernel so that all you have to do is enable the realtime options and compile:

Before you enter the "make menuconfig" section of compiling you can load the current config file from your running kernel, thus negating the need to re-enable options for your current kernel.  

Just copy your config file like so...
cp /boot/config-(uname -r) ./.config.base-config

Substitute the (uname -r) for the actual command line command "uname -r" which for me was 2.6.20-15-powerpc.

This will create a new hidden file in the /usr/src/linux directory named .config.base-config where your current kernel settings are.  Then, when you enter the "make menuconfig" you scroll down to the bottom of the list and choose "Load an aleternate configuration file" and then type in the name of the file (".config.base-config") and then load it in.

Then you just change the options that you need to change and everything should compile just nicely.

---

### Post by stmiller on 2007-05-21
> **johng4 said:**
> I'm sucky with WIKIs but I'll try to add this in the WIKI as well, but there's a step that will further dimplify the process of configuring the kernel so that all you have to do is enable the realtime options and compile:

Before you enter the "make menuconfig" section of compiling you can load the current config file from your running kernel, thus negating the need to re-enable options for your current kernel.  

Just copy your config file like so...
cp /boot/config-(uname -r) ./.config.base-config

Substitute the (uname -r) for the actual command line command "uname -r" which for me was 2.6.20-15-powerpc.

This will create a new hidden file in the /usr/src/linux directory named .config.base-config where your current kernel settings are.  Then, when you enter the "make menuconfig" you scroll down to the bottom of the list and choose "Load an aleternate configuration file" and then type in the name of the file (".config.base-config") and then load it in.

Then you just change the options that you need to change and everything should compile just nicely.


I found that creating a new .config with the make g5_defconfig or pmac32_defconfig actually enables more ppc things that the ubuntu folks left out, esp for G5 hardware. And fetching a new kernel would have more ppc features, which would be enabled by doing the defconfig, and not by just copying your old .config.

YMMV

---

### Post by mrbugspray on 2007-05-26
I think i will start working on a port. Once i'm done, i'll ask the ubustu guys if they can put in up for download. if not, i'll just make my own site. :)

---

### Post by mrbugspray on 2007-05-26
Hey peoples

i managed to put the Ubuntu studio graphics and video packages compiled for powerpc. I am making the disk image now. I have **NOT** added the low latency kernel, the audio and audio plugins, or the theme. I will post back again when I test it.

---

### Post by mrbugspray on 2007-06-05
never mind about the port. My hard drive of my laptop somehow died. :(
But it's not all bad news. I wiped my hard-drive and then used the ubuntu live cd to install the ubustu packages. It turns out that the ppc versions are in the repos and on the launchpad. I'll try to get an iso of that uploaded. Much easier than manually installing each one. ;)

Cheers

---

### Post by Aitikin on 2007-06-17
I have extremely limited experience with Ubuntu, but I'm a Pro Audio guy.  I really wanted to see how well UbuntuStudio would replace OS X, unfortunately for me, I'm on an iBook.  I don't want to be able to go through 50 steps to install UbuntuStudio when I decide to try it, I want to have the ability to switch at any given time.  That being said, I'm ready and willing to work to make that happen.  I have plenty of Linux experience, but like I said, very little Ubuntu, or Debian for that matter.  I'd be happy to help with a port, but I wouldn't have the time to help maintain or anything of the sort, so if someone wants help with this project, I'll be glad to do so.

---

### Post by mrbugspray on 2007-06-18
First things first, I now do not have the resources to make a port. I was working on one but I now need the computer for school and they don't allow linux. :( But ANYBODY with an ppc computer can. I will tell you how. I don't know why, but they have ppc versions of all the packages in the repos. Anybody who  has the time to make an iso of this with reconstructor, or remastersys, please contact me at [email]mr.miloshovel@gmail.com[/email]. I will upload them to an ftp server. I will also contact the ubuntu studio team. They might upload them. :)

Step 1: Install Ubuntu
Step 2: In terminal as root, type in:

sudo su -c 'echo deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main >> /etc/apt/sources.list'
wget -q [http://archive.ubuntustudio.org/ubuntustudio.gpg](http://archive.ubuntustudio.org/ubuntustudio.gpg) -O- | sudo apt-key add - && sudo apt-get update

Step 3: Install The Following packages with synaptic:

ubuntustudio-audio - Ubuntu Studio audio package
ubuntustudio-audio-plugins - Ubuntu Studio audio plugins package
ubuntustudio-graphics - Ubuntu Studio graphics package
ubuntustudio-video - Ubuntu Studio video package

Step 4: For the low latency kernel, (You need this.) see, 

[http://ubuntuforums.org/showthread.php?t=453497&highlight=low+latency](http://ubuntuforums.org/showthread.php?t=453497&highlight=low+latency)

Optional: If you want the theme, download this file:

[http://www.belutz.net/ubuntu/ubuntustudiotheme.tar.gz](http://www.belutz.net/ubuntu/ubuntustudiotheme.tar.gz)

;)

---

### Post by Aitikin on 2007-06-19
If you can point me to a guide for using reconstructor or remastersys, I'll do it in a little while.  I need to clear off some space so I can make a second install.

---

### Post by mrbugspray on 2007-06-19
Thanks Atikin! There is a how to here:

[http://reconstructor.aperantis.com/cgi-bin/moin.cgi/Docs/Using_Reconstructor#head-5fbb21a085c394c083e056df08dc999b593d6efd](http://reconstructor.aperantis.com/cgi-bin/moin.cgi/Docs/Using_Reconstructor#head-5fbb21a085c394c083e056df08dc999b593d6efd)

Please make it as similar as ubuntu studio as you can. Make sure that you install EVERYTHING from the ubustu repos and nothing else, including the link to the artwork i gave you. And please also contact me if you make it. I'll try to make a launchpad page of ubustu ppc. Hopefully the ubustu team will use the iso. if you do that, i'll add some drivers for airport and maybe some extra goodies. Long live Ubuntu Studio!

---

### Post by Aitikin on 2007-06-20
Cool.  Well like I said, I need a while cause my iBook's kinda swamped right now.  I'll be able to free up some space once I get done tinkering with my desktop.  Well, once I get done tinkering with this little project on it ;)

---

### Post by johng4 on 2007-06-22
I tried to get remastersys to work, but for some reason it will do everything, but won't create the iso.  Its the easiest way between the two, since its a 1 command program.  Takes a working installed system, and remasters it into an iso.

I've found reconstructor to be slow, and awkward to use.  

Remastersys works 100% on non-ppc systems though.. not sure if its just the arch difference.

Either way, as my avatar might point out, I'm working on a studio variant that is strictly audio based (TuneForge Linux).  I'm going to make it for 64-bit, 32-bit and PPC.  Each will contain realtime kernels, as well as resource optimized desktops.

---

### Post by cogitordi on 2007-06-23
I have a G4 PowerMac that I'd like to set up as a dual-boot with Ubuntu and OS X. I'm a software engineer and music/graphics hobbyist. I can help you with the port.

---

### Post by mrbugspray on 2007-06-23
> **johng4 said:**
> I tried to get remastersys to work, but for some reason it will do everything, but won't create the iso.  Its the easiest way between the two, since its a 1 command program.  Takes a working installed system, and remasters it into an iso.

I've found reconstructor to be slow, and awkward to use.  

Remastersys works 100% on non-ppc systems though.. not sure if its just the arch difference.

Either way, as my avatar might point out, I'm working on a studio variant that is strictly audio based (TuneForge Linux).  I'm going to make it for 64-bit, 32-bit and PPC.  Each will contain realtime kernels, as well as resource optimized desktops.

maybe try using reconstructor:

[http://reconstructor.aperantis.com/](http://reconstructor.aperantis.com/)

---

### Post by mrbugspray on 2007-06-23
> **cogitordi said:**
> I have a G4 PowerMac that I'd like to set up as a dual-boot with Ubuntu and OS X. I'm a software engineer and music/graphics hobbyist. I can help you with the port.

Try this for the dual boot:

[http://www.askdavetaylor.com/how_do_i_dual_boot_ubuntu_linux_mac_os_x.html](http://www.askdavetaylor.com/how_do_i_dual_boot_ubuntu_linux_mac_os_x.html)


After you do that make sure you have airport drivers installed. Once that's done just use reconstructor. If it tells you about missing dependancies use synaptic to install them. :)

[http://reconstructor.aperantis.com/](http://reconstructor.aperantis.com/)

---

