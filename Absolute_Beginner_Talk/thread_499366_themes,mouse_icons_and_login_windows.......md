---
title: "themes,mouse icons and login windows......"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by techno-mole on 2007-07-12
hello.
ive been messing about with new themes and mouse icons, and ive come across the option for having a picture on the login window, but i seem to be having some trouble getting a picture to display.
ive made sure its in the right format and such like, but it still doesnt display.
so for example i go to --> system --> administration --> login window, then on the users tab there the part at the bottom about faces.
so how do you set up a face/picture ? ive tried using various pictures, but all i get at the login window is a default icon type thing.
cheers

---

### Post by JanvL on 2007-07-12
did you check the filepermissions?

Jan

---

### Post by techno-mole on 2007-07-12
permissions ? as in where the faces file is ?
i did try to use a file in my home folder, but that didnt work either, the default faces folder is in usr/share/pixmaps/faces, which im pressuming would need the right permissions ?
i didnt think you would need to have any permissions to use a picture

---

### Post by bodhi.zazen on 2007-07-14
> **techno-mole said:**
> permissions ? as in where the faces file is ?
i did try to use a file in my home folder, but that didnt work either, the default faces folder is in usr/share/pixmaps/faces, which im pressuming would need the right permissions ?
i didnt think you would need to have any permissions to use a picture

For permissions see here : [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

For icons/themes put your downloaded items in your home directory, in a hidden file.

Hidden files start with a . like say .icons or .themes Put your mouse theme in .icons and any themes in .themes Faces for GDM can go in .face

For faces the name of the file should = your username

So for example

cp image.png /home/techno/.face/techno

replace "techno" with your actual log-in name, optional trailing ".png"

>  Users may run the gdmphotosetup command to configure the image to use for their userid. This program properly scales the file down if it is larger than the MaxIconWidth or MaxIconHeight configuration options and places the icon in a file called ~/.face. Although gdmphotosetup scales user images automatically, this does not guarantee that user images are properly scaled since a user may create their ~/.face file by hand.

GDM will first look for the user's face image in ~/.face. If not found, it will try ~/.face.icon. If still not found, it will use the value defined for "face/picture=" in the ~/.gnome2/gdm file. Lastly, it will try ~/.gnome2/photo and ~/.gnome/photo which are deprecated and supported for backwards compatibility. 

[http://www.gnome.org/projects/gdm/docs/2.14/overview.html](http://www.gnome.org/projects/gdm/docs/2.14/overview.html) (Section 2.9. The GDM Face Browser)

* Note ~ = short hand for your home directory

---

### Post by techno-mole on 2007-07-15
many thanks, i know its a small thing and most people probably wouldnt bother with it, but when i switch the other 2 systems over to ubuntu the kids and my better half will want to be able to use pictures on the login window, me personally i dont care, but knowing how to do it makes a difference.
cheers again.

---

### Post by bodhi.zazen on 2007-07-15
Small update, sorry for the previous mis-information ;)

For faces

Open a terminal, enter the following command :

```
gksu gdmsetup
```

Go to the "Local" Tab -> Under "Theme" Select "Themed with face browser"

Close that window.

Then, again in the terminal, run gdmphotosetup. This will bring up a small box "Login Photo Preferences"  Click on the picture to change it -> navigate to any picture you would like ....  Click "Open"

This will change the picture, resizing as needed, and save it as a file "~/.face" (the original picture will not be altered).

You will find a number of default faces in /use/share/pixmaps/faces

;)

---

### Post by techno-mole on 2007-07-15
thats kind of what i did, only i just typed gdmphotosetup, and found the picture i wanted and the gdmphotosetup resized it and then saved it to my home folder as .face, then i went through the process of setting a face up to appear on the login window found the .face file and selected it.
when i restarted the system there it was.
cheers for the help.

---

### Post by GrandpaLeaman on 2008-03-04
That worked like a charm. Much thanks Bodhi.zazen for this little nugget of gold. I have set up multiple users on my laptop, and their pictures on the GDM give it a finished look.  :cool:

---

### Post by LuisGMarine on 2008-03-04
To change the picture at the login screen you have to take a different route.  For some reason changing the picture under Login Window options or w/e its called doesn't work

You need to go to:

** System > Preferences > About Me**

In there click on the icon and you can choose what ever picture you want.  Now when you log in you have that custom picture at the GDM login window.  You have to do those steps for each account.

Hope this helps, took me a while to look this one up =P

---

### Post by bodhi.zazen on 2008-03-04
Try gdmphotosetup :twisted:

---

### Post by LuisGMarine on 2008-03-05
that works too!  =P

So many different ways to do one thing =P

---

