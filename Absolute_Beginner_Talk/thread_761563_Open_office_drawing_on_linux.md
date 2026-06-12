---
title: "Open office drawing on linux"
date: 2008-04-21
forum: Absolute Beginner Talk
---

### Post by 05rutterb on 2008-04-21
OK, in short, drawing on open office sucks. Where can I find a program for Linux that's free, simple to use, but actually good for drawing things! I want something where the lines actually connect to one another! (preferably like paint for windows.)
Help would be appreciated. :)

---

### Post by nathandelane on 2008-04-21
The GIMP (raster graphics) or Inkscape (vector graphics).

---

### Post by amingv on 2008-04-21
> **05rutterb said:**
> (preferably like paint for windows.)
O...K...
Without a doubt you're looking for [Inkscape]("http://www.inkscape.org") and/or [The GIMP]("http://www.gimp.org"), two excellent programs that you'll probably grow very fond of.
As a plus you'd like to know that they're nowhere near the mediocrity of MS Paint. Enjoy!

Note: Inkscape has recently released v0.46, which is light years better than v0.45; if you're gonna go for Inkscape make sure you get that one (I'm not sure if they have updated the repos).

---

### Post by 05rutterb on 2008-04-21
OK, ill try out both of those programs and see which one i prefer.
Thanks for the help! :)

---

### Post by 05rutterb on 2008-04-21
OK, slight problem, I tried installing GIMP by copying and pasting into terminal "apt-get install gimp" and it came up with the following:
"E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?"

How would I install it?

---

### Post by IanW on 2008-04-21
You got that error because you should have typed
```
sudo apt-get install gimp
```
then given your password when asked.

The "sudo" is _very_ important for tasks like this, it means "Do this with root (administrator) privileges".

---

### Post by 05rutterb on 2008-04-21
Cool, thanks.

---

### Post by gpilkay on 2008-04-21
Usually, GIMP is already installed in Ubuntu.

There's also Tuxpaint which is a lot simpler, if you just want to jot stuff, it's fine too.  Though GIMP really does work just fine.  I use it all the time as I'm too cheap to spring for Photoshop and for my very amateurish use, I can't justify the expense anyway.  If you want, look at grantpilkay.com where I have some altered pictures, you can see the quality jump as I changed from Paint to GIMP.

---

### Post by sneeks on 2008-04-21
i agree with all above but if you really want a paint clone gnu paint is one,or for litle kiddies(i have them) tux paint,i think they are all in the repository.

---

### Post by The Cog on 2008-04-21
There is also Dia - I haven't tried it so can't comment on it, but I think it's in the repos. I think (from the name) it's aimed at making diagrams.

---

### Post by CujoQuarrel on 2008-04-21
Dia is sort of like Visio.

Dia/Visio is for making diagrams (think flowcharts)

It works pretty well for things like that.

---

