---
title: "can't unmount any partitions"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by S15_88 on 2007-07-09
so i deleted my swap partition so i could use the extra space for my /home but i can't unmount the /home partition? i get a:
> 
Could not unmount /dev/sda5 
The partition could not be unmounted from the following mountpoints:
/home
Most likely other partitions are also mounted on these mountpoints. You are advised to unmount them manually.


I've attached a pic if anyone would like to reference it.

Thanks, Alain

---

### Post by KIAaze on 2007-07-09
[COLOR="Red"][edit]To any new passer-by: It seems you can do without the swap if you have enough RAM. cf post below by Happy_Man.[/edit][/COLOR]
**You need the swap partition! Don't delete it!!!**
Every GNU/Linux distribution uses a swap partition (all can use the same by the way).

I don't know how well Ubuntu will run without one, but I've never heard of anybody doing so. I wouldn't recommend you to leave it like this.

Now for the unmounting problem:
**You can't unmount /home because you are using it.** :rolleyes:

If you want to resize it, you'll have to do so either from another OS on your PC (ideally also GNU/Linux, because I have no idea how well Windows handles this) or _simply by using a Live-CD_.

Your Ubuntu installation CD could do the job or you could use a [GParted Live CD]("http://gparted.sourceforge.net/livecd.php") or a [System rescue CD]("http://www.sysresccd.org/Main_Page").

---

### Post by overdrank on 2007-07-09
> **S15_88 said:**
> so i deleted my swap partition so i could use the extra space for my /home but i can't unmount the /home partition? i get a:


I've attached a pic if anyone would like to reference it.

Thanks, Alain

Hi I believe you will have to do this from the live cd or the gparted on cd. I believe you can't unmount them because they are in use by ubuntu. Hope this helps!:popcorn:

---

### Post by KIAaze on 2007-07-09
Oh and a swap partition improves the performance of Live-CDs by the way. :)
You have more than 100GB of space. Surely, you can afford 1GB for swap.
I have 3 OSes on a 40GB HD!

---

### Post by Happy_Man on 2007-07-09
Assuming that your swap is that little bit you've got highlighted, you can't unmount it without using a LiveCD of some sort. Reason being is because if you try from the install, it would have to unmount the / and /home partitions *while it is using them*, which could never be good. So, just boot up an Ubuntu LiveCD, go to System --> Preferences --> GNOME Partition Editor, and tweak to your taste.

EDIT: actually, KIAaze, my friend doesn't use a swap partition because he's got 2 GB of RAM, and even under maximum usage, it never goes over 1.5 GB of RAM used. So he doesn't use a swap partition. I do agree that LiveCDs are much improved by using swap, btw.

---

### Post by S15_88 on 2007-07-09
jus to make sure i've got this right, i pop the live cd in and then what optioon do i select?  Should i just do install make all the partitions how i want then cancell the installation?

thanks, Alain

---

### Post by overdrank on 2007-07-09
> **Happy_Man said:**
> Assuming that your swap is that little bit you've got highlighted, you can't unmount it without using a LiveCD of some sort. Reason being is because if you try from the install, it would have to unmount the / and /home partitions *while it is using them*, which could never be good. [COLOR="Red"]So, just boot up an Ubuntu LiveCD, go to System --> Preferences --> GNOME Partition Editor, and tweak to your taste.
[/COLOR]
EDIT: actually, KIAaze, my friend doesn't use a swap partition because he's got 2 GB of RAM, and even under maximum usage, it never goes over 1.5 GB of RAM used. So he doesn't use a swap partition. I do agree that LiveCDs are much improved by using swap, btw.

I believe happyman gave you the instructions>:)

---

### Post by KIAaze on 2007-07-09
I can't try it out now, but isn't there a way to access GParted directly without launching the installation program?

If not, I guess yes: choose manual partitioning and then cancel the installation.
But I've never done it like that. I always used the GParted Live CD.

edit: yep, previous post answered my question. ^^

---

### Post by overdrank on 2007-07-09
> **KIAaze said:**
> I can't try it out now, but isn't there a way to access GParted directly without launching the installation program?

If not, I guess yes: choose manual partitioning and then cancel the installation.
But I've never done it like that. I always used the GParted Live CD.

Yes gpart is included with feisty but you can not modify the partitions while ubuntu is using them thus you use the live cd that has gpart on it and you can unmount the drives.;-)

---

