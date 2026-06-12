---
title: "@-sign in PPC Ubuntu"
date: 2010-02-21
forum: Apple Hardware Users
---

### Post by MahtiUbu on 2010-02-21
Hello all!

I have installed Ubuntu 9.xx on my old PPC iBook and I have run into a stupid problem: I cannot produce @-sign! All the tested button combinations around the space bar produce only " or 2 or nothing at all. Any suggestions, what to do? I have a Finnish keyboard. And while I am at it, one more question: where is the del-button (erase-forward)?

---

### Post by linuxopjemac on 2010-02-21
I guess that when you select the Finnish Macintosh keyboard from the keyboard selector (Preferences -> Keyboard) , you will have the &#8364; sign

---

### Post by MahtiUbu on 2010-02-22
Thank you, but perhaps I was not clear or the signs got messed up in transit. It is @-sign (at-sign, commercial-at) that i am after, not the euro-sign.

---

### Post by tom4everitt on 2010-02-22
You always have to do:

System->Preferences->Keyboard->Layouts.
make sure there's only finnish
click layout options
under "key to choose 3rd level chooser", check right win (which is your right apple-key).

If this doesn't work, tell me and I have an extra fix.

---

### Post by MahtiUbu on 2010-02-23
Thank you for the tip! The right-win thing actually did not work for me but left-alt did the trick.

---

### Post by linuxopjemac on 2010-02-23
I can also only get the left Alt to work, that's the way I have it set up too.

---

### Post by tom4everitt on 2010-02-23
Okay, I had that same problem. Although having it at alt mimics the OS X setup better, I didn't want it that way. 

If you're interested, here is a fix:

Enable right win as third level chooser.

Add the following to a (new) file named .Xmodmap in your home folder. 

```

clear control
clear mod4

keycode 37 = Control_L
keycode 104 = Control_R

add control = Control_L Control_R
add mod4 = Super_L

```

Run:
```

xmodmap ~/.Xmodmap

```

Now it should work. Next reboot xmodmap will ask you whether you always want to load this config-file (and hence make the change permanent).

Would be cool to see if it works for others than me :)

---

