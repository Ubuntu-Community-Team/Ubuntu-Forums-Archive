---
title: "Partitioning and NTFS -- Can you verify migration plan?"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by VanillaMozilla on 2007-12-27
Coming from XP, I would like to install a Ubuntu partition and share data.  The main purpose is better Internet security, plus ??.  I have several questions.  Maybe you can see if I understand this correctly and set me straight if necessary, *before* I botch it.

I have 7 GB of data on an 8 GB disc (NTFS), plus one new 80 GB disc.

Here's the plan.
1. Clone the XP disc to the new disc with Norton Ghost.
2. Using the Ubuntu live CD, create one or more Linux ext3 partitions with GPartEd.  (Can I do this from the live CD?)
3. Install Ubuntu from the live CD.
4. Share data either as NTFS or FAT32.
    To convert data to FAT32, I could just copy it to a FAT32 partition.

    I understand that the Ubuntu ntfs driver does not support writing, so I would need to install ntfs-3g if I want to share from the NTFS partition.  Or I could install the Windows FS-Driver and share data on the ext3 partition.

Question 1:  Are both of those drivers bullet-proof?  Is there any serious performance drawback to either (except for file permissions)?

Question 2:  The FS-Driver does not know about file permissions.  Is this a security hazard?  Could a Windows program then modify the Linux system?

Question 3:  I hate partitioning a hard drive into itty-bitty pieces.  (/root, /home, /boot, Windows, FAT32 is a lotta partitions.)  Is it easy to move partitions later?

Does this sound like a plan?  Thanks.

---

### Post by Paulmd on 2007-12-27
> **VanillaMozilla said:**
> Coming from XP, I would like to install a Ubuntu partition and share data.  The main purpose is better Internet security, plus ??.  I have several questions.  Maybe you can see if I understand this correctly and set me straight if necessary, *before* I botch it.

I have 7 GB of data on an 8 GB disc (NTFS), plus one new 80 GB disc.

Here's the plan.
1. Clone the XP disc to the new disc with Norton Ghost.
2. Using the Ubuntu live CD, create one or more Linux ext3 partitions with GPartEd.  (Can I do this from the live CD?)
3. Install Ubuntu from the live CD.
4. Share data either as NTFS or FAT32.
    To convert data to FAT32, I could just copy it to a FAT32 partition.

    I understand that the Ubuntu ntfs driver does not support writing, so I would need to install ntfs-3g if I want to share from the NTFS partition.  Or I could install the Windows FS-Driver and share data on the ext3 partition.

Question 1:  Are both of those drivers bullet-proof?  Is there any serious performance drawback to either (except for file permissions)?

Question 2:  The FS-Driver does not know about file permissions.  Is this a security hazard?  Could a Windows program then modify the Linux system?

Question 3:  I hate partitioning a hard drive into itty-bitty pieces.  (/root, /home, /boot, Windows, FAT32 is a lotta partitions.)  Is it easy to move partitions later?

Does this sound like a plan?  Thanks.

The Plan: 
1) Ghost will work fine. There are Linux alternatives, too. Gparted can clone as well. But use the tools you are most comfortable with. 

2+3 ) The install script on the live cd takes care of partitioning.

4) fat32 is supported natively by both windows and linux. It is probably the least hassle option. 

the Questions:

1) I would not assume that the drivers are bullet proof.  The developers of NTFS-3g have declared it stable as of feb 07.

2) Yes, it's a security hazard. You get to decide how much risk you are willing to take.

3) Moving and resizing partitions is a non-trivial task, with a risk of losing your data. Gparted can do this, pretty good. There is live-cd version of gparted that would be better to use for a task like this, rather than trying to run it from within the operating system.

---

### Post by agurk on 2007-12-27
Sounds like a solid plan to me, just a few comments on some of your point::

1. Instead of Norton Ghost, you can probably use a Linux based [GParted Live CD](http://gparted-livecd.tuxfamily.org) to copy and resize your XP NTFS partition.
2. Yes, a partition editor/creator is included in the installer.

Answer 1: Correct, you need ntfs-3g (available in the repo) to write to your NTFS partition. I have used it for two years without any problems, nothing whatsoever to complain about there. As for the Windows ext2 driver, I have no personal experience.

Answer 2: Well, using Linux, you can delete or edit every Windows file, and vice versa. I wouldn't call it a security hazard though.

Answer 3: Yes, you can create these partitions later if you wish, you can even put them on separate hard disks (google for "move home partition"). Myself, I just use a single root partition and a swap partition, that's it.

---

### Post by VanillaMozilla on 2007-12-27
Thanks for your speedy and thoughtful replies.  I'll give it a try.

---

### Post by VanillaMozilla on 2007-12-28
It worked, mostly, but I'm left a bit desperate to be able to write files.:)

In order of importance, how do I:

1. Get and install ntfs-3g so I can write on my NTFS disk, where all my files are stored?  Add/Remove doesn't show ntfs-3g.

2. Write to removable media?  Like a USB drive, for example?

3. Give myself permission to write to the system disk (ext3)?  I can write to home/my directory, but probably nowhere else.

I have limited UNIX experience -- enough to know that searching man pages is mostly an exercise in futility.if I want to get this done before 2008.  Thanks.  :)

