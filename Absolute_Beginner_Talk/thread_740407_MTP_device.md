---
title: "MTP device"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by doomedfire on 2008-03-30
First off you guys have been great in helping me. Secondly I have a Sansa View 8 GB that i want to use as a drag and drop which was a MTP when i had windows, I wanna do that on linux Ubuntu 7.10 Im kinda a linux newb so I'm still getting use to the new setup. 

Thx in advance.

---

### Post by annda on 2008-03-30
libmtp is available in the repositories. i'm not sure but you may have to reboot after installing it.

---

### Post by doomedfire on 2008-03-30
How do i install it?

---

### Post by doomedfire on 2008-03-30
Ok i installed it from the synaptic. Wheres my device gonna be found. If its sapose to be in "computer" it wasnt. Unless i missed it.

---

### Post by forrestcupp on 2008-03-30
Make sure the device is plugged in to your USB and that it is turned on.  If it doesn't automatically open up Nautilus, try opening Nautilus in the root filesystem, and look in the /media directory and see if it is there.

---

### Post by doomedfire on 2008-03-30
All thats in there is cdrom cdrom0 cdrom1 and disk when its plugged in.

---

### Post by forrestcupp on 2008-03-30
What is the one called 'disk'?  Did you try it to make sure that's not it?

---

### Post by doomedfire on 2008-03-30
Ya disk is a flash drive i have plugged in.

---

### Post by annda on 2008-03-30
i just found that tip:
[http://forums.sandisk.com/sansa/board/message?board.id=view&thread.id=5395](http://forums.sandisk.com/sansa/board/message?board.id=view&thread.id=5395)

it seems the sansa does not always show up when using the mtp protocol (my cowon d2 does, so i assumed it would work for you, although my father's creative zen also refused to cooperate)

---

### Post by doomedfire on 2008-03-30
I tried it it did show up in /media but none of the stuff showed up in the directories even though i know that are there.

---

### Post by rambaldi on 2008-03-31
I'm sorry, but in Linux it's not possible to drag and drop files like you do in Windows, when using a MTP device.

You can use Gnomad 2 to copy regular files. But for music is better you use Amarok, as Gnomad2 interface is not very advanced.

I had the same awful experience with a Samsung YP-K3 MP3 mplayer, which is also MTP.

PS:
I strongly recommend NOT to buy any MTP devices as their support in Linux is very poor.

---

### Post by doomedfire on 2008-03-31
When i got amorack i got this error

"Error Loading Media
No suitable demux plugin. This often means that the file format is not supported.
file:///media/Sansa View/SYSTEM/MTPCONTENT/0/5/B/000005B1."

---

### Post by rogerp1 on 2008-03-31
My MTP device works with Rhythymbox. It might be worth a try

---

### Post by BDNiner on 2008-03-31
I found that my device runs fine in rhythmbox, exaile and banshee if i run those applications as root. I have a creative zen 4GB. I didn't feel safe running as root so i am still using windows to manage my music.

---

### Post by forrestcupp on 2008-03-31
I have a cheap SanDisk Sansa mp3 player, and in its settings it has the option to change it to MSC rather than MTP.  Maybe yours has that option and maybe MSC would work better.

---

