---
title: "Triple Boot + VMWare Fusion Questions"
date: 2007-07-24
forum: Apple Intel Users
---

### Post by jmacdonagh on 2007-07-24
I just got a new MacBook Pro and would like to start the process of triple booting my machine.

I found the HOWTO here:

[http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu](http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu)

and I understand the process. I assume that this is the most up-to-date howto, even though it focuses on Dapper and Edgy.

I know that VMWare Fusion has the ability to virtualize Bootcamp partitions ([http://en.wikipedia.org/wiki/VMware_Fusion](http://en.wikipedia.org/wiki/VMware_Fusion)), and I'm wondering if following the process above will give me the same feature. All mentions of this feature of VMWare (and Parallels) say "Bootcamp" partition. However, in the howto, we skip using the BootCamp Utility to create a partition. I didn't know if the Bootcamp Utility somehow labeled its created partition, or if VMWare Fusion simply scanned all partitions looking for one with Windows installed.

So, I guess my question is, has anyone who has gotten triple booting working with rEFIt also been able to virtualize their Windows XP partition using VMWare Fusion? I understand that Fusion doesnt support the Ubuntu partition yet.

Thanks!

---

### Post by jmacdonagh on 2007-07-24
After researching on the VMWare Fusion forums (should have started there first ;) ), it looks like it is possible. Apparently Fusion just scans partitions looking for one with a boot.ini file (Windows). I might also be able to get it to virtualize my Ubuntu partition.

I'll post back my results for others to see.

---

### Post by cyberdork33 on 2007-07-24
> **jmacdonagh said:**
> After researching on the VMWare Fusion forums (should have started there first ;) ), it looks like it is possible. Apparently Fusion just scans partitions looking for one with a boot.ini file (Windows). I might also be able to get it to virtualize my Ubuntu partition.

I'll post back my results for others to see.

My understanding is that there are some tricks you can do to get some VMs to boot your Ubuntu partition.

---

### Post by scottfinman on 2007-12-15
I have exactly the same setup (triple boot with refit: Leopard, Vista, Gutsy), and am diligently trying myself to get either Parallels or VMWare Fusion to run the partitions from within Leopard. Did you have any success with this? Definitely not a smooth process on my end so far.

---

### Post by flaggh on 2007-12-15
From my understanding, it is not easy to switch back and forth from booting a Windows partition natively, to booting it virtually.  Windows does not like it when you switch the hardware on it, which is what you are doing, only your switching the hardware with virtual hardware.  Check out this page from the VirtualBox page:

[http://www.virtualbox.org/wiki/Migrate_Windows]("http://www.virtualbox.org/wiki/Migrate_Windows")

The same should apply in any Virtualization software unless it was actually emulating the real hardware you have installed on your computer which I don't think any software does yet.

I don't know how difficult it would be to set Ubuntu up to do this though.  I think it should be possible to boot it both natively and virtually.

---

### Post by DMF on 2007-12-16
This link my aid you in your quest.

[http://forum.insanelymac.com/lofiversion/index.php/t47576.html](http://forum.insanelymac.com/lofiversion/index.php/t47576.html)

---

