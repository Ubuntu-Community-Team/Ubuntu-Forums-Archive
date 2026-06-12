---
title: "Will Jailbreaking My iPod 4g (4.2) Allow Me To Use My iPod in Ubuntu properly?"
date: 2011-02-19
forum: Apple Hardware Users
---

### Post by Blake. on 2011-02-19
Hola!

Right now im having some horrifying experiences with my iPod 4g (iOS 4.2) and ubuntu maverick (technically Linux Mint 10, but we all know this is maverick-based). THE THING JUST WONT WORK!!!!!!!!

When i plug it in, it shows me a dialogue that basically says "this is an audio device, what would you like to do?" and lists several of my media management apps. I tried all of them, and the only one that gets somewhat towards accomplishing absolutely nothing is Rhythmbox , which properly mounts the iPod, but upon doing anything with said iPod, it immediately unmounts.  So my question is this: will jailbreaking it help me at least add my music natively through linux, no problemo? No virtual windows crap, just my beloved ubuntu laptop.

And if it will, i dont know the first clue about doing a jailbreak. I have access to windows machines, so if the jailbreaking process requires one, no problem there. Could you also guide me/point me to a guide that will help me with the process?

If for some reason you find my question incomplete/confusing/lacking details, PLEASE dont just skip over to the next forum question, ask me for whatever details you need, ill be glad to give them. I JUST WANT MY STUPID iPOD TO WORK WITHOUT NEEDING WINDOWS!!!!!!

Thanks in advance!

---

### Post by Hatsune Miku on 2011-02-19
> **Blake. said:**
> Hola!

Right now im having some horrifying experiences with my iPod 4g (iOS 4.2) and ubuntu maverick (technically Linux Mint 10, but we all know this is maverick-based). THE THING JUST WONT WORK!!!!!!!!

When i plug it in, it shows me a dialogue that basically says "this is an audio device, what would you like to do?" and lists several of my media management apps. I tried all of them, and the only one that gets somewhat towards accomplishing absolutely nothing is Rhythmbox , which properly mounts the iPod, but upon doing anything with said iPod, it immediately unmounts.  So my question is this: will jailbreaking it help me at least add my music natively through linux, no problemo? No virtual windows crap, just my beloved ubuntu laptop.

And if it will, i dont know the first clue about doing a jailbreak. I have access to windows machines, so if the jailbreaking process requires one, no problem there. Could you also guide me/point me to a guide that will help me with the process?

If for some reason you find my question incomplete/confusing/lacking details, PLEASE dont just skip over to the next forum question, ask me for whatever details you need, ill be glad to give them. I JUST WANT MY STUPID iPOD TO WORK WITHOUT NEEDING WINDOWS!!!!!!

Thanks in advance!

Even if you get it to work you wont be able to sync anything. Only music you can sync, just used a Windows Virtual machine with iTunes. Windows its in its own world, and you dnt need to leave GNU/Linux ^-^

---

### Post by Blake. on 2011-02-19
ok, thanks a bunch!!!! :D

---

### Post by dazndom on 2011-03-04
Have you got ipod applications installed??

if not goto applications / software center + type ipod in search bar
install both gtkpod and hippo

i dont use rythymboc or banshee to sync ipods

i simply open folders and i can add/remove music photos videos

hope that helps

---

### Post by ddell on 2011-03-05
I'd recommend jailbreaking it (for a number of other reasons and increased functionality published online elsewhere) regardless.  Once you do, you can install on the phone a file manager like ifile, and then with that move things around and navigate through your own device as much as you like.  

I haven't found a nice application alternative like ifunbox.exe for Ubuntu, but the last few versions of Ubuntu (now running 10.10) have natively supported for me the IpodTouch, so I've just been using a workaround wherein transfer videos (converted to ipod/iphone format using handbrake) or jailbreak app install files to the DCIM folder of the ipod, and then using ifile to move them whereever wanted.  Videos are directly opened through ifile and play through either the native video player, or vlc or whatever you like.

