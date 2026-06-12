---
title: "Wireless and Lan not working at the same time"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by Nodestar on 2008-04-13
My Wireless Card works. And my Wired Lan works. But not together. 
I'm not really expecting them to combine to make a better connection or something. It's just annoying when I need to move my laptop and I'm connected through my Wired Lan.(which is slightly faster) I have to manually switch to the Wireless connection. And while it's connecting it disables my Wired connection and I lose my connection all together for a few seconds before the wireless connects. 

When I used to run Windows XP both could be connected at the same time. Any way to duplicate that effect?

Thanks

---

### Post by t1n0m3n on 2008-04-13
What version of Ubuntu are you running?

---

### Post by Nodestar on 2008-04-13
Latest version. 7.10.

---

### Post by Nodestar on 2008-04-13
Bump

---

### Post by t1n0m3n on 2008-04-13
I think this is because networkmanager cannot handle more than one DHCP based connection at a time.
Now, I got mine to work with the wireless set to DHCP and the wired connection set to a static address.  But I was direct connecting to my PC to transfer files.  (I gave the wired connection a 1.1.1.2/30 address and the PC a 1.1.1.1/30 address.)

---

### Post by edm1 on 2008-04-13
Yes i think this is because of NetworkManager. It'd be a bit of an effort but before you disconnect the wire you could set up the wireless using 'iwconfig' in the terminal. Have a look at the manual:-

```
man iwconfig
```

I know the developers are working have on creating seamless wireless networking but it is planned for Intrepid Ibex (Ubuntu 8.10).

> "A particular focus for us will be pervasive Internet access, the ability to tap into bandwidth whenever and wherever you happen to be."

*Mark Shuttleworth*

---

