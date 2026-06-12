---
title: "Blank screen w/ underscore on boot"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by tel93 on 2008-02-18
On saturday, a problem occurred when trying to set up 2 monitors (my mum insists I have a 2 monitor configuration) and I think I might've done something there. On Sunday, when I tried to boot up my computer, Ubuntu loaded, and then I found (after the splash screen) the screen turning off 3 times, and then my computer just sits there with a flashing underscore! I can type text, but no commands. I've tried every command (via recovery mode) but nothing seemed to work. I can' install new drivers because internet doesn't work on recovery mode. How am I posting this? Live CD.

---

### Post by petersonjacob on 2008-02-18
when grub starts press e then select the 3rd item from the top and press e again and type .bak and then press enter, then press b to continue the botting process

so (whatever your linux kernel is).bak

hope it helps

---

### Post by tel93 on 2008-02-18
How do I know my kernel name? Sorry but I don't know anything!

---

### Post by tel93 on 2008-02-19
What exactly is that going to do? It doesn't sound like something that would let me go back to the original drivers and let me see my installation again.

---

### Post by oedha on 2008-02-19
what if you boot again......
then when it hangs up....press : crtl+alt+f2
can you login....
if yes.....type : sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by tel93 on 2008-02-19
Well that did nothing. Do I ned to reinstall?

---

### Post by oedha on 2008-02-19
that's the last option.......
but can you wait for other helps ?

---

### Post by tel93 on 2008-02-19
Okay. I'm desperste, I want my computer back!

---

### Post by Nick8692 on 2008-02-19
This has happend to me before
try configuring xorg by booting into recovery and typing:

**sudo dpkg-reconfigure --phigh xserver-xorg**

This will give you a seris of questions that will reset your display - just select the defult for each question (unless you know better)

If there is an error with one of the questions, or you finnish, restart and it should work fine.

you may have to reset your resolution after/

---

### Post by tel93 on 2008-02-19
Everyone keeps telling me that, and it doesn't work!

I think I might have to reinstall.

---

### Post by Therion on 2008-02-19
Do you have Envy installed?

---

### Post by tel93 on 2008-02-19
Yes.

---

