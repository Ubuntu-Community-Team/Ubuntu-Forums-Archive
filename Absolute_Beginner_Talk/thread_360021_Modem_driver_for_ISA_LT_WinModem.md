---
title: "Modem driver for ISA LT WinModem"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by Chris Beall on 2007-02-12
Xubuntu 6.10
Kernel: Linux 2.6.17-10-generic

Modem: ISA LT WinModem
FCC Reg. No. 409TAI-31347-PT-E
Lucent 1643 chipset aka Apollo FDSP aka L56xAF

I am totally new to Unix...

I got Xubuntu installed with few problems, but I'm having trouble figuring out how to get/install modem drivers.

According to [https://help.ubuntu.com/community/DialupModemHowto/ScanModem](https://help.ubuntu.com/community/DialupModemHowto/ScanModem), the scanModem tool does not work for ISA modems.  So I got a screwdriver and extracted some of the numbers shown above, and used those to find a close (though not exact) match in the list at [http://64.126.95.102:8080/gromitkc/isa_list.html](http://64.126.95.102:8080/gromitkc/isa_list.html), from which the remaining numbers came.

Next I went to [https://help.ubuntu.com/community/DialupModemHowto/Lucent](https://help.ubuntu.com/community/DialupModemHowto/Lucent), since it appeared that I had a Lucent modem, but I was concerned that I hadn't determined that via scanModem, so I didn't know if the procedure on that page would really apply to me, especially because of the ISA buss.

So I looked around and found [http://www.linmodems.org/](http://www.linmodems.org/).  There was a link to Lucent/Agere modem resources, so I followed that to [http://www.heby.de/ltmodem](http://www.heby.de/ltmodem), a no-longer-maintained page with a forwarding link to [http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/](http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/).  One of the directory entries on that page says "Go_to_martian_for_kernels_above_2.6.12" and mine is 2.6.17 so I clicked on the directory "Martian", where I found the file "Readme-NOW.html" (at [http://martian.barrelsoutofbond.org/index.html)](http://martian.barrelsoutofbond.org/index.html)).  So I read it and the first sentence was "Martian is software to serve the Agere Systems PCI WinModem under LINUX."

But I have an ISA modem...  and the instructions for installing Martian look pretty formidable to a newbie.

So, my question is, will Martian work on an ISA buss modem?  If so, which site is the best choice for obtaining files and instructions.  If not, is there any better alternative to buying a new modem?

Many thanks to anyone who can advise me.

---

