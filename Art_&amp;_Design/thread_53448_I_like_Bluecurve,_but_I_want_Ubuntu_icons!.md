---
title: "I like Bluecurve, but I want Ubuntu icons!"
date: 2005-07-31
forum: Art &amp; Design
---

### Post by stray on 2005-07-31
I've always liked the cleanliness and friendliness of the Bluecurve icon set, but I'm not wild about the "Red Hat-ishness" of them. I replaced all of my "icon-panel-menu.png" files with one bearing the Ubuntu logo, but the only other one is "icon-panel.png", which appears to be a bit harder to handle, because it's got a gradiated transparency. (See attachment.)

Is anyone out there good enough to make a new icon-panel.png with the Ubuntu Logo replacing the Red Hat logo? I'd especially like it if the look of the panel in the image could remain the same.

Even better, is there somewhere on the Web where I can get the original files in PSD or XCF format?

EDIT: This has been solved. See below!

---

### Post by PrimoTurbo on 2005-07-31
You could just put the ubuntu logo over the hat and get a shadow going while keeping the panel thing and the ^. I would do it but I'm not good with gimp only with photoshop. Good luck.

---

### Post by stray on 2005-07-31
Well, I suppose that if you want something done right, you do it yourself. After a lot of pixel-by pixel wrangling, I have my own version of **icon-panel.png**. Assuming you have the Bluecurve icon set installed, ([here's a thread with a HOWTO on getting Bluecurve installed](http://ubuntuforums.org/showthread.php?t=2696)) put this image in **/usr/share/icons/Bluecurve/48x48/apps/** and **chown root:root** and **chmod 777** on it and presto! Don't forget to scale the image down to 36x36, 24x24 and 16x16, then repeat the above process for the corresponding folders.

Now, I just have to figure out how to make the GNOME menu use the Ubuntu icon...

---

### Post by PrimoTurbo on 2005-07-31
Not bad.

---

### Post by Xian on 2005-07-31
This is looking nice. When you are finished if you could post up the other images you substituted and their file names that would be great. I'd love to incorporate such an icon set into my install.

---

### Post by TravisNewman on 2005-08-01
Change the foot into the ubuntu logo:

[http://www.ubuntuforums.org/showthread.php?t=26854&highlight=gnome+foot](http://www.ubuntuforums.org/showthread.php?t=26854&highlight=gnome+foot)

That really does look sweet.

---

### Post by stray on 2005-08-02
Well, here are all the icons in a nice, neat tar.gz at the bottom of this post.

Now, I have the Bluecurve icon set installed ([see the HOWTO for info on adding Bluecurve](http://www.ubuntuforums.org/showthread.php?t=2696)), so for me, these icons live in **/usr/share/icons/Bluecurve/48x48/apps** (and similar folders for 36x36, 24x24 and 16x16...just replace 48x48 with the appropriate dimensions), but I imagine you could put these anywhere in /usr/share/icons or whatever. For this, though, I'm going to assume you have Bluecurve installed.

First, back up the original (Red Hat) icons:
```
sudo cp /usr/share/icons/Bluecurve/48x48/apps/icon-panel.png /usr/share/icons/Bluecurve/48x48/apps/icon-panel.png_backup
sudo cp /usr/share/icons/Bluecurve/48x48/apps/icon-panel-menu.png /usr/share/icons/Bluecurve/48x48/apps/icon-panel-menu.png_backup
```and repeat this for 36x36, 24x24 and 16x16.

Then unzip the tarball and put these icons in their corresponding folders (or just unzip the tarball in /usr/share/icons).

Next, you have to make sure the icons are owned by root and that everyone has permission to use them:
```
sudo chown root:root /usr/share/icons/Bluecurve/48x48/apps/icon-panel.png
sudo chown root:root /usr/share/icons/Bluecurve/48x48/apps/icon-panel-menu.png
sudo chmod 777 /usr/share/icons/Bluecurve/48x48/apps/icon-panel.png
sudo chmod 777 /usr/share/icons/Bluecurve/48x48/apps/icon-panel-menu.png
```Lather, rinse and repeat for 36x36, 24x24 and 16x16.

Now, when you log in and the splash screen comes up and shows you that it's loading stuff, the little GNOME panel with the Red Hat fedora will be replaced with a panel bearing an Ubuntu logo!

Finally, if you want to change the GNOME foot in the Applications menu to the Ubuntu logo, just do the following:
```
sudo cp /usr/share/pixmaps/gnome-logo-icon-transparent.png /usr/share/pixmaps/gnome-logo-icon-transparent.png_backup
sudo cp /usr/share/icons/Bluecurve/48x48/apps/icon-panel-menu.png /usr/share/pixmaps/gnome-logo-icon-transparent.png
killall gnome-panel
```
Shazam!

---

### Post by TravisNewman on 2005-08-03
I might suggest renaming it to somehting other than bluecurve, so you can just extract into your .icons folder and run with it.

---

