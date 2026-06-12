---
title: "[SOLVED] firefox  about:config"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by squrl on 2007-01-19
Can someone tell me why when I do "about:config" in firefox on one machine it comes up with several pages of items in black text. Some of them are changeable some arent.  On another machine they come up in green and purple text and when you try to make a change they take you to a different page.   

Both machines are running firefox 2.0.0.1  

I am trying to get rid of "network.dns.IPV6"

Also is it possible to get rid of the tool tips on this board?

Thanks

---

### Post by r4ik on 2007-01-19
Try to do this:

1. sudo gedit /etc/modprobe.d/aliases (or your preferred text editor)
2. Find the line: alias net-pf-10 ipv6
3. Edit this to: alias net-pf-10 off
4. Save the file and reboot

Good luck !

---

### Post by squrl on 2007-01-19
Thanks ..

More than one way to skin that cat.

---

### Post by taurus on 2007-01-19
> **squrl said:**
> Thanks ..

More than one way to skin that cat.

Nobody is skinning any cat here or PETA will be on your door faster than you can say, "Oh me..."  :lolflag:

---

### Post by r4ik on 2007-01-19
Glad it worked.
credits go to 'zerhacke"

---

### Post by squrl on 2007-01-19
Pray tell who is "PETA"

---

### Post by ciscosurfer on 2007-01-19
> **squrl said:**
> Pray tell who is "PETA"People for the Ethical Treatment of Animals

---

### Post by squrl on 2007-01-19
Is this site related to Madd Comics.

---

### Post by OldTimeTech on 2007-01-19
No, not to Madd Comics, we all just have a little bit of different humor ;)

---

