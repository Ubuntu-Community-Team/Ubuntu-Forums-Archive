---
title: "Help! Multi-Boot Question"
date: 2010-05-07
forum: Apple Hardware Users
---

### Post by duke7nuke on 2010-05-07
Hi 

I have a macbook pro 2,2 and I currently have OS X, Vista and ubuntu 9.04 booting fine with reFit. I followed the example on [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

I would like to have intrepid now. What are my options? 

1. Can I just add it after 9.04, after resizing etc? can I do that?

or

2. how do I go about removing 9.04 and installing intrepid?

Thanks!

---

### Post by linuxopjemac on 2010-05-08
I don't know if you can just resize an ext3/ext4 partition. I would just run the installer and select the partition where now 9.04 runs as / and then have it deleted automatically. I only fear you might run into trouble having to tweak Grub again to have it boot Linux again.

---

