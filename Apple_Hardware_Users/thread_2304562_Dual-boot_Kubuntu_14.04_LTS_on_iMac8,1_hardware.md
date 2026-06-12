---
title: "Dual-boot Kubuntu 14.04 LTS on iMac8,1 hardware"
date: 2015-11-27
forum: Apple Hardware Users
---

### Post by rdnublx on 2015-11-27
Greetings to all,

If my question is mis-posted, please point me to the right place for it.

My assumption is that my iMac, no longer performing well under newer  versions of Mac OS X, would do just fine on Kubuntu. I need a dedicated  Linux machine, and this would be a win-win for me, preserve a good  quality computer, and avoid spending extra money.

I have reviewed several guides on various Mac related web sites,  instructing how to install Ubuntu on a Mac. The information did not give  me a lot of confidence, that it's a stable and predictable process.  Also, it did not answer my specific concern with respect to installation  of Kubuntu LTS on my specific hardware, iMac 8,1.

I would appreciate it if someone could conclusively tell me that such  installation is possible and point me to a clear and specific set of  instructions. I don't mind if it's an extensive multi-page set of steps,  as long as I could achieve a predictable, stable result.

I hope that my inquiry does not come across as too demanding. I am just  trying to avoid starting an open ended, character building exercise of  researching various compatibility issues, bootloaders, or drivers. I am  too old for this

---

### Post by Bucky Ball on 2015-11-28
*Thread moved to **Apple Hardware Users**.*

You'll get a better response here I'd think. Good luck. :)

---

### Post by rdnublx on 2015-11-28
Thank you!

---

### Post by Bucky Ball on 2015-11-28
All good. :) I'm not a Mac user, but from what I've read here and picked up along the way, you will need to arm yourself with Boot Camp and probably also reFIND. As I say, though, I am no expert.

---

### Post by rdnublx on 2015-11-28
Yes, rEFInd boot manager is what I would have to use, that's the part that I am less worried about. I felt that people are not sure whether the entire process is predictably doable or not, even people who provided guidance on Mac sites. Potential issues are graphics card, and who knows. Other concern is that I am not sure whether latest Kubuntu would work in this particular hardware. Few years ago I would have been thrilled with this adventure, but now I just need to get to the end point. I was concerned that people may perceive it as me being too lazy to do the research, but it's not the issue. The open-endness  of this undertaking was my concern, it's too much risk for me given my schedule at the moment. Regarding BootCamp, it's good for Windows dual boot, would not help with Linux, AFAIK. Appreciate your help anyway!

By the way, love your location identifier, Australia isn't it? :D

---

### Post by Bucky Ball on 2015-11-28
Best thing to do is [download the Kubuntu 14.04 LTS ISO]("http://www.kubuntu.org/getkubuntu#download-block") (bit torrent is most reliable), create boot media, either USB or DVD, boot from it and 'Try Kubuntu'. That will allow you to 'test drive' without installing or changing anything on your current setup/hard drive. If you have issues with anything, yell out. This way, you will end up with the opportunity to see how well Kubuntu 14.04 runs and you'll have install media to install, if you get to that. 

Give that a go and see if it sings in a live session. That will give you some idea. If anything is going to cause problems, yes, it will be graphics and wireless, but they are *usually* fixable.

---

### Post by rdnublx on 2015-11-28
Ok, thank you, is that the approach people call Live CD? I was not sure what it meant in one of the posts.

I guess I should do it. What stopped me was a post indicating that despite a successful try like that when the gentleman actually went ahead with a real dual-boot install the monitor was just dark, suggesting graphics problem.

---

### Post by Bucky Ball on 2015-11-28
Yea, that sometimes happens. And is usually fixable. If it worked on the Live session, there would almost definitely be a way to make graphics happen on a full install. I really wouldn't let that put you off. We can get MUCH more detail about your machine if you boot into a live session. We'll be able to identify graphics and wireless and be able to tell you with more certainty. But as I say, just because it doesn't 'just work' on a full install is no reason to not install. Usually just a matter of tweaking. Not uncommon.

Try the live session and let us know how you go when you get there. We can give you directions to give more specific hardware info. :)

* If you do get to a live session and all is working fine, open a terminal (unsure how you get there in Kubuntu but you will find it somewhere) and copy/paste these commands in and run them one at a time:

```
lshw -C network
lshw -C video
```

Post the output of each back here between code tags (see the last link in my signature).

(Note: In a terminal you need to use control+shift+c for copy. Replace 'c' with 'v' for paste. Or you can use the 'Edit' menu there.)

---

### Post by rdnublx on 2015-11-28
Thank you, your explanation gives me confidence to proceed, at least making it worth a try. Now I just need to find a clean DVD disc  :)

