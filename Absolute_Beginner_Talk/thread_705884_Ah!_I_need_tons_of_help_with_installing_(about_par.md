---
title: "Ah! I need tons of help with installing (about partitions)"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by biffinson on 2008-02-23
I am in the process of installing ubuntu right now

I want a dual boot system but i'm installing ubuntu first...

Well, i'm at the partition part and i deleted my old windows partition, and now i'm trying to create a 20gb ubuntu partition, but there are so many options and i don't know what to choose..  One dropbox has an option for fat, fat16 and a ton of other stuff, one is titled "mount" and i have no clue what to do.

Please help me :O

---

### Post by jpyanowski on 2008-02-23
The format for ubuntu is ext3 and your mount point is /   that is what I've used (many, many times  :roll:) Hopes this works for you.

---

### Post by biffinson on 2008-02-23
ok thanks :D

and it's telling me about swap space, should I assign something for it?  I'm not sure what it even is or how i would assign something, let alone what i would assign it to

ok so edit: i am creating a 1.5gb swap partition, the thing is... do i use ext3?  where do i mount it? how do i assign it? thanks.

---

### Post by warbird on 2008-02-23
i use 2gb, which is overkill for me. you would probably be ok with 512mb to 1gb if its just a normal desktop machine. filesystem should be swap, and mounted at /swap/

---

### Post by jcanini on 2008-02-23
/swap

1/2 gig of swap space is more then enough.
Its basicly for temp file which keep your programs running faster

/

Your root linux file system, ext3.is a good option

It is also a good idea to install windows first for a duel boot system, otherwise the boot loader will be overwritten.i.e when you turn the computer on you will only be able to boot windows unless you have a boot disc.

If you install Ubuntu after windows the grub boot loader will give you the option of windows or linux.

Have fun

---

