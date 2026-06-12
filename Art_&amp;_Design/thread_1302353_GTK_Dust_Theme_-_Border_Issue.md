---
title: "GTK Dust Theme - Border Issue?"
date: 2009-10-27
forum: Art &amp; Design
---

### Post by kestal on 2009-10-27
Hello there, I am trying to look around to see if there is any way to increase the border around the window in the Dust GTK. For example, Darkroom has a bigger border around the window which makes it easier for the mouse to hover over the resizing part and I was wondering where I'd be able to look.

I checked the gtkrc file hoping to find a simple 'border' setting but after scanning through I wasn't able to find anything that was different from Darkroom. Is it not a setting in the initial file? Sorry for the first-time post about theming.

Any help would be great :)

---

### Post by mcduck on 2009-10-27
The setting will be in the Metacity theme files, not in gtkrc.

---

### Post by kestal on 2009-10-27
> **mcduck said:**
> The setting will be in the Metacity theme files, not in gtkrc.

hah, wow. thanks. I read: [http://ubuntuforums.org/showthread.php?t=438687](http://ubuntuforums.org/showthread.php?t=438687) and got a bit tunnel-visioned. I should have checked metacity as that would make sense.

I changed the 

  <distance name="left_width" value="#"/>
  <distance name="right_width" value="#"/>
  <distance name="bottom_height" value="#"/>

to 3 (just to test) and that worked then I wanted to changed the titlebar borders, when I tried to 

  <distance name="left_titlebar_edge" value="3"/>
  <distance name="right_titlebar_edge" value="3"/>

There was still no border around the titlebar of each window, as all it did was "seem" to only increases the padding between the buttons and the edge (no physical border). As I kind of wanted the same physical border all around.

Is there any way to solve this?

---

### Post by oedipuss on 2009-10-28
Something a bit unrelated to window borders but maybe of interest to you :
You can resize any window by using the window movement key (in System/Preferences/Windows, default is Alt) with the 2nd or 3rd mouse button and click-drag anywhere on the window. I don't remember exactly because I've changed the default shortcut. 
Makes resizing much more practical than hitting a border no matter how wide or narrow.

---

### Post by kestal on 2009-10-28
thanks for the alternative. that might come in handy for the future. :) Right now I am just trying things out. At the moment I am just looking for a way to complete the border around the titlebar, as anything above 3 border width around the window makes the title bar look very off.

Is there even a way to do this easily?

---

### Post by oedipuss on 2009-10-28
I'm not sure I understand what you mean.. I tried a 5 px border with the Dust metacity theme (left/right_width, and left/right_titlebar_edge) and it looks ok. The window border continues to the titlebar.. 

This site might also be useful : [http://live.gnome.org/GnomeArt/Tutorials/MetacityThemes](http://live.gnome.org/GnomeArt/Tutorials/MetacityThemes)

---

### Post by BlueJaeger on 2009-10-30
> **oedipuss said:**
> Something a bit unrelated to window borders but maybe of interest to you :
You can resize any window by using the window movement key (in System/Preferences/Windows, default is Alt) with the 2nd or 3rd mouse button and click-drag anywhere on the window.
You, sir, are brilliant! You have saved me so much frustration. Should I ever have a child, it will be named "oedipuss" in your honor.

For me, the combo is Alt + middle mouse button.

---

### Post by cmcginty on 2009-11-05
Here is a solution to the original question on how to change the border sizes.

[https://bugs.launchpad.net/metacity/+bug/160311/comments/11](https://bugs.launchpad.net/metacity/+bug/160311/comments/11)

> It is relatively painless to change the dimensions of the surrounding border for themes. That said, you may end up with a gaudy looking heavy window, but I assume that you don't care about that.

To change border widths, simply open up the theme's Metacity XML file. For example, Human's theme is located in /usr/share/themes/Human/metacity-1/metacity-theme-1.xml

The stanza in question should be apparent:
  <distance name="left_width" value="5"/>
  <distance name="right_width" value="5"/>
  <distance name="bottom_height" value="5"/>

Try mucking with the values until you get something you are happy with. Unfortuanately, resolution dependency still plagues much of Gnome.

---