By the way, it appears that the following page may be out of date, with respect to the suggested boot manager. AFAIK, rEFIt is no longer maintained. The boot manager which is supposed to be used is rEFInd 
[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

The paragraph at the top of the page is somewhat confusing as well. And  [the link on the third line]("https://help.ubuntu.com/community/ubuntuprecisequantalon2011imac")
[SIZE=2]                 [/SIZE]
doesn't instill much confidence as well.

Hence my inquiry here about a recent up-to-date installation guide.

Anyway, setting this all aside, I am going to make the first step as you suggest.

Thanks again.

I see your update, added while I was replying. All understood, good instructions, thank you.

---

### Post by Bucky Ball on 2015-11-28
Just had a look at the specs of that machine. Not sure Ubuntu is what you should be going for here. You might like to try a lighter flavour. You have 1Gb of RAM? [Lubuntu]("https://help.ubuntu.com/community/Lubuntu/GetLubuntu") is what you're after, or perhaps [Xubuntu]("http://xubuntu.org/") might give some good results, too.

You could get even lighter with a [minimal install]("https://help.ubuntu.com/community/Installation/MinimalCD") but that would be a steep learning curve. Let's try and get there with Xubuntu or Lubuntu first (I prefer the former, more configurable) and save that for later. :)

Older Xubuntu has worked fine for me with 1Gb of RAM. Newer versions, not sure. Try it.

---

### Post by rdnublx on 2015-11-29
Originally, it could have been 1 or (more likely) 2GB, to the best of my recollection. However, I have upgraded RAM to 6GB quite some time ago. I had to run Fusion with Win XP, hence the memory upgrade.

in fact, I did install and run Kubuntu 10 LTS and then 12 LTS on various Macs on Fusion. The whole point of transitioning to the dual-boot or single OS configuration was to get away from additional compatibility issues with Fusion, on different levels.

My initial intent was to buy a cheap laptop and install Kubuntu on it. Then I thought, wait a minute, I have a beautiful piece of hardware which is choking a bit under the weight of newer versions of Mac OS X, making it impractical to upgrade to the latest, let's say Mac OS 10.11. Why not run Linux on it?

In my development experience, running large cross compiles on Linux was close to three times faster than on Cygwin. Hence, I was fairly confident that this iMac with dual core CPU and 6GB RAM would be flying just fine running Linux, straight on the hardware, without the burden of running Mac OS concurrently. I didn't realize that I would have to deal with so much uncertainty again. With Windows, Apple appeared to do a good job implementing BootCamp, but I don't see anything like this with respect to Linux dual-boot.

Anyway, with your encouragement and expert advice, I hope to see it through. I was joking yesterday but actually I could not find a single DVD in the house. I am thinking that I probably should set up a bootable image on a USB drive. Based on what I have read it appears to be a legitimate option. It seems that an 8GB USB should be sufficient. 

Thanks for your help.

---

### Post by Bucky Ball on 2015-11-29
Yep, 4Gb stick would also be fine. What I generally use.

Here's a couple of links to help with creating the USB:

UNetbootin:
[www.unetbootin.sourceforge.net](www.unetbootin.sourceforge.net)

Universal USB Installer:
[www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

---

### Post by rdnublx on 2015-11-29
Thank you, ready to proceed, however just a hit confused about the following reference on [http://unetbootin.github.io](http://unetbootin.github.io)
"[COLOR=#000000][FONT=verdana]Note that Live USB drives are bootable only on PCs (not on Macs).[/FONT][/COLOR]" It's even more confusing because there is clearly a Mac OS X button at the top. 

Does it only apply to the USB Drive install mode? But this defeats the whole purpose, doesn't it?

---

### Post by Bucky Ball on 2015-11-29
Try [this]("https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick#UNetbootin_.28Automated.2C_graphical_approach.29"). 

Yes, Unetbootin does have a big Mac button top right of their page but I'd suggest this is to create a USB to boot on a PC. In other words, you can create the USB with Unetbooting on the Mac to install Ubuntu on a PC. Handy ... but not here. Hmm. :-k

A DVD does look like the best way to go. Apologies, I didn't know this, but as I say, not a Mac user so unaware and trying my best to keep things rolling until a Mac aficionado chimes in. You'll get there! :)

---

### Post by rdnublx on 2015-11-30
> **Bucky Ball said:**
> 

A DVD does look like the best way to go. Apologies, I didn't know this, but as I say, not a Mac user so unaware and trying my best to keep things rolling until a Mac aficionado chimes in. You'll get there! :)

Agree, DVD is the way to go. And, no apologies necessary, please. Truly appreciate your help and guidance. Probably would have dropped it already if not for you coming back here and nudging me forward. The truth is that the exercise of "making it work" is quite seductive, often distracting from the main focus of the project. I have been down this road a few times. At some point I may need to stop and switch to the original idea of a cheap Linux only laptop, but at this point I am willing to continue and try to "get there" as you say.

---

### Post by Bucky Ball on 2015-11-30
Well, if you can get it running from a USB so you can try it 'live' (it only says you can't install to a Mac, nothing about trying it live, so worth a shot) that may give you more impetus. I can't remember: You haven't got a blank DVD handy or you haven't got a DVD drive? If the former, could you beg, borrow or steal a DVD from somewhere? If the latter, could you possibly burn a DVD on another computer?

---

### Post by rdnublx on 2015-11-30
Not going to pursue the USB approach, too much uncertainty, too little time, the web page says that it's not bootable on Mac, forget it.
Ordering a 15-DVD pack, Maxell, 16x. It should be of sufficient quality and speed of recording. I assume that 4.7 GB DVD would be sufficient for this purpose.Please let me know if otherwise. Thanks

---

### Post by Bucky Ball on 2015-11-30
All good. Let's pursue this when they arrive. They're fine for the purpose.

---

### Post by rdnublx on 2015-11-30
[SIZE=2]Thanks, ordered [/SIZE][SIZE=2]Verbatim 16X 4.7 GB, should get here on Thursday[ATTACH=CONFIG]265857[/ATTACH]:D

[/SIZE]

Well, I am back here, got my DVDs today, the adventure continues. Burned a Live DVD, verified sha256, was able to launch a boot sequence from the DVD drive. At the first menu, started with the following default options.

```

acpi=off
noapic
nolapic
edd=on
nodmraid
nomodeset

```

I believe it's not a correct configuration based on what I have seen on  the screen during the boot sequence. Specifically, I think the acpi  setting is incorrect.

Then funny thing happened on the way to the theater. Of course, I did not realize that I have wireless keyboard and mouse. When the boot sequence got to the Welcome screen, the one where it prompts to either try Kubuntu, or install it, I was not able to do anything.

I borrowed a regular USB keyboard fron another desktop, however it would not respond to Enter key when the Try Kubuntu square was highlighted. At the same time, Tab button works as I am able to move among four fields. In fact, the only selection which does not respond to Enter is the Try Kubuntu one. Even Quit responds. I am puzzled what is expected here, mouse only action, or some key combination, which seems too clever. I may reboot and see if it would recognize the keyboard. Regardless of that, there is no hope for wireless mouse, unless you have any idea how to enable Blue Tooth (should be supported?)

---

### Post by Bucky Ball on 2015-12-04
You won't have hope for wireless mouse and keyboard without drivers which won't be installed during Live install session. There will not be an issue on a HDD install. If some hardware doesn't work 'off the bat' in a Live session, don't take it as a given it is not going to work in an installed. Ubuntu. You are using the installer, not the full installed Ubuntu.  

Switch the computer off completely and switch back on with the keyboard plugged in already. Any luck? The fact it is not working is odd. So you're highlighting 'Try Ubuntu' and hitting 'Enter' on the keyboard and nothing? No change on the screen at all?

When you say you started with those options, where did you set them? You shouldn't need to set anything until the need arises. You were experimenting because the keyboard didn't work? How did you get to those options? If you changed them, how if the keyboard doesn't recognise anything but tab?

---

### Post by rdnublx on 2015-12-04
An update here.

Now, I chose Quit from the Welcome screen, and the funny thing was that it actually proceeded to log in and open a desktop. Of course, Bluetooth is on responds to requests from the wireless mouse but I can't confirm anything because the keyboard is mostly irresponsive. For example, it reacts to Ctrl-Esc and brings up a some kind of task manager.

Even if I reboot and the keyboard would be fully functional, I am not sure that I would be able to engage the mouse, because a pairing code would be required.

Intuitively though, it seems that if a full installation with an appropriate configuration was made, it should work. Possibly some drivers could be required. I am not sure whether Apple modified a Bluetooth driver, or it's just a standard protocol, completely unfamiliar with this topic. In the worst case, I could buy a regular USB mouse and a keyboard as needed.

One thing I would like to avoid for sure is an open end nature of this exercise. If I have to make N steps that's not a problem, as long as there is a clear path or two forward.

> When you say you started with those options, where did you set them? You  shouldn't need to set anything until the need arises. You were  experimenting because the keyboard didn't work? How did you get to those  options? If you changed them, how if the keyboard doesn't recognise  anything but tab?
Those are default options, I have not changed anything. To get to the options, I pressed F6 on the first dialog screen. I believe the options are described here [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

The keyboard is actually at least semi-functional, because I was able to shut down gracefully.
Right now, I am rebooting with the USB keyboard plugged in prior to the cold start.

Kubuntu advanced welcome page is a bit different. It does not have the try option.

My guess was correct, I just found out that a special key would be needed to proceed with a DVD boot from the Welcome screen
[http://docs.kubuntu.org/docs/installation.html#mac-os-x](http://docs.kubuntu.org/docs/installation.html#mac-os-x)

Getting back to that screen, will give it a try

Ok, none of these keys worked. However, a weird thing happened. I pressed Ctrl-Option-Esc and an Easter egg type effect took place. A skull and bones appeared above the Try square, and when I pressed Enter I believe the computer went away, the screen became dark. I had to wake it up, but it never came back to the menu and did shut down. I have no idea what it is. One thing for sure, the Try button does not work with Enter. I am going to try to read that documentation one more time.

[ATTACH=CONFIG]265933[/ATTACH]

Here is the skull and bone image. I can move it using arrows buttons. I have no idea what's going on here. Sorry the image got rotated, not sure how, but don't have the time to retake it.

Basically, selecting Quit from the Welcome screen and then confirming Yes to the question, 'Do you want to quit the installation?' actually boots into the desktop. Graphics looks pretty nice, fits the screen correctly, not sure what else I should do to evaluate that.

At this point, I am going to stop for now. Intuitively, I believe we have a proof of concept, it should work once installed properly, using rEFInd boot manager. However, I am not sure how long it would take to fix all potential glitches. For example, I got some errors while booting from DVD (see attached image). Based on what I have read after that, some related to kernel boot configuration, drivers, maybe harmless, not sure. 

[ATTACH=CONFIG]265936[/ATTACH]

Anyway, at least I need to get a regular USB mouse, in order to do anything.:confused:

---

### Post by Bucky Ball on 2015-12-04
Radeon relates to your graphics. Should be doable. Once you can get into a 'Try Ubuntu' session with a working keyboard we can have a closer look at the hardware and see what you might/might not need to install in the way of drivers. 

Full credit for your perseverance. :)

PS: I'm presuming it is an Apple/Mac wireless keyboard and mouse. Apple Magic Mouse? Should work 'out of the box' on a full install and the keyboard shouldn't be too hard, either. Apparently, there is a little workaround if you have trouble with the keyboard once installed.

> Press fn-F6 twice to disable numlock. To switch numlock off permanently after log-in go to System -> Preferences -> Keyboard -> Layout -> Layout Options -> Miscellaneous compatibility options -> turn on "Default numeric keypad keys"

From first answer on [this]("http://askubuntu.com/questions/12502/how-do-i-get-the-apple-wireless-keyboard-working-in-10-10") page. Worth a look at the issue the poster is having also so you know when to pull that out. ;)

---

### Post by rdnublx on 2015-12-04
Well, thank you for the kind word. Perseverance is exactly the problem here,  a normal person would stop this exercise sometime ago. It's after 3 am here, and I don't believe that I am still dealing with it.

Anyway, thank you for digging up the information on that page. It should help once I get back to the computer tomorrow. Reading the rest of the comments there where people spend days hunting for this and other details is a bit depressing.

Based on my experience today, with respect to how far the Live DVD boot went and the limited amount of errors I saw, I have a feeling that a full HD based installation would work fine. The keyboard seems to work, maybe partially, not sure. If you recall I swapped my wireless keyboard for a regular standard Mac keyboard from another desktop.

There is something weird about that Try button in the second dialog. Also, the skull and bones freaks me out. Do you know anything about that? I hope it's not one of practical jokes by some genius from Yale.

I guess my main point du jour is that, unless you tell me otherwise, why spend time and effort working out a DVD boot, when this time could be spent on the real thing. The only downside would be an installation of rEFInd boot manager. My understanding is that in the worst case it's fully uninstallable. Also, I think even if it's left there it would not disrupt Mac's operation.

Thanks again

---

### Post by Bucky Ball on 2015-12-04
Just before we go any further ... apologies if you've said this, but please refresh my memory. Is [this the Mac you have]("http://www.everymac.com/systems/apple/imac/specs/imac-core-2-duo-2.4-20-inch-aluminum-early-2008-penryn-specs.html")? If so, does it have 1Gb RAM? If yes, forget Kubuntu. You will not have a great experience with that.

You will get a better result with a lighter flavour, say [Xubuntu]("http://xubuntu.org/") or [Lubuntu]("https://help.ubuntu.com/community/Lubuntu/GetLubuntu"). They are both configurable, particularly Xubuntu. You can tweak that to look like just about any OS! Or similar ...

---

### Post by rdnublx on 2015-12-04
Sure, appreciate the heads up. This one looks like my iMac, however I have 6 GB of RAM so it should not be an issue. I have no problem running Fusion with Windows on it. If Kubuntu has a problem running with a resource like this then I would have bigger problem with it than some driver issues.

---

### Post by Bucky Ball on 2015-12-04
Right. Think you did mention it. No problem with Kubuntu and 6Gb. Stick with it. :)

---

### Post by rdnublx on 2015-12-04
Ok, thank you. But what do you think about my last point in my previous post, namely whether to proceed with a real installation? Please take a look at my reasoning in that post (one above my most recent one). Also the point about rEDInd. I guess it would more convenient if I re-post it here.

> I guess my main point du jour is that, unless you tell me otherwise, why  spend time and effort working out a DVD boot, when this time could be  spent on the real thing. The only downside would be an installation of  rEFInd boot manager. My understanding is that in the worst case it's  fully uninstallable. Also, I think even if it's left there it would not  disrupt Mac's operation.


Anyway, the decision would be mine, however your opinion is valuable for me.

Thanks.

---

### Post by Bucky Ball on 2015-12-04
As for rEFIND, there is no way around that if you are installing a modern Ubuntu, as far as I know, but again, no expert with Macs. It deals with EFI, which I don't think Mac does natively. 

As for going a full install, why not? Getting a live session going is to make sure you can and that things are going to work, at least to a desktop, prior to going 'all the way'. 

But I would definitely do the research and have a solid plan before going forward and also have any valuable data you have on the machine backed up in case things go pear-shaped. :)

