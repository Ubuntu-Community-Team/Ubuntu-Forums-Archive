---
title: "how to delete xp partition"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by jplbrmo on 2007-11-24
been doing the dual boot thing and wonder if i can just delete windows and use that space ,or would it be better to do a fresh install of Ubuntu.

                                                                           thanx.

---

### Post by pdlethbridge on 2007-11-24
I did a fresh install when I dropped XP. That way I could give my home partition 10 gigs, swap 1 gig and / the balance.

---

### Post by taurus on 2007-11-24
You can just delete and format that partition to ext3.  Then, mount it somewhere as a storage if you wish.  

You first need to unmount it and then use gparted in System -> Administration (install it if you don't have it on your machine) to format it.

---

### Post by gaylapdancer on 2007-11-24
If you use the GParted live cd, you can delete the windows partition then stretch your storage partition over it, or you could just make it as a separate storage partition.

---

### Post by jplbrmo on 2007-11-24
thanx to all for the info and for the quick replies

---

### Post by fourscore on 2007-11-25
Unless you are pressed for   disk space my advice would be to retain the XP partition.     I also have a dual boot setup ( on my HP laptop)   XP & Ubuntu and there are times  when  XP comes handy.

---

### Post by Taboo Mirage on 2007-11-25
I would suggest virtualization over straight dual booting if your situation allows it.  It's a lot more convenient to open Windows in VirtualBox rather than having to reboot to switch OS all of the time.

As for the OP's issue, I'd also recommend checking out the GParted LiveCD to delete the NTFS partition and expanding the ext3 partition mounted at /home to the end of the drive.  Of course I'd recommend backing up any crucial files before you start messing around with partitioning, but that goes without saying.

Take care.

---

