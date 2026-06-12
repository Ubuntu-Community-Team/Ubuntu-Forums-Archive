---
title: "system security"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by Raszul on 2008-02-23
Hi

I'm new to this forum and do not have the slightest knowledge about Unix beyond a few very general aspects.

No I would like to setup my system using a Unix based setup in order to ensure security.

Here is the description:

I'll create 2 partitions:
> #1 = Unix-System Drive (~2GB in size)
> #2 = Storage Drive (~58 GB in size)

when I start my PC and login (in console if possible) to the Unix system I'd like to be instantly redirected to another OS which is run from an image that is mounted as an additional partition or HD

All changes done on that OS(-image) shall be dropped. The next time anyone logs in, the partition is re-created from the image as it were when the image was first loaded.

In addition there should be a couple of other partitions being mounted, depending on the logging in users user group and the user himself.


In windows terms: *(this is how it should look from a Windows-OS that is run from/after the unix-OS)*
C:\ = system partition (5 GB), insecure, changes discarded
D:\ = user partition, size depends upon user group, insecure, changes are saved, individual for each user(200 MB = default, more important users have 1 GB)
E:\ = shared partition (2 GB), changes are saved, encrypted and requires a password to be unencrypted for mounting
F:\ = secure partition (max GB - rest available space on HD#2), only available to more important users, changes are saved, encrypted and requires a password as well as a specific file(from USB-storage) to be unencrypted for mounting



can anyone help me finding the software as well as setup to create that system?
I'll create the image for the OS on my own. (if possible there might be several different ones from which the logging in user can select one)

I'll appreciate any help I can get.

- Raszul

---

### Post by (((X))) on 2008-02-23
It is possible to set unix-system partition to start in command-line, all you have to do is set runlevel to 3.
type startx to go from commandline to grapical.

What exactly do you mean by image? file with .iso extention on second partition perhaphs?

---

### Post by Raszul on 2008-02-23
**1st:** thanks
for answering

**2nd:** with image
i meant any kind of single file that can contain a number of other files, including all data necessary to create a virtual partition from it. In this case a virtual HD.


**3ed:** re-explained
I'll try to reexplain it in a better, easier and generally simpler way so it's less confusing.

> I want to boot the PC.
> Once the Unix-OS has booted in console, I'll have to enter my user name and password.
> Then I'll get a selection of OS that might be started and are asked to provide the passwords and/or keyfiles to decrypt any image that shall be mounted for me and is encrypted.
> After all these images are decrypted and mounted as virtual HDs, the selected OS will boot.
> When I shut down the system *(in any way - even cutting the power)* all changes on the run OS-main-partition will be discarded. All changes on any other partition shall be saved *(best: instantly save them)*

In order to archive this, I've thought about installing a Unix.
That Unix will then manage the primary user accounts *(those required to login)*, the decrypting and mounting of the images as virtual partitions.
The Unix will also make sure that no change on the image/mounted partition of the OS that will be run from it is permanent.

The following images/partitions shall be mounted:
> OS-Partition (7.5 GB) *(an image that contains the OS that shall be started as well as all standard programs for it)*
> User-Partition (100 MB-1 GB) *(this one stores the users personal data and is only accessible for him/her - eg. only mounted for him/her)*
> Shared-Partition (5 GB) *(this partition contains all data that shall be accessible to all users. It is not encrypted)*
> Secure-Partition (remaining space) *(at last the secure one. This one contains the data that shall be kept secure. This one is only available to certain users and requires both: key file and password to get decrypted)*

The partition on which the Unix is installed as well as the one that contains these images *(which might be the same one)* shall not be visible for the OS that will be started.




I hope this is easier and more completely understandable.

- Raszul

---

### Post by (((X))) on 2008-02-24
Never heard of that before, as far as I know, only way system lets you use other os inside it, is by virtualization of hardware(graphical programs like: virtualbox, vmware, parallels)

Wait, wait, there is something you could try: ssh, I registered for a free account at jaguar.garofil.be, and now I´m able to browse the Internet with it for example(www-browser with no GUI´S, but it can be usefull.)
So, if you have another computer somewhere, you could create an ssh-server (you need openssh-server package for that)
This method is even better than everything stored on one machine, since you can hide your server from being phisically accessed by users.

---

### Post by Raszul on 2008-02-25
I thought about using a Virtual Machine.
I hoped that there might be another method like shutting the system down while keeping the mounts and then boot from the new OS-mount...

I've thought that this woun't work. But hope is to die last.

---

