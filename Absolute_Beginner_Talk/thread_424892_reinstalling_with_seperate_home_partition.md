---
title: "reinstalling with seperate home partition"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by xeth on 2007-04-27
When reinstalling I just select the already partitioned root and home.

When I have a separate home partition and I want to reinstall will it overwrite my home partition with the original home? If so what good it will be having a separate partition when it will just overwrite it?

---

### Post by renzokuken on 2007-04-27
i dont think it does overwrite it, but dont quote me on it.

i think the alternate based installer just allows you to manually mount your existing home partition to your new /home folder

---

### Post by mattmole on 2007-04-27
I installed xubuntu last night and I presume the installer is the same / very similar to all other Ubuntu varients. I have installed them all just not so recently!

The installer lists all of the partititions available to the system. You then tell it the mount point and whether you want to format or not!

Matt

---

### Post by xeth on 2007-04-27
> **mattmole said:**
> I installed xubuntu last night and I presume the installer is the same / very similar to all other Ubuntu varients. I have installed them all just not so recently!

The installer lists all of the partititions available to the system. You then tell it the mount point and whether you want to format or not!

Matt

actually my question was, when I have a separate home partition and decide to reinstall ubuntu again will it overwrite my home partition with the default one.

---

### Post by mattmole on 2007-04-27
I would think that it would not overwrite the data in your separate partition if you make sure the format box is not ticked.

Before I reformat I generally use "df -h" at the command line and note down the size of all of the partitions, where they are currently mounted to and which /dev/... they correspond to

In this way I then have an idea of where I want various things mounted and whether I want to format certain partitions or not.

Does that help at all?

Matt

---

### Post by louieb on 2007-04-27
> **xeth said:**
> actually my question was, when I have a separate home partition and decide to reinstall ubuntu again will it overwrite my home partition with the default one.
Maybe. Just like *mattmole* said If you use manual partitioning its your choice **Pay attention and you will see the format check box.**

---

### Post by xeth on 2007-04-27
> **mattmole said:**
> I would think that it would not overwrite the data in your separate partition if you make sure the format box is not ticked.

Before I reformat I generally use "df -h" at the command line and note down the size of all of the partitions, where they are currently mounted to and which /dev/... they correspond to

In this way I then have an idea of where I want various things mounted and whether I want to format certain partitions or not.

Does that help at all?

Matt

so I go to manual formatting and follow my old partition and check the root "/" and swap but not the /home partition? This will allow me to reinstall ubuntu without losing my settings and files?

---

### Post by antoz on 2007-04-27
That's correct, only format "/" and "swap"

---

### Post by psionyk on 2007-04-27
You still have to mount /home in the installation to your existing home partition, but like the others said, DO NOT pick to reformat it, only mount.

---

