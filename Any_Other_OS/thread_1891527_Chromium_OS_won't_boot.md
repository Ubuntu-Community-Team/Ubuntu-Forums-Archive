---
title: "Chromium OS won't boot"
date: 2011-12-05
forum: Any Other OS
---

### Post by Mars11 on 2011-12-05
I have Chromium OS installed on my SSD. When I boot from the SSD it just gives me a "sh:grub>" command line thingy. The SSD is sdb while the HDD is sda. I'm guessing Chromium OS isn't supposed to be installed on sdb and that would be why I'm getting these problems. [You can look at the grub.cfg here.]("http://dl.dropbox.com/u/16007317/Projects/Chrome%20OS/grub.cfg") Does anyone know what would I change in the grub.cfg file to fix this?

Note: I know that Chromium OS runs on this system because I can successfully run it off of a flash drive.

---

### Post by cbowman57 on 2011-12-05
Let me know what you discover, I recently tried the standard & the Lime version, both bombed out on boot.

---

### Post by Mars11 on 2011-12-05
Do you have a similar configuration to mine? With two hard drives?

---

### Post by cbowman57 on 2011-12-05
Two hard drives, but not SSD.

I just decided to give it a try the other day so I dd'ed it to thumb drive, hung as soon as it left grub.

Thought maybe it was a bad iso & the Lime edition had some features I wanted to try so grabbed that, same result.  I'm really curious to check it out.

---

### Post by Mars11 on 2011-12-05
I can successfully boot from a flash drive, it's when I install it to the SSD it gives me the sh:grub> command line.

---

### Post by cbowman57 on 2011-12-05
Oh well, at least yours boots from the flash drive, I was beginning to wonder if it worked for anybody.

---

### Post by Mars11 on 2011-12-05
I would be fine with it booting from a flash drive if it didn't freeze up every 30 seconds. I'm hoping that if I get it to boot from the SSD I won't get so much freezing up. You could try doing [this]("http://kfalck.net/2010/08/22/if-your-chromium-os-image-doesnt-boot"). I heard that might help with your situation.

---

### Post by wolfen69 on 2011-12-05
> **Mars11 said:**
> I would be fine with it booting from a flash drive if it didn't freeze up every 30 seconds. I'm hoping that if I get it to boot from the SSD I won't get so much freezing up. You could try doing [this]("http://kfalck.net/2010/08/22/if-your-chromium-os-image-doesnt-boot"). I heard that might help with your situation.

It *may* be a bad drive, as this has been known to happen. As someone who tracks newegg comments and reviews, even the big companies screw up. ;) Hardware can be as much to blame as the software, if not more.

---

### Post by Mars11 on 2011-12-05
I'm guessing it's just the slowness of the flash drive. My SSD is about 10 times as fast. And the SSD isn't bad. I've used it to boot other OSs. I talked to Hexxeh and he said that I needed to change the grub.cfg, but he didn't tell me what to change.

---

### Post by bluexrider on 2011-12-05
did you look at the instructions here:

[http://chromeos.hexxeh.net/wiki/doku.php?id=multiboot](http://chromeos.hexxeh.net/wiki/doku.php?id=multiboot)

---

### Post by Mars11 on 2011-12-05
That's not what I'm trying to do. This has nothing to do with Dual-Booting, I just installed it on a different drive than it's set up for.

---

### Post by Mars11 on 2011-12-06
Sorry for the double post. I was pointed to [this link]("https://groups.google.com/a/chromium.org/group/chromium-os-reviews/msg/d3d586435d36fb1a?pli=1"). I'm not sure if it helps. I couldn't get anything to work after playing around with the grub.cfg. Anyone an expert grub user?

---

### Post by Mars11 on 2011-12-08
Well, the simplest way is to have GRUB on the other drive and then running "sudo grub-update" from the Linux distro on the second drive. It should then show up on the GRUB menu. Hope this helps... If you need a guide on this just ask.

---

