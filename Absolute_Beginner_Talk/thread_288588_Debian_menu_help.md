---
title: "Debian menu help"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by Daergeth on 2006-10-30
I installed the debian menu from automatix2 and now my normal panel wont work, I rebooted and now I have no panels! How Do I pull up the debian OR my normal panels?

---

### Post by kerry_s on 2006-10-30
Press alt+F2 to pull up the run command and type> update-menus
You might have to logout and in(ctrl+alt+backspace, if theres no logout)

I might of miss understood, for the panel(bar on the bottom) type> gnome-panel

---

### Post by land0 on 2006-10-30
Try pressing alt and while holding the alt button down press the F2 key. This should open a run dialog box. Type **gnome-panel** in the text box at the top. If this does not bring your panels back up then press Alt+F2 again but this time enter 
**gksu synaptic** another dialog box should appear asking you for your password 
Once synaptic is running search for the Debian menu then remove it. I would also recommend that you verify that gnome-panel is installed by doing a quick search for it. After you have uninstalled the Debian Menu and verified that gnome-panel is installed Hit Alt+F2 again and try to start the **gnome-panel**

Hopefully that gets you back up and running. As for why installing Debian Menus wiped out the panels is a whole other question all together.

I hope this helps.

---

### Post by Daergeth on 2006-10-30
That worked, thanks! 

Ok next question, were at exactly is debian menu at, I dont see it under applications? ](*,)

---

### Post by kerry_s on 2006-10-30
Open up alacarte menu editor and make sure debian menu is turned on and not hidden

---

### Post by Daergeth on 2006-10-30
Ok pulled up alacarte, when I click the checkbox for debian (it is unchecked)
nothing happens, it wont let me check it. Im sorry for being so tough, Im not trying to be :P

---

### Post by kerry_s on 2006-10-30
Did you run> update-menus <in terminal?

---

### Post by NESFreak on 2006-11-10
> **kerry_s said:**
> Did you run> update-menus <in terminal?

i did. didn't work for me though.

---

### Post by ChrisNiemy on 2006-11-20
Hi,

I had the same problem this time with edgy eft (6.10) exaclty how described in this thread.

First I installed **menu** and **menu-xdg** both with Synaptic. However this did not work for me, even afte logging out and in again.

Here's how it suddenly worked :D (step by step, don't summarize)
```
sudo apt-get install --reinstall menu
```
```
update-menus
```
```
sudo apt-get install --reinstall menu-xdg
```
```
update-menus
```
optional: ```
sudo update-menus
```

(Note: leave out "--reinstall" if packages are not already installed)

For me it seems it was necessary fist to install menu and then install menu-xdg, not both at the same time. However I can not explain this properly, but it worked for me. 

Then after logging in the next time, the menu should appear under the applications menu as supposed.

Greets,
Chris

PS: If it did not work, try this a second time.

---

### Post by NESFreak on 2006-11-20
tnx ChrisNiemy. the separate installing did it for some reason.

---

### Post by darrenrxm on 2006-11-20
It works for me thank you.

---

### Post by torbherr on 2006-11-25
Hi

I had the same problem with linux mint
The instructions given by ChrisNiemy worked for me too. Thanks a lot.
Are the developers aware that there is a problem? A simple problem like this scares away newbies.

Torben

---

### Post by Papa-san on 2006-11-25
I had Automatix installed when I didn't know anything about Ubuntu, and it helped. Now I have a clean install that doesn't have it installed. Will the step-by-step instructions given work to install just the Debian menu? That menu was VERY handy for me, and I would like it back, but I don't really want to install Automatix...

Edit: I took a chance, and simpli did the installs of menu and menu-xdg. I now have the Debian menu!

Woo Hoo!!!

---

### Post by arnieboy on 2006-11-25
```
sudo apt-get install menu menu-xdg pdmenu
sudo update-menus
```

---

### Post by telovoyagarcar on 2006-11-27
Thank you guys...

Now alacarte will not work anymore.. not even show... but i dont give a f--k because i got the debian menu in there..!!

Have a nice one!

---

