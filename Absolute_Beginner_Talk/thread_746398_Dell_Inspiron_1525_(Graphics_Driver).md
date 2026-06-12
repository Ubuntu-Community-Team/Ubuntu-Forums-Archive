---
title: "Dell Inspiron 1525 (Graphics Driver)"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by cole24x on 2008-04-05
Intel Graphics Media Accelerator X3100  

and the chip set is Intel 965

any help for retrieving the drivers for this?

thanks 
Steven

---

### Post by cole24x on 2008-04-06
bump

---

### Post by cole24x on 2008-04-07
bump

---

### Post by jw5801 on 2008-04-07
It should be supported out of the box: [http://knowledge76.com/index.php/GutsyCompizIntelX3100](http://knowledge76.com/index.php/GutsyCompizIntelX3100)

What's happening that's making you think it's using a generic driver?

---

### Post by cole24x on 2008-04-07
it wont let me select higher visual effects, how do i tell if its installed right?

thanks

---

### Post by jw5801 on 2008-04-07
If that's the case follow the steps in the link I posted before. Your graphics card isn't on Compiz's whitelist, so you need to tell it that the card you have is ok for use with Compiz.

---

### Post by cole24x on 2008-04-07
ok i went to the link 

I put... into the terminal 

 sudo apt-get install compizconfig-settings-manager

it installed the manager i can see custom in visual effects but it still does not let me save

do i need to do somthing else?

thanks

---

### Post by jw5801 on 2008-04-07
> **cole24x said:**
> ok i went to the link 

I put... into the terminal 

 sudo apt-get install compizconfig-settings-manager

it installed the manager i can see custom in visual effects but it still does not let me save

do i need to do somthing else?

thanks

The part labelled "Directions" at the start that mentioned skipping checks was the most important part.

---

### Post by cole24x on 2008-04-07
yeah i tried that also. when i open that file there is already two lines with that on there, when i add a third line nothing happens. when i take two lines away and just have one line it acts like it doesn't have a vid driver installed.

what should i do?

thanks

---

### Post by jw5801 on 2008-04-07
> **cole24x said:**
> yeah i tried that also. when i open that file there is already two lines with that on there, when i add a third line nothing happens. when i take two lines away and just have one line it acts like it doesn't have a vid driver installed.

what should i do?

thanks

[Some](http://ubuntuforums.org/showthread.php?t=731476&highlight=intel+x3100) [research](http://brainstorm.ubuntu.com/idea/1266/) shows me that apparently lots of people are having problems with the X3100. The package containing the driver is "xserver-xorg-video-intel," apparently there's a newer version in Hardy which works quite well, so if you can wait 16 days until the final release you might have a bit more luck!

---

### Post by cole24x on 2008-04-07
ok thx for your time man :)

---

