---
title: "Putting new downloads onto the menu list"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by spionfox on 2007-01-14
Hi. Small beginners problem I wonder if anyone can help me with.

When I download new apps from the 'official' repositories using Synaptic, the program name and icon get listed in the right category on the programs menu. However, when I download from 'multiverse' for example, I have to do this manually. Through trial and error I managed to get the programs listed in the right places but am struggling to get an appropriate icon for the program.

As an example, I have downloaded Pacman and Pingus for my daughter and have managed to get them listed into the 'Games' section of the menu but the icon for each is just a standard white box default type icon. When I click on the icon section when adding the program to the menu there is no obvious icon set from which to choose. As mentioned earliewr, this problem does not happen with downloads from the standard repositories.

Is there an easier way to add new programs to the menu? Am I doing something wrong? How do I get an appropriate icon? So many questions!

Finally, and on an associated point, when I manually add a menu item the first place I am sent to look is in usr/bin. This threw me at first as I had to backtrack to usr/games to find the correct references. As someone trying to make the switch from Windows it confuses me that programs are kept in different folders! Is there an easy way to see where programs are placed? Maybe I missed something at the initial download stage?

Thanks for any help anyone can give :-)

---

### Post by Penguin Power on 2007-01-14
hi, to change the icons of your menu items right click on "applications" and then "edit menus"

find the app you want to change and right click on it, select "properties", and from there you just click on the existing icon to change it to a custom one.

---

### Post by mcduck on 2007-01-14
Usually programs put their icons in /usr/share/icons or /usr/share/pixmaps, so when you are creating a menu entry take a look at these directories and you have a good changes finding the right icon..

---

### Post by Ecthelion on 2007-01-14
> As an example, I have downloaded Pacman and Pingus for my daughter and have managed to get them listed into the 'Games' section of the menu but the icon for each is just a standard white box default type icon. When I click on the icon section when adding the program to the menu there is no obvious icon set from which to choose. As mentioned earliewr, this problem does not happen with downloads from the standard repositories.

Internet is your frien ;-)
If you don't find an icon, use google image search, set picture size on small and search for the name of the program ;-)
Usually the fastest way.

> Finally, and on an associated point, when I manually add a menu item the first place I am sent to look is in usr/bin. This threw me at first as I had to backtrack to usr/games to find the correct references. As someone trying to make the switch from Windows it confuses me that programs are kept in different folders! Is there an easy way to see where programs are placed? Maybe I missed something at the initial download stage?
I don't understand this.
When you want to run pingus, you don't have to put as command /bin/pingus or something like that.
If you just tell the starter to run "pingus"  (whitout the ") it should work
Commandline knows what you want when you do that ;-)

---

### Post by ekka on 2007-01-14
> **Penguin Power said:**
> hi, to change the icons of your menu items right click on "applications" and then "edit menus"

find the app you want to change and right click on it, select "properties", and from there you just click on the existing icon to change it to a custom one.

Even I have many of my packages in the menu with the “standard white box default type icon” as spionfox says. How do I change it to the icon which comes with the package, And not to a custom icon?

---

### Post by spionfox on 2007-01-14
> **Ecthelion said:**
> Internet is your frien ;-)
When you want to run pingus, you don't have to put as command /bin/pingus or something like that.
If you just tell the starter to run "pingus"  (whitout the ") it should work
Commandline knows what you want when you do that ;-)

Yes, but it's for the kids so it needs an icon rather than an off-putting (to them!) CLI!

---

### Post by spionfox on 2007-01-14
> **ekka said:**
> Even I have many of my packages in the menu with the “standard white box default type icon” as spionfox says. How do I change it to the icon which comes with the package, And not to a custom icon?

This is the crux of my problem. In fact, does the downloaded package even include an icon anywhere?

---

### Post by spionfox on 2007-01-14
> **mcduck said:**
> Usually programs put their icons in /usr/share/icons or /usr/share/pixmaps, so when you are creating a menu entry take a look at these directories and you have a good changes finding the right icon..

Can't see an suitable one there. Do downloaded apps often not include their own icon?

Thanks for the reply.

---

### Post by riven0 on 2007-01-14
Sometimes they do, but a lot of times it depends on where the program installed it. If you've installed Pacman, try to find the installation file in /usr/share and see if it has an icon there.

---

