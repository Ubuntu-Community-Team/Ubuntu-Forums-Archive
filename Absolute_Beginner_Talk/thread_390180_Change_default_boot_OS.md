---
title: "Change default boot OS"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by ZeroWing on 2007-03-21
I've finally got Xubuntu installed, but given the problems I've had with it, I'd like to set Windows XP as the default boot option.

 How could I do this? I've seen how to do this on Ubuntu, but Xubuntu doesn't seem to know what Gedit is.

---

### Post by fakie_flip on 2007-03-21
Xubuntu has a different gui text editor. I can't remember what it is, but you can use nano from the command lineto edit your menu.lst file. I think it is /boot/grub/menu.lst.

Try this command.
```
apropos text editor
```
What do you get from that?

---

### Post by doobit on 2007-03-21
> **ZeroWing said:**
> I've finally got Xubuntu installed, but given the problems I've had with it, I'd like to set Windows XP as the default boot option.

 How could I do this? I've seen how to do this on Ubuntu, but Xubuntu doesn't seem to know what Gedit is.

Xubuntu doesn't include gedit, but you can use nano the same way:
```

sudo nano /boot/grub/menu.lst
```

Then change the default boot number to where XP is in the list (-1 because grub starts from 0)

---

### Post by lloyd_b on 2007-03-21
> How could I do this? I've seen how to do this on Ubuntu, but Xubuntu doesn't seem to know what Gedit is.

Gedit is a Gnome based program, so it (as you've discovered) isn't included in Xubuntu by default.  The equivalent program in Xubuntu is "mousepad".

So: "gksudo mousepad /boot/grub/menu.lst" (in a terminal window), and change the value for "default".

Lloyd B.

---

### Post by arochester on 2007-03-21
See "Set Windows as Default OS when Dual Booting Ubuntu" at [http://www.howtogeek.com/howto/ubuntu/set-windows-as-default-os-when-dual-booting-ubuntu/](http://www.howtogeek.com/howto/ubuntu/set-windows-as-default-os-when-dual-booting-ubuntu/)

Note that using this method Windows might start at e.g. No4, but if you install a new kernel and don't delete the old version, Linux could become e.g. No4 and Windows No6. So it could boot into the wrong place until changed.

---

### Post by ZeroWing on 2007-03-21
Thanks, all.

 Everything's working fine now, but I'd like to change Xubuntu's theme. I've tried to download them, but I can't seem to find out how to install them.

---

### Post by mcduck on 2007-03-21
> **ZeroWing said:**
> Thanks, all.

 Everything's working fine now, but I'd like to change Xubuntu's theme. I've tried to download them, but I can't seem to find out how to install them.
I suppose that you can just extract them to ~/.themes (hidden directory inside your home dir)

---

### Post by ZeroWing on 2007-03-21
> **mcduck said:**
> I suppose that you can just extract them to ~/.themes (hidden directory inside your home dir)

 Hm... I'm not finding the file...

 Where's the search for files button when you need it?

---

### Post by mcduck on 2007-03-22
> **ZeroWing said:**
> Hm... I'm not finding the file...

 Where's the search for files button when you need it?

If it's not there just create it.

---

### Post by ZeroWing on 2007-03-22
> **mcduck said:**
> If it's not there just create it.

 Thanks. That solved it.:)

---

