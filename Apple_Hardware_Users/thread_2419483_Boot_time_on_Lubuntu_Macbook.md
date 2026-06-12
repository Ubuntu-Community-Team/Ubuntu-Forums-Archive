---
title: "Boot time on Lubuntu Macbook"
date: 2019-05-22
forum: Apple Hardware Users
---

### Post by jazzymac on 2019-05-22
Hi, I'm using a 2008  4,1 Macbook 2.4Ghz, 4GB, SSD with Lubuntu installed.

It takes just under 5 minutes to boot.

It there any way I can shave off 4 to 4 1/2 minutes off the boot time?

I appreciate any help you can offer.

---

### Post by howefield on 2019-05-22
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by #&amp;thj^% on 2019-05-22
> **jazzymac said:**
> Hi, I'm using a 2008  4,1 Macbook 2.4Ghz, 4GB, SSD with Lubuntu installed.

It takes just under 5 minutes to boot.

It there any way I can shave off 4 to 4 1/2 minutes off the boot time?

I appreciate any help you can offer.

Well before we get into a long output and view point, see if it shows at a quick glance via;
```
systemd-analyze
```
an example of what might show:
```
Startup finished in 5.153s (kernel) + 6.212s (userspace) = 11.365s 
graphical.target reached after 6.211s in userspace
```
EDIT: Also this one:
```
cat /var/log/boot.log
```

please use code tags for the reply, it helps keep things tidy for those who may help you.
See my sig:if needed for "code tags"

---

### Post by jazzymac on 2019-05-23
Hi, thanks so much. This is what I get after systemd-analyze:

```

Startup finished in 2min 8.317s (kernel) + 14.539s (userspace) = 2min 22.856s 
  graphical.target reached after 14.339s in userspace
```

The full boot time is:
00:00 Power button - 'Chime' black screen
02:21 Lubuntu Logo appears for a few seconds - black screen
04:10 The mouse arrow/pointer appears
04:34 The Desktop appears

Any advice on speeding up boot time would be appreciated. Just to say, that my DVD drive is not working. There's a disc stuck in it that I've never managed to remove. So if the process of shortening boot time will involve using a CDR then I'm not going to be able to do that.....

---

### Post by matanglawin on 2019-05-24
> **jazzymac said:**
> Just to say, that my DVD drive is not working. There's a disc stuck in it that I've never managed to remove. So if the process of shortening boot time will involve using a CDR then I'm not going to be able to do that.....

I'm just guessing here, but, it seems the system is trying to read what's on the drive. If it's stuck there, maybe you need to remove the drive itself.

---

