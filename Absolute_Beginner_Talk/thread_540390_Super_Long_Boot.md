---
title: "Super Long Boot"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by insub2 on 2007-09-01
[COLOR="Red"]***Originally posted in [HP Laptops Thread]("http://ubuntuforums.org/showthread.php?p=3263508#post3263508") but getting no responses***
[/COLOR]
[QUOTE=abrarey]I must admit that it takes me a lot of time, but I made it.
The ATI x1250 can works on Feisty.
When you boot the CD and the xserver fails and display the message you select no.
then in the console you type in this order:
    *  sudo -s
    *  killall gdm
    * apt-get install xorg-driver-fglrx
    * depmod -a
    * aticonfig --initial
    * gdm start

After that the xserver loads and you can install ubuntu.

When you install Ubuntu doesn´t load the restricted drivers so the same problems show up, but you can do the same and it works.

My laptop HP 6715b now works great, I´m focusing right now how to enable 3d effects when I get some news I will postit here.
:)[/QUOTE]

Has anybody else who has used this method experiencing extremely slow bootups?  It's taking my friends comp like 3 minutes to get to the login screen where mine (older w/ slower cpu)  takes less than a single minute.

also, they're running linux-mint.  I'm trying to figure out what is to blame.

also, how do i have it display verbose on boot?

---

### Post by coxy on 2007-09-01
To boot without the splash screen you can change the grub line for a single boot.

When grub is on the screen, select the Kernel you want to boot and press e (you may need to press it a second time). Go to the end of the line and remove quiet and splash. Press enter and then boot the Kernel.

---

### Post by Seisen on 2007-09-01
Tell him to install bootchart he can either search for bootchart in Synaptic or Add/Remove Programs or

```
sudo apt-get install bootchart
```

It will show you exactly how long everything is booting for

---

### Post by insub2 on 2007-09-03
> **Seisen said:**
> Tell him to install bootchart he can either search for bootchart in Synaptic or Add/Remove Programs or

```
sudo apt-get install bootchart
```

It will show you exactly how long everything is booting for

she's a her.

how does one use it?


Thnx

---

### Post by stmiller on 2007-09-04
Bootchart puts a .png image chart of what is going on in your boot process in 

/var/log/bootchart

Every boot makes a new .png image file of the chart. Very handy. :)

Check out this recent bootchart thread:

[http://ubuntuforums.org/showthread.php?t=531453](http://ubuntuforums.org/showthread.php?t=531453)

---

### Post by insub2 on 2007-09-05
> **stmiller said:**
> Bootchart puts a .png image chart of what is going on in your boot process in 

/var/log/bootchart

Every boot makes a new .png image file of the chart. Very handy. :)

Check out this recent bootchart thread:

[http://ubuntuforums.org/showthread.php?t=531453](http://ubuntuforums.org/showthread.php?t=531453)

THANKS

---

### Post by insub2 on 2007-09-06
Now what do i do with?

It seems to my untrained eyes that it is the fsck.ext3.
...isn't that only supposed to happen every 30 boots or so?

i've attached two of the charts.

---

### Post by insub2 on 2007-09-07
Solved...let's say.

did some looking.  found a link to this:
[http://ubuntu.wordpress.com/2005/10/12/tuning-the-filesystem-check-at-bootup/]("http://ubuntu.wordpress.com/2005/10/12/tuning-the-filesystem-check-at-bootup/")

used this bit of code:
```
tune2fs -c 60

```

and the result was a substantially faster boot.

---

### Post by miro_braun on 2007-09-19
hey guys.. i have kubuntu 7.04.. and it's boot up is f***ing sow... it takes more than 5 min..
i dont know what is it.. heres my bootchart:

---

