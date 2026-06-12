---
title: "RAID formating"
date: 2009-09-08
forum: Apple Hardware Users
---

### Post by tomce on 2009-09-08
Hello guys,
I need your advise in this matter.
I have one sata hdd which runs ubuntu (so I'm very happy with that) :P
And I have hardware raid (Highpoint 174x), ONE mirrored array (2x1TB hdd)
installed and ready to go.

What I want to do is:
1) create one large HPS+ partition and share it with my macs, and slack box.
(what the best utility to do that, I know well Fdisk, but I read threads and some guys recommending to use gparted) :confused: 
2) set correct security permissions for this partition (so nobody else could amend r/w apart myself and my net users) Any samples- would be great.

I would appreciate your all comments and advises.:KS
Bay the way- does HPS+ will be good option as file system in this matter?
Thanks,
regards,
Tom

---

### Post by realzippy on 2009-09-08
..shure that your controller is a real hardware RAID?
It seems to be a fakeraid controller if you have to install drivers...
Check this out first.
If so,have a look:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)




edit:
found this,it seems to be fakeraid:
[http://brainstorm.ubuntu.com/idea/15342/](http://brainstorm.ubuntu.com/idea/15342/)

---

### Post by tomce on 2009-09-08
I think Mate, you don't understand me. I installed already it. Now I just want to format. It works fine as EXT3 file system.

---

### Post by tomce on 2009-09-08
So now I will answer for myself and others...
So once you finish play with raid and your linux box can recon it, let's do some things..
By default you can't format to hfs or hfs+, but once you downloaded and installed package like:
"hfsprogs"
you can simple go to gparted and make your disks as hfs or hfs+ (don't forget "raid flags").
That's it. :popcorn: 

If you wish to mount it as auto, edit your fstab file.
If anyone else will need step by step manual, pls let me know- I can write short step by step instruction how to make your linux box as nice NAS server for your mac family.
Bay the way- Snow leopard or Leopard, Leopard server (RETAIL VERSION, NOT HACKINTOSH) can be also easy installed on pc with intel processor.

I have been using intel motherboard with dual core atom CPU.
Total cost of everything: 200£ (DUAL CORE ATOM 1.6Ghz, intel video, 2GB of RAM, 2x1TB hdds+160GB sata drive to run ubuntu+Asus mini tower, Highpoint raid 1740)
Motherboard with CPU 58£ (new from ebuyer.com)
2GB of RAM: 17.50£ (new from ebuyer.com)
2x1TB samsung spin point 108£ (new from ebuyer.com)
Raid card (ebay) 20£
+0£ spare hdd. 
Asus tower (ebay) 15£ (new)

+spare router which runs dd-wrt behind old cisco boy:)

Energy cost 10x < than normal PC :guitar:  and only 21db (I removed all fans from the tower)

---

