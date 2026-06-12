---
title: "[SOLVED] Start EyeCandy script"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by Ryuki_NdranC on 2008-04-13
Ok, im new to linux but i manage to remove windows from my life.:)

I was wondering if there is a way to make a script to load compiz, awn and a Sidebar screenlet (which loads the rest of the screenlets).

I alrdy have  a rly small script that loads the Sidebar.py and the avant-window-navigator; i know compiz auto starts with the gnome desktop, but i haven't found a way not to. I know compiz is some how integrated with the gnome desktop and i don't want to mess up with that without some backup info.

i also wanted to auto press F9 or some equivalent function for the widget layer at startup.

So far im guessing something like:

```

#!bin/bash
compiz &
avant-window-navigator &
python -u /home/ryuki/.screenlets/Sidebar/SidebarScreenlet.py

```

so my questions are: 

1. how to safely remove compiz of the startup? 
2. will that mess up my appearance manager Visual Effects tab?
3. what are the commands to start/stop compiz from the terminal?
4. is there a way to auto start the widget layer of compiz without to press f9 or simulate the pressing with a scrip?
5. what is the safe command to end awn and screenlets, is it killall???

thx in advance, im reading some script guides on the internet so i can ultimately create a  script which start/stops all that with 1 click.

P.S: if you ask why i wanna do this is because sometimes i don't need all that eye candy on my desktop. So i wanna have the nice ON/OFF button allowing me to chose :)

thx in advance ):P

---

### Post by saj0577 on 2008-04-13
3.) If your running a ubuntu install and not edited it to much then.
To start
compiz --replace

To go back to normal
metacity --replace

5.) I jus use "xkill" in terminal and click it

Saj

---

### Post by diablo75 on 2008-04-13
If you don't want compiz loading at startup, you can just go into your appearance settings and disable the Effects.

If you have a program you want to have auto-load at startup, you can go into your Preferences>Session and add the commands you want executed at login.

And... I don't think there's any wrong way to kill a process.  You can do what was mentioned earlier:  Entering "xkill" in terminal, which will change your mouse to an X (it used to be a skull and cross bones...but I guess somebody got offended by that....pfffft).  You can also right-click on your task bar and add the "Force Quit" applet, which does what xkill does, but you don't have to type anything.

---

### Post by saj0577 on 2008-04-13
Can also pkill as i think you mentioned in your opening post. All personal preference really.

Saj

---

### Post by aktiwers on 2008-04-13
Add each command in your: System => Preferences => Sessions

---

### Post by aktiwers on 2008-04-13
Hey I just found this! Looks cool and like what you are looking for.
[http://tombuntu.com/index.php/2008/01/07/toggle-desktop-effects-with-compiz-switch/](http://tombuntu.com/index.php/2008/01/07/toggle-desktop-effects-with-compiz-switch/)

---

### Post by saj0577 on 2008-04-13
Very nice little program i think il try to get the source and create my own but for other commands. Such as one for restarting apache with a little logo :P

EDIT:What i need is simpler.

Saj

---

### Post by joshrobinson on 2008-04-13
> **saj0577 said:**
> Very nice little program i think il try to get the source and create my own but for other commands. Such as one for restarting apache with a little logo :P

EDIT:What i need is simpler.

Saj

for apache couldnt you just make a launcher that you add to your panel to run the restart command?

```
gksudo /etc/init.d/httpd restart
```
i think that should be the command

---

### Post by Ryuki_NdranC on 2008-04-13
:O ok first... thx for the answers ^^...

hmmm is not bad that compiz switch. But i was looking for just to make a simple script to run compiz | awn | screenlets, i think i manage to make it. The only thing im missing right now is the F9 simulator :(, anyone has a clue? i have been looking for a command to simulate key pressing with "apropos" but nothing so far.

I can't believe isn't possible :s 

BTW i rather to make my own compiz kill scrip because awn and the screenlets work wrong when compiz isn't on. So i rather kill the 3 of them with one script :)

In the future im planning to make a sigle script with "if" functions (dont know how to use them right now) so the script stops and stars if alrdy open or closed :)

Mean time i just need some clue on the F9 pressing or auto widget screen on compiz start.

thx again

PS: for those who don't follow. When compiz starts, even if Widget layer is already ON, i have to activate it pressing F9 so the layer starts to show.

---

### Post by saj0577 on 2008-04-14
> **joshrobinson said:**
> for apache couldnt you just make a launcher that you add to your panel to run the restart command?

```
gksudo /etc/init.d/httpd restart
```
i think that should be the command

Yeah would work for apache but not all programs can be started with that command.

Saj

---

### Post by Ryuki_NdranC on 2008-04-14
/bump :( (F9 emulator)???

---

### Post by aktiwers on 2008-04-14
I never used this, but maybe its useful?
[http://linux.softpedia.com/get/System/Operating-Systems/Kernels/KBDE-11335.shtml](http://linux.softpedia.com/get/System/Operating-Systems/Kernels/KBDE-11335.shtml)

---

### Post by Ryuki_NdranC on 2008-04-14
> **aktiwers said:**
> I never used this, but maybe its useful?
[http://linux.softpedia.com/get/System/Operating-Systems/Kernels/KBDE-11335.shtml](http://linux.softpedia.com/get/System/Operating-Systems/Kernels/KBDE-11335.shtml)

thx I'm gonna try and install it from sources. I'm kinda new in linux enviroments, so maybe it will take a while.

---

### Post by Ryuki_NdranC on 2008-04-14
Failed, aparently i downladed the source did

```

tar -xvzf kbde*.tar.gz
cd kbde*
sudo make
sudo make install

```

all fine but when i do

```

sudo kbde --press=5 --release=5 -b

```

nothing happends. anyone has an idea... Im srry if im being a pain in the a**. :)

thx for the answers

---

### Post by Ryuki_NdranC on 2008-04-20
I found out the solution this is the script:

```

#!/bin/bash
python -u /home/ryuki/.screenlets/Sidebar/SidebarScreenlet.py &
avant-window-navigator &
dbus-send --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/widget/allscreens/toggle_key org.freedesktop.compiz.activate string:'root' int32:`xwininfo -root | grep id: | awk '{ print $4 }'`
```

launching compiz with the script is not worth it :)

hope it helps someone

PS: This needs DBus plugging for Compiz

---

