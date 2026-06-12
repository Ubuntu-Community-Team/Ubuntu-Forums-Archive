---
title: "Accidentally deleted add/remove programs"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by unntrlaffinity on 2007-04-02
Hi, I'm new to Linux/Ubuntu.  I was trying to customize the menus under the Applications, and I accidentally deleted "Add/Remove Programs".  Does anyone know how I can get it back?  It's kind of hard to google for.

---

### Post by Clay_Banger on 2007-04-02
what ubuntu are u running? kubuntu, ubuntu, xubuntu?

---

### Post by mikewhatever on 2007-04-02
System>Preferences>Menu Layout, click on Applications on the left and make sure Add/Remove is ticked.

---

### Post by unntrlaffinity on 2007-04-02
> **mikewhatever said:**
> System>Preferences>Menu Layout, click on Applications on the left and make sure Add/Remove is ticked.

I can't tick Add/Remove because I accidentally deleted it. 

I'm using Ubuntu, the Feisty Beta.

---

### Post by jem7v on 2007-04-02
Go back into Edit Menus... in the first level of menu it brings up, add a New Item.
Name: Add/Remove
Comment: whatever, really
Command: /usr/bin/gnome-app-install

If you deleted the program itself, reinstall the gnome-app-install package through Synaptic, apt-get, or aptitude.

---

### Post by unntrlaffinity on 2007-04-02
> **jem7v said:**
> Go back into Edit Menus... in the first level of menu it brings up, add a New Item.
Name: Add/Remove
Comment: whatever, really
Command: /usr/bin/gnome-app-install

If you deleted the program itself, reinstall the gnome-app-install package through Synaptic, apt-get, or aptitude.

You guys rock.  Thanks.  That's some awesomely fast feedback.

---

