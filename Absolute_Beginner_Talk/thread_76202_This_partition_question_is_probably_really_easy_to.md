---
title: "This partition question is probably really easy to answer..."
date: 2005-10-14
forum: Absolute Beginner Talk
---

### Post by twoseids on 2005-10-14
On Hoary, I had hda6 as root and hda8 as /home. When installing Breezy, I deleted hda6 and formatted that one for the installation. Now, however, my /home isn't where it should be. Can you tell me what to do to fix it?

Here's my /etc/fstab from Hoary - the way I want it to work:

```
# /etc/fstab: static file system information. 
# 
# <file system> <mount point> <type> <options> <dump> <pass> 
proc /proc proc defaults 0 0 
/dev/hda6 / reiserfs defaults 0 1 
/dev/hda5 /boot ext3 defaults 0 2 
/dev/hda7 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 ro,user,noauto 0 0 
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0 
/dev/hda2 /media/windows ntfs ro,users,gid=users,umask=0002 0 0 
/dev/hda8 /home reiserfs defaults 1 2
```

But here's what I now have in Breezy.

```

# /etc/fstab: static file system information. 
# 
# <file system> <mount point> <type> <options> <dump> <pass> 
proc /proc proc defaults 0 0 
/dev/hda8 / reiserfs notail 0 1 
/dev/hda1 /media/hda1 vfat defaults 0 0 
/dev/hda2 /media/hda2 ntfs defaults 0 0 
/dev/hda5 /media/hda5 ext3 defaults 0 2 
/dev/hda7 /media/hda8 reiserfs defaults 0 2 
/dev/hda6 none swap sw 0 0 
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0 
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
```

Thanks for any help you can give me!

---

### Post by manicka on 2005-10-14
During install you need to tell the expert partitioner to use the same /home partition, but **not format it**. It doesn't do it automatically.

I'm not sure if you can fix it from here. You could try altering the fstab so that the home netry looks like your old one but I don't think that will do it.

anyone else?

---

### Post by twoseids on 2005-10-14
Yeah, I was kinda scared of touching my /home partition during the installation - so that's why I didn't - well, touch it!

So manicka, is that what you did? If you did that and it worked for you, I'll just do that myself. My Breezy is only hours old so I haven't tinkered too much yet - reinstalling would be a snap.

---

### Post by SilentCacophony on 2005-10-14
So, I see this:

hda6: was /, now is swap - I would think this would be a large swap space now
hda7: was swap, now is /media/hda7
hda8: was /home, now is / - this means that what files you had in /home are lost

I would think that the partition sizes are a bit sub-optimal, since they are all rearranged now. Since swap is a different filesystem, you can't just remount that elsewhere, either.

I'd have to say it'd probably be easier to reinstall at this point, myself.

EDIT -

Just thought I'd add a tip I learned from using the old DOS Ranish partition manager: write down your original partition setup, so there's no doubt which partition to assign to what next time.

---

### Post by twoseids on 2005-10-14
[QUOTE=SilentCacophony]So, I see this:

hda6: was /, now is swap - I would think this would be a large swap space now
hda7: was swap, now is /media/hda7
hda8: was /home, now is / - this means that what files you had in /home are lost

I would think that the partition sizes are a bit sub-optimal, since they are all rearranged now. Since swap is a different filesystem, you can't just remount that elsewhere, either.

I'd have to say it'd probably be easier to reinstall at this point, myself.

EDIT -

Just thought I'd add a tip I learned from using the old DOS Ranish partition manager: write down your original partition setup, so there's no doubt which partition to assign to what next time.[/QUOTE]
Not exactly. My /home still exists but is all under /media/hda8. So not all lost. But under System Settings --> Disk and Filesystems, it looks like what was FORMERLY hda 6 is now hda8, and what was hda8 is now hda7 (I'm guessing that from the partition sizes, which I know).

Does that help?

---

### Post by manicka on 2005-10-14
[QUOTE=twoseids]Yeah, I was kinda scared of touching my /home partition during the installation - so that's why I didn't - well, touch it!

So manicka, is that what you did? If you did that and it worked for you, I'll just do that myself. My Breezy is only hours old so I haven't tinkered too much yet - reinstalling would be a snap.[/QUOTE]

Yes that's what I did. You just need to relabel the partition as /home, but **don't format it**

---

### Post by manicka on 2005-10-14
make sure you back up just in case :)

---

### Post by twoseids on 2005-10-14
[QUOTE=manicka]Yes that's what I did. You just need to relabel the partition as /home, but **don't format it**[/QUOTE]

Okay, then I'll try it. I'll be back later!

---

### Post by twoseids on 2005-10-14
Bingo! I'm back in business.  Thanks manicka!

---

### Post by manicka on 2005-10-14
[QUOTE=twoseids]Bingo! I'm back in business.  Thanks manicka![/QUOTE]
Enjoy!

---