PS: Looks like it is quite easy to [uninstall rEFIND]("http://ubuntuforums.org/showthread.php?t=2110389&p=12482382&viewfull=1#post12482382").

---

### Post by rdnublx on 2015-12-05
Guess what, I am posting this from Firefox running on Kubuntu boot from Live DVD. Below is an output of the two commands you had previously asked to run, not sure whether it's needed now.

I can't believe my mental inertia. Being completely focused on making my iMac a dedicated Linux machine, I completely forgot that I had a MBPro with 200 GB of unused HD space and 8 GB or RAM. Clearly, no wireless peripheral issues, as the keyboard and trackpad are right here. Sure enough, booted from the DVD with no problem. I was able to connect to my wireless network, hence this post.

In fact, I am thinking about installing rEFInd and Kubuntu here first, to see whether the sequence works well, then apply to iMac, where there is more uncertainty, At least I would already have my expectations set appropriately. Your comments are of course welcome here.

Thanks.

Here is the output:
```

kubuntu@kubuntu:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5764M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.137 firmware=5764m-v3.38 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:32 memory:d3c00000-d3c0ffff
  *-network
       description: Network controller
       product: BCM43224 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:17 memory:d3b00000-d3b03fff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial:
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=brcmsmac driverversion=3.19.0-25-generic firmware=610.812 ip=192.0.1.14 link=yes multicast=yes wireless=IEEE 802.11abgn
kubuntu@kubuntu:~$ 


```

