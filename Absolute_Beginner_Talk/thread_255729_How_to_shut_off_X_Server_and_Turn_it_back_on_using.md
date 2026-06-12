---
title: "How to shut off X Server and Turn it back on using Term"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by essdee on 2006-09-11
Hey guys, I'm new to Ubuntu.  What is the command to disable X and then enable it again once I am finished installing the NVIDIA driver?

Thanks

---

### Post by blakesmith on 2006-09-11
I believe that "ctl + alt + backspace" will restart X while in Gnome.

---

### Post by az on 2006-09-11
sudo /etc/init.d/gdm stop

and then 

sudo /etc/init.d/gdm start

But you can just install the package and then hit CTRL-ALT-Backspace to restart X.

---

### Post by essdee on 2006-09-11
Yes it will restart it, but it will not shut it off for a period of time and then allow me to re-enable it later. :/

EDIT:

Azz, thanks.  Also- what is the package's name which I should look for?

---

### Post by Najand on 2006-09-11
Well you can open another session just using:
CTRL+ALT+F1
(Also Ctrl+Alt+F2~F6)
And if you want to go back to your X session:
ALT+F7

---

### Post by szf on 2006-09-11
Would telinit be a solution?

i.e.
$ telinit 1

To go into single-user mode, console only?

---

### Post by bodhi.zazen on 2006-09-12
It is not too hard. azz is correct, of course.

FYI you can restart gdm with:
[indent]sudo gdm[/indent]as well.

sudo telinit 1 will also work, but is a little overkill.
You would then run sudo telinit 2 after installing nVidia driver....

See here:

[url=http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION
]Install Nvidia driver[/url]

---

### Post by az on 2006-09-12
> **essdee said:**
> Yes it will restart it, but it will not shut it off for a period of time and then allow me to re-enable it later. :/

EDIT:

Azz, thanks.  Also- what is the package's name which I should look for?
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards)

Note: Most nVidia-cards will work if you just install the nvidia-glx ("nvidia-glx-legacy" for older cards) package, and run this command: "sudo nvidia-glx-config enable"

---

