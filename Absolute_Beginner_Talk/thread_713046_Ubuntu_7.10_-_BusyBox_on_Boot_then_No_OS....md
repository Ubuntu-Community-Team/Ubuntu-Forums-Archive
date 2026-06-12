---
title: "Ubuntu 7.10 - BusyBox on Boot then No OS..."
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by DaltonAdair on 2008-03-02
I would like to start right off the bat by thanking you guys for taking time outta your day to help me out.
:D

Secondly, I am a complete newbie to anything Linux. (I have been using Windows and Mac for nearly 8 years)

So here is my issue:

After installing Ubuntu 7.10 onto my hardrive, (more details below) I restart my machine and try to boot Ubuntu. Instead of using GRUB to choose a OS, NT Loader appears. However, I can succesfully start to boot Ubuntu. After a breif moment of loading it crashes and comes to BusyBox.

Ya know, that whole (initramfs) _ deal that pretty much loops you no matter what you do.

I checked my ISO with MDK5SUM and it's good, so I know I don't have a bad file. 

My PC is:
A heavily modified eMachine:

Intel 8000 series onboard graphics controller and chipset
768MiB DDR RAM
Intel Celeron @ 2.6GHz
2 Wester Digital Caviar HDDs, HDD 0 is 40GB, HDD 1 is ~20GB.

Partitions:
On each HDD I have one NTFS partition, one ex2 partition, and one swap partition. The NTFS partitions take up roughly 45% on each hardrive, and the Linuxy partitions the rest.

Also, after rebooting my machine after BusyBox shows up, it tells me there is no operating system. :(

This is more of a project than an urgent matter, so take your time guys. I will also be digging around and if I find a proposed solution that works (as I know several times this has happened to others) I will post letting you all know.

---

### Post by DaltonAdair on 2008-03-02
Heres something I noticed in a little expirimentation:

The MBR on my machine is getting pwned somehow. I ran the XP Recovery Console to do some snooping around, and found that it was damaged. 

Also, the boot sector looks all fuddled up as well, so I wrote a new one but it made no difference. (FIXBOOT)

I am afraid to write a new MBR cause that could put my partitions out of whack. But, I am thinking I will run it so I can at least boot back to windows. (I have used this solution before succesfully.)

Sounds silly trying to use Windows to fix Linux, doesnt it? Thats all I got right now though.

---

### Post by DaltonAdair on 2008-03-02
*BUMP* of desperation.

---

### Post by DaltonAdair on 2008-03-02
Alright, after some screwing around and research I tried the following prescribed solutions:

In BusyBox, enter the command " modprobe ide_core "
That command was recognized and returned a message about IDE settings. Didnt seem to change anything. So, I entered all_generic_ide, which was an unrecognized command. (Put in a GRUB line perhaps?)

After trying that to no avail, I found that editting "quiet splash" to "nosplash" in one of the lines of code for boot was a possible fix.

I tried that, and it skipped the first splash screen like I expected. Awesome. A text rundown of the boot showed up, and then it showed another Ubuntu splash which displayed under it what it was doing. Awesome.

Then it froze on loading some casper scripts? Not sure what those are. (Remember, total linux noob. I have been using Windows for almost ten years.)

After it hung for a bit, it went straight into BusyBox again. What the hell?

Another thing I noticed: When I pick Ubuntu-Linux from NT Loader, it shows a message that says "Attempting to open gate A20... success" and then under that "Press ESC to open menu...2" which counts down to one. Unless I press ESC, it will run right into BusyBox, otherwise it loads into GRUB (or what I think might be GRUB).

Please lend me a hand here guys.

Also, is there a way to install Ubuntu without having to run Wubi in Windows? Can I just install on a clean hard-drive standalone? I am thinking Windows may have something to do with all this nonsense.

---

### Post by goma on 2008-03-02
It happened to me when suddenly a BusyBox appeared on my screen. I don't know what happened.. I just inserted Ubuntu Live CD and reinstall.

---

### Post by DaltonAdair on 2008-03-02
No format and whatnot? I will give it a shot and let you know.

---

### Post by goma on 2008-03-02
I am thinking you have your Ubuntu Live CD and boot from it. You should be able to see an Ubuntu installation interface. Boot from cd.

---

### Post by DaltonAdair on 2008-03-02
Right. I am running the install right now.

Here is what I am doing different, though:

Before, I had Ubuntu installed on the same disk as Windows. Now, I am going to try to install it on a seperate disk. Windows gets a whole HDD, Ubuntu gets a whole HDD. 

I will post up the results soon...

---

### Post by DaltonAdair on 2008-03-02
OK, finished reinstall with above mentioned parameters and still get knocked into BusyBox. I am going to try the two edits listed above to and then make another post detailing whether or not it worked.

---

### Post by DaltonAdair on 2008-03-02
modprobe ide_core does nothing now.

I changed quiet splash to no splash, and booted.

It got to this line, and looped for a good bit until it started up busybox... again...

```

[  100.632911] EXT3-fs: mounted filesystem with ordered data mode.
[  102.054291] end_request: I/O error, dev fd0, sector 0
[  104.148457] kjournald starting. Commit interval 5 seconds.

```

It loops this until the incrememnt reaches 114.750234 and then hits busybox.
Now what?

---

### Post by Sef on 2008-03-02
Check out this [thread]("http://ubuntuforums.org/showthread.php?t=474693&highlight=BusyBox+v1.1.1").

---

### Post by DaltonAdair on 2008-03-02
Thanks for trying to help.

After I insert live break=top into the line and boot, I get this

```

Loading, please wait...
Spawining shell within the initramfs

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built in shell (ash)

(initramfs) _

```

So I entered in modprobe piix, which returned this:

```

(initramfs) modprobe piix
FATAL: Module piix not found.
(initramfs)_

```

Sigh... I am > < this close to giving up.

---