```

kubuntu@kubuntu:~$ sudo lshw -C video
  *-display                                                                                                                                                                                                
       description: VGA compatible controller                                                                                                                                                              
       product: GT216M [GeForce GT 330M]                                                                                                                                                                   
       vendor: NVIDIA Corporation                                                                                                                                                                          
       physical id: 0                                                                                                                                                                                      
       bus info: pci@0000:01:00.0                                                                                                                                                                          
       version: a2                                                                                                                                                                                         
       width: 64 bits                                                                                                                                                                                      
       clock: 33MHz                                                                                                                                                                                        
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom                                                                                                                              
       configuration: driver=nouveau latency=0                                                                                                                                                             
       resources: irq:30 memory:d2000000-d2ffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:2000(size=128) memory:d3000000-d307ffff                                                         
kubuntu@kubuntu:~$ 



```

---

### Post by Bucky Ball on 2015-12-05
Good news! Getting somewhere. If everything is working, no, the outputs aren't that important, but good to know what's in the box for future reference.

I am a bit confused about this:

```
*-network
       description: Network controller
       product: BCM43224 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:17 memory:d3b00000-d3b03fff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial:
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=brcmsmac driverversion=3.19.0-25-generic firmware=610.812 ip=192.0.1.14 link=yes multicast=yes wireless=IEEE 802.11abgn
```

