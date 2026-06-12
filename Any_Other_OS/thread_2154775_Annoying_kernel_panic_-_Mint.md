---
title: "Annoying kernel panic - Mint"
date: 2013-06-15
forum: Any Other OS
---

### Post by mastrsushi on 2013-06-15
I'm a mint user, but i got very little help on that forum. I've been getting these annoying kernel panics about 3 times a day, typically when im running flash player.

This is what it typically says.

[http://imgur.com/QAkolVB](http://imgur.com/QAkolVB)

---

### Post by hansdown on 2013-06-15
Hi mastrsushi.

Does mint make it through to a reboot?

Are you running mint 14?

Are you using intel chipset?

Just trying to see the big picture.

Thanks.

---

### Post by QIII on 2013-06-15
*Moved to **Other OS/Distro Support***

I've modified the title of your thread to make it clear that this issue is in Mint.  There are forum users who seek out specific items to help with, and adding 'Mint" should attract some.

Best wishes!  I hope this community lives up to your expectations!

---

### Post by buzzingrobot on 2013-06-15
If it's Mint 15, the default kernel panics for a good many people. A "sudo apt-get dist-update" will install a slightly later kernel that fixes it. That's how I handled it.

---

### Post by mastrsushi on 2013-06-16
> **hansdown said:**
> Hi mastrsushi.

Does mint make it through to a reboot?

Are you running mint 14?

Are you using intel chipset?

Just trying to see the big picture.

Thanks.

I'm running Mint 15 with an Intel Core 2 Duo and 2gb ram

---

### Post by mastrsushi on 2013-06-16
> **buzzingrobot said:**
> If it's Mint 15, the default kernel panics for a good many people. A "sudo apt-get dist-update" will install a slightly later kernel that fixes it. That's how I handled it.

tim-desktop tim # sudo apt-get dist-update
E: Invalid operation dist-update

u sure its not dist-upgrade?

---

### Post by mastrsushi on 2013-06-16
Ok I think the problem might have to do with cpu usage, because whenever I play minecraft or run youtube videos in 1080p the total cpu on conky goes all the way up and the fan starts roaring then the kernel panic, this is ridiculous considering on windows 7 it was never this loud. I dusted my cpu fan with compressed air yesturday, i also sprayed the area where the cpu is held, could it have something to do with the cpu being exposed to cold air?

---

### Post by buzzingrobot on 2013-06-16
> **mastrsushi said:**
> tim-desktop tim # sudo apt-get dist-update
E: Invalid operation dist-update

u sure its not dist-upgrade?

Oops!  Yep, that's right.  Blame late night brain...

---

