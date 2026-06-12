---
title: "Compaq Armada M300 laptop white screen / no graphics"
date: 2005-07-30
forum: Absolute Beginner Talk
---

### Post by spudse on 2005-07-30
Hello, I just installed Ubuntu on my Compaq Armada M300 laptop. 

But, during the booting (or when X starts, I can't really determine) my screen turn white with a blue square inside it, the blue square fades into white within like 2 seconds.

This problem first occured when I hit enter to install Ubuntu. I rebooted and used vga=771 and it installed without a problem, but when the install is ready and Ubuntu boots, the screen fades into white again.

When my screen has faded into bright white, I can go to console with Cntr+Alt+F1 and login, but I cant get any graphics.

I found a topic about the same problem and the same laptop, but I don't understand what the solution was, maybe someone can help? This is the topic: [http://ubuntuforums.org/archive/index.php/t-32202.html](http://ubuntuforums.org/archive/index.php/t-32202.html)

Any help is appriciated (I'm really new to linux).

---

### Post by varunus on 2005-07-31
What that howto has done is:

- When your computer is booting and the menu for GRUB is showing (which has Ubuntu listed) press the "e" key.
- Look through the line, and delete the vga=771 parameter

Then try booting up (I forget what key it is, maybe b, its listed there).  Does that work?

---

### Post by spudse on 2005-07-31
Thank you varunus, it works.


The solution for other people with the Compaq Armada M300:

The key was "e" in grub.

Just remove "vga=771" and it boots like a charm.

---