Do you have two wireless interfaces, one in the box and a wireless USB dongle? Anyhow, you're doing well and nothing wrong with the idea of installing on the MBP first and familiarising yourself with things prior to attempting the iM. Note: A live session generally runs a little slower than a HDD install so expect a slight difference in performance when installed. :)

You could do a bit of investigating with the hardware and the iMac, for instance, 'GeForce GT 330M ubuntu imac' might cough up some ideas about graphics if you have issues with that on the iMac. Good luck on the next phase of your quest. :)

---

### Post by rdnublx on 2015-12-08
Ok, thank you for the information and follow-up. I am pretty much ready now for the installation, just wanted to complete a few upgrades and cleanup steps preparing MBP, also wanted to make sure I had a full (non-incremental) backup to an additional external drive (some people around me call it paranoia).

Anyway, the remaining question is about one place (hopefully a Ubuntu site) with a clear and reliable guide for the entire sequence. The issue is not that I don't know what to do. Actually I do, as I have gleaned and double checked information from several sites, mostly on the Mac site.

I am kind of puzzled why the Ubuntu.org page guiding through this process still refers to a supposedly obsolete boot manager, rather than to rEFInd. Plus, the entire description seems convoluted and iffy. Possibly I am looking at a wrong or outdated page.If you have such a pointer handy please let me know, otherwise please don't waste your time researching. I believe I have enough information to move forward.

Thanks again

---

### Post by Bucky Ball on 2015-12-08
> **rdnublx said:**
> ... also wanted to make sure I had a full (non-incremental) backup to an additional external drive (some people around me call it paranoia).

And I would call you sensible and them crazy as they're the ones who'll appear to be when their hard drives crash and burn! :evil:

We got a slip of paper in our letterbox a few years ago with a heart felt plea for any help with finding a lost mobile phone. It had all the guys photos of his kids from birth til ... age five!!! That's right. Pics that valuable, one copy, on a mobile phone, not backed up in five years! I felt sorry for the family, but ...

Anyway, back to the issue at hand. :) Have you seen [these Mac images]("http://cdimage.ubuntu.com/releases/14.04/release/")? I was looking near the beginning of all this and couldn't find. I have no idea if that is what you should be using. There is this, though:

> Remember that you'll probably need the Mac-specific version to boot on a Mac if you've got a 64-bit system.

From [here]("http://www.rodsbooks.com/ubuntu-efi/index.html"). That link gives instructions for 12.04 LTS, but doubt it will be any, or much, different. And I got the link to that from [the answer here]("http://askubuntu.com/questions/455883/installing-14-04-mac-version-to-macbook-pro-9-1"). 

A bit more food for thought. Good luck. :)

---

### Post by BobUgh on 2015-12-08
> **rdnublx said:**
>    … I am kind of puzzled why the Ubuntu.org page guiding through this process still refers to a supposedly obsolete boot manager, rather than to rEFInd. Plus, the entire description seems convoluted and iffy. Possibly I am looking at a wrong or outdated page…. 

The software is in much better condition than the documentation. Second time in a week that I have seen the word "convoluted" used. If you weren't dual booting, it should be simpler.

AFAIK, sometime recently, I think with version 14, Ubuntu releases covered both "PC" and Mac-intel, no longer are there Mac specific releases. When I read documentation that says otherwise, I assume either that doc is old, or I have to do some further digging.

The things I would add about backups is: have you saved a single disc image of the *full disk* which should include the EFI and restore partitions? (not just the partition that has your data). And/or do you have CD/DVD discs that originally shipped with your Mac? If not, might want to make your own "rescue/restore" CD/DVD or usb stick that has an OSX that you can use to boot the iMac just in case.

With the MacBook Pro it may be easy to remove and dock the hard drive, with the 2008 iMac it is more difficult getting to the hardware. If you brick the hard drive in the iMac, I'm not sure if you can still boot it into target disc mode and reformat it that way. You may have to boot off of DVD or usb.

By the way, I have a 2008 iMac, with only 2 gigs of ram, it is running snow leopard and does fine. But it does very little, essentially a file and print server. It is connected to my LAN but not to the internet. I do have spotlight somewhat disabled on it so the discs can sleep more.

---

