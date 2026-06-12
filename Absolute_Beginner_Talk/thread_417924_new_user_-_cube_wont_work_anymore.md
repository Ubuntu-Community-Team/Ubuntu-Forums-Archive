---
title: "new user - cube wont work anymore?"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by punkypine on 2007-04-22
ok so i just started using ubuntu, and i have it loaded on my laptop along with xp. i'm fairly confused right now, but i'm hoping to figure all this stuff out in time.

anyway, when i was testing it out, with the OS running straight from the CD, i enabled desktop effects and had the cube on as well. i could then rotate between workspaces.

now when i turn on desktop effects (and cube), their is only 1 workspace by default. so i then increased it to 4, but when i switch between them, it doesnt rotate like a cube, which was really cool. also, none of the workspaces besides the first have that bar on the bottom. how do i get that on there?

sorry if it sounds like a dumb question, lol.

---

### Post by johnny4north on 2007-04-22
what kind of video card do you have, and are the drivers for it are up to date?

---

### Post by punkypine on 2007-04-22
i have ati mobility radeon x300

and the drivers were up to date on windows... do i need to get different drivers now?

also, why would it work off the CD and not now?

---

### Post by johnny4north on 2007-04-22
do you have ubuntu 7.04.  if you do, go panel > system > administation > resticted drivers manager, then enable ati card.  you may also need to install another file fglrx  i think... dont worry someone that knows more, will help soon.:)

---

### Post by punkypine on 2007-04-22
i have 7.04

i enabled the ati card, restarted the computer, an when it turned back on, a restricted driver thing popped up in the top right. also, when i tried to enable desktop effects, it "composite extension not available"- before i atleast was able to enable them and use the wobble.

and uh.... fglrx? i dont know what that is or how to install it, lol

thanks for helping so for the replies

---

### Post by punkypine on 2007-04-22
so i found out what fglrx is and a guide to install it on 6.10, i dunno if its the same for 7.04.

also, there are ton of commands... do i just type them in terminal?

---

### Post by johnny4north on 2007-04-22
im eating diner.  help you find the fglrx file here panel > system > synaptic package manager. enter password.  click All to the left, then search for=fglrx.  check the box next to org-drvier-fglrx ,mark for installation. click apply then apply.  reboot pc.  there might be some editing in the xorg. file.  i dont know how to do this. some will help you with this final step.  good luck, the cube is worth the wait..:)       i have a nvidia 4000.  i dont know much about ati

---

### Post by DSn0wMan on 2007-04-22
I am using a X300 ATI card in my laptop.  There is no need for the restricted driver (fglrx) as the opensource one works better.

---

### Post by punkypine on 2007-04-22
ok i did that, it installed it, i rebooted, but still get the same issue when enabling desktop effects

edit: Dsnowman, can you explain to me how to get your setup? and remember that i'm a complete newb at linux lol

---

### Post by DSn0wMan on 2007-04-22
You may want to take a look here.

[http://ubuntu-tutorials.com/2007/03/28/enabling-the-cube-in-feistys-desktop-effects/](http://ubuntu-tutorials.com/2007/03/28/enabling-the-cube-in-feistys-desktop-effects/)

---

