---
title: "Mouse pointer disappears on wake up"
date: 2010-11-06
forum: Apple Hardware Users
---

### Post by nolanpro on 2010-11-06
I know a "disappearing mouse" has been covered in other threads but my specific symptoms seem different from all the others that I have read.

This has been happening for some time now on 2 systems with 2 versions of ubuntu.

Macbook Pro 4,1 with ubuntu Jaunty 9.04
Macbook Pro 6,1 with ubuntu Mavertick 10.10

About 1 in 5 times I wake up from suspend, the mouse pointer disappears. I can still highlight and click on things as if it was still there. All the functionality seems to be there.

The ONLY way that I have found to get the pointer back is to log out and log back in (restart X)

Switching workspaces with ctrl+alt-RightArrow does not work as some threads have suggested. I even managed, without the pointer, to change resolutions with the NVidia X Server Settings but that didn't bring back the pointer.

It's not just close-the-lid suspend, it's also when I select suspend from the top-right power menu.

Any ideas? Thanks!

---

### Post by nolanpro on 2010-11-08
Ok so now changing my screen resolution using nvidia x server settings DOES bring my pointer back (but creates another world of pain)

Anyway, I'll keep testing, but the problem is so random, it may take a day or two for it to happen again.

The best thing I can hope for is a keyboard shortcut to a script that does something with nvidia or xrandr to refresh the resolution. I'll post my results here.

---

### Post by Forthy on 2011-03-15
Did you get any further with this?

I have precisely the same issue (although on Xubuntu) and am at a loss.

Logout/login seems to be the only solution, but it's mega inconvenient!

---

### Post by nolanpro on 2011-03-18
I never did find out what the problem was, but I did figure out a hack that made it work for me.

Try messing around with the xrandr command.

I usually have an external monitor connected to my laptop using Nvidia's TwinView so I can pick a few different 'xrandr -s' sizes. When ever I switch settings with xrandr, my mouse pointer comes back!

So if i'm on my laptop only at 1440x900, and the mouse disappears after a wake-up, i run 'xrandr -s 3120x1050' then back to 'xrandr -s 1440x900'

But this hack might only work for nvida cards with the proprietary nvida drivers.

---

### Post by NoBugs! on 2011-03-18
Try making a script with:```
modprobe -r appletouch
modprobe appletouch
```

Saving as "fixtouchpad.sh" or some other name, then:
```
chmod +x fixtouchpad.sh
```

Then when the mouse won't work, get to the terminal and type ```
./fixtouchpad.sh
```
to fix it :)

---

### Post by Forthy on 2011-04-07
Nice one guys, we'll see how we go! :)

---

