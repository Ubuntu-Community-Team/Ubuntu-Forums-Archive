---
title: "iPod Touch + USB + Ubuntu 8.04 = HOW?"
date: 2008-06-25
forum: Apple Hardware Users
---

### Post by taffypride on 2008-06-25
How exactly do I get Ubuntu 8.04 to recognise the iPod Touch as exactly what it is?

Ubuntu seems to think the damn thing is a camera.....

Amarok seems to have the capability to replace iTunes software - rather appears to be the iTunes replacement for Linux - but I can't get the thing detected.

HELP!!!!

---

### Post by Technobabel on 2008-06-25
Hi,

you may want to check this site out:
[http://gtkpod.wikispaces.com/](http://gtkpod.wikispaces.com/)

or have a look here:
[http://amarok.kde.org/wiki/Media_Device:IPod](http://amarok.kde.org/wiki/Media_Device:IPod)

Hopefully that was useful!

CU
Babel

---

### Post by taffypride on 2008-06-25
Cool thank you.

Strange it comes up as a camera.

I mean, christ, my Sony Ericsson W950 comes up correctly as a Media Device so why can't the iPod??

---

### Post by taffypride on 2008-06-25
all well and good but they involve using wifi.

I don't have wifi.

How do I do it via **usb**?

---

### Post by rakan21 on 2008-06-26
Ah ****. OK here's the problem with the iPod touch. Its not ******* compatible with Linux Ubuntu @ the moment, but don't panic. Just use gtkPod that should work. but one problem with that

1.There's also preliminary support for the iPhone and the iPod Touch but they must be jailbroken to work. 

I want to get the 3G iPhone and I'm going to jailbreak it for Free apps of course. Anyway try gtkPod. I don't know about any other players. I've tried them all with my friends iPod touch's and iPhone's. Nothing works other than gtkPod and Wifi with Amarok (which is ******* kick ***). 

Oh and I think one program is going to have support for iPod Touch and iPhone to work on Linux and thats Songbird. Its a iTunes clone, and you can even add iTunes skin to it. Check it out I know you'll like it.

Rabayah, Rakan

P.S. another bad thing about all these players is that must of them are Music Players and not Media Players. So there's like no way you can get Video's on your iPod touch. 

But this is a stupid alternative. If you have wine installed (sudo apt-get wine) then you can try Media Monkey for Windows. They say they have iPod touch and iPhone support. 

tell me how it goes [email]rakan21@gmail.com[/email]

---

### Post by taffypride on 2008-06-26
got gtkpod installed but I can't see the ipod.

Still only shows up as camera (go figure).

---

### Post by rakan21 on 2008-06-26
Is your iPod Touch Jailbroken?
It has to be if you want it to work.

---

### Post by rakan21 on 2008-06-26
OK I think I have found a really good solution for all Apple iPod Touch Linux users.

Its called YamiPod. It looks like it has iPod Touch support. Check it out. I don't think you have to Jailbreak your iPod now with this program. Looks really good. Easy-To-Use.

Tell me how it goes by Emailing me @ [email]rakan21@gmail.com[/email]

---

### Post by rakan21 on 2008-06-26
Nevermind about the YamiPod I just read there whole entire page and found this 
"# All iPod generations **(except iPhone and iPod touch)** were reported to be working under:   Mac OS 10.3 or newer
# Windows 98SE or newer
# Any linux distribution with GTK 2.0"
Which sucks ***.

SO make sure your iPod is Jailbroken. I know this really sucks. I wish they had better support. If everything works out if you jailbreak your iPod then email me. 

Thanks
Rabyaha, Rakan
[email]Rakan21@gmail.com[/email]

---

### Post by taffypride on 2008-06-26
Ipod is definitely jailbroken.

Got version 1.1.4

I assume I'm using GTK2.0 on my system - how can I check?

Also got Yamipod installed.

sorry for sounding and being a complete Ubuntu Noob :(

---

### Post by Brandon Jenko on 2008-06-26
HI my name is Brandon Jenko, I appreciate the help ive seen on this website and the detail put forth i encourage all computer programmers to keep up the discussions 


Thank you
Brandon Jenko

---

### Post by IamReck on 2008-06-27
To the best of my knowledge, the only option at the moment to use your iPod Touch and Ubuntu is to Jailbreak it, and using Open SSH Wirelessly have it sync and mount with Amarok.

Takes a little Technical know how to do this, but here are the instructions.

[https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)

---

### Post by joezamboni on 2008-06-27
sudo killall apple fans

---

### Post by MaddMatt on 2008-07-04
Firstly, Songbird seems interesting, but doesn't remedy the iPod touch problem. Also, in addition to, [that previous statement] Amarok is the best music player on the planet. I mean, I have converted numerous people to Linux just on letting them play with the flexibility and awesomeness of Amarok, and I'm a Gnome user... 

Anyway, on to the Meat and Potatoes:
[SIZE="4"]
**Does anyone ACTUALLY know why the new iPod touch file system can't be read under Linux?**[/SIZE]

   I mean, F-Spot *can **actually*** detect it. Right now I'm looking at the "camera import" dialog that pops up, so I don't suppose that Apple has some secret USB command that is sent via iTunes to unlock  syncing mode (which would be a weak form of protection anyway). 

   Furthermore, the way that it works with SSH suggests that it is running on some sort of UNIX-esque filesystem, which I would be willing to bet some beans is a HFS+ derivative (the OS X filesystem (which is unfortunately not writable yet under Hardy)). 

**   In answer to the question of this post:** It doesn't matter what you use, gtkpod, or this yippiepod or whatever, or Amarok for that matter, you still need to jailbreak it (which requires a MAC or M$ computer) **AND** you need to set up Ubuntu to connect to it through SSH, which is not hard to do with the current number of competent guides available. 

   However, I personally have nuked my iPod by playing around too much with the SSH hashes, etc, so tread with caution. 
  Screw the critics: The thing's awesome - people doubt it, but right now I'm reading books on it that I downloaded from [http://manybooks.net/]("http://manybooks.net/"). So now this device is sleek, easy to use, AND is expandable to do whatever you want. 

 The main point is, and I know this rambles:
Connecting to your iPod via WIFI is **COOL**. No doubt! Guys in the Apple store were geeking when I told them what I could do with my iPod and Ubuntu. (Which I run on my MacBook Pro, and it's sick.) **_The thing is, WIFI syncing is WAY slower than USB, and for those of us with large audio collections, or changing the movies on the iPod constantly, the WIFI really doesn't cut it._** 

   Especially because it doesn't work AD-HOC, so you need to have a router as well. You're going to bring your own router on your trans-Atlantic plane flight when you want to swap out half of your collection? I think not. 

   So does ANYBODY know who is trying to work out a solution to the USB thing? I'd like to know/contribute, and I think others would too, no?
Thanks, 
-M

---

### Post by DarthPooky on 2008-07-07
i remember having read somewhere that the ipod touch and th iphone use some sort of encryption so iit doesn't work. i also read soemwhere that if you and your computer are connected to the same network the ipod or iphone via wifi you can download the lates version of gtkpod build it and sync over the air **how ever do not use the gtkpod from the repos it will corrupt your ipod's music datatbase.** i have not tried this

---

### Post by obzidian on 2009-02-12
Anyone know of an update to this?

My ipod touch is still being detected as a camera and none of the software mentioned in this thread recognizes it either.

I've tried gtkpod as well with no luck.

Also, I'm using 8.10.

:(

---

### Post by 3rdtreenz on 2009-02-24
There are instructions on the amarok wiki ([)here]("http://amarok.kde.org/wiki/Media_Device:IPod#iPod_Touch_and_iPhone")) for getting the ipod touch to work through usb, even using the latest firmware. I tried it with a jailbroken original ipod touch with firmware 2.2.1 and amarok 1.4.9.1. All that was required was to compile ifuse and libiphone, and change the DBVersion of my ipod with a text editor. Also the ipod needs to be restarted/refreshed to see the song updates.

---

### Post by hooless on 2009-05-18
. 

Anyway, on to the Meat and Potatoes:
[SIZE="4"]
**Does anyone ACTUALLY know why the new iPod touch file system can't be read under Linux?**[/SIZE]

  um I do not have the exact answer, but im pretty sure it has to do with the same as an itouch and 360 not connecting. I heard somewhere that the iPhone and iTouch have a different data transfer format than the other iPod gens. so i suppose that they don't work due to this. but don't ask me to fix it- i wouldn't know where to start :p

---

### Post by earrame on 2009-08-30
Shame. If only Apple used something similar to Linux for their OS platform. Oh wait...

Fortunately we have an iMac in the house. I just do my iPod Touch stuff on there. Then I run the back up to CD and update my music library on my Ubuntu notebook.

I still would rather just have iTunes on Ubuntu without having to jump through a bunch of hoops to get it running in some fashion.

Of course, in my black and white view of the world the iPod doesn't show up as a storage device for no reason other than the developers are idiots. :D

---

### Post by 22by7 on 2009-10-26
I wonder if the program iFuse works for any of you. I read this article which says iFuse can be installed on Ubuntu to get your iPod Touch/iPhone detected as a hard disk. It works without having to jailbreak. Apparently it is also said to work without SSH too. Give it a try.

[http://www.ubuntugeek.com/how-to-connect-iphoneipod-touch-using-usbin-karmicjauntyintrepidhardy.html](http://www.ubuntugeek.com/how-to-connect-iphoneipod-touch-using-usbin-karmicjauntyintrepidhardy.html)

I gave it a shot on my Karmic Beta but apparently something called devkits-disks keeps on crashing, which I presume to be related to iFuse, so it ain't working for me right now but anyone with a stable Ubuntu can give it a try and let me know if that works.

Cheers!
22by7

---

### Post by CanadianBac0n77 on 2009-12-12
If your device is jailbroken you should try out this:

[http://lifehacker.com/388785/sync-your-iphone-wirelessly-in-linux](http://lifehacker.com/388785/sync-your-iphone-wirelessly-in-linux)

---

### Post by luigi.viggiano on 2009-12-15
I do not use the USB to access iPod files. But this is what I have done: [http://en.newinstance.it/2009/12/03/ipod-touch-with-linux/](http://en.newinstance.it/2009/12/03/ipod-touch-with-linux/)

---

