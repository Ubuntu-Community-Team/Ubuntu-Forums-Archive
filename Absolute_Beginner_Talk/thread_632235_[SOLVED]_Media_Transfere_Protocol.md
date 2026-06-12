---
title: "[SOLVED] Media Transfere Protocol"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by discoade on 2007-12-05
ok guys one last crack at this please. if you would

I have a Samsung YP K3 mp3 player that uses MTP (media transfer protocol) to load data etc.
When i plug it in rhythmbox launches but the k3 dosnt show up as a device or drive so i cant access it!

Im sure at some point i saw a tag in rhythmbox that said add support for mtp devices but i cant find it now (i could be wrong of course).

any ideas anyone!?

---

### Post by Hospadar on 2007-12-05
Is this the case after you close rhythmbox?  only one program can get a lock on the MTP device at one time.  Also do you use rhythmbox?  I got annoyed by it popping up and I always use amarok anyways so I just removed rhythmbox "sudo apt-get remove rhythmbox"

Alternatively, it might be a k3b issue, are you sure you have k3b configured correctly?  try using your device with some other mtp program, gnomad2, amarok, banshee

---

### Post by discoade on 2007-12-05
Hi ive installed amarok

when i click connect it asked for a pre connect command and a post disconnect command!

what should i enter into the fields?

---

### Post by g2g591 on 2007-12-05
you shouldnt need to put in anything afaik, just configure it in the main config dialog, under media devices

---

### Post by Tomosaur on 2007-12-05
> **discoade said:**
> Hi ive installed amarok

when i click connect it asked for a pre connect command and a post disconnect command!

what should i enter into the fields?


Plug your device in, then under the main amarok settings, go to the media device tab. You should then be able to add your new device, choosing to add it as an MTP device. This way you won't need to input any extra stuff, and when you click 'connect', your device should work with amarok.

---

### Post by discoade on 2007-12-05
Hi guys!
couldn't get it to connect it was saying no device was detected! luckily i found something drawing on a lot of ram and cpu rescorces ! totaly different issue i had a power management icon in the top panel telling me my battery was dangerously low!  hmmm desktop pc!  don't know why it appeared and i  couldn't kill the process so i did a restart! power management thing has gone! I thought i'd try amarok again and what do you know! connected straight up!

so to cut a long story short!   Thanks for your help!  you rock :guitar:

---

