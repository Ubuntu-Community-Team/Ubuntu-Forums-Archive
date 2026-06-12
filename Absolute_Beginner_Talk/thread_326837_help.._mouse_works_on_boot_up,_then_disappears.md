---
title: "help.. mouse works on boot up, then disappears?"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by GrahamPR on 2006-12-28
eep.

hi. just trying out an install of ubuntu 6.06. Whilst the CD is loading the mouse cursor works fine. when the box in the middle disappears (the one showing window manager, nautilus etc) then the mouse cursor disappears, and the keyboard doesn't work. I can't even switch caps lock on and off.

I have a P3 933mhz, 1gb Ram, and have PS/2 mouse and keyboard. Have tried swapping mouse for known good one, and doesn't make a difference. I am typing this out on another keyboard, and I am just about to try booting Ubuntu again from disc with this keyboard.

Have treid searching the forums for similar problems, but most answers seem to need the keyboard to inact. 

Any suggestions? Thanks. Back soon. :)

---

### Post by wpshooter on 2006-12-28
Are you attempting to install from the ALTERNATE CD ?

If not, try it, it is text based and supposed to do a somewhat better job of hardware detection and configuration.

---

### Post by GrahamPR on 2006-12-28
thanks for the reply. keyboard change didn't help either. although I did notice with the mouse that the light on the back of the mouse still came on, so it must be recognising it someway?

I think I tried the Atlernate CD a while ago, but gave up on it as the formatting and partitioning options were too confusing.

Are there any cures for this CD version? ](*,)

---

### Post by GrahamPR on 2006-12-29
ok, I can get mouse and keyboard working by switching between ctrl-alt-f1 and ctrl-alt-f7 whilst logging in. would like a permanent fix if possible.

also ubuntu freezes up when going to log off/ switch off etc. :( 

and finally..... when trying to load up windows.. it seems to stall on the login user page (blue page). I click the username.... it then says "loading your settings" but doesn't go any further. doesn't freeze completely, because you can stiull move the mouse.

any ideas on these greatly appreciated. cheers.

edit .. for now I am stuck with my daughters p3 333mhz on a dial up link. :(

---

### Post by GrahamPR on 2006-12-29
at last! :D 

the mouse problem I got around by switching between ctrl-alt f1 and ctrl-alt-f7 when logging on. since I did the auto update it seems to be fine. now can't log onto windows anymore. ](*,)  get the sound, and "loading personal settings" message, but goes no further. 

oh well, least I'm connected back to the web to fix things.

I take it I can run my Thunderbird profile from C: ? should not matter which OS I am running? or do I assume wrong? :-k ubuntu is on my slave drive.

---

### Post by bodzasfanta on 2007-01-04
Hello!

I had a similar problem but thanks God someone told me a good way to fix it.

"In grub, hit e to edit the boot line. Then move the selection over the kernel line and hit e again. Move the cursor to the end of the line and add the following:
Code:

noapic irqpoll pci=routeirq

Then hit enter to get our of line editing mode and b to boot the modified kernel line.

This will set you up until you power down or reboot. Edit /boot/grub/menu.list to make it permanent." (thanks for Frem)

I hope I could help you

---

### Post by morphet on 2007-01-15
I find that most of the time, if the mouse/keyboard work during the boot-up process, and even in the sign in screen, but then stop working, /etc/X11/xorg.conf is to blame. Can you:

```
sudo gedit /etc/X11/xorg.conf 
```

And post the contents of the file? Good luck.

---

