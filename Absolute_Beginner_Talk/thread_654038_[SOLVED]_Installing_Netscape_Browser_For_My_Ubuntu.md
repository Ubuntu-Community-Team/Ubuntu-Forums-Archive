---
title: "[SOLVED] Installing Netscape Browser For My Ubuntu 7.04"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by Taras on 2007-12-30
Hello i would like to try Netscape Browser 9 (the Latest Version).
I know how to install it by using Wine, but i found that there is a Version for Linux, i downloaded the file netscape-navigator-9.0.0.5.tar.gz  But i have no idea how to install it. 

Can anyone give me a command that i can paste into terminal ? and also if it gets installed how can i find it ? or where would it appear ?

thank you for reading

---

### Post by pissedoffdude on 2007-12-30
> **Taras said:**
> Hello i would like to try Netscape Browser 9 (the Latest Version).
I know how to install it by using Wine, but i found that there is a Version for Linux, i downloaded the file netscape-navigator-9.0.0.5.tar.gz  But i have no idea how to install it. 

Can anyone give me a command that i can paste into terminal ? and also if it gets installed how can i find it ? or where would it appear ?

thank you for reading

Extract it and run the navigator script inside the folder.  I would suggest you make a "local programs" folder inside of your home folder and place netscape there.  If you want to make a gnome-menu entry for it, then go to system>main menu>internet>new item and place netscape there.

---

### Post by Taras on 2007-12-30
I dont know how to run the script, and i cant find main menu it system then prefferances or administration ?

---

### Post by pissedoffdude on 2007-12-30
> **Taras said:**
> I dont know how to run the script, and i cant find main menu it system then prefferances or administration ?

You should just be able to double click the navigator script inside the extracted files.  Main menu should be under preferences.  If that doesn't work, then try ```
cd Desktop/navigator
``````
sh navigator
```  If you didn't extract it to your desktop, then cd to the directory where you have extracted netscape.

---

### Post by p_quarles on 2007-12-30
You do realize that AOL just announced that Netscape is going to be discontinued next month? Given that web browsers are one of the main security holes on a desktop computer, you probably don't want to be using a browser that isn't getting any security patches.

---

### Post by Taras on 2007-12-30
Ohh i didnt know that,  so in that case i am not going to install it

---

### Post by daulex on 2007-12-30
sorry if you might consider this offtopic or anything really stupid, however:

why the **** would you use netscape? firefox kicks *** and it's preinstalled, just go to [http://addons.mozilla.org](http://addons.mozilla.org) , tune it up and never ever think about using anything other than fiferox :)

---

### Post by sailor2001 on 2007-12-30
after 13 years, netscape is pulling the plug..........r.i.p.

---

### Post by jbrunton on 2008-02-19
One reason to chose Netscape over Firefox is that Firefox doesn't work 100% of the time. Quite frequently Firefox crashes when I open my email account not to mention how unreliable it is when rendering pages running on a Ubuntu platform. 

I don't know how Netscape performs on Ubuntu because I haven't been able to get it to run after installing it. Opera is ok but it doesn't have some of the nice features the other browsers have so the choices are limited.

---

### Post by Tumdayen on 2008-02-27
i like firefox better than all other browsers but some sites don't support firefox. i ran into that problem at my school. we are trying to put ubuntu on a lab for this autotech class because their computers have issues with Windows. a friend and my teacher for computer networking brought up using ubuntu for the school district. neways the tech class's online site they need supports IE or Netscape. due to the damn district blacks and such getting wine has been a hassle so we have tried using netscape, but there is no installer from the site and supposedly it should run fine according to the directions use command ./netscape/navigator. there is no netscape folder its called navigator so i tried ./navigator/navigator but it won't find the libraries it needs even though it is there..

tried using the user agent switch from firefox and the IE tab from firefox. with he agent switcher i was able to actually get there, but not log on. i then found the IE tab but i needed flash player. i DL flash player and then i went back to the site and still didn't work.

also tried to install Ie4linux same thing as netscape though. i'm running out of ideas unless i can get wine working any suggestions

---

