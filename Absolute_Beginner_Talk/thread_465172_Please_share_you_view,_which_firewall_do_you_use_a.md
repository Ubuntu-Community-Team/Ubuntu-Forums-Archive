---
title: "Please share you view, which firewall do you use and why?"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2007-06-05
Hi
Thank you for reading my post
Can you please explain which firewall do you use and why?

Thanks

---

### Post by Acglaphotis on 2007-06-05
Linux has a built-in firewall at the kernel, and there are no ports listening i believe. If you want a GUI for the firewall install firestarter.

---

### Post by alanphil on 2007-06-05
I don't run a software firewall on Ubuntu. I have a hardware router on my home network and the Ubuntu machines are always behind this router.

---

### Post by xpod on 2007-06-05
I use the built in firewall but being as i dont really have a clue about iptables i use firestarter to allow ics.nfs & ssh on the pc`s about the house.
We have two seperate ip address compliments of our isp so have never really needed a router......yet.:D

---

### Post by silent1643 on 2007-06-05
bah, i was using firestarter just because it had a nice gui that would show you the attacks and it ran in the background... but now i dont even load it up, as the days go by in ubuntu you realize you really dont need anything other than a few firefox extensions to block unwanted scripts, ads, or flash. woot

---

### Post by Gina on 2007-06-05
I've found Ubuntu like a breath of fresh air after M$ Windows.  Security built in and pop-ups and other irritations easily blocked in Firefox :)

---

### Post by starcraft.man on 2007-06-05
I agree with the above, I run the simple IPtables with no firestarter or other gui. The only other security measure I take is 3 extensions I think are really important in firefox on any OS. [No Script]("https://addons.mozilla.org/en-US/firefox/addon/722") (stops all javascript from running on pages until you authorize, and prevents cross site scripting flaws, the latter is VERY important), [Ad block Plus ]("https://addons.mozilla.org/en-US/firefox/addon/1865")(one click blocking of ads on sites), and [cookie safe]("https://addons.mozilla.org/en-US/firefox/addon/2497") (powerful cookie manager that has snap to filtering like no script and allows blocking of 3rd party cookies). Thats it, the browser really may be the most insecure part of Ubuntu, thats why you need to lock it down.

---

### Post by Chayak on 2007-06-05
I've got firestarter on my laptop but for my network I have a smoothwall firewall connected to the cable modem.

---

### Post by southernman on 2007-06-05
> **starcraft.man said:**
> I agree with the above, I run the simple IPtables with no firestarter or other gui. The only other security measure I take is 3 extensions I think are really important in firefox on any OS. [No Script]("https://addons.mozilla.org/en-US/firefox/addon/722") (stops all javascript from running on pages until you authorize, and prevents cross site scripting flaws, the latter is VERY important), [Ad block Plus ]("https://addons.mozilla.org/en-US/firefox/addon/1865")(one click blocking of ads on sites), and [cookie safe]("https://addons.mozilla.org/en-US/firefox/addon/2497") (powerful cookie manager that has snap to filtering like no script and allows blocking of 3rd party cookies). Thats it, the browser really may be the most insecure part of Ubuntu, thats why you need to lock it down.Thank you, starcraft.man! 

To add to the OP's thread:

If you are sitting behind:  DSL/Broadband Modem > Router (store bought or self made) > Ubuntu Machine the only thing left to worry about is your browser. Starcraft.man took care of that for us. :D

Thanks again our Canadian friend!

---

### Post by starcraft.man on 2007-06-05
> **southernman said:**
> Thank you, starcraft.man! 

To add to the OP's thread:

If you are sitting behind:  DSL/Broadband Modem > Router (store bought or self made) > Ubuntu Machine the only thing left to worry about is your browser. Starcraft.man took care of that for us. :D

Thanks again our Canadian friend!

Your most welcome. Those 3 extensions are my only essentials (I have 20 or so others most are for convenience). They lock Firefox down so much I think it would take a stroke of luck to bypass them and exploit something. Most browser exploits for instance are triggered with javascript. Even if Firefox is vulnerable to it, if no script is on it prevents all scripts on a site by default and your safe. They are invaluable extensions that really should be built into Firefox 3 (I doubt it though, a lot of users get annoyed by all the micromanaging but it is worth it for security, just like Sudo :) ).

Anyway, just a bit of final Canadian words. Off I go, more people to help around here :).

---

