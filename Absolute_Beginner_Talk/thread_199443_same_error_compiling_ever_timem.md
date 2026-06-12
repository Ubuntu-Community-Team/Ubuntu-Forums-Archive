---
title: "same error compiling ever timem"
date: 2006-06-18
forum: Absolute Beginner Talk
---

### Post by szwety on 2006-06-18
when ever i try to compile with the  "./configure" comand anything i always get an error that i don't have gtk-+2.0 installed and i can't find a package for it any help?

---

### Post by AndyCooll on 2006-06-18
Have you installed "build-essential"?

Secondly, it might be worth opening up Synaptic, doing a search for gtk and installing whatever you consider appropriate.

:cool:

---

### Post by szwety on 2006-06-19
I tried all of that, and still the same error example equals, rhythmbox 9.4, and avahi. is there a way i can list the packages i've installed?

---

### Post by [S|G] on 2006-06-19
Can you post the exact error? Most likely you don't have the -dev packages. You might have, say, gtk-+2.0, but in order to compile something you'll need gtk-+2.0-dev.

You can use synaptic on ubuntu or adept on kubuntu to see a list of installed packages.

---

### Post by szwety on 2006-06-19
here's exactly what it says:
[INDENT]> checking for GTK20... configure: error: Package requirements ( gtk+-2.0 >= 2.4.0 ) were not met:

No package 'gtk+-2.0' found
[/INDENT]

that's after it goes through a bunch of other stuff.  but what is gtk anyways?

---

### Post by szwety on 2006-06-19
i guess i just had to get more gtk stuff, but now it's onto libglade, which should be an easy one, but man there is alot of stuff that i need for this program, maybe ubuntu simplified some things a little to much...

---

### Post by ifokkema on 2006-06-19
[QUOTE=szwety]i guess i just had to get more gtk stuff, but now it's onto libglade, which should be an easy one, but man there is alot of stuff that i need for this program, maybe ubuntu simplified some things a little to much...[/QUOTE]

Not really - Ubuntu just doesn't come with dev packages installed that very few people will use, and which will just take up lots of space on people's drives. Most people use the package manager to install software. People compiling their own stuff usually know how that works and can expect to need lots of dev packages.

By the way, the GTK libraries are used by apps to create graphical GNOME elements (windows, buttons, slides, etc).

---

### Post by [S|G] on 2006-06-19
By the way, why don't you install rythmbox and avahi from synaptic? I'm not sure about equals, but you can find those two ready to use.

---

