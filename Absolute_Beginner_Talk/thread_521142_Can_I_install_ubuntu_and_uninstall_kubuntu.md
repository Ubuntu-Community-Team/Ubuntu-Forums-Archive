---
title: "Can I install ubuntu and uninstall kubuntu?"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by myk.dinis on 2007-08-09
ok...Here's my setup...for the past couple of weeks I've been messing around with (k)(x)ubuntu...

I would install one...complain to anyone who would listen (no one because I'm the only one in my area that knows linux) and I would change to another desktop...

I'm now on my 3rd install of k and I really just don't like it...but I finally got all my ducks in a row (part of the reason I changed so frequently was I had no idea how to do some basic type stuff and kept breaking the machine), my partitions are the right size...xp is playing nice...my xp/linux fat shared HDD is working perfectly...and /home lives on it's own happy little partition so I can do stuff like break the OS w/out worrying too much...

I really don't like kde all that much...it has a couple of nifty little programs and I like the way konqueror works with amarok and stuff like that...but overall it's somewhat irksome to use...

Some of the nicer features of u and x just don't map...they don't come over...and I REALLY like some of those nicer features...

What I need to know is: Can I install u and blow away k so there aren't any k style programs laying around...I really don't like the k programs that much...except a select few...K3B, Amarok, yakuake, and maybe katapult...

Also I love some of the context menus options like logout and stuff like that....pretty much I'm trying to figure out how to get the best of all the desktops...


BTW (edit) I need to know if my user files can be untouched by this..IOW will the switch wipe my files?

Sorry for the ramble...

thanks for the help!

myk

---

### Post by Martje_001 on 2007-08-09
Do in a terminal:
```
sudo apt-get install ubuntu-desktop
```
after that you have to remove all the kde packages trough synaptic.

You're files will not be touced!

---

### Post by crav on 2007-08-09
if you install as listed above, you'll keep k, as well as the new gnome. At the login screen, on the lower left, under sessions, you can choose which one to use. If for any reason you'd like to keep K as a backup, you can just install the ubuntu-desktop and not worry about uninstalling the k stuff.

---

### Post by myk.dinis on 2007-08-09
sweet!! Well, it's 4...AM, So, I'll go pretend to sleep before I have to be up in 3 hrs...

Night folks...!!

---

