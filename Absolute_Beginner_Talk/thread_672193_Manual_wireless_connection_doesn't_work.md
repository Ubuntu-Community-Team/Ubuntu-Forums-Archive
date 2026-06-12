---
title: "Manual wireless connection doesn't work"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by toughasnails001 on 2008-01-19
I am trying to get a static IP configured for my computer and I'm having some problems. I am currently on roaming mode connected to my wireless network and everything works fine, but when I try to set up a manual connection, it doesn't work. I typed "iwconfig" and it said that my ESSID was "linksys". I don't have a password. Then I went into wireless connection properties, put in "linksys" as the ESSID, left the password type as "WPA Personal" and the password field blank, and set the configuration to DHCP. When I do that, no connection. What am I doing wrong? How do I fix it?

---

### Post by toughasnails001 on 2008-01-19
bump

---

### Post by toughasnails001 on 2008-01-19
another bump, sorry but i would really like some help on this

---

### Post by dwhitney67 on 2008-01-19
I'm not an expert, but doesn't WPA Personal require a password?  If you do not want to secure your router with a password, and that's understandable if nobody lives within 300-400 feet of your residence or if you want to share it with neighbors, then set your router's wi-fi security settings to "disabled".  Other than this little issue, the other stuff you are doing is correct.

Oh, by the way, if you are attempting to set up a static IP address on your system, then you should NOT be specifying DHCP as your connection type to the router.  I have never done a static IP setup for wireless (can't think of why I would want to), so you will need to seek help with this elsewhere.

---

### Post by toughasnails001 on 2008-01-19
> **dwhitney67 said:**
> I'm not an expert, but doesn't WPA Personal require a password?  If you do not want to secure your router with a password, and that's understandable if nobody lives within 300-400 feet of your residence or if you want to share it with neighbors, then set your router's wi-fi security settings to "disabled".  Other than this little issue, the other stuff you are doing is correct.

Oh, by the way, if you are attempting to set up a static IP address on your system, then you should NOT be specifying DHCP as your connection type to the router.  I have never done a static IP setup for wireless (can't think of why I would want to), so you will need to seek help with this elsewhere.

Yeah, but there is no option in the network settings window for no password. I see "WEP Key (Hexadecimal)", "WEP Key (ASCII)", "WPA Personal" and "WPA2 Personal". I don't know what to do besides select one of these and leave the password field blank.

Configuring the static ip is the next step. I just want to make sure this works first before I mess around with that.

---

### Post by dwhitney67 on 2008-01-19
Why don't you edit your router's wi-fi settings to enable "WPA Personal", setup a password of "password", or anything else you desire, then try configuring your Linux system with that information.

---

### Post by eolson on 2008-01-19
What dwhitney67 said.   The option for password or no password is set on your router.  should be something on there someplace like

Enable WAP
or
Disable WAP

probably with a check box.

---

