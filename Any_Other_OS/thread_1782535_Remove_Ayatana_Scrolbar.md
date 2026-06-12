---
title: "Remove Ayatana Scrolbar"
date: 2011-06-14
forum: Any Other OS
---

### Post by dontgetshocked on 2011-06-14
Anyone know how to remove ayatana scrolbar and go back to original one? I hate it. (Mint 11)

Thanks,

---

### Post by JRV on 2011-06-14
To disable the overlay scrollbars in Ubuntu it is:
```

   sudo apt-get remove overlay-scrollbar
   sudo echo "export LIBOVERLAY_SCROLLBAR=0" > /etc/X11/Xsession.d/80overlayscrollbars

```

Is Ayatana Scrollbar in Mint the same as Overlay Scrollbar in Ubuntu?

In Ubuntu Natty the scroll bar is 3 pixels wide and when you touch it with the mouse a little thing appears to let you scroll.

Is this what you are talking about?

I am not familiar with Mint, but I hope this helps.

---

### Post by Perfect Storm on 2011-06-15
Moved to Other OS/Distro Talk.

---