### Post by rdnublx on 2015-12-10
> From [here]("http://www.rodsbooks.com/ubuntu-efi/index.html"). That link gives instructions for 12.04 LTS, but doubt it will be any, or much, different. And I got the link to that from [the answer here]("http://askubuntu.com/questions/455883/installing-14-04-mac-version-to-macbook-pro-9-1"). 

A bit more food for thought. Good luck. :smile:[INDENT]                                      Last edited by Bucky Ball; 1 Day Ago at 03:55 AM.                                               
[/INDENT]



Getting back here again, hopefully for the final phase. Thank you for providing the links, I have read all the information. The one from the tech writer is very useful, provides an excellent perspective on the boot manager issues, kind of a different angle at the same issue. However, the subsequent description of the installation has too much ambiguity for my outdated nervous system.

I would like to share with you that I have a philosophically different approach to this kind of issues than both of these guys in the links, and probably a few other people. I would like to state explicitly that it is not a judgment on my part, just a different approach. Believe me, I am fully respectful to my fellow computer travelers. I view a solution to this kind of issue as a well thought out, repeatable process, like a sequence of "black box" steps, strung together as a result of a search inquiry, such as the one you are guiding me through in the last couple of weeks, thank you again!

The challenge usually is to find such a combination of "black boxes", without cutting them open and mucking about with their internals. I don't attempt to step on this "moving belt", until I fully see the entire process, and, with certain degree of certainty, an eventual outcome. To me, Ubuntu.org is one of reputable places where I would expect to find such a guide. Unfortunately, AFAIK, it ain't so.

In our case, I didn't mind experimenting with Live DVD, as there was (almost) no downside risk, just the time spent. However, once we start dealing with partition changes, replacement of a boot manager, and similar trivial operations, I would like to do everything possible to increase my odds to a significant degree. Hence my inquiry about such a clear guide from a reputable site. I found one earlier (please see [here]("http://www.howtogeek.com/187410/how-to-install-and-dual-boot-linux-on-a-mac/")), but was not sure. It's supposedly a known site, and the guidance looks logical, quite specific, and certain. In other words, based on my experience and (limited) knowledge of the subject, it makes sense to me. I was hoping for an independent verification of the rEFInd information from another known site, but I don't see it.

Before I proceed, I would like to ask you another question though, **Kubuntu vs. Ubuntu**. Clearly, Ubuntu is more popular and has bigger support, as evidenced by the site and forums. The reason I picked Kubuntu, sometime around 2012, may be laughable to some people, but it was KDE. At that time, if I recall correctly, Ubuntu replaced it with another GUI, which created some controversy, and it was going back and forth, adding the option for people to go back, and being unclear where it all would go. I did not want to follow that, figure it all out, and I liked KDE from my previous experience with Linux (Red Hat ?). I installed Kubuntu on my Fusion, liked it and just stayed with it. Yesterday, I was starting to think (it happens to me from time to time), that the GUI issue must have been resolved by now, and Ubuntu is a great system, with bigger user base and support, as I said above. Why not install Ubuntu, given that I am in transition anyway? **What do you say to that?**

---

### Post by Bucky Ball on 2015-12-10
The decision is entirely yours. Can't really help with it. The desktop environment Ubuntu switched to was Unity. It is still using it. Kubuntu still uses KDE. That's about the size of it. :)

Desktop environments are a personal thing. Whatever suits the way you work best and your tastes I suppose. I use xfce4 myself on a minimal install with no bells and whistles. That's all I need and its fast.

Why not just try both from a DVD and see which you like best? Give Xubuntu, Lubuntu and Mate a go while you're at it. Or Ubuntu Gnome, but that is not officially supported here. If you didn't like the change to Unity back then you are not going to like Ubuntu now. Having said that, it was three years ago. Tastes change and technology does with it. :)

(PS: Unity was a step toward convergence: a DE that could be used on any device. Same user experience regardless of device. :))

---

### Post by rdnublx on 2015-12-10
> **BobUgh said:**
> 
AFAIK, sometime recently, I think with version 14, Ubuntu releases covered both "PC" and Mac-intel, no longer are there Mac specific releases. When I read documentation that says otherwise, I assume either that doc is old, or I have to do some further digging.

Thank you for the contribution. That's interesting. I didn't think that releases may be PC and Mac specific. I thought that a Ubuntu image would be abstracted from the vendor by the boot manager layer. Meaning, that once rEFInd is installed it would manage the vendor selection. The built-in boot loader is probably vendor agnostic, it is not aware whether it's PC or Mac by the time it loads the Linux kernel. Of course, there is an issue of supporting of variety of cards and devices, but that's true from PC to PC, not only from PC to Mac. I have no idea how it's done, probably by dynamically loaded device drivers. If this was not the case, I think, we would have to have numerous images for a variety of corresponding hardware configurations. As far as I see, there is only one image for "all" Intel based machines.

Of course, distinct images have to be built for respective data sizes, but that seems orthogonal. My understanding is that when selecting an image all I should care is whether it's i386 (32-bit) or amd64 (aka x86-64 ?) (64-bit) image.

If my understanding is incorrect, and indeed there are Mac and PC variants of a given image, I would appreciate a clarification.

> **BobUgh said:**
> The things I would add about backups is: have you saved a single disc image of the *full disk* which should include the EFI and restore partitions? (not just the partition that has your data). And/or do you have CD/DVD discs that originally shipped with your Mac? If not, might want to make your own "rescue/restore" CD/DVD or usb stick that has an OSX that you can use to boot the iMac just in case.


