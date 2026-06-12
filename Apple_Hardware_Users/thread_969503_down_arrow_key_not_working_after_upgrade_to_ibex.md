---
title: "down arrow key not working after upgrade to ibex"
date: 2008-11-03
forum: Apple Hardware Users
---

### Post by anando on 2008-11-03
Hi

I upgraded to ibex from hardy on my macbook pro. Everything works out of the box including multiple monitors, wireless, compiz etc. Congratulations to the Ibex team.

However, I am plauged by this strange bug - my down arrow key does not seem to work any more. All the other arrow keys work. It works when I boot up OS X and also up to the point where I choose the kernel in the grub menu. But as soon as Ibex boots up, I am unable to make the down arrow key to have any effect.

Any advice will be gratefully received.

Thanks,
Anand.

---

### Post by kosumi68 on 2008-11-03
Upgrade suggests prior tweaks and settings on your computer. Personally I was bitten by my own xmodmap settings at one point. Also, mouseemu seems to still be around; make sure to uninstall it.

---

### Post by anando on 2008-11-03
> **kosumi68 said:**
> Upgrade suggests prior tweaks and settings on your computer. Personally I was bitten by my own xmodmap settings at one point. Also, mouseemu seems to still be around; make sure to uninstall it.

Ah - it turned out to be xmodmap ! Thanks a million. I got rid of my ~/.xmodmap file and re-started X. That seems to have sorted out the problem.

On a related note, I do see that my little key-board lights (e.g the one on the Caps Lock key) works only if I get rid of the mouseemu package. But then F11 and F12 don't work as middle and right mouse clicks. Is there a work around ? I would like to get rid of the mouseemu package and also have keys mapped to the middle and right mouse clicks. Your advice is highly solicited.

Thanks,
Anand.

---

### Post by kosumi68 on 2008-11-03
Yes, from this page you can click your way to your particular model: [https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages)

---

