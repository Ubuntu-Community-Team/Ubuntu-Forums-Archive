---
title: "install ubuntu 7.10 in 2nd drive-slave (master=windows xp)"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by cosmas on 2008-01-26
hello i'm cosmas from Greece.
I'm totaly newby in ubuntu and i have some questions:
I have 2 drives the 1st(master) has windows xp. So i think if i could install ubuntu in the second drive without affecting the windows installation. Can i have this way a dual boot screen to choose each time wich OS i want to use? Before installation do i have to format the disk in fat32(i use in both drives NTFS)?
Can i do this also the reverse way? first install ubuntu in master then install windows in slave?
thank you

---

### Post by bufsabre666 on 2008-01-26
yes the dual boot screen is called the grub and it gets automatically installed
you can format the drive from within linux, id suggest ext3 not fat32
if you wanted to reverse it you could format the second drive to nfts and move all the windows files over to the second one and then install linux on the first ((usually but their have been failed attemps so beware))

and always remember to back up your data cause formatting deletes it and makes it hard to recover ((it can be done but its not easy))

---

### Post by nrs on 2008-01-26
> **cosmas said:**
> hello i'm cosmas from Greece.
I'm totaly newby in ubuntu and i have some questions:
I have 2 drives the 1st(master) has windows xp. So i think if i could install ubuntu in the second drive without affecting the windows installation. Can i have this way a dual boot screen to choose each time wich OS i want to use? Before installation do i have to format the disk in fat32(i use in both drives NTFS)?
Can i do this also the reverse way? first install ubuntu in master then install windows in slave?
thank you

Yes to everything except having to format FAT32.

---

### Post by cosmas on 2008-01-26
thank's for the help
And something about the installation:
[IMG]https://help.ubuntu.com/community/GraphicalInstall?action=AttachFile&do=get&target=5.png[/IMG]
in this screen should i choose the 2nd or the 3rd,4th one?
I mean is it better to delete the partition (in windows) of the 2nd drive before the install of ubuntu?

About ext3 format: if i do so , can i read the files in the 1st drive(ntfs) from within ubuntu or copy them in the 2nd drive ?

---

### Post by bufsabre666 on 2008-01-26
just chose the entire drive that your windows isnt on

it makes no differnce what platform youre on

[http://linuxhelp.blogspot.com/2007/03/mount-ext2-or-ext3-partition-in-windows.html](http://linuxhelp.blogspot.com/2007/03/mount-ext2-or-ext3-partition-in-windows.html)
and theres a nice guide on howto read ext3 in windows

---

