---
title: "What video driver am I using?"
date: 2006-08-02
forum: Absolute Beginner Talk
---

### Post by adds2one on 2006-08-02
Hello,

Could someone tell me how to find out what video driver I am using?

Cheers - J

---

### Post by zxee on 2006-08-03
> **adds2one said:**
> Hello,

Could someone tell me how to find out what video driver I am using?

Cheers - J

Open a terminal, if you're not already in one, and type > lspci -v
Somewhere in the output should be your video card.

---

### Post by adds2one on 2006-08-03
Thanks for the reply but that only tells me what my video card is. I already know what card I have, what I want to know is what driver is being used. I am on a fresh Dapper install and I want to know what default driver is being used. I have an ATI Technologies Inc Radeon R250 Lf [FireGL 9000].

---

### Post by Hexx on 2006-08-03
The video card driver currently installed can be found somewhere in the xorg.conf file, if I remember correctly.

---

### Post by zxee on 2006-08-03
> **adds2one said:**
> Thanks for the reply but that only tells me what my video card is. I already know what card I have, what I want to know is what driver is being used. I am on a fresh Dapper install and I want to know what default driver is being used. I have an ATI Technologies Inc Radeon R250 Lf [FireGL 9000].

Ok, I read too fast :) The driver being used is in /etc/X11/xorg.config. You can open that with less from a terminal or gedit and scroll though the file to find the driver.

---

