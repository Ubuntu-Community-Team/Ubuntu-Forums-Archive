---
title: "EFI worries"
date: 2008-11-02
forum: Apple Hardware Users
---

### Post by Sonadow on 2008-11-02
Hi,i just installed Ubuntu Hardy on my Macbook late 2006.

But since i was not able to get Boot Camp to dual boot the system properly, i just decided to wipe the entire harddisk and install Ubuntu in it.

Now i, worried if by doing so, i will damage the EFI on the Macbook? Becuase in the event i need to reuse Mac OS X for my assignments, i need to be able to reinstall it quickly into my Macbook. And if the EFI is damaged, it's curtains.

Thanks in advance.

---

### Post by alwayshere on 2008-11-02
If ya get stuck ta could alwayds use virtualbox to install any other os you want 
have a look [http://www.virtualbox.org/wiki/VirtualBox](http://www.virtualbox.org/wiki/VirtualBox)

---

### Post by Sonadow on 2008-11-02
> **alwayshere said:**
> If ya get stuck ta could alwayds use virtualbox to install any other os you want 
have a look [http://www.virtualbox.org/wiki/VirtualBox](http://www.virtualbox.org/wiki/VirtualBox)
That's NOT the point.

If Ubuntu does something funny to the Macbook's EFI then im screwed if i try to reinstall OS X.

---

### Post by cyberdork33 on 2008-11-02
no you're fine. You just need to make sure to format the disk with DiskUtility on the Installation DVD before you can actually install.

---

### Post by Sonadow on 2008-11-02
> **cyberdork33 said:**
> no you're fine. You just need to make sure to format the disk with DiskUtility on the Installation DVD before you can actually install.

So that i can take it to mean that the EFI firmware is safe?

---

### Post by cyberdork33 on 2008-11-02
> **Sonadow said:**
> So that i can take it to mean that the EFI firmware is safe?
yea it has nothing to do with your EFI firmware unless you go find the tools to go mucking around with it.

---

### Post by Sonadow on 2008-11-03
> **cyberdork33 said:**
> yea it has nothing to do with your EFI firmware unless you go find the tools to go mucking around with it.

I see.

thanks very much! ^^

---

### Post by ronocdh on 2008-11-03
For anyone that's still not clear on this subject, EFI is really totally analogous to BIOS, just with improvements. Also, on BIOS systems, the hard drive will have an MBR, whereas EFI systems typically have a GPT, which is a more sophisticated partition scheme.

More info in wikiland....

[LIST=1]
[*][EFI]("http://en.wikipedia.org/wiki/Extensible_Firmware_Interface")
[*][BIOS]("http://en.wikipedia.org/wiki/BIOS")
[*][GPT]("http://en.wikipedia.org/wiki/GUID_Partition_Table")
[*][MBR]("http://en.wikipedia.org/wiki/Mbr")
[/LIST]
HTH.

---

