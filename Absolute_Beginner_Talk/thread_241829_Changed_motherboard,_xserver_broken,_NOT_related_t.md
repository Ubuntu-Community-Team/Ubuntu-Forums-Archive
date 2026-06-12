---
title: "Changed motherboard, xserver broken, NOT related to 10.3 update"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by Tom Brokaw on 2006-08-22
I went from an MSI KM4M-L to an Asus A7N8x Deluxe.  Same video card and hard drive.  I last used this computer a week ago and just turned it on again today, so I'm pretty sure it's not the busted update.  I saw no GUI whatsoever before the error.

When I started Ubuntu it went through the normal routine of listing what it was doing.  Then I got an error saying xserver couldn't start, and I should restart GDM when it was properly configured.  It asked me if I wanted to view the error, which I did, but I don't know what it meant and can't remember it.

I had a shell, but was not sure what to do with it.  I typed ```
sudo less /etc/X11/xorg.conf
```
and got my conf file, but I don't know how to edit it.  The arrow keys appear to just navigate.  Now I don't have a prompt; it says (END) 
which is highlighted, and I'm not sure how to get back to a terminal without rebooting.  Would rather not do a hard reboot.

Thanks for any and all suggestions.  Would greatly appreciate a pointer as to how to get a shell as a first priority.

---

### Post by bodhi.zazen on 2006-08-22
Tom Brokaw: gotta say love the avitar.

less is not an editor. Scroll (down)to the end of the file, type "q" (at any time), or use Ctrl-C to exit less.

to edit xorg.conf
```
sudo nano /etc/X11/xorg.conf
```

Otherwise you are in a shell.

---

### Post by Tom Brokaw on 2006-08-22
Bodhi,
thank you and likewise, and thank you.  

Got to a terminal, looking for a solution.  Typed "sudo shutdown now" but it brought me to a shell, I think... shell /= terminal, right? It says root, not my login.  

Edit, added -r switch to reboot, so I'm fine on that.

Will be looking for answers on my own; more responses certainly appreciated.

---

### Post by Tom Brokaw on 2006-08-22
Well, a reboot seems to have fixed it.  Typing this on Ubuntu box, not Windows box.  Thanks for the help, bodhi!

---

### Post by bodhi.zazen on 2006-08-22
It sounds as if you are logged in as root?

You are on "tty1" in a bash shell as if you wre running in a terminal in a window manager.

to shutdown, assuming you are root
```
shutdown -h now
```

to reboot
```
shutdown -r now
```
or
```
reboot
```

If you are not root add sudo (of course)

To configure X try
```
dpkg-reconfigure xserver-xorg
```
again, add sudo in needed.

I see you're too fast for me.

---

