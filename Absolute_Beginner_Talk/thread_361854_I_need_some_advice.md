---
title: "I need some advice"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by Donnie Darko on 2007-02-14
I'm a completely new user, and was referred here by my local computer enthusiast. I have a few questions about the entire ubuntu os. Should I run Dapper Drake or Edgy Eft? I've heard that Drake is easier for beginners, but I'm unsure at this point. Also, should I downgrade my vista home premium to XP media center? I read that vista is really hard to get working with ubuntu.  How should I go about partitioning the 200gb seagate barracuda hd I have? are there any good programs? Will my 60 gb video iPod work with ubuntu? I really want to go and get this running, but I need some guidance. 
Thanks in advance
-A confused new user

---

### Post by batholith on 2007-02-14
I recently upgraded to Edgy...and quite frankly for a new user I don't think you'd see much difference in installation or otherwise...My advice would be go with Edgy..it's the latest and greatest...

As far as the windows dual-boot, I've dropped my windows completely so I'm not one to pass advice on this topic...Ubuntu install a boot-manager (GRUB), that can allow you to boot into Windows or Ubuntu..I don't think the version of Windows matters...but again, I don't have any experience with that, but plenty of people here do!

---

### Post by kolinab on 2007-02-14
I was completely new to Linux a few months ago. I installed Edgy right off the bat and it's been a good experience. We're coming up on the new release of Ubuntu soon (in April I guess). I think Edgy is probably as good a bet as anything. 

I can't give you any advice about Vista since I don't have it. I jumped right in and got rid of XP altogether and haven't looked back. I guess as time goes on people will work out their kinks with dual booting Vista - there will be more guidance in coming weeks I suppose.

I could tell you about how I partitioned my drive but since I'm not dual booting I doubt it would do you much good!

There are some good guides on partitioning, one of which is: [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

Good luck and keep using the forums.

K

---

### Post by sda5150 on 2007-02-14
Hi Donnie,

The choice of Dapper of Edgy depends on how long you want to go before you need to upgrade. Dapper has a longer support cycle, so it will be longer before you need to upgrade it. This is great for servers. If you are looking to have a bit of fun with the latest and greatest, then go for Edgy.

Don't know anything about running it along side Vista. All my home machines are Ubuntu, I don't use any Microsoft software... Pretty funny considering my day job is as a Microsoft Server Specialist.

Again I don't run microsoft on any of my machines. My Ubuntu machines are partitioned as defaults at install, I've had no problems with this on any of my machines.

Heaps of great programs, just depends what your into... I'm a musician, so I use Jack Audio, Audacity, Ardour for recording. OpenOffice.org2 is as good if not better than MS Office, Frostwire does all my P2P needs, and Skype runs a treat.

For my iPod I use gtkpod, it works great... There are some great FAQs on how to set this up, just do a google for "iPod Ubuntu", I'll see if I can get the link for you.

Most importantly, if you get stuck, just ask. We are all happy to help you out!

Cheers,
Sam.

PS here's the link to set up your iPod: [http://www.ubuntux.org/how-to-use-an-ipod-with-ubuntu](http://www.ubuntux.org/how-to-use-an-ipod-with-ubuntu)

---

### Post by Donnie Darko on 2007-02-14
Ok, I now have the full burned iso of edgy, is it possible to create a partition with ubuntu, or do I have to use windows to do that?

---

### Post by Donnie Darko on 2007-02-14
ok, you sold me completely haha. I'm just worried my microsoft MN-510 usb network card won't work on my wireless network, its the only way I get internet.

---

### Post by sda5150 on 2007-02-14
Hi Donny,

If you have spare space on your Windows machine, I believe the install alows you to repartition the spare space into your Ubuntu partition, and leave the other space in-tact for Windows.

I haven't done this myself, so can't advise what happens.

As I say to people, don't do anything to your machine without a backup of the stuff you want to keep!

Sam.

---

### Post by i-am-me on 2007-02-14
> **Donnie Darko said:**
> I'm a completely new user, and was referred here by my local computer enthusiast. I have a few questions about the entire ubuntu os. Should I run Dapper Drake or Edgy Eft? I've heard that Drake is easier for beginners, but I'm unsure at this point. Also, should I downgrade my vista home premium to XP media center? I read that vista is really hard to get working with ubuntu.  How should I go about partitioning the 200gb seagate barracuda hd I have? are there any good programs? Will my 60 gb video iPod work with ubuntu? I really want to go and get this running, but I need some guidance. 
Thanks in advance
-A confused new user

I'd say to get Edgy Eft. It's the latest and it wasn't very hard for me to learn. I'm a newbie too. If you have Vista, then why do you want to downgrade? Since Vista and Ubuntu will be on separate partitions, they shouldn't have trouble "getting along". You can partition your HD with a program that's in Vista. Go here:
[http://lifehacker.com/software/vista/screenshot-tour--repartition-your-hard-drive-in-windows-vista-231613.php](http://lifehacker.com/software/vista/screenshot-tour--repartition-your-hard-drive-in-windows-vista-231613.php)
There's also a partitioner built into the CD. I belive it's called GParted (I use Kubuntu and it was called QtParted, so I don't know for sure). You'll find it in the Ubuntu equivalent of the Kubuntu System menu. How much to give Ubuntu is your choice.

---

### Post by IanGB on 2007-02-15
The Dapper CD will just offer to partition the whole drive or the free space or give you a manual choice. It will leave Windows alone and set up its two partitions before installing.

 [http://www.linuxplanet.com/linuxplanet/tutorials/4269/1/](http://www.linuxplanet.com/linuxplanet/tutorials/4269/1/)

Will help you understand this.

---

### Post by Patrick K on 2007-02-15
I know this may be beyond you at the moment, but I suggest that you partition the drive with a separate "/home" partition. The /home partition is where all you settings and data will reside. That way if you have to reinstall, you settings are preserved. 

So this would mean providing three partitions for Ubuntu. A "/" partition (that is where the OS itself resides) a swap partition (much like the swap file in Windows), and a /home partition. BTW, expect to be somewhat, or maybe completely, baffled when it comes time to partition the drive. None of the drive letters you are use to will be there. Instead you will see things like "hda1" or "sda1". This is how Linux names drive partitions. Just try to keep them straight and you'll be fine. With a single 200gb drive and a fresh install of Vista, you shouldn't have any problems. I suggest defraging the drive first, that way all the files on the drive are moved to the start of the drive. 

Also, if you want to easily transfer data between the two OS's you may want to create a FAT32 partition. I'm guessing Vista can read and write to the FAT32 file system. But Linux cannot natively write to NTFS, although there are ways around this.

---

### Post by MrKlean on 2007-02-15
BEFORE you install Edgy or whichever version you choose......run defrag on your Windows partition first !!!!    Most suggest twice.  This will get all your windows stuff together so you won't lose anything...BUT..backing up is also recommended !!!

---

### Post by Donnie Darko on 2007-02-15
Ok, I have the drive partitioned to around 20GB, now I ran the installation cd, and the screen format is way too big (800x600), and I need *at least* 1024x 768, and the best for my HP vs17 is 1280 x 1024. I can't even see the buttons, but I try to get through. Also, I'm not connected to the internet at all with ubuntu, as I have an older microsoft wireless usb network adapter (MN-510). Does anyone know how to get internet running and the screen resolution smaller?

---

