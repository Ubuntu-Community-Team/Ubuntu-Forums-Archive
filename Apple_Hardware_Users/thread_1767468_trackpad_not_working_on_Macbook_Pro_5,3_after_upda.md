---
title: "trackpad not working on Macbook Pro 5,3 after update to 11"
date: 2011-05-25
forum: Apple Hardware Users
---

### Post by dbvisel on 2011-05-25
I have a dual-booting MacBook 5,3 which I was running 10 on with no trouble. I just upgraded to 11, and the trackpad doesn't work at all - no clicks, no movement. I've restarted several times - no change. Any ideas as to what I can do? 

I did play with my drivers a bit in 10 to get the trackpad to behave a bit more smoothly - but that was a while ago, and I'm not sure exactly what I can do. I realize this is a vague question . . . but thanks!

---

### Post by dbvisel on 2011-06-12
Still having a problem with this - an external mouse works fine, but I can't get the touchpad to work for the life of me. One thing I've noticed: if I go to the terminal and run tpconfig, there's a difference between if I do it as a user and if I sudo it:

dan@Nothing:~$ tpconfig
Could not open PS/2 Port [/dev/psaux].
dan@Nothing:~$ sudo tpconfig
Found Synaptics Touchpad.
Firmware: 8.96 (multiple-byte mode).

Does this mean anything?

---

### Post by phrawzty on 2011-06-23
I have a macbook pro 7,1 and am experiencing exactly the same problem as you (with identical tpconfig output).  Surely we can't be the only ones who've lost touchpad funcitonality on our macbooks after upgrading to 11.04 ?

---

