---
title: "xmodmap and loadkeys are ignored?! am i missing something?"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by Scarath on 2008-01-17
Hi

I am wanting to alter my keymap, so first i tried doing the whole dumpkey - edit - loadkey way but when i loaded the new keys up nothing was different >.<

So then i thought i'd give xmodmap a try, i gave it a few rules to test it out, restarted, it asked my if i wanted to use the rules in my .xmodmap and i said yes .... nothing had changed

Do i have to enable an option somewhere to allow my keymap to be changed? Or make the .xmodmap file a root file? 

Is there an answer?

thanks in advance

---

### Post by macogw on 2008-01-17
I think it has to be named .Xmodmap with a capital X.  That's what mine's named, and it works.

---

### Post by Scarath on 2008-01-17
thanks, changing the x - X worked, it came up with the option to use the rules when i stopped and started X again.
However now when i reboot or logout/in it does not give me the option to use the rules anymore.

Is there a way of manually loading .xmodmap like the "load mykey" way of doing it?

thanks

---

