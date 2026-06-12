---
title: "Changing the default theme color"
date: 2006-05-15
forum: Art &amp; Design
---

### Post by nigelenki on 2006-05-15
I hear there's a way to change the color of GTK+ themes, so that you can take a green theme and make it a grey theme or a brown theme and make it a blue theme.

Ubuntu's default themes-- especially in Dapper-- are quite nice looking, except that **brown is about the ugliest color in the universe** and they managed to take a good theme and make Windows XP beautiful when placed next to it.

Anyone have any clue as to how to change the Ubuntulooks color into something nicer, like a grey-blue?  While at it, the notification bubbles that come from update-manager and Rhythmbox are brown no matter what theme you're using, I want to tint them a different color too...

Some time someone needs to make a program to color shift the current theme, in case some color blind person decides to use eye-piercing yellow or ugly brown motifs that make the system look dead.

---

### Post by johnc4510 on 2006-05-15
If your talking about the window border colors, do this:
System>Preferences>Theme
Click on Theme Detail
Click on Window Border and go through the list to see what colors they change to
As for the bubble colors, I don't know

---

### Post by nigelenki on 2006-05-15
[QUOTE=johnc4510]If your talking about the window border colors, do this:
System>Preferences>Theme
Click on Theme Detail
Click on Window Border and go through the list to see what colors they change to
As for the bubble colors, I don't know[/QUOTE]

Nope.  I'm talking about keeping the same window border theme ("Human"), but changing its color.  What can be done through themes are as follows:

1.  Change the window border ("Human" etc)
2.  Change the control set ("Clearlooks" etc)
3.  Change the icon set

I want to change the colors of the theme, without changing the theme itself.  The colors, by the way, are controlled by the controls.  Nuvola and Clearlooks are blue, Lush is green, and Human is some sort of orange-brown.  They control the window border colors too.

---

### Post by duff on 2006-05-15
[QUOTE=nigelenki]I want to change the colors of the theme, without changing the theme itself.  The colors, by the way, are controlled by the controls.  Nuvola and Clearlooks are blue, Lush is green, and Human is some sort of orange-brown.  They control the window border colors too.[/QUOTE]

Never tried it myself, but try editing the appropriate file in /usr/share/themes/??????????/gtk-2.0/gtkrc

---

### Post by nigelenki on 2006-05-15
Wow, that's a big file.  Have to toy with it and see what happens.

---

### Post by deadlydeathcone on 2006-05-22
You might want to check this out:

[UbuntuLooks Pack]("http://www.gnome-look.org/content/show.php?content=37461")

It's a fairly large collection of color variations for the human theme, and I recommend the graphite mod especially.

---

### Post by JGKC9AYC on 2006-05-28
How about changing the background (brown) color for my splash screen?  It's not big enough to cover the entire screen & just doesn't look right with that brown background.
Thanks.

---

### Post by ComplexNumber on 2006-05-29
[quote=nigelenki]
Some time someone needs to make a program to color shift the current theme, in case some color blind person decides to use eye-piercing yellow or ugly brown motifs that make the system look dead.[/quote] its funny you should mention that, because i've had that idea written down in my diary for several months now. i just haven't got round to it. it was going to read the gtkrc file and display the colours next to a colour selector and the widget(and widget state) and allow the user to change the colours. because of gconf, the user would be able to see the changes in the theme immediately. when the user is satisfeid with the colours, they can click on "save", whereby the changes would be written back to the gtkrc file. that was a very rough plan anyway.

note that, sometimes the window borders are determined by the gtk theme. sometimes they have their own colour which the gtk theme doesn't change. i would have to incorperate that functionality into the program too in the form of some prior checks.

this functionality is going to be present in gtk 2.9 and gtk 2.10....so i wonder if its even woth it.

---

### Post by Nonno Bassotto on 2006-05-29
JGKC9AYC, you can change that in System-->Administration-->Login Window.

---

### Post by JGKC9AYC on 2006-05-29
[QUOTE=Nonno Bassotto]JGKC9AYC, you can change that in System-->Administration-->Login Window.[/QUOTE]

How so if i'm using a themed greeter?
Is there a way I can change the splash screen colors on the menu.lst?

---

### Post by Nonno Bassotto on 2006-05-29
menu.lst is a configuration file for grub, the software which presents you a list of operating systems just at the bootup. It can have themes, but those are very simple and cover the entire screen.
The splash screen I assume you are talking about is the one after you have done the login, before gnome is ready. You can change the background color for it under
System-->Administration-->Login Window
(I'm not sure this is the correct translation, my PC is localised in italian). It is the little coloured square under the themes.

---

### Post by fheinsen on 2006-05-29
Here's an all-orange version of Dapper's Human theme -- no brown anywhere.

Theme file:
[ATTACH]10254[/ATTACH]

Screenshot #1 (full screen):
[ATTACH]10255[/ATTACH]

Screenshot #2 (showing progress bar):
[ATTACH]10256[/ATTACH]

---

### Post by JGKC9AYC on 2006-05-29
I see what you're talking about.  I was under the impression that it wouldn't work with a GTK theme.
Thanks for the help!

---

### Post by ComplexNumber on 2006-05-29
i must be the only one who finds that new orange to be absolutely repulsive. the old brown was _MUCH_ nicer and easier on the eye.

---

