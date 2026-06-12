---
title: "get rid of red-brown colors"
date: 2007-04-10
forum: Art &amp; Design
---

### Post by O-pos on 2007-04-10
Hello,

I like ubuntu, but I don't like it's red-brown colors. Of course first thing what I did was that I changed the color theme, but when I start Ubuntu, there are still things which appear in red-brown:
the page where I should enter username and password
[http://content.zdnet.com/2347-12554_22-38830-38853.html?seq=23](http://content.zdnet.com/2347-12554_22-38830-38853.html?seq=23)

and the page after that which shows things like nautilus etc.. loading. 
[http://content.zdnet.com/2347-12554_22-38830-38834.html?seq=4](http://content.zdnet.com/2347-12554_22-38830-38834.html?seq=4)

after that everythin is like  I want. But how can I get rid off of these two things? either change their colors, or remove them at all.. ??

---

### Post by meborc on 2007-04-10
well... you can modify your loginscreen yourself or you can download one from gnome-look.org: [http://gnome-look.org/index.php?xcontentmode=150](http://gnome-look.org/index.php?xcontentmode=150)

splashscreens are also here:
[http://gnome-look.org/index.php?xcontentmode=160&PHPSESSID=e4ae5c8b4350a6069ecc36623193cabb](http://gnome-look.org/index.php?xcontentmode=160&PHPSESSID=e4ae5c8b4350a6069ecc36623193cabb)

---

### Post by justleen on 2007-04-10
check [http://art.gnome.org](http://art.gnome.org) as well. In there FAQ section they explain how to  apply the different themes.

---

### Post by justleen on 2007-04-10
ohw... almost forgot. There is a package called gnome-art as well. 
It is a tool to preview and install loads of themes and icons..

```
 sudo apt-get install gnome-art 
```

---

### Post by O-pos on 2007-04-10
I chose GMP theme [http://www.gnome-look.org/content/show.php/Ubuntu+Smooth+Blue+Dark?content=55465](http://www.gnome-look.org/content/show.php/Ubuntu+Smooth+Blue+Dark?content=55465)

and splashscreen
[http://www.gnome-look.org/content/show.php/gtm+splash+screen+pack?content=45666](http://www.gnome-look.org/content/show.php/gtm+splash+screen+pack?content=45666)

However I don't knowhow to install them. This site has no FAQs so  Iwent to [http://art.gnome.org/faq.php](http://art.gnome.org/faq.php) but I dodn't understand anything there.. can someone explain in primiteve language what should be done?

---

### Post by jlk on 2007-04-10
To install you new login screen use the menu systme to go to

System->Administration->Login Window

and use the "Add" button which will bring us a file browser.  Select your newly downloaded theme and use the Install button to install it.  Then select it as the login screen.

To install you new splash image:

```
sudo cp your_new_image.png /usr/share/pixmaps/splash
```

then

```
cd /usr/share/pixmaps/splash
sudo rm ubuntu-splash.png
sudo ln your_new_image.png ubuntu-splash.png
```

Naturally you have to log out and back in the see the results

---

### Post by O-pos on 2007-04-10
That trick with login window worked fine, but the one with splash didn't work:

after command sudo cp your_new_image.png /usr/share/pixmaps/splash I get message: Cannot stat ...file.png:  No such file or directory

I tried to place the png file on the desktop and then gave the whole address /home/username/Desktop/splash_ubuntu2.png  - doesn't work, the same thing..

Maybe you also can tell me how to install cursors file to change mouse cursor design? it's a tar.gz file. should I enter something in terminal?

---

### Post by chri5tina on 2007-05-16
I used the instructions on the following page to change the splash and login in screens.

[http://www.linuxextremist.com/?p=54](http://www.linuxextremist.com/?p=54)

HOWEVER, a solid brown screen still appears three times during system start up:

before the login screen appears
after entering user name/password in the login in screen
immediately after splash screen & before desktop appears

This is very irritating.  I look in the folder /usr/share/pixmaps/splash for a *.png that is solid brown, so that I could change it, but none appears in the that folder.  My desktop background color is black, so it's not that, and I am out of ideas.

Anyone?  Bueller?

---

### Post by lyceum on 2007-05-16
You need to install gnome-splsahscreen-manager. You can apt-get it or use Synaptic Package Manager. Once up, just click the "install" button to add new pictures.

---

### Post by chri5tina on 2007-05-16
I figured it out, it was stupidly obvious.  No new packages or installers necessary.  

Though I had successfully changed splash and login screens, I forgot about the background color: there are two types of background color, one for login and one for desktop.  I changed desktop background color, but not login background color.

To change background color for login: 

system --> administration --> login window --> local  --> background color

doing that and finally, all the brown is GONE!

---

### Post by 99bluefoxx on 2007-05-17
lol this thread was exactly what i needed
chose the "relaxing water" package and then changed around all the backgrounds in it to this
[IMG]http://tbn0.google.com/images?q=tbn:UfyGDNmq9xD6SM:http://www.soulpix.com/download/desktop_pics/Ab_blue_matrix.jpg[/IMG]
looks awsome now, easy for my grandfather to use, and pretty to look at^_^

---

