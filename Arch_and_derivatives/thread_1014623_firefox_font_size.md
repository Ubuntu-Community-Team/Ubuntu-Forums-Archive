---
title: "firefox font size"
date: 2008-12-18
forum: Arch and derivatives
---

### Post by Benzaa on 2008-12-18
Hi,

I just finished installing my brand new arch in my laptop.

It has been an interesting experience and to be honest im loving it.

I installed fluxbox as my main window manager. It is really fast and I like the minimalistic approach. But, there are some things that I still need to fine tune to make it work the way I want it. 

Now I require your help, Im looking for a way to change the font of the menus.

Attached to this post there is a picture with some arrows pointing to the fonts that I want to change.

I also want to change the color of that part.

Could you please help me??

---

### Post by handy on 2008-12-18
Have you played around in the Firefox Menu: Edit/Preferences/Content Tab ?

That is where I set my font sizes for Firefox.

I can't help you with Fluxbox as I don't know it. :-)

---

### Post by Benzaa on 2008-12-18
> **handy said:**
> Have you played around in the Firefox Menu: Edit/Preferences/Content Tab ?

That is where I set my font sizes for Firefox.

I can't help you with Fluxbox as I don't know it. :-)


I tried that, but it doesnt work. I also want to change the font for other applications, such as my terminal, gimp, etc, etc.

I read something about gtk files, but in fluxbox there is none. So now im a bit lost.

---

### Post by handy on 2008-12-18
You will have to do everything by editing config files in the ***~/.fluxbox*** directory.

Hopefully they are well commented, as it sure makes it easier.

---

### Post by chucky chuckaluck on 2008-12-18
> **Benzaa said:**
> I tried that, but it doesnt work. I also want to change the font for other applications, such as my terminal, gimp, etc, etc.

I read something about gtk files, but in fluxbox there is none. So now im a bit lost.

*pacman -S gtk-chtheme* will get you the app you want. it will create a *.gtkrc-2.0* file for you and you can use it to change your gtk theme as well as control your font selection and size (the areas you pointed out are controlled by the gtk theme, not firefox). additionally, the .gtkrc-2.0 file will point to a *.gtkrc.mine* in which you may control which icon theme is used, but you have to create this file yourself. the format for selecting an icon theme in that file is *gtk-icon-theme-name= "whatevertftheincontheme'sstupidnameis"*.

---

### Post by Benzaa on 2008-12-18
> **chucky chuckaluck said:**
> *pacman -S gtk-chtheme* will get you the app you want. it will create a *.gtkrc-2.0* file for you and you can use it to change your gtk theme as well as control your font selection and size (the areas you pointed out are controlled by the gtk theme, not firefox). additionally, the .gtkrc-2.0 file will point to a *.gtkrc.mine* in which you may control which icon theme is used, but you have to create this file yourself. the format for selecting an icon theme in that file is *gtk-icon-theme-name= "whatevertftheincontheme'sstupidnameis"*.


Thanks for that, it worked like a charm.

I just need to find a way to change the color, but I think that I could just copy a gtk theme from gnome-eyecandy or similar website.

---

### Post by handy on 2008-12-18
> **Benzaa said:**
> Thanks for that, it worked like a charm.

I just need to find a way to change the color, but I think that I could just copy a gtk theme from gnome-eyecandy or similar website.

You can edit the theme's gtkrc file to fine tune the colours too.

You may find this how-to ineresting:

***_[http://ubuntuforums.org/showthread.php?t=377397](http://ubuntuforums.org/showthread.php?t=377397)_***

I use [***_Gcolor2_***]("http://gcolor2.sourceforge.net/"), which is fantastic for finding out the hex name of a colour & for seeing what a hex colour name looks like.

It is a tedious job changing colours in a theme for the uninitiated (maybe everyone) but once you have a theme set up how you like it, you can make a backup copy of it kept off your machine, & use it again & again, if you so desire.  I make mine easy on my eyes, I don't care for glamorous desktops, they only distract me & add eye strain.  

It is what happens to us when our eyes get old. :lolflag:

---

