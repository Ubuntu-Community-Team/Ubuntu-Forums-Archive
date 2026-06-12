---
title: "Mounting Discs"
date: 2006-02-09
forum: Absolute Beginner Talk
---

### Post by greeniearun on 2006-02-09
I want to browse the windows files while i'm working in ubuntu. How can I do that?

---

### Post by Sutekh on 2006-02-09
Quite easily

[Mounting Windows Partitios in Ubuntu - by ]("http://www.psychocats.net/linux/mountwindows.php")[aysiu]("http://www.ubuntuforums.org/member.php?u=21941")

Is about the best link I can think of to achieve mounting Windows type partitions in Ubuntu.

---

### Post by poiuytr on 2006-02-09
It's helpful, but I wish it had a little more explanation for why it suggests certain settings.  For example, I would like to have my Windows partition mounted every time that I log into Ubuntu, and umounted when I log out.  Does this change to fstab accomplish that?  Or does it merely give me the ability to manually mount Windows after I log on?  I want such mounting to be automatic.

Also, I want only me, THIS user, to have that ability - I don't want other users on my machine, to have that ability, to see Windows.

So, what do those various umask etcetera settings mean?  Are those settings making an assumption and mounting Windows fdor all users?  Is mounting a user-specific process?  (i.e., does a different user on my machine have a DIFFERENT fstab?  Or is there only one fstab?)

If there is only one fstab, then what should be the settings to allow only one user to mount Windows, versus the settings for it to be mounted for everybody?

Etcetera etcetera.  As you can see, I have many questions on this, probably more questions than the parent poster.  And I know, through some Googling and reading of man pages, I could probably eventually figure this out.  But if that document is an effort at a guide, it would be greatly appreciated if it strove to be a little more of a comprehensive guide, and explain the things that it is suggesting.

---

### Post by Sutekh on 2006-02-09
> **poiuytr]It's helpful, but I wish it had a little more explanation for why it suggests certain settings.  For example, I would like to have my Windows partition mounted every time that I log into Ubuntu, and umounted when I log out.  Does this change to fstab accomplish that?  Or does it merely give me the ability to manually mount Windows after I log on?  I want such mounting to be automatic.[/QUOTE]
/etc/fstab **is** the automatc way to mount filesystems.  They are mounted at log on, and unmounted at log off.

To manually mount a partition you need to use the **mount** command, which is another kettle of fish.


[QUOTE=poiuytr]
Also, I want only me, THIS user, to have that ability - I don't want other users on my machine, to have that ability, to see Windows.
[/QUOTE]
Do you mean ability to edit the fstab or ability to see partitions?

You can limit who can have access to /etc/fstab.  To do this make sure that your user is the only user with **administration privileges**.  Usually the **first user** is given administration privileges by **default**, surplus users after that **do not** gain these privileges by default, but must be set if desired.

If users do not have administration privileges they will not be able to edit the fstab.  (You can also change the permissions of /etc/fstab so users can't even *look* at it if you would like)


If you meant access to partitions, you can limit this by introducing an extra flag to the entry in /etc/fstab said:**
> 
So, what do those various umask etcetera settings mean?  Are those settings making an assumption and mounting Windows fdor all users?  Is mounting a user-specific process?  (i.e., does a different user on my machine have a DIFFERENT fstab?  Or is there only one fstab?)
If there is only one fstab, then what should be the settings to allow only one user to mount Windows, versus the settings for it to be mounted for everybody?

There is only one fstab, and umask is the flag you can use to control access to the partitions mounted by fstab.

As I said **umask** is the flag that sets the permissions to the partition.  It works by *removing* permissions from full access.  There are **three** parameters that are represented by a number.  Each number corresponds to a level of access; namely **read access, write access and execute access.**

The **first** number corresponds to the **file owner's** level of permission.  The file owner corresponds to the **uid**

The **second** number corresponds to the **group owner's** level of permission.  The group owner correpsonds to the **gid**

The **third number** corresponds to **everyone else's** level of permission.

A mounted partition starts with 777 as the permissions, meaning read/write/execute permission for owner/group owner/everyone else.  A umask equal to 000 means that permissions are unchanged.  A umask of 777 means *all* permissions are removed.

Here's a table for describing the way the permissions are removed (from the Gentoo Wiki - they describe everything in detail)
[QUOTE=Gentoo-Wiki]
umask: octal file permissions

You can change permissions using the parameter umask. But be aware that it must be the bitmask of permissions that are not present for the mountpoint. It is an octal number, formed like this:

* character '0': Indicates that this is an octal number, not decimal.
* first digit: owner user permissions
* second digit: owner group permissions
* third digit: world permissions (every other user on the system)

The modes are as follows (the first column is the mode octal number):

M | R W X
-------------
0 | * * *
1 | * * -
2 | * - *
3 | * - -
4 | - * *
5 | - * -
6 | - - *
7 | - - -

For example, if you want that everybody be able to read, write, and execute every file in your /mnt/c, you should specify the mask 0000: [/QUOTE]
I probably went over that a bit fast, so ask if you want more explanation.


[QUOTE=poiuytr]
Etcetera etcetera.  As you can see, I have many questions on this, probably more questions than the parent poster.  And I know, through some Googling and reading of man pages, I could probably eventually figure this out.  But if that document is an effort at a guide, it would be greatly appreciated if it strove to be a little more of a comprehensive guide, and explain the things that it is suggesting.[/QUOTE]
Well to be fair, he didn't ask for a guide, he asked how to browse his Windows partitons.  That link I originally gave him will mount them so he can achieve this.  It is meant for people who just want it done with minimum fuss.

If you want more detailed stuff...

[http://www.tuxfiles.org/linuxhelp/fstab.html]("http://www.tuxfiles.org/linuxhelp/fstab.html")
[http://www.tuxfiles.org/linuxhelp/mounting.html]("http://www.tuxfiles.org/linuxhelp/mounting.html")
[http://www.die.net/doc/linux/man/man5/fstab.5.html]("http://www.die.net/doc/linux/man/man5/fstab.5.html")
[http://www.die.net/doc/linux/man/man8/mount.8.html]("http://www.die.net/doc/linux/man/man8/mount.8.html")

---

### Post by poiuytr on 2006-02-10
Thank you so much, Sutekh, for all of this detail.  I will explore all of it - greatly appreciated!

---

