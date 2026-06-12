---
title: "Debian Menu wont load??"
date: 2006-05-19
forum: Absolute Beginner Talk
---

### Post by Absolute Zero on 2006-05-19
Hello all, 
    I am trying to get the Debian menu installed in X and am having some trouble getting it to display.  I have gone into Synaptic and installed the menu package and have done ctrl + alt + backspace to restart X.  

The menu did not show up when I logged back into X so I right clicked on the menu bar and brought up sMeg;  I see the Debian menu displayed in the left pan and in the right pan but it is shaded out in both cases and can not click on the check box in the right pan to enable it. 

Any ideas?

---

### Post by mostwanted on 2006-05-19
The debian menu is always very tricky :) If you wait long enough it's bound to show up at some point.

Subscribing to this thread in hope someone will know a better method.

---

### Post by 5-HT on 2006-05-19
Have you tried installing menu-xdg?

I needed that to get the menu to show up in GNOME (wasn't needed for XFCE, dont' know about other DE/WMs).

Additionally, you may need to do an 'update-menus'

Hope that helps.

---

### Post by catlett on 2006-05-19
[QUOTE=5-HT]Have you tried installing menu-xdg?

I needed that to get the menu to show up in GNOME (wasn't needed for XFCE, dont' know about other DE/WMs).

Additionally, you may need to do an 'update-menus'

Hope that helps.[/QUOTE]
Thank you, thank you and thank you. menu-xdg did it. I had the Debian menu in Breezy but lost it in Dapper. Install menu didn't do it and I never heard of xdg until your post. 
My upgrade has been tough but at least with my Debian menu I am starting to feel comfortable in Dapper. I'm such a visual guy I need all those entries or I think the apps aren't there:)  Thanks for the tip.

---

### Post by 5-HT on 2006-05-19
[quote=catlett]Thank you, thank you and thank you. menu-xdg did it. I had the Debian menu in Breezy but lost it in Dapper. Install menu didn't do it and I never heard of xdg until your post. 
My upgrade has been tough but at least with my Debian menu I am starting to feel comfortable in Dapper. I'm such a visual guy I need all those entries or I think the apps aren't there:)  Thanks for the tip.[/quote] 
Glad you got it working! :)

---

