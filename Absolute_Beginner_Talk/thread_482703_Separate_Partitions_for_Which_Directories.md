---
title: "Separate Partitions for Which Directories?"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by coldstatue on 2007-06-24
I just transfered my /home to it's own partition, and I feel safer, even though I wouldn't know how to be sure that partition was protected and used in a new install... or how to reinstall programs, but have them use the existing info stored in my new /home directory. I guess I'll figure that out if I *need* to. I am wondering if there are any other directories that should have their own partition, like /etc. Is there any benefit to doing this with any directory other than /home?

Thank you

---

### Post by alan_daniel on 2007-06-24
The most common directories that have their own partitions are /home and /boot, with everything else on /. There's also usually a swap partition that acts as the primary memory (similar to your RAM).

That said, it's not unheard of to have separate partitions for other directories, but most of the time it's not really necessary.

Do you have any kind of server running or any open ports that are accessible over the internet? If so, you may want to consider putting anything that might be uploaded to your computer on its own partition, but that's really the only other option I can think of.

---

### Post by coldstatue on 2007-06-26
No, no server or open ports. I have swap in it's own partition. I don't have boot in it's own because ubuntu went in after windows. I am using GRUB in the mbr of a  windows disk right now. Is there still a benefit of having a /boot partition? 

Soon, I will be taking the first (windows) physical hard drive out,. and adding another high-speed drive for Ubuntu media, but am a bit scared of what that will do with my device ids/booting.. I assume I will need to reinstall GRUB and fiddle with fstab with a live cd. guess I'm getting off topic here.

---

