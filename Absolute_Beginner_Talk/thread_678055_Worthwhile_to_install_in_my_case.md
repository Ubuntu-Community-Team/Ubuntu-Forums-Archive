---
title: "Worthwhile to install in my case?"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by Otharius on 2008-01-25
I've read all of the issues with the Radeon series, and I'm an owner of a 9250. When I try to load it from the "Install or Start Ubuntu" button after the disc boots it'll tell me about the low resolution mode, I hit okay and then it never loads. It sits on the screen where it has four lines of checks with [OK] at the right hand side.
It works fine on "Safe Graphics Mode" and I'm enjoying it :), I would enjoy installing it, but not at the (high) risk that I won't start correctly. So is there much I can do, or am I effectively just unable due to my 9250?

Also: When I'm looking at the window for graphics cards it still detects my integrated in the top slot as well, which I disabled in Windows, is it's function only disabled in Windows or has it cut off permanantly? (This is just more of a curiosity, I have no desire to use it.)

---

### Post by Cypher on 2008-01-25
The LiveCD is a good gauge of how things will behave when Ubuntu is installed on your hard drive. If you do choose to go ahead and install it, perhaps with the latest restricted ATI drivers you might get a better chance of the Radeon working..

---

### Post by startherepodcast on 2008-01-25
I agree with cypher. It was the same for me, Ubuntu Gutsy wouldn't even load in safe graphics mode. I had to install via VMWare in Windows. I suggest that look up on the forums if your card is supposed to work with the fglrx driver and if it is, try to install...

---

### Post by ugm6hr on 2008-01-25
According to ATI ([http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)), the Radeon 9250 is supported by their latest (proprietary) driver.

This is actually pretty easy to install on Ubuntu using Envy - see the link *Graphics Card Drivers* in my signature below.

So feel free to install in "Safe" mode, then run the Envy script, and it should work OK.  There is still 1 unresolved issue with the newest drivers though - AIGLX doesn't play nice with Compiz and video players - so you have to disable Compiz to watch video.  You can achieve that with a panel click though...

If you want it *really* easy - apparently Linux Mint comes with Envy as default installation.

---

### Post by Otharius on 2008-01-25
Thanks for all the help, I appriciate it. :)

---

