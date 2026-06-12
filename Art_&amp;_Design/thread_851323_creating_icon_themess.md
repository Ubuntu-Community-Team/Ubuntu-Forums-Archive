---
title: "creating icon themess"
date: 2008-07-06
forum: Art &amp; Design
---

### Post by daz4126 on 2008-07-06
I've designed some of my own icons, but am having trouble finishing the theme as there seem to be loads of different names and naming conventions for each file. Is there a quick or automated way to create all of the necessary symbolic links as well as resizing to all the required sizes?

thanks,

DAZ

---

### Post by smartboyathome on 2008-07-06
> **daz4126 said:**
> I've designed some of my own icons, but am having trouble finishing the theme as there seem to be loads of different names and naming conventions for each file. Is there a quick or automated way to create all of the necessary symbolic links as well as resizing to all the required sizes?

thanks,

DAZ

Not currently, but if you make the icons as svg you won't have to resize them. Also, you can just use another icon theme as a template and put the icons in place of the appropriate file.

---

### Post by Giant Speck on 2008-07-07
OMG!  You finished the Googol icons?!?

---

### Post by daz4126 on 2008-07-17
...errr not quite yet! I've made some icons called ICE icons ( [http://gnome-look.org/content/show.php/ICE+icons?content=84852](http://gnome-look.org/content/show.php/ICE+icons?content=84852)) and the Googol ones will be based on these. It should take me a few weeks to get Googol icons out there, sorry for the delay.

DAZ

---

### Post by daz4126 on 2008-07-17
As smartboyathome says above, the best way is to find an established theme and use the icons already there. The symbolic links are relative (I could do with knowing how to create those...) so you only need to make copies of the icons that are not links, then delete any icons that you don't need in your theme. I use the Gnome icons as a starting point as they seem to be very complete.

I had some trouble just using scalable icons only as some programs seemed to need specific sizes, although I could be doing something wrong?

It seems strange that there isn't a program to do this for you - i.e. you create the relevant icons in svg format and it creates all the links for you and resizes inot png format too. If only I was better at shell scripting.... :(

DAZ

---

### Post by Hairy_Palms on 2008-07-19
ya couldnt have a program, because most theme designers set up links totally differently to each other, oh and to make symbolic links, open the terminal and type

ln -s orignal.png link.png 

simple :)

---

