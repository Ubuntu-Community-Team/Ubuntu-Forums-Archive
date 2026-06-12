---
title: "Keyboard Layout, wtf?"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by Muppeteer on 2006-12-14
I´m wondering if this is normal in Linux, but i haven´t experienced it in other distros...

Whenever i use certain special characters, i have to press the key twice. Eg, 

Apostrophe
´ - had to press twice
it&#347; - pressed once, it goes above the letter....weird
^ - had to press twice
~ - pressed twice again

:-k 

I dunno what´s up with this or if it´s normal. But i did check my keyboard preferences and it´s set to UK board with dead keys and just chose generic 105 keyboard. I had a look in the layout options but there doesn´t seem to be anything relevant. 

Anybody have any ideas?

---

### Post by mcduck on 2006-12-14
It's normal, because the normal use for those characters is combining them with letters to make special characters used in some languages. If you only want the character you don't actually need to push it twice, but the next letter you press must be one that cannot be combined with that character. Space works fine for example.

---

### Post by tonywhelan on 2007-01-06
> **Muppeteer said:**
> I´m wondering if this is normal in Linux, but i haven´t experienced it in other distros...

Whenever i use certain special characters, i have to press the key twice. Eg, 

Apostrophe
´ - had to press twice
it&#347; - pressed once, it goes above the letter....weird
^ - had to press twice
~ - pressed twice again

:-k 

I dunno what´s up with this or if it´s normal. But i did check my keyboard preferences and it´s set to UK board with dead keys and just chose generic 105 keyboard. I had a look in the layout options but there doesn´t seem to be anything relevant. 

Anybody have any ideas?
In case you haven't sorted it out yet:

I had the same problem on a rebuild, and realise it was because when setting up I had said I wanted "US International" as my keyboard layout" rather than just plain "US".

Here's how I fixed fix it: 
(adapted with thanks from a post at [http://ubuntuforums.org/showthread.php?t=272494&highlight=change+keyboard+mapping](http://ubuntuforums.org/showthread.php?t=272494&highlight=change+keyboard+mapping)  )

1. Make a backup of the xorg.conf file: 
sudo cp /etc/X11/xorg.conf /etc/X11/xorg_conf_backup

2. Open the xorg.conf file in a text editor:
sudo gedit /etc/X11/xorg.conf

3. Find the following code:

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"

4. Delete the "Xkbvariant" line:
        Option		"XkbVariant"	"alt-intl"

5. Save the file.

6. Reboot the PC. 
After logging in may get a window telling you that Gnome has a different keyboard config to what X has. You need to tell it to keep the X version. The response buttons in this window are a bit confusing, make sure you read the message carefully before you choose.

cheers

Tony

---

### Post by jem7v on 2007-01-07
Or, if you want to do what TonyWhelan suggested by clicking buttons instead, I believe you can go to System -> Preferences -> Keyboard, then go to the Layouts tab. Click the Add button and decide what's going to work best for you.  If you want to stay away from the keys you have to press twice to get your character, I think you avoid layouts that are marked "with dead keys."  For the UK layout, don't use the International one. Just choose the United Kingdom option... I know that it looks like a heading for other options, but it's an option too.

then again, it might not solve the problem, but you could try! And I think it's less scary than editing your xorg.conf file, myself.

---

