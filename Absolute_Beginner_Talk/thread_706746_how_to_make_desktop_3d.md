---
title: "how to make desktop 3d?"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by mgoktwo on 2008-02-24
i want to make my desktop 3d...how can i do it?i looked at several forums but i could not get the right answer...help pls.

---

### Post by mwanstall on 2008-02-24
I'm assuming you're talking about the Desktop Cube from Compiz?

[http://compiz.org/Documentation/Documentation](http://compiz.org/Documentation/Documentation)

There's the documentation link...

And  here's a quick guide from google: [http://ubuntu-tutorials.com/2007/10/29/enabling-the-cube-in-compiz-fusion-on-ubuntu-710-gutsy-gibbon/](http://ubuntu-tutorials.com/2007/10/29/enabling-the-cube-in-compiz-fusion-on-ubuntu-710-gutsy-gibbon/)

---

### Post by Crooksey on 2008-02-24
1) Setup your xorg.conf for Composite and 3d acceleration
2) Install compiz-fusion

If you cant find how todo the above, then you are obviously not searching enough.

---

### Post by Paqman on 2008-02-24
If you have a recent version of Ubuntu then Compiz-fusion should already be installed. Make sure your graphics card drivers are up-to-date and then enable "desktop effects". Installing compiz-config-settings-manager will give you more control over all the effects, so you can customise the animations and effects.

---

### Post by aktiwers on 2008-02-24
Install compiz-config-settings-manager like this from Terminal (applications => accessories => Terminal)
and type:
```
sudo apt-get install compizconfig-settings-manager
```
and open it by typing:
```
ccsm
```Then disable "Desktop Wall" and enable "Desktop Cube".

To make it with 4 sides, go to your workspace switcher in your panel and right-click it with your mouse and pick "preferences" and set it to 4 Colums and 1 Row.

Done! :)

---

### Post by amyst on 2008-02-24
Follow this 2 page tutorial: 

[http://www.howtoforge.com/compiz-fusion-ubuntu-gutsy-gibbon-nvidia-geforce-fx-5200](http://www.howtoforge.com/compiz-fusion-ubuntu-gutsy-gibbon-nvidia-geforce-fx-5200)

The keyboard shortcuts will work once you enabled the special features in the Advance Feature (?) setting.

---

### Post by mivo on 2008-02-24
Before you try anything else, you should probably select *System -> Preferences -> Appearance* and select "Extra" in the "Visual Effects" tab. If this worked, proceed with aktiwers' suggestion, then go back to the Appearance dialog and choose "Custom". :) This is assuming that you use Ubuntu 7.10 / Gutsy.

---