Ok, this one concerns me as well. In fact, I would not want to proceed, before clarifying it, otherwise my "full" backup would be useless. To my knowledge (again, I am not an expert), formatting and partitioning is a logical layer on top of the physical media  layer. Are you suggesting that a Time Machine backup contains partition and firmware information, and that when it's restored, it would partition the destination disk and update the firmware?

I would not use the original disks anyway, because I have upgraded several times and in fact a  few days ago again to the latest 10.11. However, your point about a rescue CD/DVD needs to be considered. It probably would preserve my current EFI System Partition and who knows what else, and would allow me to fully recover, given that I would be installing a different boot manager, rEFInd. Please feel free to comment or provide an additional information if you find anything.

Again, to the point I made in the earlier post, it's all walking in the dark, I don't know all the details and wish it was described coherently somewhere. I don't understand why Apple, in all their wisdom developing BootCamp for a dual boot for Windows, could not do the same for the Linux community.

---

### Post by rdnublx on 2015-12-10
> **Bucky Ball said:**
> The decision is entirely yours. Can't really help with it. The desktop environment Ubuntu switched to was Unity. It is still using it. Kubuntu still uses KDE. That's about the size of it. :) 

Well, that's all I needed to know, thanks for the clear answer. Given that, I am going to stick to Kubuntu, at least for now. I may follow your suggestion and try other versions, just to see how they look, if everything goes well here. Thank you.

---

### Post by rdnublx on 2015-12-10
> **Bucky Ball said:**
> 
Anyway, back to the issue at hand. :) Have you seen [these Mac images]("http://cdimage.ubuntu.com/releases/14.04/release/")? I was looking near the beginning of all this and couldn't find. I have no idea if that is what you should be using. There is this, though:


It looks like in all my wisdom, I have missed the fact that you actually did point me to Mac specific images, although these are Ubuntu, not Kubuntu. Maybe that was the reason for my ignorance, because I opened the Kubuntu download page and did not see any Mac specific downloads. I am going to check again, but if this is the fact then it probably leaves me no choice but to install Ubuntu.

---

### Post by Bucky Ball on 2015-12-10
Not so fast:

> Kubuntu is an free, complete, and open-source alternative to Windows and Mac OS X which contains everything you need to work, play or share.

From the Kubuntu page. This would suggest it will install just fine on a Mac (as OSX can't be installed anywhere but a Mac). Just because there are no Mac specific ISOs, no biggie. Some spins don't have them and not even sure if those images are necessary for installing Ubuntu on your machine. 

My advice would be to simply get it [from here]("http://www.kubuntu.com/getkubuntu/"), bit torrent is most reliable if you're au fait with torrenting (checks the file on the way down), and go for 14.04 LTS 64bit (presuming you have a 64bit processor which I believe the majority of Macs are).

* I also spotted [this]("http://tech-devnet.blogspot.com.au/2012/05/running-ubuntu-1204-on-mac.html?_escaped_fragment_#!") on my travels. Might give more clues re. installation. Ignore the fact it is for Ubuntu. The Kubuntu installer would be pretty much the same except for perhaps some of the graphics you see on the way. The pre-install prep. etc. would be identical. All the spins run on the same Ubuntu base kernel which is tarted up from there. Same installer. (For instance, you could do a minimal install, which is just the base kernel, then install 'kubuntu-desktop' and you would have Kubuntu.)

* [And another]("http://lifehacker.com/5934942/how-to-dual-boot-linux-on-your-mac-and-take-back-your-powerhouse-apple-hardware") which has plenty of detail and you may have already [seen this]("https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation"). :)

---

### Post by BobUgh on 2015-12-10
> **rdnublx said:**
> Thank you for the contribution. That's interesting. I didn't think that releases may be PC and Mac specific. ...

If my understanding is incorrect, and indeed there are Mac and PC variants of a given image, I would appreciate a clarification.

