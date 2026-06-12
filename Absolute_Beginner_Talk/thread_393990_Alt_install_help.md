---
title: "Alt install help"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by Teegro on 2007-03-26
I literally just spent 2 days trying to get ubuntu in some form or another onto my laptop.

I've got two separate hd's so i thought i'd give it a whirl and keep xp on my other one and just swap when i need to.

Ultimately ive worked out that my laptop simply doesn't have anough oomph to run an install from the live cd (ubuntu wouldn't get past the keyboard slect and Xubuntu just refused to run the partitioner) so I've turned to the alt install.

Now I have managed to get Ubuntu installed but its all in a command line format! wheres the desktop? wheres the GUI? I can barely get my head round linux when it looks like windows and I struggle with DOS so I need serious help here!

How do I get the desktop running from the command line? Or am I destined to stare at a black and white screen until I swap hard drives again?

BTW: My machine is a Dell Latittude with 500mhz, 128mb ram, 8mb ati graphics and a 6.4gig hd.

Also I've installed the dapper of Ubuntu.

---

### Post by lamalex on 2007-03-26
to start the desktop type
```

sudo startx

```

---

### Post by Teegro on 2007-03-26
thanks!

is there any boot files i can alter so it automaticlly goes straight to it?

---

### Post by lamalex on 2007-03-26
I'm sort of surprised it doesn't. I've heard if this happens the easiest thing to do is to reconfigure X server (source: [http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm) figure 51) sudo dpkg-reconfigure xserver-xorg. also check /etc/init.d to make sure that gdm is in that folder.

---

