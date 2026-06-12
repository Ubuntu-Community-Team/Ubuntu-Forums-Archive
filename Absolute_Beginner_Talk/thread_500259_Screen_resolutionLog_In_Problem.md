---
title: "Screen resolution/Log In Problem"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by zweiundzwei on 2007-07-13
I've been having ongoing problems with my screen resolution (which should be 1280x1024). Everything worked fine when I used Dapper, but since I've updated it either doesn't go past 1024x768 or, if I do manage to get the right resolution, won't let me log in (it keeps redirecting me to the log in screen).

Now I was really fed-up with that situation and re-installed Dapper. This worked great on the Live CD, I got the right resolution and all, but as soon as I installed Dapper I had the same old problem again: I can't log in.
This might actually be an improvement because usually after installing Ubuntu on my hard drive the screen resolution goes back to 1024x768, but an OS that won't let me log in is pretty unusuable. 

Any ideas?

---

### Post by Happy_Man on 2007-07-13
If the LiveCD can get the resolution right, why don't you copy the LiveCD's version of xorg.conf onto maybe a USB drive, and then replace your install's xorg.conf with the LiveCD version. Perhaps that may work....

---

### Post by zweiundzwei on 2007-07-13
how do i access the data on the usb stick in the terminal?

---

### Post by BDNiner on 2007-07-13
I wouldn't use the terminal i would just browse to the file like i would in windows. then just drag it over to the usb stick. that is how i have copied files to and from my ubuntu box to my windows box.

---

### Post by Happy_Man on 2007-07-13
Just boot the LiveCD and plug in your USB stick. It should autodetect like normal.

---

### Post by zweiundzwei on 2007-07-13
The problem is I can't use anything else but the Terminal while using Linux on my computer, seeing how I can't get past the log in screen. And I need to get the xorg.conf file on there somehow.

---

### Post by Happy_Man on 2007-07-13
Oh... then we need to use plan B. Here we go:

First, mount your existing / partition: (assuming that it's /dev/sda2)

```
sudo mount /dev/sda2 /mnt/Linux
```

Now, for some copying:

```
sudo cp /etc/X11/xorg.conf /mnt/Linux/etc/X11/xorg.conf
```

And there we go! Reboot into your install and see if everything's OK.

---

### Post by zweiundzwei on 2007-07-13
are you sure that's the right command?
d```
mount: mount point /mnt/Linux does not exist
```

---

### Post by Happy_Man on 2007-07-13
Oh, sorry! Before my first command, put this in:
```
sudo mkdir /mnt/Linux
```

---

### Post by zweiundzwei on 2007-07-13
Did not work. :(

---

### Post by Happy_Man on 2007-07-13
Did you boot up a LiveCD first? 

Because, there's no reason for that not to work.....

---

### Post by zweiundzwei on 2007-07-13
I don't think I understood your question.
I copied the xorg.conf from the LiveCD configuration to my hard drive and then rebooted with the real Ubuntu. And I can't get past the Log In screen.
Last time, I "fixed" that by doing the dpkg-reconfigure thing, but then I got the wrong screen resolution which won't go away, no matter what, and I'm not too keen on having that problem again, either.

---

### Post by Happy_Man on 2007-07-13
Oh. Well, if you'd tried dpkg-reconfigure, i'm out of options. Sorry.....

---

### Post by zweiundzwei on 2007-07-13
Oh well. Thanks for your help, anyway :)

...anyone else got an idea?

---

### Post by BDNiner on 2007-07-14
I need some more information. what kind of video card do you have? I have a geforce 7300gt and i had a similar problem for a while. Every time i rebooted my resolution would go from 1440 x 900 to 1280 x 1024. it used to piss me off because no matter what i did this would happen, even manually editing the xorg.conf and only leaving 1440 x 900 as the only resolution didn't work. I finally used the screen resolution link in System>Preferences and check the option to make it my default and i stopped having the problem.

to get to your usb drive type cd /media/disk

---

### Post by zweiundzwei on 2007-07-14
My video card is Nvidia Geforce 6100.

I've tried installing the nvidia driver (though I never used that when everything was working fine in Dapper), manually editing xorg.conf and of course the system-preferences-screen resolution, which never has the right option available :(

Right now I deleted the 1280x1024 option from xorg.conf because this way I can use my computer, even if it's just 1024x768...
The thing I really don't understand is why my computer won't let me log in when I have the right screen resolution.

---

