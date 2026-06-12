---
title: "How Do I Define the Root File System?"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by tlinux on 2007-05-17
I'm trying to install Kubuntu 7.04 using the Alternate Live Disk. The hard drive already has several partitions on it. Two are for Windows and three are are for Mandrake. I want to use the Mandrake partitions and install Kubuntu there in place of Mandrake. With the Alternate disk I am directed through procedures to change or remove the partitions. When I do what I think is the correct thing for each of the three partitioned areas, i end up with an error message that says, "No root file system is defined." I never saw any option that would let me do that. So how do I tell it where I want the root file system installed?

Thank you.

---

### Post by justin whitaker on 2007-05-17
> **tlinux said:**
> I'm trying to install Kubuntu 7.04 using the Alternate Live Disk. The hard drive already has several partitions on it. Two are for Windows and three are are for Mandrake. I want to use the Mandrake partitions and install Kubuntu there in place of Mandrake. With the Alternate disk I am directed through procedures to change or remove the partitions. When I do what I think is the correct thing for each of the three partitioned areas, i end up with an error message that says, "No root file system is defined." I never saw any option that would let me do that. So how do I tell it where I want the root file system installed?

Thank you.

When you get to where the installer asks you to use Guided partitioning (resize), Guided (whole disk)...there should be a manual option at the bottom.

---

### Post by tawniteamo on 2007-05-17
if you do manual partioning, it should give you the option during partitioning, I blieve it is right under the option for filesystem type (i.e ext3) and there change it from media/.../...(don't know exactly) to just / and that makes it root

---

### Post by hyper_ch on 2007-05-17
And think it's called "mount point" in the installer...

---

### Post by tlinux on 2007-05-17
Following your suggestions I found the root file option in "mount point" option. I selected it and the installation process ran without a problem. When it finished installing, I tried to boot into the new installation, That didn't work and now I can't get into either Kubuntu or Windows. However, this is a different problem from what's discussed here, so I'll start a new post.

Thanks for all your help. I really do appreciate it!!!:)

---

### Post by hyper_ch on 2007-05-18
Hmmm, do you have IDE and SATA drives in the same machine?

---

### Post by tlinux on 2007-05-18
I don't know what kinds of drives I have and I don't know how to find out.:confused:

---

### Post by tawniteamo on 2007-05-19
ok go here: [http://www.ackadia.com/computer/images/sata-vs-ide-bg.jpg](http://www.ackadia.com/computer/images/sata-vs-ide-bg.jpg)   the one on the left is IDE the one on the right is SATA

---

