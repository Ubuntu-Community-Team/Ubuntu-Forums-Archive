---
title: "Changing the GNOME Splash Screen"
date: 2005-10-25
forum: Absolute Beginner Talk
---

### Post by CyiPherX on 2005-10-25
Ive followed the instuctions on [http://art.gnome.org/faq.php](http://art.gnome.org/faq.php) to install a new splash screen.

Ive downloaded the .png file, the guide says to put it in the /.gnome/splash.png location, done that, and ive gone into the "configuration editor" and changed the splash_image to splash.png, but the default brown unbuntu screen still comes up.

Do i need to tell the configuration editor where the new picture is??, if so how do i do that :confused: 

Thanks

CyiPherX

---

### Post by atoponce on 2005-10-25
It sounds like you did it correctly.  What are the permissions on the file?  Are you sure that you overwrote the default splash.png file with yours?  Just some things to check.

---

### Post by LorenzoD on 2005-10-25
You could install gnome-art a nice little program written in a very excellent language. :smile: It comes with a tool to install and select splash screens. The downside (?) is that it currently only knows how to download themes from art.gnome.org.

---

### Post by johannes on 2005-10-25
I think you have to put it in /usr/share/pixmaps/splash/ and name it "ubuntu-splash.png".

```
sudo mv your_new_splash.png /usr/share/pixmaps/splash/ubuntu-splash.png
```

---

### Post by LorenzoD on 2005-10-25
[QUOTE=johannes]I think you have to put it in /usr/share/pixmaps/splash/ and name it "ubuntu-splash.png".

```
sudo mv your_new_splash.png /usr/share/pixmaps/splash/ubuntu-splash.png
```[/QUOTE]

No, you don't, if you change the gconf key instead. 

But I noticed something else. Did you say you copied the splash image to /.gnome/splash.png? I hope you meant ~/.gnome/splash.png (or /home/<your user name>/.gnome/splash.png).

---

### Post by johannes on 2005-10-25
EDIT: nevermind

---

### Post by LorenzoD on 2005-10-25
BTW, I hope you specified the full path of the image in the gconf key. /home/<your user name>/.gnome/splash.png.

---

### Post by CyiPherX on 2005-10-25
Got it working in the end , i found these instructions after looking through heaps of threads!.
I put the .png picture in the desktop folder, then used these commands to copy it to the splash folder.

cd /usr/share/pixmaps/splash
sudo mv ~/Desktop/putyourfilehere .

Then did this:

Open the configuration editor (Main menu->System tools->Configuration editor)
Go to /apps/gnome-session/options and click on the folder.
Check "show_splash_screen"
Click twice, slowly, on the splash_image field and enter "splash/name_of_file", without quotes, replacing name_of_file with the name of the file WITH THE EXTENSION.
Close the Configuration Editor. To see the splash screen in action, log out and log back in to Gnome.

And now it works fine:) 

CyiPherX

---

### Post by CyiPherX on 2005-10-25
Just done a reboot, and notice that although the new splash screen works, the default unbuntu brown is still in the background, i have different wallpaper and a different login screen, so is it possible to change the brown to say my wallpaper picture ??

CyiPherX:smile:

---

### Post by aysiu on 2005-10-25
There's a graphical splash screen manager called gnome-splashscreen-manager. You just have to [add the Universe repositories](http://www.psychocats.net/sources.html) then ```
sudo apt-get update
sudo apt-get install gnome-splashscreen-manager
```

---

### Post by CyiPherX on 2005-10-25
Installed the gnome-splashscreen-manager, but it doesnt let you change the background, the splash screen works fine, but the rest of the screen is the default Ubuntu brown colour while the gnome desktop loads.:confused: 

(SOLVED!, found that in the "login screen setup" system-administration-login screen setup,in the GTK+greeter tab their is an option to change the colour of the splash screen background, from the default brown to any colour you want.)

CyiPherX

---

### Post by CyiPherX on 2005-10-26
SOLVED:)  yay!

CyiPherX

---

### Post by deepclutch on 2008-02-22
sry for the bUmP!
but for info, Gnome-splash are stored in /usr/share/images/desktop-base ;)

---

