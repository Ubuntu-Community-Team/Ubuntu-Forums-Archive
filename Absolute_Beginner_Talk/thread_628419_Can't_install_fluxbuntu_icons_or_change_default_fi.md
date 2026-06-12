---
title: "Can't install fluxbuntu icons or change default file browser"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by rfurman24 on 2007-12-01
As Stated in title I can not change icons in fluxbuntu. I have tried three different icon themes. I also hate rox filer and want to change default to pcmanfm or thunar and can not seem to find out how. I have both pcmanfm and thunar installed and can use them but I can not find where to set as default so when I click home folder they are used instead of rox.

---

### Post by bodhi.zazen on 2007-12-01
Well desktop icons are managed by rox, so you will need a plan.

I suggest you run without rox. To do this , edit ~/.fluxbuntu/startup and comment out the line reading  rox --pinboard=Default & (it might be ~./fluxbox/startup)

Restart fluxbox and you will no longer be running rox, but you will have no icons either. If you want desktop icons you will need to sort out how you want to do icons.

If you want to stay with rox, look at how to configure it. For wxample :

o configure ROX to take an action (start a program, open a file as text, etc) when clicking an icon.

> Right click on an icon (for example text.txt)
Go to the menu " File 'text.txt' "
Click "Set run action"
On the bottom of the window there is a box "Enter a shell command:"
the "$@" is a variable and represents the file in question.
Add the name of the program to open the file with
For example:

abiword "$@"

Now click the box "Use Command" on the bottom right

Now when you click on the icon "text.txt" the file will open with Abiword
Abiword will now, by default, open any *.txt file in fact when you select it in rox-filer.
This only needs to be set once and some settings are already configured in ROX

There is a lot of information and ideas on the fluxbuntu site :

[http://community.fluxbuntu.org/index.php#1](http://community.fluxbuntu.org/index.php#1)

---

### Post by rfurman24 on 2007-12-01
That is very helpful. I will run without rox. I was refering to the icons in thunar or pcmanfm. I would like some kind of dock like I see in screenshots in various places. The fbpanel osx I see on box-look is cool but I can not get it to work. I like clean minimalistic desktops but I do not like right clicking all the time and that is why I would like a dock.

---

