---
title: "Change icons..."
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by gimpguy2000 on 2007-08-14
Hi all, could anyone tell me how to change the icons to my own created icons? I did a search but mainly comes up with other theme icons, etc... I just want to implement my own created types, not pre-made. 

Thanks,

 Paul

---

### Post by ThinkBuntu on 2007-08-14
Just draw the image as an SVG or PNG. Then replace the target image, which may be in "/usr/share/icons" or "/usr/share/pixmaps".

---

### Post by Hospadar on 2007-08-14
Also if you right-click on the launcher (if you are wanting to change launcher icons) and go to properties, click the icon here, and select a new image.

---

### Post by gimpguy2000 on 2007-08-14
Ok, thanks. So I just find the target image icons. I noticed there isn't a lot of play with the Gnome desktop. If I make toolbar trans, it comes out pixled with black instead, etc...but with KDE desktop, it works fine. Anywho, thanks and i'll give it a try. 

Paul

---

### Post by gimpguy2000 on 2007-08-14
> **Hospadar said:**
> Also if you right-click on the launcher (if you are wanting to change launcher icons) and go to properties, click the icon here, and select a new image.

Cool thanks for that :) It does work with desktop icons too but not as many options. So if I simply want my icons in the lists, I just add them to the lists? 

TX

Paul

---

### Post by ThinkBuntu on 2007-08-14
If you just want to switch icons in your Applications list, etc, just go to the "Edit Menus" program, and view the properties of different entries. As another poster said, clicking the Icon button when viewing the properties of any of these entries will allow you to select another icon, including one from a file not located in /user/share/pixmaps or icons/.

The tip I gave you is for actually replacing icons in your current icon theme. This is a little more involved, but is the only way to directly edit an icon theme.

---

### Post by gimpguy2000 on 2007-08-15
> **ThinkBuntu said:**
> If you just want to switch icons in your Applications list, etc, just go to the "Edit Menus" program, and view the properties of different entries. As another poster said, clicking the Icon button when viewing the properties of any of these entries will allow you to select another icon, including one from a file not located in /user/share/pixmaps or icons/.

The tip I gave you is for actually replacing icons in your current icon theme. This is a little more involved, but is the only way to directly edit an icon theme.

Thanks for the info :) That is what I want to do then. I could probably keep a copy of the original icons setup and just modify the icon sets with my own. Or so I hope. 


Paul

---

### Post by Hobo Joe on 2007-08-15
I think what you are asking is when you click the icon under 'properties', that you only see the theme icons, and you want to see your own. In that case, click browse, find the FOLDER that they are located in, not the files themselves, and open that foler, it will have ll the pictures in there for you to pick now. 

Hope that helps. :)

---

### Post by gimpguy2000 on 2007-08-18
> **Hobo Joe said:**
> I think what you are asking is when you click the icon under 'properties', that you only see the theme icons, and you want to see your own. In that case, click browse, find the FOLDER that they are located in, not the files themselves, and open that foler, it will have ll the pictures in there for you to pick now. 

Hope that helps. :)

Hi HJ, thanks for the info. What I really want to do, is create my own icon set. So when the computer and home, etc...icons are up, they display my own. I tried putting them in the folders, etc..but wouldn't work. 

Thanks again,

 Paul

---

### Post by Ek0nomik on 2007-08-18
> **gimpguy2000 said:**
> Hi HJ, thanks for the info. What I really want to do, is create my own icon set. So when the computer and home, etc...icons are up, they display my own. I tried putting them in the folders, etc..but wouldn't work. 

Thanks again,

 Paul

If you want to create your own icon set then you can either modify from an existing set or create your own.

You need to make sure that you have the icon set that you are modifying or creating chosen in *System/Preferences/Theme*.  (Icon themes are placed in ~/.icons)  Otherwise your changes will be happening without you being able to tell as you don't have the theme activated.

Now, icon themes follow a pattern for their layout.

The best way to see how they work is to download an existing icon theme.  You can get plenty from [http://www.gnome-look.org](http://www.gnome-look.org).  If possible, you will want to have all your icons as .svg files and put them in the 'scalable' folder.  This way they will work regardless of the size of your icon (in the panel, in nautilus viewing as icons, etc).

---

