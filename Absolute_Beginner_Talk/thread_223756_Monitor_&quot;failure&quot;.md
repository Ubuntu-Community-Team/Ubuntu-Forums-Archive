---
title: "Monitor &quot;failure&quot;"
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by Antinomy on 2006-07-26
Hey all.

Just bought a used (1 year old?) dell flat screen.

It works fine on my windows box.

But when I use it on my linux box (hoary hedge) it says "cannot display this video mode".

I am a total newbie.

Any suggestions?

Peace,

Antinomy

---

### Post by Antinomy on 2006-07-26
Oh yeah! Sorry. My box has a NVIDIA GeForce 2 Mx/Mx 400 vid card.

Thanks folks

Antinomy!

---

### Post by djsroknrol on 2006-07-26
you might try this in terminal:

```
sudo dpkg-reconfigure xserver-xorg
```

after you finish (go with the defaults as much as possible...

```
sudo /etc/init.d/gdm start
```

---

### Post by Antinomy on 2006-07-26
Thanks!

I did it, and here's what happened:

* Starting GNOME Display Manager...                                    [fail]

That doesn't sound good...am I right?

Antinomy

---

### Post by trent dillman on 2006-07-26
try restart instead of start on that command...

...or reboot :-)

---

### Post by Antinomy on 2006-07-26
I did! The whole mispucha. Same thing.

Perhaps I should just upgrade to dapper?

Anti

---

### Post by trent dillman on 2006-07-26
hmmm...post your xorg.conf here. maybe you need to set your connected monitor type?

---

### Post by Antinomy on 2006-07-29
Thanks for all your advice trent - but I upgraded to dapper, and all is good.

Additionally, dapper seems to deal well with my laptop - a problem I've had for quite some time now! Bonus!

Many thanks,

Antinomy

---

