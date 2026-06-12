---
title: "Icons Not Showing?"
date: 2006-05-18
forum: Absolute Beginner Talk
---

### Post by Phrostay on 2006-05-18
After using the wireless installer 0.6 from the wpa & wpa2 howto I have my wpa and wpa2 network at home and university working successfully. However I was told there was a bug of sorts that removes your icons and to fix such a problem you would issue this command in terminal:

sudo gtk-update-icon-cache -f /usr/share/icons/hicolor/

However this did not fix the problem. The icons that i have missing are:

About Me
Synaptic Package Manager
Update Manager

It would be nice to have my icons back :)

---

### Post by brettr on 2006-05-18
What do you mean they are missing? Do you mean that they were originally on your panel, and now they are gone?

---

### Post by Phrostay on 2006-05-18
Yes. They do not show up in the panel or the menus!

---

### Post by brettr on 2006-05-18
For the update manager in the panel i know it is in a notification area...  So you can try --> Right click on the panel --> Add to panel ---> Notification area.

For the other icons in the menu try going into Applications --> Accessories --> Alacarte Menu Editor


Then go to the ones with the missing icons and right click --> Properties --> Click on the icon... and select the icon

Here are some locations for the icons if you can not find them in the location that comes up: 

```
 /usr/share/pixmaps
/usr/share/icons
```

I don't know too much about the inner workings of ubuntu/linux yet but i hope this is some help

Brett

---

