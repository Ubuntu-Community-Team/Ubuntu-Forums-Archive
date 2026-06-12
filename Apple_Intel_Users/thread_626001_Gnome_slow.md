---
title: "Gnome slow"
date: 2007-11-28
forum: Apple Intel Users
---

### Post by blippy on 2007-11-28
Here's a weird thing. I tried Gutsy Tribe 2, Gutsy full release, and just last week I reinstalled Gutsy.

There's a strange phenomenon. When the box is relatively fresh, Gnome goes OK for a few days, and then works really slowly. I try to start a terminal, and it takes quite a few seconds to load up. The same happens when I, say, try to start up vim.

I found that on the first two occasions, I tried a different Windows Manager. When I eventually switched back to Gnome.I found that Gnome behaved itself properly. Really weird. What's going on? It doesn't make any sense.

I'm thinking of switching to a different Windows manager to see if I can persuade gnome to behave nicely.

On a slightly rambling note: anyone seen Dreamlinux? I've got it running in virtualbox, but it wont seem to boot properly from CD. Very weird. However, it looks really fast, and from what I've seen of it, it is GORGEOUS. Why can't Ubuntu have gorgeous graphics like that, instead of the stinky orange-brown mess that it currently has?

---

### Post by cyberdork33 on 2007-11-28
what hardware?

Are you using compositing?

Did you install proprietary graphics drivers?

---

### Post by Grey Box on 2007-11-28
> On a slightly rambling note: anyone seen Dreamlinux? I've got it running in virtualbox, but it wont seem to boot properly from CD. Very weird. However, it looks really fast, and from what I've seen of it, it is GORGEOUS. Why can't Ubuntu have gorgeous graphics like that, instead of the stinky orange-brown mess that it currently has?
I agree, ubuntu sometimes strikes me as a little bit TOO human with so much brown. Sometimes less is more (the default background of an OS should never be a dedicated colour - always grey/white/black in my opinion, because otherwise it always presupposes the tastes of the user and will offend more people than it pleases, and it looks butt ugly on a crappy display). The wallpapers for Ubuntu have improved though, and I don't think Ubuntu should deviate too far from brown/orange as its signature look, but Dreamlinux does look nice, though coincidentally it looks identical to my current Ubuntu desktop. It's a trivial matter to get the app-launcher happening and getting some pretty icons. 

There is a lot of professional art around for Linux, but nowhere near enough. Considering the amount of work people are putting into skins and so forth for short-lived software like media players, I'm surprised there isn't more for the basic OS.

---

### Post by blippy on 2007-11-28
> **cyberdork33 said:**
> what hardware?

Are you using compositing?

Did you install proprietary graphics drivers?

21" iMac from April 2007 (Intel dual core). No compositing. I'm using the restricted drivers provided with Gutsy.

---

### Post by cyberdork33 on 2007-11-28
> **blippy said:**
> 21" iMac from April 2007 (Intel dual core). No compositing. I'm using the restricted drivers provided with Gutsy.

Make sure you are getting 3d acceleration.
I am assuming you meant 20" iMac...
what does this output?
```
fglrxinfo
```

---

### Post by blippy on 2007-11-29
> **cyberdork33 said:**
> Make sure you are getting 3d acceleration.
I am assuming you meant 20" iMac...]

D'oh! Yes, 20". fglrxinfo outputs the following:

```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1600
OpenGL version string: 2.0.6473 (8.37.6)

```

How do I find out if I'm using 3-D acceleration?

---

### Post by cyberdork33 on 2007-11-29
> **blippy said:**
> D'oh! Yes, 20". fglrxinfo outputs the following:

```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1600
OpenGL version string: 2.0.6473 (8.37.6)

```How do I find out if I'm using 3-D acceleration?

You are. That was the output of the command. The OpenGL providor would normally be Mesa if you weren't.

I would guess that the problem is occuring somewhere in gnome, as it looks like Xorg is working properly. (If you are sure desktop effects are turned off). I really couldn't tell you the specific issue from here. Is it occuring after you install a specific application or utility?

---

### Post by blippy on 2007-12-01
Interesting. I am using static IPs. I logged out of Gnome, and switched to an XFCE windows manager. As it was starting up, it said it couldn't find the IP address of 'picasso', which is the name of my machine. I edited hosts so that picasso pointed to my internal IP, aborted XFCE, and went back into Gnome.

Everything seems to work much faster now. Freaky. It looks like either switching Windows Managers gives Gnome some kind of attitude adjustment :), or Gnome is trying to resolve IP addresses when you start any application. It doesn't make sense, but there we have it.

---

### Post by Steah on 2008-03-08
Thank you for posting your solution, Blippy.  I was having the same problems starting applications in Gnome.  Nothing quite as frustrating as sitting there waiting for a quad core machine to take 16 seconds to open a terminal.

I added my hostname to /etc/hosts, saved it, and everything pops right up now.

Thanks again!

---

