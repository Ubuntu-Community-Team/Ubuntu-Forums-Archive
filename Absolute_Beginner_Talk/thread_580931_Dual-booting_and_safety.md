---
title: "Dual-booting and safety"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by Nyct on 2007-10-19
Ok, so Ive downloaded 7.10.

Ive burned it to a disk, and checked the md5 thing.

Now... Im on Windows atm, how can I setup Ubuntu without over-writing Windows? 

I have one hard drive, which currently has all my Windows stuff on it (with some free space, ofc), and I dont want to lose this data.

Can someone link me to, or guide me through, how to set Ubuntu up while allowing me the option to use Windows OR Ubuntu each time I reboot?

Many thanks in advance...looking forward to it :)

Oh, and remind me EVERYTHING I need to do before booting Ubuntu, I dont want to ruin my copy of Windows :P (yet :D)

---

### Post by montres on 2007-10-19
Hi there!

If there is enough free space, you can dual boot without problems. Start by reading this:
[https://help.ubuntu.com/community/WindowsDualBoot?highlight=%28dual%29%7C%28boot%29]("https://help.ubuntu.com/community/WindowsDualBoot?highlight=%28dual%29%7C%28boot%29")

---

### Post by montres on 2007-10-19
Oh, and the part where it says you can't write to NTFS partition is obsolete. Ububntu 7.10 was built in capability to read and write to NTFS, so don't worry!

---

### Post by Nyct on 2007-10-19
Ok thanks a lot! Going to have a first try at installing soon :)

---

### Post by Nyct on 2007-10-19
Oh, thanks again - also, should I be choosing manual or automatic partitioning?

---

### Post by Paqman on 2007-10-19
> **Nyct said:**
> Oh, thanks again - also, should I be choosing manual or automatic partitioning?

Manual is a bit more involved, but better. First of all, defrag your drive in Windows and back up all your data.

Best practice is to make three new partitions:

Root partition (6-10GB)
Home partition (as big as you like)
Swap partition (1-2x amount of RAM in your system)

[More info and links about Ubuntu disk partitioning](http://www.sp0rk.co.uk/Archive/Issue10/stayingin_install_ubuntu5.php)

---

### Post by sayuki288 on 2007-10-19
if your not sure about what your doing better use automatic partitioning :)

---

### Post by montres on 2007-10-19
I guess manual gives you more control. Just make sure you leave some free space to your windows partition, or it won't function properly.
I think you will find this thread quite helpfull:
[http://ubuntuforums.org/showthread.php?t=569290&highlight=partition+size]("http://ubuntuforums.org/showthread.php?t=569290&highlight=partition+size")

---

### Post by Paqman on 2007-10-19
> **sayuki288 said:**
> if your not sure about what your doing better use automatic partitioning :)

Doing it manually will allow you to create a separate home partition, which is VERY useful, especially if you're new and may be installing/reinstalling.

It's not *hard* really, it just requires a little forethought. Gparted is fairly intuitive.

---

### Post by Scroobytec on 2007-10-19
Two good sites for tutorials for setting up a dual boot system are:

1)  [http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)

2) [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

and the best may be:

[http://howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty](http://howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty)

Of course they all start with installing Win XP so just skip down to the Ubuntu install section.

---

### Post by Nyct on 2007-10-19
OK....seem to be getting there.

Booted Ubuntu, managed to connect to internet, still using Live or something though...haven't installed yet.

Last time I tried to install, I saw one partition (obviously the c:// from Windows stuff) with a 160gb limit, 60gb or so used. Tried to resize to 100gb, but it stayed at 0% resized for a bit...

Should I expect it to take upwards of 30 mins to resize a partition, or is there something Im doing wrong here? Fast reply appreciated :)

---

### Post by Nyct on 2007-10-19
Just got to the 'Edit Partition' bit again.

Clicked on the current partition, clicked Edit, but all I see is this :

Use as: ntfs
Mount point: /media/sda1

When I click OK, nothing happens just takes me back to previous screen.

---

### Post by Paqman on 2007-10-19
You have to specify the new size for that partition. Does it come up with boxes denoting the start and end point of it on the disk?

[img]http://gparted.sourceforge.net/screens/gparted_5_big.jpg[/img]

---

### Post by Nyct on 2007-10-19
Will have another look, previously, I didnt see anything like that.

---

### Post by Nyct on 2007-10-19
Getting annoyed now...when I click Edit partition, I get a screen like :

[http://img241.imageshack.us/my.php?image=problempartul6.png](http://img241.imageshack.us/my.php?image=problempartul6.png)

Why can't I see one that allows me  to edit partition size? :(

---

### Post by Nyct on 2007-10-19
Had enough for now, cant seem to get anywhere past partitions stage.

Going back to Windows for a bit... will check thread for replies

---

### Post by Nyct on 2007-10-19
Slight bump here, can someone take a look at my screenshot and see if anything is wrong?

Off for another try at booting and installing :)

---

