---
title: "pictures folder screensaver"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by zekaito on 2007-06-30
I have installed ubuntu and was trying to setup the pictures screensaver but I can't find the pictures folder anywhere and ubuntu will not let me create folders. why is this? I installed ubuntu on my computer therefor I AM the administrator and should be able to make any change I wan't. Can someone please help.

---

### Post by yagood on 2007-06-30
In your home folder, create a folder called "Pictures" and put your pictures there - screensaver will then pick them up.

> I installed ubuntu on my computer therefor I AM the administrator and should be able to make any change I wan't.

Well, it's not exactly how you describe it - by default you're not logged in as an administrator. Of course you can do anything you want on your system, for example go to menu System > Administration and then click Network. You'll be asked for your password and then granted access to the administrative part of the system. On the other hand, it's best to keep things like pictures, sound files etc. in your home folder where you always have full right to create/delete files.

---

### Post by zekaito on 2007-07-02
thanks. I guess I'm not used to the unix file system. I've only used windows before and when you click on the hard drive you are imideatly in the root.

---

### Post by yagood on 2007-07-02
Sure, some things may seem unintiutive at first when the user only worked with Windows before, but the truth is that Ubuntu and Linux in general are fundamentally better designed than Windows so it's worth to learn the differences.

When in doubt, you can always browse the documentation, there's plenty of helpful stuff there:

[https://help.ubuntu.com/](https://help.ubuntu.com/)

And there's of course the community at the Ubuntu Forums :)

---

### Post by freesitebuilder on 2007-07-02
This has lots of useful info on the way Linux workd differently from Windows:
[http://www.whylinuxisbetter.net/](http://www.whylinuxisbetter.net/)
And this is useful on directory structure:
[http://www.goitexpert.com/entry.cfm?entry=A-guide-to-Linux-directory-structure--Part-One](http://www.goitexpert.com/entry.cfm?entry=A-guide-to-Linux-directory-structure--Part-One)

---

### Post by pdebruyn86 on 2007-07-03
I have a file structure in Windows with about 12,000 fotos that I would like to use as my "pictures" folder.  I hate to have to copy all those over to my Home folder.  Is there any way I can have Screensaver use the existing pix?
Is there a screensaver changer for Unbuntu?  One that I can specify the folder and the time grequency of changing the screen?
Thanks.
Paul

---

### Post by fakie_flip on 2007-08-11
How is it possible to get gnome-screensaver to look in another directory besides ~/Pictures for the screensaver? I've looked in gconf, but no luck yet.

---

### Post by eentonig on 2007-08-11
You could create a symlink ~/Pictures, that points to the directory that holds all those pictures

---

### Post by Freelance Physicist on 2007-12-09
There's two ways to set the folder the Pictures Folder screensaver uses.

change /path/to/your/Pictures_folder as needed.

1) Make a symlink:```
ln /path/to/your/Pictures_folder ~/Pictures
```
or, if your pictures are on a separate partition from your Ubuntu install,
```
ln -s /path/to/your/Pictures_folder ~/Pictures
```

2) Edit the Pictures folder configuration file: ```
sudo gedit /usr/share/applications/screensavers/personal-slideshow.desktop
```

Find the line ```
Exec=slideshow --location=Pictures
```
and change it to ```
Exec=slideshow --location=/path/to/your/Pictures_folder
```

The lack of configuration options for any of the screensavers is rather odd.

---

