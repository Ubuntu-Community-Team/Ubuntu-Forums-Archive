---
title: "ubuntu install on ntfs ibm laptop"
date: 2006-01-21
forum: Absolute Beginner Talk
---

### Post by Daniel McLaws on 2006-01-21
I have ubuntu on my home desktop, and it works wonderfully. My work laptop has windows XP on an ntfs partitioned hardrive. I've heard horror stories with installing other linux distributions (mandriva) that it wiped out the hard drive when trying to install, I imagine during the re-partition phase of the installation. The hard drive actually had to be replaced.

Is there a great risk installing Ubuntu, or is that a problem with other distros. Other that backing up data is there some other precaution to take that would eliminate/reduce the risk; or there no problem with Ubuntu HD install? I do like Ubuntu/Gnome and would like to use it when I can when I travel with my work laptop (ibm thinkpad R40). Right now I use either Beatrix (kind of a Ubuntu live CD offshoot) or Gnoppix (cant save configuration on USB). If someone knows of a way to save Gnoppix (which is Ubuntu's demo live CD) configuration on a usb memory, that would be appreciated.

Thanks,
DJM

---

### Post by public_void on 2006-01-21
If you defrag your your hard drive under windows it should remove any fragmented sectors from the end of your drive. The install will partition your drive creating a ext3 and swap partition. I did it on my laptop and all when well, no problems. IMO there isn't anything to worry about. But do backup, even  if the install goes perfectly its good computer practice.

---

### Post by Daniel McLaws on 2006-01-21
I ran disk defragmenter from WXP, but it still shows on the bar sections of blue continuous files at both sides of the bar. Does that mean that files still exist all over the drive, rather than moved to the front ?

---

### Post by mips on 2006-01-21
IBM laptops are linux user friendly. Just do a search on this forum for your model and i'm sure you will find something. I think problems arise when people overwrite the IBM boot partition.

---

