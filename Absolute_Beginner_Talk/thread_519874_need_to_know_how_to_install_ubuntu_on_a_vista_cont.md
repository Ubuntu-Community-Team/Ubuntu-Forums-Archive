---
title: "need to know how to install ubuntu on a vista contaminated laptop"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by Jonnothin on 2007-08-07
I just a new laptop and I can't boot linux for some reason with vista on it. help me destroy the vista partition please.

---

### Post by thefoolisme on 2007-08-07
You shouldn't have a problem booting up with Vista on the system.  Is the BIOS set to boot from a CD?  That would be the first thing I check because otherwise, I'm betting nothing else will work either. 

My recommendation for "destroying" Vista would be to download the Gparted live CD.  It's a lot more powerful than the gparted on the live CD.  It should be able to remove your vista partition.  However, BIOS has to be set up to boot from the CD for this too.

Link for Gparted:  [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by Hospadar on 2007-08-07
When you say you can't boot, do you mean that your machine won't boot of the cd at all, or that there are some problems loading up linux?

If the case is that it's just not booting off of the cd, you probably need to change the boot order in the bios to boot off of the cd before the hard drive where vista is installed.

If you see some options while booting up that say something like "F12 to enter boot menu" or "del to enter setup" hold down these keys and you'll get to some menus where you can change the boot order.  the laptop manual can probably help with this.

It may be the case that the manufacturer has hidden these options for a smoother looking boot.  try mashing all the F# keys while booting, as well as esc, enter, del, and backspace (you only need to be pressing one of these keys, but it won't hurt anything to mash them all while you are booting so you don't have to boot 15 times to figure out which one you should be using)

If you are getting to boot off the cd, but unable to load linux properly, post any error messages you might be having

---

### Post by Jonnothin on 2007-08-07
windows boots fine but when linux gets past starting up it goes to a weird screen

---

### Post by Jonnothin on 2007-08-07
windows boots fine but when linux gets past starting up it goes to a weird screen. Like right before the splash screen.

---

### Post by Arisna on 2007-08-07
What does the weird screen look like?  Is there text?  Error messages?

---

### Post by Jonnothin on 2007-08-07
> **Hospadar said:**
> When you say you can't boot, do you mean that your machine won't boot of the cd at all, or that there are some problems loading up linux?

If the case is that it's just not booting off of the cd, you probably need to change the boot order in the bios to boot off of the cd before the hard drive where vista is installed.

If you see some options while booting up that say something like "F12 to enter boot menu" or "del to enter setup" hold down these keys and you'll get to some menus where you can change the boot order.  the laptop manual can probably help with this.

It may be the case that the manufacturer has hidden these options for a smoother looking boot.  try mashing all the F# keys while booting, as well as esc, enter, del, and backspace (you only need to be pressing one of these keys, but it won't hurt anything to mash them all while you are booting so you don't have to boot 15 times to figure out which one you should be using)

If you are getting to boot off the cd, but unable to load linux properly, post any error messages you might be having

It doesn't come up with error message at all, it does weird effects on the screen, whether I do KDE or Gnome it does it in the same spot.

---

### Post by Jonnothin on 2007-08-07
Nope just silverish liquid.

---

### Post by Jonnothin on 2007-08-07
Anything special you have to do to burn Gparted?

---

### Post by skymera on 2007-08-07
i like your terminology for Vista. contaminted .
im stumped. can u get a photo? off a phomne?

---

### Post by thefoolisme on 2007-08-07
So, does that mean your laptop is booting to the CD in the BIOS?

Next question, what speed did you burn the ISO disk at?  And did you check the MD5 checksum and then check the disk for errors after burning.  Did you burn it at 4x or slower?  That is the suggested speed to prevent errors.

---

### Post by Jonnothin on 2007-08-07
Nope don't have a phone to do so. Ok here's the info vista came pre-installed, so it works fine. The problem is getting rid of vista and putting linux on it.
How do you burn with Vista?

---

### Post by Hospadar on 2007-08-07
is it the funky blue and grey x error (something like [this]("http://shaffox.files.wordpress.com/2007/02/xerror.jpg")?).  If that is the case, the problem is that the x server is having issues starting up on your machine.  this doesn't mean it won't work, but it may mean you have to do a text install with the alternate cd and then do a little research on your hardware to get your xserver configured properly so you can get graphics.

If that's not it, are you sure you are running the correct version of a livecd? for example if you are trying to install the x64 bit edition on a x86 32 bit (intel architecture) processor you might get some really funky behavior.  If you are using the 64 bit, try the 32 bit version and see what happens.

Also, are you seeing any linux boot messages at all before it crashes? or just the system boot messages.

---

### Post by Jonnothin on 2007-08-07
It goes through booting up all the drivers, the desktop manager etc. . . right after that it goes to a smooth silver screen with three bars that are black going across (horizontally)the screen. That's where the CD drive stops spining. No that isn't what the screen looks like and i've tried both versions.

My computer is an AMD64AthlonX2 Dual-core 1.7Ghz

---

### Post by Jonnothin on 2007-08-07
I downloaded GParted.
How do I burn it with vista?

---

### Post by Ub1476 on 2007-08-07
Download power-iso (search google) and burn it with 4x speed. 

Now, before you delete your Vista partition, Vista is not the problem. It's likely the hardware on your PC, or the Ubuntu CD is faulty.

---

### Post by Jonnothin on 2007-08-07
One of the CD's I used to install ubuntu on my desktop PC yesterday and it works fine. 
I've already burned GParted.

So do you run this llike a live CD?

By the way Vista is slower and less compatable even with updates, than XP so if I'm going to have any windows it's going to be XP

I'll be back and to tell you guys if I got it fixed or not.

---

### Post by Jonnothin on 2007-08-07
How do you opperate the terminal?

---

