---
title: "Installed NVIDIA driver in Edgy - gray screen"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by derspiess on 2006-12-05
I had this happen before, after I had installed some things from Automatix2, and wasn't sure what caused it.  Had to reinstall Ubuntu, having gotten most everything just about the way I wanted it :(    

Now I'm pretty sure what is causing the problem.  I installed the nvidia driver a couple nights ago & am getting a gray screen when I boot Ubuntu.  It get through grub, then shows the Ubuntu load screen, and when that is finished I only get a solid gray screen.  No login prompt, no sound, no nothing.  It looks like the hard drive spins intermittently but nothing else happens, even if I let it sit for an hour.

Any idea what I can do, other than reload Ubuntu & start over again?  :confused:

---

### Post by kakalaky on 2006-12-05
can you post the output of

```
cat /etc/X11/xorg.conf
```

and

```
cat /var/log/Xorg.0.log
```

---

### Post by stupidkid on 2006-12-05
What does your xorg.conf look like?

cat /etc/X11/xorg.conf

---

### Post by steve.horsley on 2006-12-05
You should be able to use Ctrl-Alt-F2 to get to a black&white text screen where you can log in and look at xorg.conf - maybe copy it to a usb stick so you can post it from windows. Or use a live CD to post it to us.

---

### Post by kakalaky on 2006-12-05
You can also install a text mode web browser like this:

```
sudo apt-get install links
```

or

```
sudo apt-get install lynx
```

I prefer links.

---

