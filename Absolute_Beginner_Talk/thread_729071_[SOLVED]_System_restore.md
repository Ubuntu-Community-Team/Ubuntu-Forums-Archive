---
title: "[SOLVED] System restore"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by cartisdm on 2008-03-19
Out of the blue I can't connect to my wireless network.  Nothing changed I just rebooted and now when I log in it keeps asking me for the passkey.  I have a weather monitor on my dock which collects data within the first 10 seconds so I know I get a connection and if I'm quick enough I can open up a web page.  But after about 10 seconds I loose connection and can't do anything.  It just keeps asking me to enter in my passkey, which of course doesn't work.  The rest of the house has internet.

I'm so confused.  Is there a system restore (like in windowz) that I could just back up to a few days ago? Or does anyone have any ideas?

I tried to manually connect as well using the terminal

```
sudo iwconfig eth1 essid HotGuysNextDoor
```

then

```
sudo dhclient eth1
```

---

### Post by glennric on 2008-03-19
This may not help but your last command should be 
```
sudo dhclient eth1 up
```

---

### Post by Barrucadu on 2008-03-19
That happened to me, I had to change the network password to get it to work.

---

### Post by cartisdm on 2008-03-19
> **glennric said:**
> This may not help but your last command should be 
```
sudo dhclient eth1 up
```

No such luck, I got some weird error when doing that.  I'd copy and paste it but I'm on a different pc because...well.....that one doesn't have internet lol

---

### Post by cartisdm on 2008-03-19
> **Barrucadu said:**
> That happened to me, I had to change the network password to get it to work.

Duuuuuuuuuude, you're a friggin' lifesaver.  Thanks a bunch man! Now I have to quickly hop on sparknotes.com and do my reading homework before my 3:30 class!!!!:shock:

---

