---
title: "Screen Resolution/Ubuntu Distros"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by SquashlingChaotic on 2008-03-22
I am running Xubuntu.  Unfortunately, my version only supports up to a 600by800 resolution.  Most of the time, I use a resolution several notches higher.  As a result, everything looks large and grainy, and I feel like my screen is cramped.  

Does Ubuntu proper offer higher resolution?  Should I just update my Xubuntu?  Would Kubuntu improve the resolution?  

(note: My computer's other OS is Vista, so ability to run at speed is not an issue.)

---

### Post by R3d3y3 on 2008-03-22
vi /etc/xorg.conf and find your resolution 800x600 and put in 1024x768 and see if that works.

---

### Post by SquashlingChaotic on 2008-03-22
Pardon?  I really am a raw beginner.  Can I recieve these directions at an 'idiot' level?

No, really.  Directions for a true idiot, please.

---

### Post by angryfirelord on 2008-03-22
> **R3d3y3 said:**
> vi /etc/xorg.conf and find your resolution 800x600 and put in 1024x768 and see if that works.
vi?! I understand that vi is a wonderful tool to use, but certainly not for beginners!

In any case, you can do one of two things:
-open up your xorg.conf:
```
sudo mousepad /etc/X11/xorg.conf
```
Scroll down to modes. Add "1024x768" to the left of the current resolution. In other words, it would look something like this:
```
Modes		"1024x768" "800x600" "640x480"
```

or 

-use: ```
sudo dpkg-reconfigure xserver-xorg
```
This tool is handy in case you screw up your xorg.conf. If you decide to run it, keep the default settings (just press enter) until you hit the resolutions and pick the ones you want. When choosing the best resolution, select Medium and pick the best from the list. (that's the default one)

---

### Post by S.Milo on 2008-03-25
> **angryfirelord said:**
> vi?! I understand that vi is a wonderful tool to use, but certainly not for beginners!

In any case, you can do one of two things:
-open up your xorg.conf:
```
sudo mousepad /etc/X11/xorg.conf
```
Scroll down to modes. Add "1024x768" to the left of the current resolution. In other words, it would look something like this:
```
Modes		"1024x768" "800x600" "640x480"
```

or 

-use: ```
sudo dpkg-reconfigure xserver-xorg
```
This tool is handy in case you screw up your xorg.conf. If you decide to run it, keep the default settings (just press enter) until you hit the resolutions and pick the ones you want. When choosing the best resolution, select Medium and pick the best from the list. (that's the default one)

I seem to have the same problem, but I already have the exact mode listed :
```
Modes		"1024x768" "800x600" "640x480"
```

and I went through and selected the "medium" setting and whatnot, but I still do not get a choice to select the higher screen res.  Is there anything else I could try?

---

### Post by Therion on 2008-03-25
Open a Terminal:```
sudo gedit /etc/X11/xorg.conf
```
Using your **Tab** button to move around and **Enter** to select, accept all the default options UNTIL you come to the part (near the end) where it prompts you about screen resolutions.  The low-end resolutions will be selected (480 x 600, 600 x 800, etc.), meaning the selection will look like this: [ * ].

You're going to remove the "*" by using the spacebar since those resolutions suck.

Scroll up the list and, using the spacebar again, enter new "*" in THREE resolutions you find acceptable (3... no more, no less) and bearing in mind that -- THE HIGHEST RESOLUTION YOU SELECT HERE WILL BE THE NEW DEFAULT RESOLUTION.  Capped for emphasis.  :)

You will only see part of the list displayed... The higher resolutions are there, but you have to scroll up the list in order to be able to select them.

Save, okay the file-overwrite, exit and restart.  You should be good to go.

---

### Post by stchman on 2008-03-25
> **Therion said:**
> Open a Terminal:```
sudo gedit /boot/grub/menu.lst
```
Using your **Tab** button to move around and **Enter** to select, accept all the default options UNTIL you come to the part (near the end) where it prompts you about screen resolutions.  The low-end resolutions will be selected (480 x 600, 600 x 800, etc.), meaning the selection will look like this: [ * ].

You're going to remove the "*" by using the spacebar since those resolutions suck.

Scroll up the list and, using the spacebar again, enter new "*" in THREE resolutions you find acceptable (3... no more, no less) and bearing in mind that -- THE HIGHEST RESOLUTION YOU SELECT HERE WILL BE THE NEW DEFAULT RESOLUTION.  Capped for emphasis.  :)

You will only see part of the list displayed... The higher resolutions are there, but you have to scroll up the list in order to be able to select them.

Save, okay the file-overwrite, exit and restart.  You should be good to go.

Xubuntu does not come with gedit.  Mousepad is the default text editor.

---

### Post by stchman on 2008-03-25
> **angryfirelord said:**
> vi?! I understand that vi is a wonderful tool to use, but certainly not for beginners!

In any case, you can do one of two things:
-open up your xorg.conf:
```
sudo mousepad /etc/X11/xorg.conf
```
Scroll down to modes. Add "1024x768" to the left of the current resolution. In other words, it would look something like this:
```
Modes		"1024x768" "800x600" "640x480"
```

or 

-use: ```
sudo dpkg-reconfigure xserver-xorg
```
This tool is handy in case you screw up your xorg.conf. If you decide to run it, keep the default settings (just press enter) until you hit the resolutions and pick the ones you want. When choosing the best resolution, select Medium and pick the best from the list. (that's the default one)

No vi is not wonderful.  vi is a cryptic text editor for elitists.  I see no reason to use it, ever.

---

### Post by Therion on 2008-03-25
> **stchman said:**
> Xubuntu does not come with gedit.  Mousepad is the default text editor.
Well... Mousepad might be the better option then.  Use that instead.  :)

---

### Post by angryfirelord on 2008-03-25
> **stchman said:**
> No vi is not wonderful.  vi is a cryptic text editor for elitists.  I see no reason to use it, ever.
Well, back in the day when Unix hackers worked extensively with text files, using the arrows to move through 500 lines of code or to a certain position in the file was a pain. Having certain keystrokes do certain things allowed text editing to be done faster. It's still installed on every Unix and Unix-like OS out there today, so vi is a very cross-platform, cross-OS editor.

But yes, I find it horribly complicated and cryptic to use as well. nano & gedit serves well for what I have to do.
[QUOTE=S.Milo]I seem to have the same problem, but I already have the exact mode listed :
```
Modes		"1024x768" "800x600" "640x480"

```
and I went through and selected the "medium" setting and whatnot, but I still do not get a choice to select the higher screen res. Is there anything else I could try?[/QUOTE]
If you're trying to adjust the resolution through the XFCE tool, don't. Set it through the xorg.conf. If it's not working, then post your xorg.conf here.

---