It appears to me that MAYBE there ARE different releases. I have started a new thread for that.
[http://ubuntuforums.org/showthread.php?t=2305936&p=13404808#post13404808](http://ubuntuforums.org/showthread.php?t=2305936&p=13404808#post13404808)

> **rdnublx said:**
>  Ok, this one concerns me as well. In fact, I would not want to proceed, before clarifying it, otherwise my "full" backup would be useless. To my knowledge (again, I am not an expert), formatting and partitioning is a logical layer on top of the physical media  layer. Are you suggesting that a Time Machine backup contains partition and firmware information, and that when it's restored, it would partition the destination disk and update the firmware?

No, Time Machine would not contain partition information. To back up the partition table, boot partition, boot loader and all the rest, you need to do something such as clone the disk, most primitive method is the terminal command "dd" and requires a second disk that is the same size or larger than the source disk, and the second disk will be completely written over. There are other programs that are a bit easier to use, such as clonezilla. There are good and bad ways to use dd to skip over bad sectors, and one could even use ddrescue even on a good disc. A better alternative is to create disk images. With OSX disk utility, you can create a compressed disk image of the disk (not a single partition) and save that just like any other file to an external drive or even a network drive. But if you use OSX disk utility to create a disk image, then if you bric your hard drive, you then either (1) need to be able to boot your iMac into OSX off the optical or usb drive (caveat: maybe an alternate OS but I don't know if alternate OSs can restore a disk image created with OSX disc utility) or (2) remove the internal hard drive and put it in a dock and connect it to a system that is running OSX. If the latest versions of disk utilities under linux can create similar disk images I do not know.

> **rdnublx said:**
>  I would not use the original disks anyway, because I have upgraded several times and in fact a  few days ago again to the latest 10.11. However, your point about a rescue CD/DVD needs to be considered. It probably would preserve my current EFI System Partition and who knows what else, and would allow me to fully recover, given that I would be installing a different boot manager, rEFInd. Please feel free to comment or provide an additional information if you find anything. 

Apple's mode of recovery, for your 2008 iMac, if the hard drive crashes and you replace it with a blank, then after putting it back together you would use either the original install optical discs (Tiger?) that were shipped with your machine, or the Snow Leopard opticals (that Apple still sells) and install OSX on the hard drive, then either or a combo of (1) run updates and upgrades and/or restore from Time Machine. (You can boot off usb if you do it right ahead of time and make the restore process easier. Just depends how much work you want to do for the 1% chance you will need to restore.) Worse case if you get your system where it can't boot off the hard drive, you would do something like this but leaving the internal disk in place - again, worse case, and that gets you back to where you are now, if you have been using Time Machine or have some other back ups. If you have made a disk clone or image, then you should be able to boot off the (apple) installation disks and instead of installing, go to terminal or disk utility and restore your image.

Removing and installing the internal hard drives in iMacs is not trivial, so the first Mac system that I will install Ubuntu on will be a 2010 MacBook Pro, which is easy to get to the hard drive.

> **rdnublx said:**
>   Again, to the point I made in the earlier post, it's all walking in the dark, I don't know all the details and wish it was described coherently somewhere. I don't understand why Apple, in all their wisdom developing BootCamp for a dual boot for Windows, could not do the same for the Linux community.

The major problem is that the actual way of doing things, hardware and software, changes faster than the documentation does.

I have read on the apple discussion boards lots of questions and problems about boot camp and linux booting, and I get disappointed. Then the details of installing Ubuntu on Apple using *efi* and grub* seems unnecessarily complex. Supposedly if you don't want to dual boot, you can just install ubuntu and not even worry about EFI and grub and all that? I would be happy if I could simply create a linux partition, create a linux swap partition, install ubuntu. And it would always boot into OSX unless I held Option or C down while booting and then I could select what to boot. I don't need the default to be to ask. If that is possible I do not know and I wish I understood this well enough to make a real contribution.

Now that I've been thinking about it, if you have updated to the latest OSX 10.11, I think you can go back into the app store or whatever it is called (not the normal software update), and by holding some meta key down, ask to re-install the latest system again, and when it asks where to install, you can specify a USB (thumb) drive - if you have formatted it properly, and when it finishes, you should be able to boot off of it. I'm writing this last paragraph from memory, if you are interested in this look it up on apple.com and ask me further here. I might be confusing this with creating an "install USB drive" but that gets you almost to the same point.

---

### Post by BobUgh on 2015-12-10
Here, I hope, is a more concise answer about backups, and a small correction: you don't really need a clone of your drive.

My assumptions is your iMac is single boot OSX El Capitan, and you want it to dual boot: Ubuntu or OSX.

If you have backups of your data that you have confidence in, such as Time Machine, and either
1) a usb that you can boot from: into full OSX, or OSX rescue/utilities or OSX install.
or
2) a second Mac computer running OS X El Capitan, Yosemite, or Mavericks (if so, apparently you can create (1) above later if need be. A second working computer allows one to procrastinate *some* tasks until only necessary)

With backups and ((1) or (2) above) and it is single boot, then you are ok to mess with your hard drive. You don't need to have a clone or disc image of your hard drive first. It would simplify things if you need to restore from it, but it can be a bit too complicated to create - compared to the small chance you will need it. If your machine was already double boot, then saving a disc image could be more worth it.

If your iMac is your only recent OSX system, or you get to the point your iMac won't boot off your hard drive, then you need to have a way to boot your iMac from usb, either boot into OSX or boot so you can re-install OSX and restore from backups, so look at these links, they can say it much better than I can:

#Create a bootable installer for OS X
[https://support.apple.com/en-us/HT201372](https://support.apple.com/en-us/HT201372)

[http://macs.about.com/od/OSXElCapitan/ss/Create-a-Bootable-OS-X-El-Capitan-Installer-on-a-USB-Flash-Drive.htm](http://macs.about.com/od/OSXElCapitan/ss/Create-a-Bootable-OS-X-El-Capitan-Installer-on-a-USB-Flash-Drive.htm)

[http://macs.about.com/od/usingyourmac/qt/How-To-Re-Download-Apps-From-The-Mac-App-Store.htm](http://macs.about.com/od/usingyourmac/qt/How-To-Re-Download-Apps-From-The-Mac-App-Store.htm)

[http://macs.about.com/od/usingyourmac/ss/Create-Your-Own-Os-X-Lion-Recovery-Hd-On-Any-Drive.htm](http://macs.about.com/od/usingyourmac/ss/Create-Your-Own-Os-X-Lion-Recovery-Hd-On-Any-Drive.htm)

[http://macs.about.com/od/Troubleshooting/fl/Starting-Up-From-the-OS-X-Recovery-HD-Volume.htm](http://macs.about.com/od/Troubleshooting/fl/Starting-Up-From-the-OS-X-Recovery-HD-Volume.htm)

What is kind of interesting is that OSX terminal has a command "createinstallmedia" but apparently only in the 3 most recent versions of OSX.
If you want some reassurance, you can always create a bootable usb as above and practice booting from it a few times until you feel comfortable, then proceed installing [k]ubuntu.

---

