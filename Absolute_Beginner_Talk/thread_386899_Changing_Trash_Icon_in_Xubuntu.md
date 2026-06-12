---
title: "Changing Trash Icon in Xubuntu"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by Brendantb on 2007-03-17
Hi, 

I would like to replace the default green bucket icon in Tango on my panel, with a wire basket icon (from MacosX.)

I have found the equivalent Tango icons in /usr/share/icons/Tango/scalable/places, and /status, respectively. They are .svg files. Does this matter, and how do I switch the icons if it's possible?

---

### Post by Brendantb on 2007-03-17
I meant to add the macos icons are .png.

---

### Post by Brendantb on 2007-03-19
Hi, 

I have changed the trash icon in the Tango/scalable/places folder, and in the /status folder, but althought the new icon now shows up in the thunar file manager, it doesn't appear in the panel, even after restarting. 

Can anyone give me some pointers as to what I should do next?

---

### Post by LanDan on 2007-03-19
did you do a right on your ugly green bucket click and then go to properties?

---

### Post by Brendantb on 2007-03-19
Hi, 

When I right click on the bucket, there is no properties option. I am using Xubuntu, with the icon for trash on the panel. What options am I supposed to see under "properties?"

I would like to learn a bit about Linux, too, and how the icons for Xfce are managed, and hopefully, manipulated. If anyone can give me a link to such a resource, I would be much obliged.

---

### Post by Brendantb on 2007-03-24
I have finally figured out how to do this; you have to update the icon cache after you change the various icons. Code: 

sudo gtk-update-icon-cache -f -t /usr/share/icons/<theme-name>

Information gleaned from the Xfce wiki, hints and tips.

---

