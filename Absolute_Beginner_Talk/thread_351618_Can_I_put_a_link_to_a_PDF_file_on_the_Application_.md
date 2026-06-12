---
title: "Can I put a link to a PDF file on the Application Menu on the top panel?"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by David Floyd on 2007-02-02
I was hoping to put a short cut (link) in the Applications Menu to a PDF file but I can't get it to work.

If I place a link on the desktop - that works, but when I use Alacarte Menu Editor and add an entry for a PDF file, nothing happens when I click on the new menu item.

Any ideas please,

Thanks,
David

---

### Post by shareMenaPeace on 2007-02-02
Hi, 
you can right click the menu - choose edit menu than choose --add item. I guess it works if you add the link to the command line or browse.
Sorry if this alacarte, than i dont know.

Cheers

---

### Post by RomeReactor on 2007-02-02
Hi. In Alacarte click on "New Item", and on the "Command" section write "evince" and the path to your document. For example, to open the [Nethack]("http://www.nethack.org/") guidebook i have on my home folder (my user name is "sho"), i would add:

```
evince /home/sho/nethack-343-Guidebook.pdf
```

in the menu.

---

### Post by David Floyd on 2007-02-02
> **RomeReactor said:**
> Hi. In Alacarte click on "New Item", and on the "Command" section write "evince" and the path to your document. For example, to open the [Nethack]("http://www.nethack.org/") guidebook i have on my home folder (my user name is "sho"), i would add:

```
evince /home/sho/nethack-343-Guidebook.pdf
```

in the menu.

Smashing, thanks, works a treat.

I was just thinking about experimenting along those lines, thinking about what I might have done in Windows.

David

---

