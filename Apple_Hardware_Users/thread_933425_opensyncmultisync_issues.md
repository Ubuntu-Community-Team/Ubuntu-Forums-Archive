---
title: "opensync/multisync issues"
date: 2008-09-29
forum: Apple Hardware Users
---

### Post by niteblind on 2008-09-29
HHi,

Wasn't really sure where to post this so I hope someone takes pity on me. I have a macbook which I am trying rather unsucessfully to sync with my nokia phone and Kontact. I have found and followed this howto and now I am a little lost : [http://ubuntuforums.org/showpost.php?p=1998822&postcount=62](http://ubuntuforums.org/showpost.php?p=1998822&postcount=62)

I followed it as far as step 42 I had a little touble installing things as I am using Hardy and they are named differently in the repos. I BELIEVE I have all I need but I do not understand where I am supposed to configre this sync. Also when I check multisync there is nothing in there.

Can anyone point me in the correct direction or provide a better how to. I do not want to use evolution as i habe issues with it and as far as I can see this is my only option to sync with Kontact as I have tried kitchensync and have absolutely no idea what I am supposed to do with that at all.

Help please?
niteblind

---

### Post by niteblind on 2008-09-30
could someone let me know where I can find this app, as it is not in mu current repos, is it included as part of something else maybe?

multisync-qad

cheers

---

### Post by cyberdork33 on 2008-09-30
With a quick search I haven't found much. Looks like the last dev for Ubuntu was with Edgy.

You can browse the source, or ask the developers at their site if there is a replacement.

[http://opensync.org/](http://opensync.org/)

---

### Post by niteblind on 2008-09-30
okay, thanks for the response but things seem to have moved on I found a better howto for opensync and got past step 42 all the way to the end. Hooray.... where it failed! Now I have followed the config file for the syncml-obex-clent plugin to the letter and when I try and sync with my Nokia E51 I get thisL

niteblind@Wolverine:~$ msynctool --sync kontact2phone
Synchronizing group "kontact2phone" 
The previous synchronization was unclean. Slow-syncing
Member 1 of type kdepim-sync had an error while connecting: KOrganizer is running. Please finish it
Member 2 of type syncml-obex-client had an error while connecting: Bluetooth connect error
All clients have disconnected
The sync failed: Unable to connect one of the members
Error synchronizing: Unable to connect one of the members
Pipe closed! Exiting.
niteblind@Wolverine:~$ Pipe closed! Exiting.

Anyone got any idea why it I use the Kubuntu obex push program it send fine and why I cannot get it to sync through the same thing?

niteblind

---

### Post by gatman3 on 2008-10-30
I had syncing to my Nokia N75 working with Gutsy and Hardy.  Having trouble with Intrepid, but still working on it.

Your first problem: KOrganizer still running... is probably because you have Kontact running while you try to sync.  I found that you have to quit out of Kontact/KOrganizer in order to sync.

Your second problem about a bluetooth connection error... could be lots of things.  Are you able to pair with the device?  In Intrepid I have found that Bluetooth is pretty much totally hosed with KDE... might be a KDE4 problem specifically, don't know for sure.  I have found that using the GNOME bluetooth applications allow me to pair with my phone and browse the phone file system using Nautilus (although Nautilus kind of sucks).  You need to use bluetooth-wizard and bluetooth-browse to do this.  Making sure you can pair with the device is the first step.

---

### Post by Dareajoe on 2008-10-31
HI....I have SX1 2 days, before s55 and c65. Multisync with rs cable works fine.Now i buy USB cable with phone and i don't known how sync my mobile with evolution.... thanks....:guitar:

---

