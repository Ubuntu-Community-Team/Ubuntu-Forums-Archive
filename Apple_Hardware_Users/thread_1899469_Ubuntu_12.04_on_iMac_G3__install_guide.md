---
title: "Ubuntu 12.04 on iMac G3 : install guide"
date: 2011-12-23
forum: Apple Hardware Users
---

### Post by agentsteel on 2011-12-23
Hi all,

I juste wrote a small howto for installing Ubuntu 12.04 (development version) on my iMac G3, I thought I could share it :)

(I used 12.04 because the 11.10 mini.iso lacks the pata_macio module which prevents hard disk detection)

[http://agentoss.wordpress.com/2011/12/23/ubuntu-12-04-precise-pangolin-on-imac-g3-powerpc/](http://agentoss.wordpress.com/2011/12/23/ubuntu-12-04-precise-pangolin-on-imac-g3-powerpc/)

Have fun!

---

### Post by raganius on 2012-01-23
Thank you for your step-by-step instructions how to install 12.04 Precise Pangolin to Mac G3 from network. I have succesed to install 12.04 Precise Pangolin from LiveCD (daily build of January 20th) without using internet connection on Mac PowerBook G4 with 867Mhz Cpu & 512Mb of RAM (I tried more than 2 times & it freezes when I used installation with network connection).

You can find description of installation & my experience with 12.04 Precise Pangolin here:
[http://ubuntuforums.org/showthread.php?p=11633906#post11633906](http://ubuntuforums.org/showthread.php?p=11633906#post11633906)

---

### Post by iqtedar on 2012-05-03
**Trying to install Ubuntu 12.04 on an iMac G3 (slot loading 500MHz iMac Snow) using a CD (no hope via a USB flash drive)**

PLEASE HELP!!!

The standard auto installation procedure eventually leads to a command line prompt from which I don't know what to do. Prior to this, a message appears: 'The system is running in low graphics mode - Your screen, graphics card and input-device settings could not be detected correctly. You will need to configure these yourself.' So I select okay. Then the second message states 'What would you like to do?' and gives the options: Run in low-graphics mode for just one session, reconfigure graphics, troubleshoot the error, or exit to console login. I've tried all these options.

There is also a 'clock problem' by the way, but there is nothing I can do about it. Replacing the battery is not a possibility so there must be some parameter perhaps that can be entered to either set the time manually or make the installer ignore this problem?

UPDATE: I've learned how to set the time manually after booting into open firmware. The command is 'decimal dev rtc sec min hour day month year set-time'.

I've browsed and tried a lot and wasted a lot of time but I can't get past the command line prompt and let the Ubuntu installer run.

It is suggested to edit the xorg.conf file but this is not possible until after installation (?)

It is suggested to type 'Linux' at the yaboot boot prompt but this command is not recognised. The options begin with either 'live', 'driver' or 'check' (which appear after pressing the tab key).

It is suggested to add the parameter 'video=ofonly' and to boot into single user mode by adding the 'single' parameter but these options either separately or combined do not make anything work. Entering 'live-nosplash-powerpc video=ofonly single' for example, eventually leads to a blank white screen and when I pressed a key it was slowly displaying an unending list of 'Squashfs' errors (unable to read directory blocks and metadata cache entries).

If there is no way to bypass the command line, is there a way to install from the command line instead (and I would need to reformat the hard drive first)?

I think the installation has to be done via the cd only because I have not been able to successfully create a bootable usb drive. On another MacBook, I was able to boot from an external cd drive instead without any problems. After I'm done with this, I also have an older iMac (tray-loading, non-USB bootable, non-working CD drive) to install Ubuntu on. These Macs are in a school in case you're wondering why there are more than one.

Any help is appreciated!

---

### Post by iqtedar on 2012-05-05
Isn't there anyone who can guide me past the command line to get Ubuntu installed? Or, do I have to start a new thread?

---

### Post by iqtedar on 2012-06-02
Disappointed that no one could help but just thought I should share my experience in installing Ubuntu on an iMac G3 (with ATI Rage 128 graphics card) for others who might be trying the same. Key points:

1. Both the desktop and minimal ISOs are no good for this task. The ALTERNATE ISO is the way to go. With the Desktop CD, you will come up with the low graphics problem (see#6) and with the Minimal CD, you need an Internet connection and it will get stuck at the stage where you have to select a mirror.
2. It doesn't seem to be possible to create a bootable USB drive so that's another red herring.
3. Using the Alternate CD and an Internet connection (via Ethernet), I installed a CLI first and later Edubuntu. For the language options, it is best to leave the default settings, at least for now, otherwise it will add to the installation time significantly.
4. If the computer seems to hang during 'Configuring language-pack-en-base' be patient. You can check for signs of activity on the console output (Alt+Ctrl+f4). Return to the installer display by pressing Alt+Ctrl+f1.
5. If 'sudo apt-get install' doesn't work at first, use 'sudo tasksel' instead and select your choice by 'tasksel install...'.

6. The installation should be done now. But this is where I realised IT IS NECESSARY TO CONFIGURE THE XORG.CONF FILE (to deal with the low graphics mode problem), and maybe also the yaboot.conf file (with the parameter video=aty128fb:1024x768-24@75 just to make the installation easier I think).
7. The suggested parameters to include in the xorg.conf file are 'Option "UseFBDev" "False"' and 'Option "NoInt10" "True"' in the 'Device' section and 'HorizSync 58-62' and 'VertRefresh 75-117' in the 'Monitor' section as detailed at [https://wiki.ubuntu.com/PowerPCFAQ#Configure_graphics](https://wiki.ubuntu.com/PowerPCFAQ#Configure_graphics).

Now the installed system should load. It did in my case (!), but it was VERY SLOW - even Mac OS 10.4 Tiger that was on the iMac previously was better. I then installed Lubuntu/LXDE/LXDM thinking it might due to not having enough RAM (I have 640MB) but strangely it makes no difference. This leads me to think it is not the RAM but some setting, perhaps in the xorg.conf file.

So where do I go from here to gain a usable system? For the other iMac with a non-working CD drive, I guess I will have to try the above mentioned networking method.

---

### Post by rsavage on 2012-06-02
> **iqtedar said:**
> Disappointed that no one could help

I did help you. I wrote the FAQ and known issues (which you haven't read?) pages for you. 
 
> 
7. The suggested parameters to include in the xorg.conf file are 'Option "UseFBDev" "False"' and 'Option "NoInt10" "True"' in the 'Device' section and 'HorizSync 58-62' and 'VertRefresh 75-117' in the 'Monitor' section as detailed at [https://wiki.ubuntu.com/PowerPCFAQ#Configure_graphics](https://wiki.ubuntu.com/PowerPCFAQ#Configure_graphics).

It doesn't say to use them. It says this will give you an inferior setup (some people say it is slower). You should only need "UseFBDev" "False" and "NoInt10" "True" with 12.04 to get the live CDs working.

---

### Post by iqtedar on 2012-06-03
Thanks. I sure did read your pages and also information from elsewhere. But the instructions for tinkering with the xorg.conf settings looked so daunting that I didn't try it earlier until I realised it was necessary. Also, if the live CDs are a hassle, I think you should strongly recommend the Alternate CD for PPC users from the outset, and better still, it should be able to install without the need to have an Internet connection while installing as with the Desktop/Live CD.

I had to make those xorg.conf settings even after having installed a system due to a 'Low Graphics Mode' alert (and a freeze thereafter). Right now, the iMac is not even powering on so I have to sort out this problem first before trying again to achieve a better setup.

---

### Post by iqtedar on 2012-06-04
Could some expert please give straightforward instructions for doing a netinstall on an iMac G3 connected to another computer running Ubuntu via ethernet using the Alternate PPC ISO. I have already read the official and other documentation but there is conflicting information and so far nothing has worked.

---

### Post by finty on 2012-07-16
> **iqtedar said:**
> Could some expert please give straightforward instructions for doing a netinstall on an iMac G3 connected to another computer running Ubuntu via ethernet using the Alternate PPC ISO. I have already read the official and other documentation but there is conflicting information and so far nothing has worked.

Hi. I'm only starting to look into installing Ubuntu, but I'm surprised you haven't found a solution to the problem you're having. In almost my first Google search I read an excellent article by Andy Barrat about recycling a G3 iMac (find it [here]("http://www.andybarratt.co.uk/recycle-imac-g3")) that seems to have a fix for what you're talking about. The relevant paragraph reads: 

[I]"Ubuntu won&#8217;t work straight off the disk with the iMac G3 as it can&#8217;t quite cope with the graphics on board, resulting in a blank screen.  It&#8217;s easy to fix though, just make sure that at the first prompt after booting your machine from the CD, you don&#8217;t just type &#8220;live&#8221; like it suggests, type &#8220;live video=ofonly&#8221; and then hit enter.

This will start Ubuntu in Low Graphics mode.  Once you&#8217;re in, double click to install Ubuntu on the hard drive.  Once you&#8217;re done, you&#8217;ll want to fix that graphics problem properly, it&#8217;s easy to do, just create a text file and copy the text found at [this little linky]("https://wiki.ubuntu.com/PowerPCFAQ#Video_settings_for_G3_iMac") into it.  Now save that file at /etc/X11/xorg.conf and reboot your machine.  Done, you can now get installing all your new software like Firefox 9.  Be warned, there&#8217;s a few things that won&#8217;t want to be installed on a PowerPC chip, like Chrome for instance but you&#8217;ll still get a lot more on there then you were able to before.  Happy recycling."[/I]

Note: The page you'll get when you click the "this little linky" is a wiki. Scroll down to the Graphics section to find what you'll need.

Hope that fixes your issue.

To anyone else reading this, Hello! Nice to be here.
I was on the verge of throwing out a perfectly good G3 iMac, but now I'm quite excited about giving it a new lease of life. I have a very fond attachment to my iMac and I'm delighted that I don't have to send it off to be scavenged! If someone has suggestions for where I should go to get started with Ubuntu (I'm thinking primarily of a quality 'professional' YouTube channel please) I'd be very grateful. It's time to get Ubuntu-ing!

Cheers :o
finty

---

### Post by 2blue on 2012-07-16
Hi 

I don`t know if we can run full Ubuntu 12.04 on the older apple hardware, which I assume any G3 would be (not that I know all possible specs). However, I am almost sure lubuntu 12.04 would install and run fine. I have an iBook G4 only 512MB RAM and 1.4GHz cpu, and I went straight for the lightest Ubuntu derivative, lubuntu. There should be solutions and alternatives for  most applications. I think Totem (media player in Ubuntu) needs at least 1GB to run, and preferably a fast cpu. Totem is very nice on regualar more current hardware, and a lighter running setup is probably a must for the older. 

I don`t know if there are any youtube install guides, or anything comprehensive outside the Ubuntu Forums, but all you need is here, good help and several wiki-pages. Some of the stuff come rather easily, I just went for it and followed instructions along the way. To make all applications work you might have to spend a bit of time tweaking the system with the right software and plugins. It is nice to be able to breathe some life into your old favorite computer ;- )

---

### Post by olds442fun on 2012-07-30
I am new to officially running ubuntu and to be honest, I'm lost just a little. my disc drive on my G3 iMac wont read a 12.04 boot disc. what could be causing this?

---

### Post by theos911 on 2012-08-01
What type of media did you burn the disk to? Can you use the disk drive from within Mac OS? Are you sure you downloaded the correct iso? You likely need the alternate iso:
[http://cdimage.ubuntu.com/releases/precise/release/ubuntu-12.04-alternate-powerpc.iso](http://cdimage.ubuntu.com/releases/precise/release/ubuntu-12.04-alternate-powerpc.iso)

---

