---
title: "Feisty not working, Edgy works fine! (CD-ROM)"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by guysmiley25 on 2007-06-02
I tried installing Feisty onto a Hewlett Package Vectra, P3.

It complained about not being about to load the module or something like that for the CD-ROM, I can not remember now.

I managed to boot to a Edgy live CD. From there I did a Feisty install from the ISO.

Feisty installed fine, and is working, however it still cannot see my CD-ROM. However the Edgy Live CD could. The Feisty Live CD would not boot at all.

Anyone know how I can get the CD-ROM to work?

Thanks

---

### Post by freebird54 on 2007-06-02
I don't guarantee I can help - but with a machine of that vintage it is worth asking:  What method of hookup does the CD-ROM use?  Is it running on its own card?  Perhaps off a SCSI card?  Is it running as a slave to the HD?

This information might help in tracking the anomaly down....

---

### Post by guysmiley25 on 2007-06-02
To be honest I do not know. Is there anyway I can find out without opening the case?

I would suspect that it is running as a slave to the HD, but I do not know.

---

### Post by freebird54 on 2007-06-02
If it is running as a slave on the same line as the HDD, a close eye on the boot sequence text should let you know.  If it is a master or slave on another line, again it should be reported - perhaps 'drive found' and a description.

If it is a separate card, there will likely be some other 'banner' at boot up which will mention it as well.  Another test would be as follows...

```
cat /etc/fstab
```

if your CD drive shows up as hda, hdb, hdc, or hdd, then it is, respectively, master on IDE interface1, slave on interface 1, master on 2, or slave on 2.  This would also tell you.  If it comes up as sda, sdb it is likely to be on a SCSI card.  And, of course, if it doesn't show up we don't know much!  I guess it could be tried from the Edgy LiveCD in that case....

Beyond that, you're stuck opening the case after all (as far as I can thnk of at the moment, anyway)

---

### Post by guysmiley25 on 2007-06-05
During boot in all the text that shows up, This appears:
```

Fixed Disk 0; Maxtor 90640D3
ATAPI CD-ROM: SR243T

```

In edgy it showed up as hdc. So I guess that means it's a master on 2? Does that mean it's the master on the second IDE cable thing? I'm not sure sure about theses things I'm still learning.

When I try to install Feisty the normal way. When I get up to "Detect and mount CD-ROM" step. I get this message:
```

No common CD-ROM drive was detected.

You may need to load additional CD-ROM drivers from a driver floppy.
If you have such a floppy available now, put it in the drive, and
continue. Otherwise, you will be given the option to manually select
CD-ROM modules.

Load CD-ROM drivers from a driver floppy?

```

Edgy has no problems, when I tried to do an upgrade from edgy to feisty the CD-ROM will disappear.

Maybe there is away to find out what module I need in edgy, then download this driver floppy for it?

Any Ideas?

---

### Post by freebird54 on 2007-06-05
Well - first off you are right - that should be a master on port/cable 2.  Why it wouldn't pick it up is bit of a mystery though.  What is the module list it shows you after you decline to give it a floppy?  It MUST be in the list, as ATAPI has been around for ever....

Is there anything in that list that looks like a maybe?

---

### Post by guysmiley25 on 2007-06-05
Ok so I select No and got this message:
```

No common CD-ROM drive was detected.

Your CD-ROM drive may be an old Mitsumi or anther non-IDE, non-SCSI
CD-ROM drive. In that case you should choose which module to load and
the device to use. If you don't know which module and device are
needed, look for some documentation or try a network installation
instead of a CD-ROM installation.

Manually select a CD-ROM module and device?

```

So I select yes, and here are my choices:
```

none
cdrom
gscd
isp16
mcdx
optcd
sjcd
sonycd535

```

Randomly I chose mcdx and get this:
```

In order to access your CD-ROM drive, please enter the device file
that should be used. Non-standard CD-ROM drives use non-standard
device files (such as /dev/mcdx).

You may switch to the shell on the second terminal (Alt+F2) to check
the available devices in /dev with "ls /dev". You can return to this
screen by pressing ALT+F1.

Device file for accessing the CD-ROM:

```

Any ideas on what one I choose? or what I'm looking for is /dev?

I don't mind going though each module, but going though everything in /dev is a bit unrealistic.

Thanks heaps freebird.

---

### Post by freebird54 on 2007-06-05
Well - don't know why it isn't detecting it, but the most likely driver for that device is name **cdrom**.  Give that a try.  Beyond that I would recommend logging a bug report for this one - it should not happen...

---

### Post by guysmiley25 on 2007-06-05
Yes /dev/cdrom does not exist, and I think that is the probelm.

Thanks for all the help.

The part of feisty I like the most is the version of Xfce. do you know of a way I can keep edgy, but have the lastest version of xfce?

I have a thread [here]("http://ubuntuforums.org/showthread.php?t=463827").

If anyone else out there has the same problem, if I find a solution I will post it here.

Thanks.

---

### Post by freebird54 on 2007-06-05
Is there any reason you can't grab that file elsewhere, and put it on?  For instance, it could be the one in* /lib/modules/2.6.17-11-generic/kernel/drivers/cdrom* - if you dump that in /dev/ it might work!

Let me know what you find...

---

