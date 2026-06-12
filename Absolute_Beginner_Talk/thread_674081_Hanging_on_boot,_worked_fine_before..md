---
title: "Hanging on boot, worked fine before."
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by Ludford on 2008-01-21
I have Ubuntu 7.04 dual booted via Wubi on my computer. It has worked flawlessly for the past 3 days but just now I couldn't get on :(

It gets to the bit with the ubuntu logo and the bar that fills with orange... The bar fills a little then just stops and hangs.

What can I do? It was working fine this morning . And I didn't do anything radical... the only thing I did do was plug my Ipod in to let it charge.

Any ideas?

---

### Post by Ludford on 2008-01-21
Anything?

---

### Post by gangrelsurf on 2008-01-21
Lets get some info:

boot up and in the grub menu, pick 'recovery mode'
You'll get a bunch of boot info streaming by. Let's see what it's trying to do when it hangs...

---

### Post by Ludford on 2008-01-21
> **gangrelsurf said:**
> Lets get some info:

boot up and in the grub menu, pick 'recovery mode'
You'll get a bunch of boot info streaming by. Let's see what it's trying to do when it hangs...

I don't have a grub menu... Wubi doesn't install it. It just modifies windows''s boot.ini to allow the choice to boot into linux.

I could try Ctrl + alt + f1 to get into a command line... could I do anything useful in there if I can get in?

---

### Post by gangrelsurf on 2008-01-21
Ahh.. I missed that part. I've never used Wubi. Sorry, I don't have a clue.

---

### Post by Ludford on 2008-01-21
Is there any commands I can enter to bypass the splash and force a login?

---

### Post by gangrelsurf on 2008-01-21
Like I said, I don't have a clue about Wubi in particular, but I'll assume that you do and know how to edit the boot options. Since this thing works off of the windows boot manager, I assume they are in boot.ini on windows partition. Where ever they are there must be a line that specifies the kernel to use. In Grub it looks like this:
```
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=f79e3441-530c-4e3e-b852-ac0a34a8d4fd ro vga=791 quiet splash
```

So you're looking for something like that.
Just take off the 'quiet' and 'splash' options and you'll have the boot messages instead of the splash, or make another boot option if you know how to do that. Also you could add 'single' to get into Single user mode, aka 'recovery mode'

Hope that helps.

---

