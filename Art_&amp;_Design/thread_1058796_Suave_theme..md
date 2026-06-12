---
title: "Suave theme."
date: 2009-02-03
forum: Art &amp; Design
---

### Post by Gordon Bennett on 2009-02-03
Hi folks, I have posted a new GTK2 theme up in Gnome-looks that is designed to sit alongside the user.

[Link to Suave theme at Gnome-look]("http://www.gnome-look.org/content/show.php/Suave?content=98715")

Screens of it in action:

[Screenshot 1]("http://www.gnome-look.org/CONTENT/content-pre1/98715-1.jpg")

[Screenshot 2]("http://www.gnome-look.org/CONTENT/content-pre2/98715-2.jpg")

---

### Post by Sand &amp; Mercury on 2009-02-03
Looks pretty... suave, honestly. :D

---

### Post by Giant Speck on 2009-02-03
Nice, but the color scheme reminds me more of Pert shampoo rather than Suave shampoo.  :p

---

### Post by Crafty Kisses on 2009-02-03
Looks nice! Good job my friend!

---

### Post by Gordon Bennett on 2009-02-04
Thanks!  All made on Ubuntu :)

---

### Post by glotz on 2009-02-04
Great for some late night hacking! I wonder when will we see a proper dark theme included?

---

### Post by Crafty Kisses on 2009-02-04
> **Gordon Bennett said:**
> Thanks!  All made on Ubuntu :)
That's impressive my friend.

---

### Post by janicejan on 2009-02-05
Amazing, you had a nice concept, I really like dark themes especially the one you created with flowers...

---

### Post by Gordon Bennett on 2009-02-05
Cheers for the feedback, appreciated!

I've noticed with all dark themes that some apps that are not fully GTK savvy display dark text on a dark background (because they assume the background is white), making it rather difficult to read.  Many dark theme creators have commented on having the same problem.

I have thought of a solution which I will propose to the GDK/GTK team - I might try to implement it myself although I am new to the Linux commit cycle and will probably break something :P

The concept is this for non-gtk text: the more similar the text colour is to its background, the more it gets inverted to that background.

So for example, bright green text on a black background is largely unaffected because the difference between the two is large.  However, white text on a yellow background gets inverted more (relative to the background), because the difference between the two is low.

It might even tie in nicely to the text renderer's antialiasing system.

---

