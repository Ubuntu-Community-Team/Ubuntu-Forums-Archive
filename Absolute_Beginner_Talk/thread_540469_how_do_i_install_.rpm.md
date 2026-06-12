---
title: "how do i install .rpm"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by newbie1122 on 2007-09-01
hi, i have .rpm file which is the driver for my IBM lenova x41 tablet ethernet, and i don't know how to install it since this is first time using linux. in other post ppl said to use alien. but i can't use "sudo apt-get install alien" command since i don't have internet. is there any other way to install .rpm without using other software?

---

### Post by Majorix on 2007-09-01
EDIT: Oops ignore me, no internet :)

```
sudo apt-get install alien
alien rpmfile
sudo dpkg -i debfileThatWasCreated
```

---

### Post by meborc on 2007-09-01
i don't know if the alien program is on the ubuntu cd. if so you can add the cd as a source (if you haven't toutched it, it probably already is) in /etc/apt/sources.list

comment out all other sources, then "sudo apt-get update" and "sudo apt-get install alien"

but this will work only when the alien package IS on the cd...

---

### Post by newbie1122 on 2007-09-01
i have ubuntu on usb stick, x41 laptop dont have cd/dvd drive, whats the command to see if alien is on the usb stick.
also i heard that you need other files such as dpkg-dev and debhelper to get alien to work

---

### Post by meborc on 2007-09-01
> **newbie1122 said:**
> i have ubuntu on usb stick, x41 laptop dont have cd/dvd drive, whats the command to see if alien is on the usb stick.
also i heard that you need other files such as dpkg-dev and debhelper to get alien to work

well... i guess i need to start using newer hardware :D can't help you there... sorry

maybe someone has a hint?

---

### Post by newbie1122 on 2007-09-01
thx for quick reply. i appreciate your help.

---

### Post by oOJINxOo on 2007-09-01
you'd be better off looking for a deb package if there's one available for the application your tryna install

---

### Post by newbie1122 on 2007-09-01
it doesnt come with dev, only other package that downloaded with were "tg3-3.71b.tar.gz" and "tg3_sup-3.71b.tar.gz"

---

