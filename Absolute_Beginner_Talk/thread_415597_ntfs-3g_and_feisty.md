---
title: "ntfs-3g and feisty"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by weedwacker on 2007-04-20
I'm tempted to try ntfs-3g on my feisty upgrade from edgy.

With ntfs-3g I could set up mounting on my fstab (?) AND rename my four windows partitions.

Although feisty shows my windows partitions, I found it necessary to rename them by booting back into windows and in explorer right click on each disc and click "Rename."  I could not use the rename process explained in the community help pages.

Speaking of the fstab.... when I call it up it does not list my windows drives.  Only the Ubuntu drives.

Editing fstab does not work for me.  Editing blocks me from accessing windows drives.  Tells me I am not root.  Or some such.

So, my renaming, as described above, now works, but I have to enter my password when I "mount" my windows drives from "Places>Home Folder."  Once mounted here, no prob.

But it seems ntfs-3g was SO MUCH EASIER.

Does anyone know if it's OK to use ntfs-3g on feisty? :popcorn:

---

### Post by weedwacker on 2007-04-21
Never mind... got my answer here... and it worked for me!
**[COLOR="Blue"]https://help.ubuntu.com/community/MountingWindowsPartitions[/COLOR]**

<snip>
**For NTFS partitions**

Ubuntu 7.04 can read and write files on the NTFS drives commonly used by Windows.  [COLOR="Red"](I could read/copy from, but not write/paste to my windows drives!)
[/COLOR]
Ubuntu 6.06 LTS and 6.10 came with older, beta versions of the NTFS 3G driver. These worked well for many users but were not guaranteed to be stable. Use Ubuntu 7.04 for stable access to NTFS partitions. Alternatively, a stable version of NTFS 3G for older versions of Ubuntu can be obtained from a third-party software repository - see using a third-party NTFS 3G.

       Enable the universe repository and install the ntfs-config package. See Installing Software.
 
      Click Applications &#8594; System Tools &#8594; NTFS Configuration Tool
 
      The upcoming tool will detect NTFS partitions on your system. Check each partition you wish to access, and, if you wish to, click the mount directory to change it. When finished, click Apply.
   
      On the next screen Enable write support for internal device will be selected by default. Click OK.

Your NTFS drive will be now be available in the mount point you selected.

<snip>

[COLOR="Red"]Get the **NTFS-CONFIG** package from Systems>Administration>Synaptic Package Manager
Accept no substitutes.  This one works!  The other directions in the Help/Guides were no help for me.[/COLOR] :KS :KS :KS :KS :KS

---

### Post by chakkaradeep on 2007-04-21
I used automatix2 to install the windows drivers and it did all the job and now i get all partitions mounted at the startup with writable permissions.

Why dont you try automatix2 once?

---

### Post by Jormanks on 2007-04-21
I just.... can't....

tried ntfs-config and automatix, but still one partition doesn't have writable access and the other one is, apparently, with no available space.... but it's not true...

---

### Post by braveerudite on 2007-04-21
I also can't get writeble acces to my external USB HDD Someone please help.

---

