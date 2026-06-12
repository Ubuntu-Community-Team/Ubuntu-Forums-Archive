---
title: "Strange characters"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by eirirlar on 2006-11-09
Hi all,

I've messed up. I did a dist-upgrade to Edgy. I got asked some questions about charsets or something from two different packages. I answered utf-8 in the first and iso-8859 or something in the other. I discovered what I had done when I did a dkpg-reconfigure of a package today - check the link to the pic:

[http://eirirlar.tihlde.org/strangechars.jpg](http://eirirlar.tihlde.org/strangechars.jpg)

Can anyone please tell me how to correct this? I think I have to reconfigure some packages but I don't know which ones, and also have no idea what to answer about the charsets.

Any help greatly appreciated.

---

### Post by subluid on 2006-11-15
i am experiencing the same problem since i migrated from ubuntu to xubuntu (very annoying when using midnight-commander)

appreciating help aswell.

---

### Post by po0f on 2006-11-15
It looks like a problem with ncurses, but I haven't run across it before, hope this helps.

---

### Post by kenrmcl on 2006-11-22
G'day there One & All,

Can anyone please tell me how to correct this? I think I have to reconfigure some packages but I don't know which ones, and also have no idea what to answer about the charsets.

     I haven't had this with Ubuntu, but I have seen it when installing other distros. IIRC it's simply the wrong choice for a terminal font. If you're using Gnome Terminal you can select "Edit | Profiles" and then choose whichever profile you use (default in my case). Once it's selected click on Edit and a dialogue will open. On the "General" tab, uncheck the "use system terminal font" check box and select another font from the "Font:" dropdown. You may have to choose a few until you find one that works. I have "monospace 12" selected and MC appears fine. 

     You can also set the font in the terminal resource file somewhere, but you'd have to check the Man pages for that. It's not hard, but it's too long ago since I did it for me to be able to give accurage information at the moment.

Hopefully you'll be back on track soon.
See ya
Ken McLennan
Qld, Australia

---

### Post by eirirlar on 2006-11-26
> **kenrmcl said:**
> You can also set the font in the terminal resource file somewhere, but you'd have to check the Man pages for that.

Hi and thanks for the replies.

The last one especially seemed very useful, but unfortunately I'm not running X on this machine. I've checked the man page for bash and some others, but have no idea where to look really. Is it possible for you to give me some more specific hints about where to look? These fonts are starting to get really annoying :)

Eirik

---

