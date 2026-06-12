---
title: "xorg blew up and THEN"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2007-01-28
Yikes, now I'm panicking. 

While following a post about fixing the ALSA, I received some help to:

sudo dkpg --reconfigure xserver-xorg

That had to be done from the command line. After rebooting and selecting recovery mode and sudo-ing the above, I came across the following (which I paste below, verbatim):

From the recovery boot in dapper

* Setting up LVM [ok]
* Checking all filesystems ...

fsck.ext3: No such file or directory while trying to open /dev/hdb1 /dev/hdb1

The superblock could not be read or does not describe a correct ext2 filesystem. If the device is valid and it really contains an ext2 filesystem (and not swap or UFS or something else), then the superblock is corrupt and you might try running e2fsck with an alternate superblock:
       e2fsck -b 8193 <device>

[COLOR="Red"]*[/COLOR] File system check failed. Please repair manually.
[COLOR="Red"]*[/COLOR] CONTROL-D willexit from this shell and continue system startup

Root@Lex:~#

---

### Post by Shatrat on 2007-01-28
This looks like it is a hardware problem, possibly a dead or dying drive, /hdb.

---

### Post by goatflyer on 2007-01-28
1) you mistyped dpkg-reconfigure.  There is only 1 hyphen, and no space.

2) If you abandoned the thread where people were helping you, then don't expect those people to follow you here, ie. its considered bad manners to cross post the same problem.


Much luck to you.

---

### Post by Mark_in_Hollywood on 2007-01-28
Yea, I'm confused as to why it read /dev/hdb, since it's sitting on the cable as /dev/hda, so in order to try to clarify ALL this:

Months ago, I added a 2nd harddisk. That 2nd disk had Dapper installed from the Canonical CD. That's what I call a clean install, not an upgrade (as in misscrowsoft). After that disk was "working", I added the broken harddisk back to the ide cable as the slave. By broken, I mean that the xserver was blown up, if I remember correctly.

After transferring the /home to the newly installed primary master, the harddrives were switched to that what had been master was now slave and vice-versa.

Then the /home was moved back to the primary master.

Months went by, I still couldn't fix the modem problem, so I got another modem and now that problem is gone.

I started working on the sound. No sound program that can "tune-in" a radio station would play without stuttering or sounding choppy. I was following a post titled: Comprehensive sound problem, or some such title when I got to commands using apt-get to remove alsa and then reinstall it. As I watched the remove process, I saw it removed many pieces of ubuntu that seemed to have nothing to do with alsa. But then I'm no programmer. When I did the apt-get install alsa, again, following the post, I rebooted only to get a ruined xserver-xorg.

Using the liveCD, I got back to this forum and am posting and following here, but every time I have to do a re-boot, I then have to completely configure wvdial and such. I'm not asking for sympathy only understanding.

If the disk is going bad it would be an anomaly and I'm holding off on following that:

as for goatflyer and his post:

1) you mistyped dpkg-reconfigure. There is only 1 hyphen, and no space.

[COLOR="Red"]I did not mistype the command at the command line, only here in reporting it at the forum[/COLOR]

2) If you abandoned the thread where people were helping you, then don't expect those people to follow you here, ie. its considered bad manners to cross post the same problem.

[COLOR="Red"]As far as my limited understanding of linux programming goes, this very much seems to be a problem unrelated to xorg. BUT, if it is related, and you find yourself reading this and knowing what I dont', please forgive me. Yikes! I'm really distressed by this computer stuff at the moment. More than 24 hours, really. [/COLOR]

---

