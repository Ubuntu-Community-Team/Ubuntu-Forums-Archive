---
title: "partially internet conection - why ?"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by doron387 on 2007-01-15
(i am a newbi, working  with laptop amd mobile sempron 3400 / wired / dhcp / live-cd 6.10)

well, after long tryings with connecting to the web and changing the settings in the SYSTEM>NETWORKING page (though i had not too many clues of what i was doing)
the first time i got connected to the web was after i wentinto : SYSTEM>NETWORK CONNECTIONS, and there i tried to ping some addresses, the only one that responded was : [www.walla.co.il](www.walla.co.il), an israeli site.
the rest of the sites did not respond (even [www.google.com](www.google.com)) weird, isn't it ?
the ping took around 145 ms (isn't it a lot ?)
what might it be ? what should i check in order to be able to work in all the sites? 
thnx

---

### Post by mikewhatever on 2007-01-15
Hi again, and sorry I can not help. I hope you'll figure it out, and then, please post a howto. I've pinged walla.co.il now, and the time was ~20 ms, so 145 is alot.

---

### Post by k1001001 on 2007-01-15
First of all, when using the terminal, "ipconfig" is not the correct command to view network connections. Linux uses "ifconfig" instead. Don't ask me why, but that's the way it is.

When using the Live CD, the Internet should work right out of the box, especially when using a wired connection. You shouldn't have to change any network settings, especially if you are unsure of what you are doing. Restart your computer and try to use the Internet without changing any settings.

Let us know if this does or does not work.

---

