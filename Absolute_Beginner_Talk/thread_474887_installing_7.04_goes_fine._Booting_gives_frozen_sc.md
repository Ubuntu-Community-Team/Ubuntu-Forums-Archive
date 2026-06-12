---
title: "installing 7.04 goes fine. Booting gives frozen screen."
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by dronepower on 2007-06-15
I installed 7.04 on my SATA 500GB seagate drive just fine via the live CD. Partitions were made in auto mode.
When I am booting and Ubuntu goes in gui mode i see one brownish screen, i hear the HDD doing some reading afterwards and that's it :s
What could this be?

further specs are: E6400 core 2, 2GB, nvidia7600GT.

On my second pc with IDE drive all goes ok.

---

### Post by shelzmike on 2007-06-15
> **dronepower said:**
> I installed 7.04 on my SATA 500GB seagate drive just fine via the live CD. Partitions were made in auto mode.


Is this a single OS install (main), dual-boot, or virtual? I had the same issue before, but it may have been a different problem that your situation. 

One thing that I can say though is that if at any point in time during the install there is an error, a message wouid pop up telling me what the issue was, but then it would go away, so if I was not watching the whole entire time I missed it. Did this twice before I figured it out. 

By the way, there can be many reasons here, mine was because I was installing it as a virtual machine using VMWare player and I didn't designate enough HD space in the vmdk file.

---

### Post by dronepower on 2007-06-16
well, when boot up for the first time from harddisk your HDD is being checked.
At the end of the check it gives an error (didnt had the time too read it), it reboots end then it will end up with a blue screen.

When I install another linux distro like PClinuxOS 2007 all goes fine.

---

