---
title: "Need help install restricted formats, please."
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by L Campbell on 2007-12-11
I tried using the method described here:-   [http://tinyurl.com/r9oot](http://tinyurl.com/r9oot)  to install the Restricted Formats on my Gusty system.

For whatever reason it didn't work out totally the way it was supposed to and have enclosed a screenshot of the error message.

I then went to Synaptic, shearched for 'broken' files and got this other screenshot.

When I tried to re-install these files from Synapric, they still ended up as 'broken' files, so I did a 'fully remove'.

Other than following the directions at the above URL, is there something else I could have done to get this install to work?

---

### Post by crjackson on 2007-12-11
Try this...

Menu your way to  System>Administration>Software Sources

Then enable all your extra repositories.

Somewhere in the process it should update your apt-get.

Then go to the Application menu > Add/Remove > select the drop down box that indicates ALL Available Software > Search for "Restricted" or "Restricted Extras"

Then select to apply the Restricted Extras...

That MIGHT do the trick.  You may have to first remove them if they are indicating all ready installed, then reinstall.

---

### Post by rsambuca on 2007-12-11
You have to open a terminal and run```
sudo apt-get -f install
```

---

