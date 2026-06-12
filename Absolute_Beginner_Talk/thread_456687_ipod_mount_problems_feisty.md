---
title: "ipod mount problems feisty"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by frankeleone on 2007-05-27
Hello,
       I am running Kubuntu Feisty. I have a 4G ipod. I had no problems until upgrading to Feisty from Edgy. Now, I cannot mount my Ipod. When I plug it in, nothing happens. I get the do not disconnect warning on my ipod, but no icon indicating that the device is mounted. However, if I leave the ipod connected and restart the computer, the ipod mounts reliably; the icon is on my desktop. It says it is on /media/FRANK'S IPO.  It says the device node is /dev/sdg2. I can read it, execute a program on it (Floola). However, if I right click and "safely remove" it, it will not mount again if I unplug it and plug it back in. Under properties, I have the box checked under mounting that says mount automatically. Any help would be greatly appreciated. Thanks, Frank

---

### Post by kordite on 2007-06-02
I had a very similar problem. I had a 30Gig iPod that worked fine with 6. I upgraded and then lost it. It does not appear on the desktop. It does not appear in /media. It doesn't show up in dmsg. When I reboot, it shows the "Do not disconnect" message while the PC is starting but once the OS starts booting, it goes back to only getting a charge from the USB port. 

A number of other "not mounting iPod" issues have been listed on the forums have been discussed but all the solutions from those begin with the assumption that when you plug in the iPod, it shows up somewhere.

Wherever that somewhere is, I can't find it.

---

### Post by renohal29 on 2007-06-22
I have a problem similar to both of yours. After rebooting, I plug in the ipod and it will show up. After transferring about the 6th song from Rythmbox, Ubuntu will stop communicating with the ipod. I can't open the ipod icon on the desktop and can't eject it. It worked fine in Edgy.

---

### Post by gordboy on 2007-06-27
I have a similar problem, i can plug in my 5th gen ipod and it will be detected, but the connection drops midway through file transfers. The ipod icon disappears from my desktop, but the ipod still shows the "do not disconnect" message. I can unplug and plug it back in without rebooting and it will reappear, but the connection will drop again if i start transferring files. 

It works fine when i boot into XP, but i hate doing that :)

---

### Post by Inxsible on 2007-06-27
Wow, quite a few of you having problems with iPods. Lucky I dont have any.
 
I use RhythmBox to connect to my iPod. Transfer files merrily. 
 
Have you tried using pmount to mount your iPods. pmount will mount it under /media and automount every time you connect it.

---

### Post by Mano_vardas_Tomas on 2007-07-02
Hi,

so, does anybody know solution? When I first installed Ubuntu 7.04, iPod was detected and mounted. After I reinstalled Ubuntu because of Internet problems, it doesn't detect my iPod. USB slots are OK - checked. Theres is no disconnection warning, just charging or charged icons on iPod's display.

Please, help me :)

---

### Post by fugative on 2007-07-04
yeah, i've got the same problem except my devices (ipod mini, se k750) don't even charge. 
 usb stick is fine, voip phone connects ok but no ipod or phone, which btw connects fine with bluetooth.
so far noone has the answer.
please somebody help us!!!!!

Dave

---

### Post by fugative on 2007-07-04
OK, so i've been doing my usual of hitting stuff till it either works or it's broke for good and to quote Dora (if you've got kids you'll understand) WE DID IT!!!!!!!!!!!!
so try this....
reboot ipod (mine was still connected to the usb, don't know if that helped) to reboot ipod lock: on, off, on off then push menu and centre together.
as for the phone i just turned it off and on again.

hope this helped someone

Dave

---

### Post by otakonx on 2007-07-04
I'm having the same exact problem with my 5th gen (black) 60gb iPod.  This is the first time I've had a problem that no one on the groups can offer insight to. It seems like a lot of people are having this issue so I hope the Ubuntu team is working on a fix.

---

### Post by HermanAB on 2007-07-04
See this guide: [http://aeronetworks.ca/ipod-howto.html](http://aeronetworks.ca/ipod-howto.html)

It should prove to be helpful.

Cheers,

Herman

---

