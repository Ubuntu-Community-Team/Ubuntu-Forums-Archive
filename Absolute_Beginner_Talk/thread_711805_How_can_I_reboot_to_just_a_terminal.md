---
title: "How can I reboot to just a terminal?"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by whoscheesemine on 2008-03-01
I was wondering if there was a way to reboot to just a terminal or Grub (if that's what its called). I am trying to use an installation file that will detect my Nvida card and install the driver for me, but I don't currently have the card in as when I do put it in and turn on my comptuer it will not load the Xubuntu Interface. If I could reboot to just a terminal then I could use the graphics card and it would be able to detect it.

Thanks all.

Here's a link to the thread dealing with what I'm doing, but what I'm more interested in is booting to just a terminal:

[http://ubuntuforums.org/showthread.php?p=4432514&posted=1#post4432514](http://ubuntuforums.org/showthread.php?p=4432514&posted=1#post4432514)

---

### Post by Shadowmeph on 2008-03-01
I think that the command is alt F1

---

### Post by _Phineas_ on 2008-03-01
press ctrl+alt+F5

---

### Post by tubasoldier on 2008-03-01
Actually you could use ctl+alt+F1 through F5
any of those F'n buttons will work.

you will also have to kill your xserver: 
```
sudo /etc/init.d/gdm stop
```


Even better than all that is to simply install the Nvidia graphics drivers with the restricted drivers manager. Besides, using the driver directly from nvidia will give you kernel module issues on Ubuntu.

---

### Post by whoscheesemine on 2008-03-01
Thanks everyone, but I was directed to a pretty good guide right here:

[http://ubuntuforums.org/showpost.php?p=4284483&postcount=8](http://ubuntuforums.org/showpost.php?p=4284483&postcount=8)

---

### Post by imT on 2008-03-01
...you can also choose your session type at login.

---

### Post by tubasoldier on 2008-03-01
> **imT said:**
> ...you can also choose your session type at login.

Yes, but he can not install the Nvidia drivers that way because the X server is still running.

---

### Post by whoscheesemine on 2008-03-01
If anyone's curious about the full story here's a link to the previous thread I was working with:

[http://ubuntuforums.org/showthread.php?p=4432953#post4432953](http://ubuntuforums.org/showthread.php?p=4432953#post4432953)

---

