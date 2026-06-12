---
title: "Gutsy problem with wireless I dont have wireless"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by nynoah on 2007-10-23
My gutsy system keeps on crashing.  The lock up happens just after the computer looks for a wifi connection.   Here is the problem, I have NO wireless at all.  But the computer keeps on looking for it and then locking up.  The computer locks up every hour.  This is driving me NUTS.  I took off my blue tooth packages because it was saying on another lockup that it was trying to use that too.

my net work manager says:

Oct 23 13:22:38 nyn-desktop NetworkManager: <info>  Updating allowed wireless network lists. 

Oct 23 13:22:38 nyn-desktop NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 

Oct 23 13:22:40 nyn-desktop kernel: [   65.181520] eth0: no IPv6 routers present



Anyone got a clue.  My Gutsy system is running like poop.

Noah


Edit:

Did it again!!!!!!!!!!!

Oct 23 13:54:00 nyn-desktop hald: mounted /dev/sdc1 on behalf of uid 1000

Oct 23 13:54:03 nyn-desktop NetworkManager: <info> Updating allowed wireless network lists.

Oct 23 13:54:03 nyn-desktop NetworkManager: <WARN> nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored..



Why is my computer searching for something I DO NOT HAVE AT ALL?

I have filed a bug report too.

Bug #156378

---

### Post by nynoah on 2007-10-23
Did it again!!!!!!!!!!!

Oct 23 13:54:00 nyn-desktop hald: mounted /dev/sdc1 on behalf of uid 1000

Oct 23 13:54:03 nyn-desktop NetworkManager: <info>  Updating allowed wireless network lists. 

Oct 23 13:54:03 nyn-desktop NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 



Why is my computer searching for something I DO NOT HAVE AT ALL?

---

### Post by nynoah on 2007-10-23
I have filed a bug report too.

Bug #156378

---

### Post by Alchera on 2008-05-11
Same problem >> [Bug #105352 in knetworkmanager (Ubuntu)]("https://bugs.launchpad.net/ubuntu/+source/knetworkmanager/+bug/105352")

---

