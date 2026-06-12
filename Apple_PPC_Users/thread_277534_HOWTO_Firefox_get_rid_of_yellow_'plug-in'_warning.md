---
title: "HOWTO: Firefox get rid of yellow 'plug-in' warning"
date: 2006-10-14
forum: Apple PPC Users
---

### Post by DirtDawg on 2006-10-14
There is no Flash for (X)Ubuntu on PPC computers. But Firefox refuses to let us forget that and throws an awful yellow "warning" bar across the top every-single-time you try to open a page with the missing Flash plugin (or Java plugin if you're like me and too lazy to go through the rigamaroll to install it).

Since there's no option to get rid of it, here's how it's done:

Open Firefox, in the address bar, enter:```
 about:config 
```
in the filter line, enter:```
 plugin 
```
Find the option called:```
 plugin.default_plugin_disabled 
```
Double click it so it's set to **off**. 

Restart Firefox and you're done!
:KS

---

### Post by salguod on 2006-10-18
i used automatix to install the opera browser and several plug-ins (not sure which), and it is able to display many of the items which are not possible on my firefox browser.
Maybe that helps.

---

