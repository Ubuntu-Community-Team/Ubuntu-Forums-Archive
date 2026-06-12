---
title: "Internet connection"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by unplugged on 2007-05-20
Hello,

I have just installed Ubuntu
I have no clue what to do about getting my internet working.
I connect to the internet though a USB cable into a D-Link Modem.
Can someones please help me? 
I really want to make the full switch but i need the internet to faccillitate this.

Cheers, and many thanks

---

### Post by Bachstelze on 2007-05-20
USB cable ? Can you connect with an Ethernet cable instead ? It will make things way easier...

---

### Post by unplugged on 2007-05-20
I will only be able to connect with an ethernet cable wednesday, and then only temporarily. If i set it up using a ethernet cable, can i revert back to USb for nomal use?

eitherway, how do i do it with an ethernet.

---

### Post by misfitpierce on 2007-05-20
you plug it in :)

---

### Post by unplugged on 2007-05-20
So basicly if i connect using an ethernet cable rather than a usb cable it will just work?

---

### Post by Bachstelze on 2007-05-20
Yes, assuming your network card is properly detected but most of them are.

---

### Post by unplugged on 2007-05-20
thank you.

---

### Post by Deros on 2007-05-20
And how does one ensure their network card is properly detected?

Thanks,
Deros

---

### Post by Bachstelze on 2007-05-20
```
sudo ifconfig -a
```

should apear as ethSomething.

---

