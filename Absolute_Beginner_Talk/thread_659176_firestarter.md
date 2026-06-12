---
title: "firestarter"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by jhvillegas2 on 2008-01-05
I am connected to the internet through a wireless residential gateway. What settings should I make to get Firestarter working?

Thanks,
jhvillegas2

---

### Post by oldb0y on 2008-01-05
Firestarter is just a GUI for iptables. It's setup is just fine deafult:)

---

### Post by Steve1961 on 2008-01-05
> **jhvillegas2 said:**
> I am connected to the internet through a wireless residential gateway. What settings should I make to get Firestarter working?

Thanks,
jhvillegas2

Just start the programme and accept the defaults.  By default firestarter allows all outbound traffic, which is probably what you want.  You can also tweak inbound traffic by selecting the policy tab and creating rules for any services you want to give access to (samba, bittorrent etc) - the second box is what you need, the first box is for specifying specific ip addresses or hosts that you want to give access to.  However, the default settings are fine to get you going.  You might also want to go into preferences/firewall and tick the option to start the programme on dhcp lease renewal.

---

### Post by jhvillegas2 on 2008-01-05
I am trying to grant access for Azureus.  I take it that that is not done automatically.  All of the items in my policy tab are shaded out.  Any ideas?

Thanks,
jhvillegas2

---

### Post by Steve1961 on 2008-01-05
> **jhvillegas2 said:**
> I am trying to grant access for Azureus.  I take it that that is not done automatically.  All of the items in my policy tab are shaded out.  Any ideas?

Thanks,
jhvillegas2

Just right-click anywhere in the 'allow service' field in policy tab.  Select add rule, then from the drop down menu select bittorrent.  If you've configured azureus to use a particular port, just select add rule again and then manually enter the port number.  That should be all you need to do - although you might also have to configure the router/access point for port forwarding.

---

### Post by Steve1961 on 2008-01-05
One more thing, from preferences/firewall/network settings make sure the detected device is correct.

---

