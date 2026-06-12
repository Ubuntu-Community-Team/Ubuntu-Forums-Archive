---
title: "Help creating icon set?"
date: 2007-09-03
forum: Art &amp; Design
---

### Post by exploder on 2007-09-03
I posted this in the LinuxMint forums but thought I would ask for help here too.

I would like to combine the best of three sets of icons to make a new icon theme. I want to have the mint start button and the mint logo for "All Applications also.

I have extracted the icon sets but I am not sure how to put it all together. Does anyone have a "How To" or simplified explanation for this?

The icon sets I am looking at are nuoveXT2.2 and Vista Inspirate 1.0 and of course the Mint icons.

I think these can be mixed and matched to make a very modern and elegant icon set.

Any help or information would be greatly appreciated. The icons are licensed under GPL so there is no problem with using them.

Thanks!

---

### Post by exploder on 2007-09-03
So far, I keep getting the Ubuntu logo on the menu instead of the mint logo. Also, I get the default Gnome icons if I sudo nautilus. 

Any ideas? Anyone?

---

### Post by exploder on 2007-09-03
Fixed half of the problem. The theme is now in the root profile. Still no luck with the menu...

---

### Post by backinthecity on 2007-09-03
I've never messed with this but it can be that you can replace the .icon/.png/ect files in a main install folder. use one of the install instructions. and just make sure to rename the files you insert in the folder (the ones you want) with the name of the original file.

give it a shot. Like i said i have no experence just not sure how to go about this..

good luck

---

### Post by exploder on 2007-09-03
I tried moving things around, no luck. The menu properties show that it wants to use "distributor-logo" but I am unable to set it to always use the mint logo. LinuxMint uses a variation of the slab menu. I am at a loss on how to fix this...

---

### Post by Hairy_Palms on 2007-09-03
i dont use the 'Mintmenu' but the two icons uses are usually distributor-logo.png and start-here.png,

---

### Post by redseventyseven on 2008-04-04
It may be possible to combine them by editing the index.theme file.

For example, I use a theme called UltimateGnome which brought up the Ubuntu distributor-logo (I wanted Mint, same as you).

Here's what I did (change UltimateGnome to whatever your theme name is)

```
gedit ~/.icons/UltimateGnome/index.theme

```

You should see a line which reads:
```
Inherits=Human,gnome
```

The Human theme contains the Ubuntu logo. Change it to:
```
Inherits=Cassandra,gnome
```

Save the file, and your distributor logo should change next time you start your computer.

You can probably use this technique to combine the three themes you mentioned. Install all three separately, then play around with the inheritances.

---

