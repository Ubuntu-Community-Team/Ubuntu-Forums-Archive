---
title: "Error 17"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by nickej on 2007-07-18
I've tried using Ubuntu several times now (since Dapper) only to be frustrated by difficulties related to my ATI card. Envy won't work, nor will three other attempts to get OpenGL to work manually. This makes the whole exercise pointless, since my main reason is to use Blender, which crashes and burns without OpenGL.

Anyhow, I'd installed Feisty on a separate disk from my primary install of Win2K. When I rebooted to Win, I reformatted the Ubuntu drive to clear the decks, but now when I restart, I get a GRUB Error 17. I've tried rebooting from the Win disk and rewriting the boot sector, but to no avail, immediately after BIOS, it's off to frozen uselessness with GRUB. Any ideas on how to ditch GRUB, or at least let me get back to my Win install without having to reformat and reinstall?

---

### Post by jombeewoof on 2007-07-18
what file system did you format /dev/hda1

might as well tell us your exact partition scheme and file systems used actually.

```

Error 17 indicates GRUB can't id the partition type. Check http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting for more info. Here is the relevant entry:
"17 : Cannot mount selected partition
This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB."
```

---

### Post by nickej on 2007-07-18
I've temporarily ameliorated the problem by re-installing Feisty where GRUB expected it to be. Now I just get the standard OS choices after the BIOS screens. This is fine since I'm going to want to keep experimenting with Linux for the foreseeable future (I've just ordered a book on using terminal scripting). At the moment, Win2K is on local disk C, Ubuntu on Local Disk D. That would be hda and hdb, I guess. The Ubuntu install was straight from the ISO and then updated. The install did the formatting for whole disk. It's not directly accessible through Windows, and I'm honestly not sure how to access drive information yet in Ubuntu, but as I recall, the setup previously was to break the disk down into a 77GB section and a 3 GB section, which is where I presume the OS lives.That would thus be hdb1?

---

