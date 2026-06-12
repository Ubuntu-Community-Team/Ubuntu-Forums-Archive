---
title: "Touchpad problem"
date: 2013-06-28
forum: Asus Ubuntu Support (CLOSED)
---

### Post by chemical1608 on 2013-06-28
Hello all,

I am a newbie to ubuntu and I using an ASUS K55-VM laptop and I recently installed 12.04 LTS. I wasnt able to right click with the touch pad/external logitech G 400 mouse as well. So, I did some research and I came across a solution which made the problem worse.Now, my right click works but my two finger scrolling is missing from the settings of the touchpad and two-finger scrolling no longer works. 

The commands I pasted on terminal are below:


sudo su -
echo options psmouse proto=exps > /etc/modprobe.d/psmouse.confAfter entering the above commands, I logged out and logged in again and from then on, I am facing this problem.Please helpThanks in advanceChemical

---

### Post by torteloni on 2013-08-04
I am having the exact same problem on my Sony Vaio SVE1711C5E. And I also went through the same procedure as the thread starter.

Though I am even more interested in vertical scrolling when moving along the right side of the touchpad. Two-finger scrolling would be an alternative for me that is less handy for me.

---

