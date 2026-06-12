---
title: "[SOLVED] I messed up dpkg-reconfigure xserver-xorg"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by cde on 2007-07-12
I ran dpkg-reconfigure xserver-xorg to disable 1280x1024 screen resolution because it gave me problems. After the setup completed, I typed sudo reboot and after the Ubuntu loading screen, it halts on a black screen. 

I can enter console from the black screen and I've tried running recovery. The xserver driver is set to vesa as it was by default. It can still boot from the Live CD. I assume the Video Adapter is an ATI because it's a Dell OptiPlex GX150 but I've already tried setting it to ati.

Lemme know if there's any other information I need to give. Thanks for any help.

---

### Post by aktiwers on 2007-07-12
This command will set your xorg back to default:
```
sudo dpkg-reconfigure -p high xserver-xorg
```

Then you should be able to log in to Gnome or KDE or whatever you use :)

---

### Post by cde on 2007-07-12
Thanks for the post but still no go :(

That command gave the 2 screens to specify driver and resolution which I both okayed the defaults but it still doesn't work.

---

### Post by Raineer on 2007-07-12
That means that the defaults are not working, maybe vesa is not working for you for some reason.

You also can do the following:
```
tail -20 /var/log/Xorg.0.log
```
to see the last 20 lines of your X log, this will verify that is actually is the display that's crashing. X will also to fail if the mouse/keyboard drivers are wierd somehow.  Post the output of that if you can. If it is a display issue I'd expect the last line to say "No Displays Found", which is normal in this situation.  We need some info above that line perhaps.

Don't be afraid to run that dpkg command and try different drivers as well, maybe something else will work.

---

### Post by cde on 2007-07-12
I messed around and tried Intel. it worked :)

Thank you.

---

