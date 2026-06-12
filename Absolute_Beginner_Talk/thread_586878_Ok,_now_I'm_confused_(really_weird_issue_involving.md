---
title: "Ok, now I'm confused (really weird issue involving partitions, sessions, and others)"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by Kymus on 2007-10-22
I've got 3 internal SATA drives; the first two are Ubuntu partitions and the 3rd is  a windows partition.

First time in, I installed from an Ubuntu Ultimate DVD. Then later, some funny things were happening and I decided to just use a regular Ubuntu DVD, so I reinstalled. Later on, I discovered that my second drive (which we'll call HD2) had Ubuntu Ultimate installed onto it just as it was on the first one. I dunno if this is normal, but I really didn't care; I'm used to all sorts of hardware and software failures, so I figured that keeping it around can't hurt any, and I kept it there.

 Now, since I'm paranoid about my data, I unhooked the SATA cable from HD2 when I reinstalled Ubuntu on HD1 (I had the original backup of all my data on there), this was probably mistake #1.. we'll see. So now on HD1 I've got vanilla (mago?) Ubuntu, and HD2 has Ubuntu Ultimate. I'm strange, I know.

Later, I needed to put Windoze on HD3 (the smallest of the 3)(it was originally on a different drive), and well, I don't trust Windoze much, regardless of what logic tells us, so when I put windoze on HD3, I unhooked HD1 & HD2 (I told you I was paranoid about my data!). Windoze installed... like windoze does... and I go back to my land of milk and honey: the Ubuntu partition. 

Here's where the problems start. X was giving me crap, cause it just doesn't like me that much. I didn't feel like posting to the forums and waiting for help to my problem, I wanted to fix things then and there. So, I reinstalled again. I was having some issues with a few little things anyway, so I figured whatever, and rationalized such actions. 

Whelp, you can possibly imagine what came next. Yup, I unhooked HD2 (even though i noticed later that my data was untouched through the previous reinstalls) because Ky doesn't take chances with his data. Nope nope. Reinstall, everything is beautiful again, angels sing.. etc etc. Afterwards, I hook HD2 back in, boot, and... wait, what's this? Oh, now grub looks different (ok, understandable. That's what happens when you mess with things), but my old friggan data... like... how everything looked before I reinstalled, is right there nice and pretty (right down to the problem with X. Thanks X!). 

Now I'll wrap everything up. 

If I hook in:

HD1, HD2, & HD3, then that = old data, old problem. Can't have that.
HD1 & HD3 = how things are supposed to look.

What's doubly interesting (for me at least) is that earlier today after I was done with Windoze, I decided to hook in all 3 drives for the hell of it. The first option on Grub boots to the "old data", the second option "other operating systems" no longer boots; it gives some error. Well, I booted to the "old data", and did actually fix the problem with X, and then after that I powered down, unhooked HD2, and booted to the functional setup. The problem I had with X on the "functional setup" was gone as well. 

All I want to know, is how the heck do I fix this hole I dug? ie: have all 3 drives hooked in, no problems. Reinstall Grub? If so, can someone link me to that?

much thanks to anyone who actually read all of my ramblings!

the moral of this story kids: don't be paranoid; put your data on the *external* drive ;)

---