---

### Post by Paulmd on 2007-12-28
> **VanillaMozilla said:**
> It worked, mostly, but I'm left a bit desperate to be able to write files.:)

In order of importance, how do I:

1. Get and install ntfs-3g so I can write on my NTFS disk, where all my files are stored?  Add/Remove doesn't show ntfs-3g.

2. Write to removable media?  Like a USB drive, for example?

3. Give myself permission to write to the system disk (ext3)?  I can write to home/my directory, but probably nowhere else.

I have limited UNIX experience -- enough to know that searching man pages is mostly an exercise in futility.if I want to get this done before 2008.  Thanks.  :)

1) ntfs-3g should be incorporated in the latest release of Ubuntu. In case it's not:

```
sudo apt-get install ntfs-3g
```

1a) the windows disks may be mounted under /media

2) Removable media is a broad category. The disks are usually automounted in/media.
to burn CDS, install k3b or another cd burning program. Flash disks and external hard drives, when mounted, give you an icon on the desktop. You can also access them under the PLACES menu.

3) you shouldn't need to write to system files on a regular basis, so I'd advise against giving yourself blanket permission. Just use sudo when you need it.

---

### Post by VanillaMozilla on 2007-12-29
**EDIT:  It all boils down to #2 below.  How do I permanently enable Read/write access to the ntfs volumes for nonprivileged accounts?  I don't have a clue here.**


EDIT:  the very long version:
==========================
Thanks.  A bit of progress, but I am an absolute beginner at *nix, and this stuff isn't exactly spelled out in neon letters in the documentation.  Critical questions remain.  To wit:

> **Paulmd said:**
> 1) ntfs-3g should be incorporated in the latest release of Ubuntu.
1. OK, it looks like it might be.  I managed to set the file system to ntfs-3g in the Volume tab of properties.  That got me Read/write access even though the Permissions tab says I don't have it.  I think that means I haven't really been able to change permission, :confused: but ntfs-3g doesn't support file permission.  ???

I hope that's really ntfs-3g.  Don't want to risk a meltdown.

2. But I still can't figure out how to get Read/write access from a nonprivileged account unless I have mount it from the administrative account and switch users.  :confused:

> **Paulmd said:**
> 1a) the windows disks may be mounted under /media
If this helps the case, here are the properties of one mounted disk at the moment:
Location:  computer:///
Filesystem type:  ntfs
Owner:  unknown
Label:  System disk
Mount point:  /media/System disk
File System:  fuseblk [whatever that is]
Mount Options:  rw nosuid nodev noatime user_id=0 group_id=0 allow_other

> **Paulmd said:**
> 2) Removable media is a broad category. The disks are usually automounted in/media
Problem may have solved itself.  I was referring to a USB Flash drive, but I seem to have Write permission at the moment.  I thought I didn't.

> **Paulmd said:**
> 3) you shouldn't need to write to system files on a regular basis, so I'd advise against giving yourself blanket permission. Just use sudo when you need it.
I managed to figure out
sudo gedit
and
sudo rm, sudo rd, etc., but more complicated commands will be a challange.

---

### Post by Paulmd on 2007-12-29
[QUOTE=VanillaMozilla;4032866]**EDIT:  It all boils down to #2 below.  How do I permanently enable Read/write access to the ntfs volumes for nonprivileged accounts?  I don't have a clue here.**


I'm not sure about that. I have it here, for my one-account system. What happens when you try to write to it?

It may be that you can write to some folders but not others. Can you test that?

---

### Post by maybeway36 on 2007-12-29
Add the accounts to plugdev, I suppose.

---

### Post by VanillaMozilla on 2007-12-30
plugdev?  Help documentation doesn't show anything about it.  Looking at user groups, there are lots and lots of names, but plugdev isn't one of them.  Even if I could implement it correctly, I have no documentation on what this actually does.  Can you explain further?

