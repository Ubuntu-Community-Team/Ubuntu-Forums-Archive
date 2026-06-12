---
title: "Dual-boot help plz?"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by ferod on 2007-10-25
Hmm it's weird, i had server 2003 installed previously... Working fine. Wanted linux because i generally prefer it for everyday typing,surfing, coding. So i installed it, resized my partition, guided install to create partitions, everything installed fine. Ubuntu boots fine. But for windows, i press enter to boot and it just hangs on starting up............ Does nothing else >.<.

---

### Post by dward526 on 2007-10-25
can you see your windows partition from your Ubuntu desktop?

---

### Post by ferod on 2007-10-25
:confused: If by that you mean can i see the disk, then yes, i can acces it, browse and such..

---

### Post by ezak on 2007-10-25
Try running:

fixgrub

at the command line. 

Or I would better suggest Super Grub Disc. Highly reccommended. You can DL straight from here and burn it to disc.

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

It's a pretty handy tool to have on disc for any Linux or windows system to recover/fix/boot your system the way you want.

---

### Post by dward526 on 2007-10-25
I agree with ezak, I have used the SGD before for a similar problem and it worked.

---

### Post by ferod on 2007-10-25
Meh, fixgrub isn't recognized, i'll try the tool ^^.

---

### Post by ezak on 2007-10-25
My bad, the command surely wasn't fixgrub. I guess I need some sleep badly! You would simply type grub to get to the menu, which I haven't had to do in quite some time. Anyway, here's a simple and informative solution, if you want to fix your grub from command line. 

Open a shell (Terminal)

Type the following to re-configure GRUB

sudo grub

Type the following followed by the TAB key

root (hd

This will provide you with a list of possible physical drives eg:

hd0 or hd1

Type the number of the drive you installed ubuntu on, not to worry if you unsure, the next step with tell you if you on the right path. Add a &#8216;,&#8216; after the number and press the TAB key again:

root (hd0,

You will see something similar to the following:

grub> root (hd0,
Possible partitions are:
Partition num: 0, Filesystem type unknown, partition type 0×7
Partition num: 2, Filesystem type is ext2fs, partition type 0×83
Partition num: 4, Filesystem type unknown, partition type 0×7
Partition num: 5, Filesystem type is fat, partition type 0xb
Partition num: 6, Filesystem type is fat, partition type 0xb
Partition num: 7, Filesystem type unknown, partition type 0×82

Notice the ext2fs partition, this is the one Ubuntu is installed for the above example. I would therefore type:

root (hd0,2)

Now type the following, replacing hd0 with the physical drive Ubuntu is installed

setup (hd0)


This solution does not list the name of your hdd partitions, of course, but you will have to query the names using the method above. This is merely an example. In any case, however you decide, I still highly recommend Super Grub Disc for recovery and changng boot options. Much easier.:wink:

---

### Post by ferod on 2007-10-25
Hah when trying that i got cannot mount selected partition... Is there any chance it has to do with my user account? =\. I have to type a password to mount the drive whilst on ubuntu, maybe that's causing trouble >.<.

---

### Post by ezak on 2007-10-25
Yes, sudo means you need to have "superuser" permissions and therefore you will have to type in your password. It's for doing administrative commands, so to speak. :mrgreen:

---

### Post by dward526 on 2007-10-25
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

I have used this sequence many times.

---

