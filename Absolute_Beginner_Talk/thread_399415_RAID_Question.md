---
title: "RAID Question"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by ScotchontheRocks on 2007-04-02
I am in the process of building a new PC, with RAID 5 SATA. By the time I get all the parts together, Feisty will be available and I plan on starting with a fresh install. Does it matter whether I go with Desktop or Server Ubuntu for RAID 5 support or is it more important which mobo/RAID controller I use?
Thanks.

---

### Post by carlosfocker on 2007-04-02
If you are using the system as a server then the Server type install in always optimal(The RAID support will be the same for both tho). Be warned that the server type Ubuntu does not install a GUI desktop. You should be more worried about the RAID controller on the motherboard supporting RAID 5. A lot of mobo's support 1 and 0 but not 5.

---

### Post by rearden on 2007-04-02
You should make sure that whatever mobo/RAID controller you have is supported in some way with a Linux driver, either there is a driver already in the mainline kernel or the manufacturer provides a driver in either a patch to the kernel or some other way to make sure that you can make the full use of the hardware you buy.

---

### Post by arbulus on 2007-04-02
You will want to use the "Alternate Install".  Neither the Desktop or Server editions of Ubuntu support installtion onto a RAID.  It was fairly uncomplicated to install.  When you boot it up, it will give you several choices of installations.  I used the OEM Install option.  This was perfect for me; I'm using a 3 disc software RAID 0.  I can't remember clearly if it gave options of RAID 5, but it's definitely worth checking out. 

 I've never used a hardware RAID, so I can't really comment much on that.

---

### Post by psusi on 2007-04-02
You should read [https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto).

Raid 5 fakeraid is not currently supported in Linux without using a proprietary driver from the manufacturer of your raid card, which may or may not be available, and may or may not work.  

Instead of using the fakeraid, you could just install a small /boot partition on the primary disk, and then software raid5 the rest.  This will be easier to do and better supported.

---

