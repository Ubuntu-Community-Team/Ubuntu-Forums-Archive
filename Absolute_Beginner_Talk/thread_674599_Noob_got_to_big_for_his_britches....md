---
title: "Noob got to big for his britches..."
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by jtbrookreson on 2008-01-21
Ok...

I know so little about linux and Ubuntu, it is sad. Quite sad.

But I managed to install 6.06 on a iBook G3 500 Mhz without a hitch...wireless worked...I was so happy. The world was beautiful....

I then started the computer in a different room (away from my wirelss netwrok within the house), and I got a bonobo activation server code 3 erreor...

So I looked it up on this fourm list.

I found a solution. Looked easy enough. Gave it a try. Rebooted....

Restricted Driver [FAILED]
Enabloing Configured Network [Failed]

then a terminal screen come up, with a whole bunch of type....eventually a blue screen comes up and says in the middle

Could not start the X server (your graphical envuiroment) due to some internal error.
Please contact your system Admin or check your Syslog to diagnose.
In the meantime this display will be displayed. Please restart GDM when the probelm is corrected.

Now, before I go and and try to fix this with my DeWalt circular saw...

could someone please try to help me?

Thank you very very very much.

-JTB

---

### Post by JoshuaRL on 2008-01-21
Okay, if the installer detected everything automagically then run:
```

sudo dpkg-reconfigure xserver-xorg

```

If not, I still have an idea for you.  Boot up the Live CD and print out the output of:
```

sudo gedit /etc/X11/xorg.conf

```

Then boot into recovery mode in Grub and make sure the file reads the same.

---

