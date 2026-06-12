---
title: "How do I dual boot Kubuntu and Ubuntu?"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by kexodusc on 2007-01-02
Hello folks.  Been running Ubuntu for about a month now after XP's genuine Advantage thing produced a false positive - yeah, XP crashed, when I reinstalled, it didn't take kindly to the BIOS update my manufacturer recommended - the support guys even accused me of pirating at first until they calmed down.  They sent me a fix, but that was it - I've vowed to avoid Windows at all costs.

Love Ubuntu, and had previously installed KDE desktop by the "sudo aptitude install kubuntu-desktop" line...

Not sure, but I'm wondering if I can actually install Kubuntu and Ubuntu on separate partitions rather than using the above - sort of a dual boot - I'd like to keep them separate since my wife prefers the Kubuntu Destop to Ubuntu (my preference).  Is this possible, or is the "sudo aptitude install kubuntu-desktop" method my only choice?  Thanks

---

### Post by halitech on 2007-01-02
No real need to dual boot them. when you are logging in, I believe you can select what DE  you want so just install both and pick when logging in.

---

### Post by bruenig on 2007-01-02
It is possible and fairly easy. Just put them on two separate partitions. Have the last one write grub and grub should detect both. If it doesn't you can always add it later.

---

### Post by boutros on 2007-01-02
hey there,

no need for dual boot. use synaptic or apt-get install kubuntu-desktop as you mentioned. Then you will create 2 different users if you desire; one for you and one for your wife. Then on the log-in page you can choose a gnome session or your wife can choose kde session and log-in as her user.

peace,
boutros

---

### Post by Sef on 2007-01-02
To install on seperate partitions, read these:

[Psychocat's installing]("http://www.psychocats.net/ubuntu/installing") (from the Live CD.)

The [Illustrated Dual Boot]("http://www.users.bigpond.net.au/hermanzone/") (from the alternate cd.)

They are both for Windows/Ubuntu, but the same principle applies.  Just ignore the part about making a FAT32 partition.

> no need for dual boot. use synaptic or apt-get install kubuntu-desktop as you mentioned. Then you will create 2 different users if you desire; one for you and one for your wife. Then on the log-in page you can choose a gnome session or your wife can choose kde session and log-in as her user.

If you do that, you'll have all Kubuntu and all Ubuntu's apps on one os.   It is not so clean then.   Better to have them on separate partitions.

---

### Post by kexodusc on 2007-01-02
Wow thanks for the fast responses guys...

Yeah, I'd prefer the dual boot just to keep things clean - I tried web searching this before posting and this one was tough for me to find a complete answer to.  One of the reasons I liked Gnome was the relative minimalist approach compared to KDE (though I'm really impressed with the polish of Kubuntu, just not for me).
Wife is a WIndows user.  I'd like Kubuntu to be the default OS just to make it easy for her.
I can select Ubuntu when I log in.

---

### Post by iammeagain on 2007-06-23
im trying to do the same thing, with Kubuntu and Ubuntu. I did as suggested above, but grub fails to install. 
I figured i need to then just manually edit the menu.lst, only i don't know for sure what i need to put for the kernel, initrd, etc. How would I find that out? 
So I need to add an Ubuntu 7.04 fresh install, installed at (hd0,2) or my third partition on my first hard drive, to grub.

When i do try to boot the Ubuntu partitions entry it gives me: "Error 17: Cannot mount selected partition" 
Also there is no menu.lst in the Ubuntu partition only the Kubuntu since grub failed to install

---