It's not a perfect solution, and it doesn't work for putting music in the library (which for me has always worked fine with Rhythmbox - just make sure the device is plugged in first before opening rhythmbox), but it works.

---

### Post by arabis on 2011-03-05
You can install this PPA:

[https://launchpad.net/~pmcenery/+archive/ppa]("https://launchpad.net/~pmcenery/+archive/ppa")

And update your system.

After that, you should be able to use your ipod

---

### Post by Spyderkid on 2011-03-05
not jailbreaking needed just install gtkpod from the software centre for transfering music, films. however if you want to sync apps your in a bit of a pickle without windows unfortunatly

---

### Post by MacintoshLover on 2011-03-06
Just search "Wine" in the searchbox of Ubuntu Software Central. Then download and install it and iTunes. Boom! App management, music management, etc.

---

### Post by JaxPenguin on 2011-07-09
> **MacintoshLover said:**
> Just search "Wine" in the searchbox of Ubuntu Software Central. Then download and install it and iTunes. Boom! App management, music management, etc.

While I was able to install iTunes under WINE it wouldn't work properly. I could click on the library but nothing showed up on the right window. I also couldn't exit (menu grayed out). I had to kill the process.

None of the apps like Rhythmbox, Amarok, Banshee, etc show the iPod when I plug it in. I have yet to find a usable solution to using my iPod Touch 4g under Linux. :(

---

### Post by handy on 2011-07-09
Is there a way to sync contacts on the iPod Touch, via Linux?

---

### Post by JaxPenguin on 2011-07-10
I don't use my iPod for contacts so I've never tried it. And I don't use a desktop app. All of my contacts are stored with my GMail account which syncs across devices.

However, I did finally get everything syncing using VirtualBox and a XP VM. I thought it was giving me trouble passing the USB port from Ubuntu to the VM but it finally started working. So it's not technically syncing under Ubuntu (so much for "out of the box" support) but at least it's working on my desktop now.

---

### Post by rosencrantz on 2011-07-10
Just to clear up a few points:
-The libgpod approach works for the iPod classic, nano and shuffle (I think) and the touch up to 3G. No success yet with touch or iPhone 4G
-From my personal experience (iPod classic 6G and touch 4G), you can export contacts and calendar by copying them directly on to an iPod classic, for the touch I sync both my laptop and the iPod to my Google account. 
-There is limited access to the touch 4G file system with ifuse, but you can't use it yet to upload music (some encryption issue, I think). When I tried to change something on my touch with gktpod, it only scrambled the album covers.
-Even if you get iTunes to run on Wine, it's not going to sync as Wine can't deal with USB connections yet. iTunes on Windows on Virtual Box can, but it's usually very slow.

Neither of the above methods require jailbreaking.

There seems to be some jailbreaking approach:
[http://marcansoft.com/blog/iphonelinux/usbmuxd/](http://marcansoft.com/blog/iphonelinux/usbmuxd/)
I didn't try it since I lost my jailbreak with a device reset. On the other hand, there are rumours about future iOS versions featuring WiFi sync, which might get at least the Wine solution running.

---

### Post by JaxPenguin on 2011-07-11
> **rosencrantz said:**
> Just to clear up a few points:
-The libgpod approach works for the iPod classic, nano and shuffle (I think) and the touch up to 3G. No success yet with touch or iPhone 4G

I read that 10.04 supported the 4G but then it was broken in 10.10.

> 
Lucid natively supports both iPhone and iPod Touch 1G, 2G, 3G, 3GS and 4G models

Take from [here](https://help.ubuntu.com/community/PortableDevices/iPhone).

> 
-Even if you get iTunes to run on Wine, it's not going to sync as Wine can't deal with USB connections yet. iTunes on Windows on Virtual Box can, but it's usually very slow.

It seems to be running ok for me. The only thing I found slow was adding album art. My Windows 7 laptop was so fast I never saw any dialogs but in the VM I had to wait while it updated the tags. Beyond that syncing seemed normal.

---

