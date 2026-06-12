---
title: "trying to install Fingerprint bootsplash"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by nick24 on 2007-04-08
Hi :) 

Has anyone downloaded and installed the Fingerprint splash screen? If so can you please 
tell me how to install it on a edgy eft machine? Thankyou

---

### Post by ajmorris on 2007-04-08
> **nick24 said:**
> Hi :) 

Has anyone downloaded and installed the Fingerprint splash screen? If so can you please 
tell me how to install it on a edgy eft machine? Thankyou

I had it installed ages ago and can't remember how i did it, but if you go into "gconf-editor" (also in the menu  (applications >> System Tools >> Configuration Editor)) Navigate  apps >>gnome-session>>Options>>splash image change the key value to you splash screen image (must be a .png)

Also can you please upload that splash screen i wish to use it again:).

Also i assumed you were using gnome.

---

### Post by ajmorris on 2007-04-08
ah sorry you mean replacing the ubuntu "bootscreen". My bad i thought you meant GNOME's splash screen. follow this guide for that
[https://sourceforge.net/docman/display_doc.php?docid=40914&group_id=187765](https://sourceforge.net/docman/display_doc.php?docid=40914&group_id=187765) it requires a package called upsplash.

EDIT: sorry the package is called usplash no upsplash

---

### Post by nick24 on 2007-04-08
> **ajmorris said:**
> ah sorry you mean replacing the ubuntu logo. My bad i thought you meant GNOME's splash screen. follow this guide for that
[https://sourceforge.net/docman/display_doc.php?docid=40914&group_id=187765](https://sourceforge.net/docman/display_doc.php?docid=40914&group_id=187765) it requires a package called upsplash.

Than you very much. I will go ahead and try it.

---

### Post by Madmoose on 2007-04-11
I know someone has pointed out:
[https://sourceforge.net/docman/display_doc.php?docid=40914&group_id=187765](https://sourceforge.net/docman/display_doc.php?docid=40914&group_id=187765)

I used this splash for all of my boxes, but as of todays update it no longer works.  I don't know what changed, but I had to switch back to the default Ubuntu Splash. Saddness...

Moose

---

### Post by ppan76 on 2007-04-23
> **Madmoose said:**
> I know someone has pointed out:
[https://sourceforge.net/docman/display_doc.php?docid=40914&group_id=187765](https://sourceforge.net/docman/display_doc.php?docid=40914&group_id=187765)

I used this splash for all of my boxes, but as of todays update it no longer works.  I don't know what changed, but I had to switch back to the default Ubuntu Splash. Saddness...

Moose

I dont think the package is broke. I installed it yesterday and everything is working fine (Running Feisty)

Make sure your /etc/usplash.conf is using 1028x768 and have VGA=791 in your menu.lst

---

