---
title: "New Ubuntu user-need help with macbook wireless"
date: 2008-04-03
forum: Apple Intel Users
---

### Post by shlomo705 on 2008-04-03
I have a macbook 2.1 and I am trying to dual boot Ubuntu and OS X 10.4.11. I am beginning by running Ubuntu off of a CD that I burned from an ISO (Not sure if this is would be called a Live CD). Everything appears to be fine, except that my wireless card is not being detected. I have no idea what to do now, so any and all help is greatly appreciated.

Thanks,
Shlomo

---

### Post by berbs on 2008-04-03
Not sure what wireless card is in a macbook 2.1 (check lspci output), but if its an Atheros AR54xx you will need to download the latest trunk snapshot from madwifi and build the module yourself.

---

### Post by schauerlich on 2008-04-03
This howto should work for you:
[https://help.ubuntu.com/community/MacBook#head-e4a1f2cde8ad66bc01c97bfdadc85996ad80f688](https://help.ubuntu.com/community/MacBook#head-e4a1f2cde8ad66bc01c97bfdadc85996ad80f688)

That page can save you time waiting for responses on the forums - it has a lot of good info and covers a lot of what you'll need. One of the benefits of having a small pool of possible hardware configurations.

---

### Post by cyberdork33 on 2008-04-03
> **shlomo705 said:**
> I have a macbook 2.1 and I am trying to dual boot Ubuntu and OS X 10.4.11. I am beginning by running Ubuntu off of a CD that I burned from an ISO (Not sure if this is would be called a Live CD). Everything appears to be fine, except that my wireless card is not being detected. I have no idea what to do now, so any and all help is greatly appreciated.

Thanks,
Shlomo
Unfortunately if you are not installing, it is not that simple. you would need to modify the LiveCD files in order to have it work every time.

---

### Post by shlomo705 on 2008-04-03
Thanks for the help so far guys. I already did the full install of Ubuntu onto a partition on my macbook's hard drive. I looked at the link EDavidBurg posted, but I'm not really sure what either daily snapshots or Subversion are or how I access them, as I did not see either under applications. If someone could help me access them and explain what they are, I would be very grateful.

Thanks,
Shlomo

---

### Post by Viro on 2008-04-04
To follow those instructions, you need to open up a terminal and type those commands in. Go to Applications -> Accessories -> Terminal and from there, you can copy and paste those commands into the terminal. I suggest copying and pasting the first line with the "sudo" command into the terminal to get yourself authenticated. Then, you can copy and paste the rest of the commands as a block.

---

