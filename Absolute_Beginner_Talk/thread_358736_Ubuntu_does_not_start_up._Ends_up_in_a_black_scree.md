---
title: "Ubuntu does not start up. Ends up in a black screen.."
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by kramer65 on 2007-02-11
Hello,

I've installed ubuntu about a week ago. In the beginning I was a bit hesitent but after a few days I started apreciating it more and more. I started putting files on it and I started using it, until today.

I started it like I always do, just with grub. Then I get the loading screen with all the ok's after which it suddenly ends in a total black screen. I tried waiting for a while but that doesn't help anything..

Now I have files on there which I don't have in windows anymore..

WHAT CAN I DO??

---

### Post by %hMa@?b&lt;C on 2007-02-11
boot a live cd, mount the harddrive, copy the files off

---

### Post by arochester on 2007-02-11
Is the screen absolutely black and blank? Or is there some writing on it?

---

### Post by kramer65 on 2007-02-11
Ehm... ok thanks. But I'm not so advanced yet. 

'boot the live cd': ok, I can do that.
'mount the harddrive': what does that mean? How should I do that?
'copy the files off': meaning that I can then copy the files to something?

Does it mean that I have to install ubuntu again? Or can I somehow fix it?

---

### Post by kramer65 on 2007-02-11
@arochester
yes, the screen is totally black, not a single thing on it..

---

### Post by kramer65 on 2007-02-11
Hello,

I can start up ubuntu again (using it now) But I've had this problem a couple times now. Does anybody know what the problem might possibly be?

And one other thing: How do I start gparted? I cannot find it in the applications>system tools menu.. Any other place where it could be?

---

### Post by johanvandermeer on 2007-02-11
you probably should read up on the xorg.conf file, in the /etc/x11 directory

try: man xorg.conf

and also get the right video card driver. This may mean a visit to your local video card's website to get the linux driver for it (ATI cards -while okay now- used to have really crummy linux support).

I've had a completely black screen when i first installed it on my laptop, but i fixed it.
It's a thing that has to do with having the correct video card driver (linux version!) installed as well as having the right definitions in your xorg.conf.

---

