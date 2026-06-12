---
title: "dual boot problem"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by antisocialist on 2008-01-02
i was following this post
> **_asc_ said:**
> Hello!

Boot with the Live-CD. Then mount your Ubuntu root partition. Go to 
the /boot/grub directory of your root partition and open the file menu.lst. Then set the timeout value to a higher value (e.g. 10).

e.g. If your root partition is hda1:
```

sudo su
mkdir /mnt/ubuntu
mount -t ext3 /dev/hda1 /mnt/ubuntu
cd /mnt/ubuntu/boot/grub
gedit menu.lst

```

and i was wondering how i can mount my ubuntu partition?? (my problem is my computer automatically boots the windows partition without asking if i want to boot ubuntu)

---

### Post by p_quarles on 2008-01-02
> **antisocialist said:**
> i was following this post


and i was wondering how i can mount my ubuntu partition?? (my problem is my computer automatically boots the windows partition without asking if i want to boot ubuntu)
Maybe give a little more info? I take it that the above procedure didn't work for you, but what was the output?

---

### Post by logos34 on 2008-01-02
that's using the live cd...go into your bios and set it to boot from cdrom first ahead of hard drive.  Then if necessary change the timeout to above.  Also 'hiddenmenu' should have # before it (i.e. disabled)

---

### Post by cecure on 2008-01-02
if you are still having trouble... in the live system cd to the disk where you have installed ubuntu and post the output of the following
```
cat boot/grub/menu.lst
```

---

### Post by lisati on 2008-01-02
> **antisocialist said:**
> i was following this post


and i was wondering how i can mount my ubuntu partition?? (my problem is my computer automatically boots the windows partition without asking if i want to boot ubuntu)

Note that it says to boot from  the Live CD, which should bypass your normal Windows start-up. You'll be able to mount your Ubuntu partition from there.

---

### Post by antisocialist on 2008-01-02
i used livecd and flagged my ubuntu partition as boot, and when i boot from my hdd it says error loading operating system.

last night i decided i need xp for one program so i resized my ubuntu partition and then installed xp, now it says when i boot to ubuntu "error loading operating system" and nothing happens, how do i get ubuntu to boot?

---

### Post by thelatinist on 2008-01-02
> **antisocialist said:**
> i used livecd and flagged my ubuntu partition as boot, and when i boot from my hdd it says error loading operating system.

last night i decided i need xp for one program so i resized my ubuntu partition and then installed xp, now it says when i boot to ubuntu "error loading operating system" and nothing happens, how do i get ubuntu to boot?

You need to restore grub.  Search the forums, there are plenty of howtos.

---

### Post by logos34 on 2008-01-02
And reflag windows as boot

---

### Post by antisocialist on 2008-01-02
why flag windows as boot?

---

### Post by logos34 on 2008-01-02
> **antisocialist said:**
> why flag windows as boot?

because windows is the only one that cares about the boot flag (signifies 'active' partition), ubuntu doesn't need it

> last night i decided i need xp for one program so i resized my ubuntu partition and then installed xp, now it says when i boot to ubuntu "error loading operating system" and nothing happens, how do i get ubuntu to boot?

that's a [windows error]("http://users.bigpond.net.au/hermanzone/p15.htm#Error_Loading_Operating_System")...I thought you restored grub after you reinstalled windows? not sure what your status is

---

