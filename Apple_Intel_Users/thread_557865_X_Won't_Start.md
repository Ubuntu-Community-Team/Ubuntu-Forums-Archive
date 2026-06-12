---
title: "X Won't Start"
date: 2007-09-23
forum: Apple Intel Users
---

### Post by cbk1994 on 2007-09-23
I've been trying to install Ubuntu 7.04 on my MacBook Pro. I've been using Boot Camp, and using this guide: [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

I can get it to boot, but there are two problems.
First, the keyboard doesn't work part of the time. About a third of the time it will work. If it doesn't, then after it does the 30 second count down and then selects to boot, I can use my keyboard.

Second, and more importantly, X won't start. It tells me that X cannot start and to reboot when I fix the configuration. I can get the exact wording if you need it. This happens every single time.

Thanks so much for your help in advance,
Tom Marthenal

---

### Post by alephsmith on 2007-09-23
Which MacBook Pro are you using?

If it is is post June 2007 it is a Santa Rosa Macbook Pro and this is the appropriate guide: [https://wiki.ubuntu.com/MacBookProSantaRosa](https://wiki.ubuntu.com/MacBookProSantaRosa)

If it is older, pre June 2007, try this guide instead: [https://wiki.ubuntu.com/MacBookPro](https://wiki.ubuntu.com/MacBookPro)

In relation to the keyboard- this s a know GRUB issue I believe. If you have an external keyboard I think that may be used instead.

---

### Post by cyberdork33 on 2007-09-23
> **alephsmith said:**
> In relation to the keyboard- this s a know GRUB issue I believe. If you have an external keyboard I think that may be used instead.It is a bug in the apple firmware. There is no fix. Plugging a USB keyboard on the selection screen should allow you to make changes, otherwise you just have to keep rebooting until you keyboard is usable.

---

### Post by cbk1994 on 2007-09-23
Okay, now I'm using a text-based installer, but the problem is that there is no count-down timer. I don't have a USB keyboard.

---

### Post by cbk1994 on 2007-09-23
It's installed. X won't run, and like the tutorial says, I'm trying to install drivers. The problem is that I can't get to a terminal.

It gives me something like the terminal, and it says ubuntu login:

If I type anything there, it asks for the password. I put in the absolute correct password (I've reinstalled 3 times to make sure), and it says Incorrect Login.

Can you help me get logged into the terminal?
"ubuntu" was what I entered after DHCP settings (I used the text install).

Thanks so much in advance!

---

### Post by cyberdork33 on 2007-09-23
Your login is the username and password that you set during the install.

---

