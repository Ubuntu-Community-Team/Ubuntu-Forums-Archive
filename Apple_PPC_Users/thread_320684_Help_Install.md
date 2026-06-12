---
title: "Help Install"
date: 2006-12-17
forum: Apple PPC Users
---

### Post by darkdragoon on 2006-12-17
HI i am usieng a external harddrive to runmy computer i have two partion with 10.2  and one wit nothing on it. i downloaded the ubuntu_powerpc_dapper the ubuntu-6.06.1-desktop-powerpc.iso.  how do i install in on a firewire drive.  my internal harddrive is dead and don't work. that's why i am running my computer off my external firewire drive.  which is made by western digital 250gb.  all respones would reall help. thanks.

---

### Post by linear on 2006-12-17
> **darkdragoon said:**
> HI i am usieng a external harddrive to runmy computer i have two partion with 10.2  and one wit nothing on it. i downloaded the ubuntu_powerpc_dapper the ubuntu-6.06.1-desktop-powerpc.iso.  how do i install in on a firewire drive.  my internal harddrive is dead and don't work. that's why i am running my computer off my external firewire drive.  which is made by western digital 250gb.  all respones would reall help. thanks.

If you want to install to an external firewire drive, download the Edgy alternate install disk instead of the Dapper LiveCD. (Firewire support is fixed in Edgy.) In a dual boot configuration, I was able to install Edgy to an external FW drive without trouble (but be patient with it - it may appear to stall for 15-20 minutes). Your empty partition is first on the disk, I hope?

---

### Post by darkdragoon on 2006-12-17
well how do i get the edgy version cuz i've burn the dapper version. and 10.2 is on the frist partion the second partion is empty.  and thank you for responding.  no one else has.

---

### Post by linear on 2006-12-18
Edgy is available from the usual download sites; start [here]("http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download") to find one near you.

Having OS X on the first partition may be a problem. Normally, you're instructed to let the Ubuntu Installer have the first partition. It may still work, but I really don't know. Can you afford to wipe the disk and start over?

---

### Post by darkdragoon on 2006-12-18
yeah i cold just boot from os x 10.2.  and partion the harddrive to hfs which i 've read that linux works with that format. and not install 10.2.  well i've donwloaded the live iso for kubuntu the install iso of eduntu and i think the live iso of unbuntu.  and burned the iso on to a cd.....   so how do i go about installing the kubuntu and ubuntu.  ?  keep in mind that my interal harddrive is dead and will not work. i am runing m y computer off the external drive.

---

### Post by linear on 2006-12-18
However you decide to do it, don't format the partition you plan to put Ubuntu on as hfs. Leave it unallocated (unformatted) and let the Ubuntu Installer take care of the formatting.

Boot from an Edgy (6.10) alternate install CD (whether Ubuntu, Kubuntu, Xubuntu, or Edubuntu shouldn't matter) and just follow the prompts.

(It would be a good idea to search this forum for posts about your model Mac, to find out if there are any model-specific quirks.)

---