Using Google, I did find this:
"We solved (4) by introducing a new group called 'plugdev'. Every user
who is a member of this group can access hotpluggable devices (digital
cameras, USB drives etc.)."
[http://lists.debian.org/debian-devel/2004/11/msg00201.html](http://lists.debian.org/debian-devel/2004/11/msg00201.html)

Well, these are fixed hard drives, not hotpluggable devices, but maybe it would work.  I'm a little unsure of just trying black magic at random.

I also found this:
[http://ubuntuforums.org/showthread.php?t=526903](http://ubuntuforums.org/showthread.php?t=526903) (see message 4).  fstab sets mount options for all users at boot time, right?  Now if I only knew where the documentation was.

FYI I'll tell you what I have tried so far.
1. Tried editing user privilege to allow access to external storage (not external, and this doesn't work anyway).

2. Tried editing Permissions in disk properties tab.  Not grayed out, but can't reset permission.  No explanation is given.

Now there's a new problem.  I had set file system to ntfs-3g, but that setting doesn't persist through a reboot.

Gee, I thought this should be easy, but they sure don't make it simple.  I'll reiterate the requirements, and they're pretty simple.
1. I need to set NTFS volumes for automatic read/write access by any user.
2. The volumes should be mounted automatically at boot/login, or alternatively, nonadministrative users should be able to mount them easily.

Not essential at this time, but very helpful:
3. It would be very nice if I could find some documentation, so I could (a) be confident; and (b) solve the next, slight variation on the problem for myself.
4. I have no idea where the documentation is for devplug, mount options, or for parameters in fstab.

Thanks.

---

### Post by VanillaMozilla on 2007-12-30
> **Paulmd said:**
> I have it here, for my one-account system. What happens when you try to write to it?

It may be that you can write to some folders but not others. Can you test that?
These are NTFS volumes.  I have write access if I set the file system to ntfs-3g and mount from an administrative account.  But, (1) I can't mount or set the file system from a general user (nonprivileged) account, and (2) the file system reverts to ntfs (readonly) on rebooting.

---

### Post by Paulmd on 2007-12-30
> **VanillaMozilla said:**
> These are NTFS volumes.  I have write access if I set the file system to ntfs-3g and mount from an administrative account.  But, (1) I can't mount or set the file system from a general user (nonprivileged) account, and (2) the file system reverts to ntfs (readonly) on rebooting.


first, I'm a bit out of my depth, but a bit of googling has turned up a text file called "fstab". 

[http://en.wikipedia.org/wiki/Fstab](http://en.wikipedia.org/wiki/Fstab)

It controls what is mounted where, and who has access to everything.

it can be edited with a standard text editor, but it requires root permissions to save changes. 
```
sudo pico /etc/fstab
```

*you can replace pico with gedit, if you want a more graphical editor.

[COLOR="Red"]edit: please make a backup copy of this file prior to editing it.[/COLOR]

the part you want to pay attention to is

"
user / nouser
    Permit any user to mount the filesystem. This automatically implies noexec, nosuid, nodev unless overridden. If nouser is specified, only root can mount the filesystem.
defaults
    Use default settings. Equivalent to rw,suid,dev,exec,auto,nouser,async.
"

 
There is a more in-depth tutorial here

[http://ubuntuforums.org/showthread.php?p=1653968#poststop](http://ubuntuforums.org/showthread.php?p=1653968#poststop)

---

### Post by eternicode on 2007-12-30
/etc/fstab defines "mount rules", if you will, for various volumes.  It defines what gets mounted where, and who can do the (un)mounting.

The format for a mount rule is
```
<device> <mount-point> <fs-type> <options> <dump> <pass>
```

I'm not sure what the "dump" and "pass" options are for.

Some options as I understand them, from my ntfs-3g mount:
"auto" gets mounted upon boot.  Also allows mounting with "mount -a"
"users" allows all non-privileged users to mount/unmount the volume.
"fmask" sets the default file permissions for all files on the mounted system.
"dmask" sets the default file permissions for all directories.

In the fstab (back it up first!), you want to add a new line (or modify an existing line) to have your NTFS volume mounted at boot with full read/write permissions.  Here's the line I use to mount my NTFS volume:
```
# windows
/dev/sda2  /media/windows  ntfs-3g auto,users,silent,fmask=0000,dmask=0000,utf8=true 0 0
```
The fmask=0000 gives full ("world") read/write access to the drive.  dmask=0000 does the same for directories.  This is not the "most secure" setup, but it does work.  The main reason I do it that way is because it auto-mounts at boot-time under the ownership of root.
I'm not sure how the device properties dialogue interacts with fstab.

---

### Post by VanillaMozilla on 2008-01-08
Thanks for all the information.  I haven't quit on this.  I just have a lot of other problems to solve as well, and it's going to take me a while to grind through all of this and get it right (since my mount commands are so different from eternicode's).  It looks like the information will work, however.

---

