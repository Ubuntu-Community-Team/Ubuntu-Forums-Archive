---
title: "Missing Lines on the CLI"
date: 2006-05-18
forum: Absolute Beginner Talk
---

### Post by thomashauk on 2006-05-18
On the odd occation that I use linux without X I have noticed the the bottom three lines are off the bottom of the screen although the screen is fine when using gnome etc.
](*,)
Anyone know why this is and how to fix it?

---

### Post by WakkiTabakki on 2006-05-18
This is just a guess, but... 
You say that, when using gnome it's fine, but when you are in (fullscreen) text mode the bottom three lines are missing...

Are you using a CRT monitor? If so, could it be that the monitor is off-sync in text mode? 
There is usually a menu (OSD) on the monitor where you can adjust the height/width as well as the placement of the screen. These settings are usually saved in the monitor per resolution/refresh-rate...

Good luck
/N

Edit: I see this is posted in the "Beginner community", so just want to point out that this is (if the above is correct) completely non-linux related. Just to avoid any *this-would-never-have-happened-in-<insert you favorite op-system here>* rants ;)

---

### Post by thomashauk on 2006-05-18
[quote=WakkiTabakki]This is just a guess, but... 
You say that, when using gnome it's fine, but when you are in (fullscreen) text mode the bottom three lines are missing...

Are you using a CRT monitor? If so, could it be that the monitor is off-sync in text mode? 
There is usually a menu (OSD) on the monitor where you can adjust the height/width as well as the placement of the screen. These settings are usually saved in the monitor per resolution/refresh-rate...
[/quote]

Nope It's an LCD on a laptop. An acer aspire 1362LC. There is someone else's notes on it here:
[http://people.arcada.fi/~westerlk/Aspire1362LC.html]("http://people.arcada.fi/%7Ewesterlk/Aspire1362LC.html")

---

### Post by WakkiTabakki on 2006-05-18
Ok, then! There you go...

Open the file /boot/grub/menu.lst by typing this into a terminal:
```
sudo gedit /boot/grub/menu.lst
```
Scroll way down 'til you see something like this:
```

title       Ubuntu, kernel 2.6.15-22-686
root       (hd0,1)
kernel     /boot/vmlinuz-2.6.15-22-686 root=/dev/hda2 ro vga=0x323 quiet splash
initrd      [etc...]

```
See the line starting with kernel, and that it has a parameter (vga=0x323) change 0x323 into 773 as the page you referred to states (I have 0x323 there, you may have something else...).
Reboot and see if it works!

/N

---

