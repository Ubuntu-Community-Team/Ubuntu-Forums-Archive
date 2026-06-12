---
title: "Created partition for /home"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by leupi on 2007-07-22
During the installation of 7.04, I created a 18GB partition on my 80GB hard drive that I wanted to use for /home so that if I wanted to reinstall the OS again (I have a habit of doing that) then my personal data would still be there. It is /dev/sda3 and I mounted it to /home.

I am unclear if this is correct. When user accounts are created will they be on the new partition or on the same partition as the OS? Is there an application in Gnome that I can use to view the contents of the different partitions on the hard drive?

Thanks,
Todd

---

### Post by autocrosser on 2007-07-22
1> yes this is correct--just looking at the file system you would think that information is created in two places--but that is not the case.

2>I am unclear as to what you are asking--Gparted will show you what your partitions look like & there is a disk useage tool in accessories to see the contents of a partition.  Nautilus (the file manager) shows all the contents in a seamless way--your /home even though on a different partition, is listed as part of the main filesystem.

---

### Post by Sef on 2007-07-22
> During the installation of 7.04, I created a 18GB partition on my 80GB hard drive that I wanted to use for /home so that if I wanted to reinstall the OS again (I have a habit of doing that) then my personal data would still be there. It is /dev/sda3 and I mounted it to /home.

I am unclear if this is correct. When user accounts are created will they be on the new partition or on the same partition as the OS? Is there an application in Gnome that I can use to view the contents of the different partitions on the hard drive?

Mine is set up under its own partition.   When I have updated via the alternate CD, my home partition is left instact.

---

### Post by leupi on 2007-07-22
Thanks for the reply. To clarify what I was asking, I was wondering if there was an app that I could use to drill down into the partition that I used to put /home on (sda3 in this case) just so that I could see that the data was actually on a different partition. As you said, Nautilus does not show that. I guess that I am just paranoid that the user accounts are not on that partition and if I reinstall, bam, they're gone...

Thanks again,
Todd

---

### Post by autocrosser on 2007-07-22
Then take a look at Disk Useage Analyzer--at Main Menu>Accessories. It will not show contents of a file, but it will show a very good amount of information.

---

### Post by leupi on 2007-08-12
Thanks for all of the info guys. I am quite confident that my /home is on a separate partition now.

---

