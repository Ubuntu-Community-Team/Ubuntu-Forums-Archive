---
title: "blacklist modules doesn't"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by davidsrsb on 2007-10-23
I am trying to solve some sound stutters and want to prevent some unused modem drivers from loading
 lsmod extract
snd_atiixp_modem       17160  0 
snd_via82xx_modem      16264  0 
snd_intel8x0m          18572  0 

I have modified /etc/modprobe.d/blacklist-modem
# Uncomment these entries in order to blacklist unwanted modem drivers
blacklist snd-atiixp-modem
blacklist snd-intel8x0m
blacklist snd-via82xx-modem

but these modules are still being loaded. How to block them?

---

### Post by ofb on 2007-10-24
I'd like to know why it doesn't work too.

I used rc.local to get around the problem. You might want to try that.
[http://ubuntuforums.org/showpost.php?p=3493364&postcount=11](http://ubuntuforums.org/showpost.php?p=3493364&postcount=11)

---

### Post by davidsrsb on 2007-10-24
Removing modules after loading is a horrible solution. This looks like a bug to me

---

### Post by ofb on 2007-10-25
I agree, but I also don't quite understand modules.d. 

For instance, the only reference to blacklist I can find is in the manpage for modprobe.conf:

>  blacklist modulename
Modules can contain their own aliases: usually these are aliases describing the devices they support, such as "pci:123...".  These "internal" aliases can be overridden by normal "alias" keywords,  but  there  are  cases where  two  or  more modules both support the same devices, or a module invalidly claims to support a device: the blacklist keyword indicates that all of a particular module&#8217;s internal aliases are to be ignored.

Why the emphasis on aliases? Ignoring all of a module's internal aliases isn't precisely the same as preventing a module from being loaded. **If** I read that correctly, then a module would still be loaded if it is called by its proper name, just not by any of its internal aliases.

---

### Post by cjbehm on 2007-10-25
> **davidsrsb said:**
> I am trying to solve some sound stutters and want to prevent some unused modem drivers from loading
 lsmod extract
snd_atiixp_modem       17160  0 
snd_via82xx_modem      16264  0 
snd_intel8x0m          18572  0 

I have modified /etc/modprobe.d/blacklist-modem
# Uncomment these entries in order to blacklist unwanted modem drivers
blacklist snd-atiixp-modem
blacklist snd-intel8x0m
blacklist snd-via82xx-modem

but these modules are still being loaded. How to block them?

I'd love to find out how to actually blacklist a module, too, since I don't have a floppy drive but it insists on loading the driver and adding a floppy in fstab. Luckily commenting it out of fstab fixes half the problem, but I can't find anything other than "blacklist floppy" should work.

---

