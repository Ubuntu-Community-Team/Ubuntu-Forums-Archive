---
title: "Video settings for Tecra8000 laptop"
date: 2006-06-09
forum: Absolute Beginner Talk
---

### Post by Reprobate on 2006-06-09
Hello all,

I have been through this before and yet seem to be dealing with a new beast this time.

The short story is that I need help on where to insert the HorzSync and VertRefresh lines within the xorg.conf file in /etc/X11 directory to make my laptop display correctly.

I did put in the extra options for resolution (800x600, etc) but when I insert the  sync and refresh parameters X gives up and leaves me with the line prompt to log-in.

This seem so very simple, yet out of reach.  Can anyone help me?

Thanks much

---

### Post by Reprobate on 2006-06-09
TO whom... 
My problem was in not capatilizing the first words in each of the entries for Horiz and Vert in the xorg.conf file.

I did not realize that Xwindows was as picky about case.  It is!

With the correct case, I am on my way.

---

