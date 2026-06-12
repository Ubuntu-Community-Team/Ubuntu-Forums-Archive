---
title: "[SOLVED] Using Television as a Monitor ?"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by Dr Small on 2007-09-18
Ok, I have a dual-boot pc with Windows and Dapper Drake on it, with a monitor, and a Tobisha television setting fairly near it. 

I saw on the back of the computer a S-Video Output port, and I have a S-Video cable.
The back of the Tobisha Television has a S-Video In port, so I plugged in my S-Video cable to the pc and television.

Is there any way to port what is on the computer, through the S-Video cable, over the the television, and use the television as a second monitor ?

Any help would be appreciated.

Dr Small

---

### Post by JustAboutRealJAR on 2007-09-18
if your graphics card is ATI then you can try atitvout. to install it, open a terminal and type:

```
sudo apt-get install atitvout
```

you'll need the [universe repoisitory enabled]("http://monkeyblog.org/ubuntu/installing/#enabling_extra_repositories") to install it

---

### Post by mikeyphi on 2007-09-18
A search of the wiki gave this: [https://wiki.ubuntu.com/Radeon7500TVOut?highlight=%28s-video%29](https://wiki.ubuntu.com/Radeon7500TVOut?highlight=%28s-video%29)

someone got some success - there might be more out there

---

### Post by Error403 on 2007-09-18
Hi, I use my box as a media center in my living room with the S-video out of my graphics card (nvidia 5200) but I'm not sure if it supports dual screen as I don't use a screen at all.

However, my MX440 in my other pc does not support dual screen at all.

---

### Post by olieviya on 2007-09-18
What happens if you just plug it in and restart gnome/kde?

---

### Post by Dr Small on 2007-09-19
> **mikeyphi said:**
> A search of the wiki gave this: [https://wiki.ubuntu.com/Radeon7500TVOut?highlight=%28s-video%29](https://wiki.ubuntu.com/Radeon7500TVOut?highlight=%28s-video%29)

someone got some success - there might be more out there
Thanks, I got it to work finally, after messing around with it for awhile.

Thanks everyone :D

Dr Small

---

### Post by Tombo5150 on 2007-10-08
What about if one had an Intel video card?

---

