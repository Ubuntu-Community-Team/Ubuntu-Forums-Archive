---
title: "Mac G4 Will not boot from CD"
date: 2006-06-04
forum: Apple PPC Users
---

### Post by fran22431 on 2006-06-04
I have a Mac G4 867. When I boot from the CD, after I give the boot command, the screen truns grey and is blank. The CD spins for a while and then stops. command-Option-f1 has no effect. Any ideas?

Thanks,
Fran

---

### Post by godard on 2006-06-05
This is a bug i have too, the developers are aware of the problem, please see discussion here:

[https://launchpad.net/distros/ubuntu/+source/ubiquity/+bug/34508](https://launchpad.net/distros/ubuntu/+source/ubiquity/+bug/34508)

---

### Post by unicycler on 2006-06-05
Have you tried holding "C" down during boot? Worked for 6.06 Live on my iBook.

---

### Post by DeadSamurai on 2006-06-05
"C" Worked for me on my Mac Mini 1,5Ghz (though I had to hold it down for a couple of secs).

---

### Post by cagdasinan on 2006-06-12
I think mac mini sometimes fail to boot form cd. Only solution is to open mac in open firmware page (command like). After starting the mac hold down the COMMAND-OPTION-O-F  (I have a windows keyboard so the key squence is different WINDOWSKEY-ALT-O-F is worked for me) Don't release the keys until the white screen appears. And in the command line I wrote exactly this without the quotes "boot cd:,\\:tbxi"  
In one forum someone said boot cd:,//;tbxi  it didn't worked
boot cd:,\\:tbxi worked for me.

Hope this helps

---

