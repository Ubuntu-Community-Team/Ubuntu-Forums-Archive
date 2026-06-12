---
title: "Is x-window-system package no longer in the depositaries?"
date: 2006-01-28
forum: Absolute Beginner Talk
---

### Post by Akhran on 2006-01-28
On Debian, I installed Fluxbox with the following commands:

aptitude install x-window-system
aptitude install fluxbox

On Ubuntu, when I tried to install x-window-system, it gives the following error:
No candidate version found for x-window-system

Is there a replacement package for x-window-system? 

Please advise how to install fluxbox from the Ubuntu 'server' installation.

Thanks !

---

### Post by No-Brain on 2006-01-28
Try x-window-system-core

That should do it.

Roger

---

### Post by Akhran on 2006-01-28
Thanks for the prompt reply.

After installing x-window-system-core, the system is rebooted and after it is rebooted, it drops me back to the command line. No GUI nothing. I also noticed during the installation of x-window-system-core, it doesn't prompt me for the usual stuff that I have with x-window-system installation like 'Autodetect video adapter, enable framebuffer?, Mouse configuration, etc'.

Please advise.

Thanks !

---

### Post by No-Brain on 2006-01-28
to run the setup 

sudo dpkg-reconfigure xserver-xorg

Did you install GDM or WDM  ?

sudo apt-get install WDM (or GDM)

You might also want to try "startx"

Roger

---

### Post by Akhran on 2006-01-28
After installing x-window-system-core, I installed fluxbox. When I try a manual 'startx', the following error message pop up'

Xsession: unable to start X session --- no "/home/john/.xsession" file, no "/home/john/.Xsession" file, no session managers, no window managers, and no terminal emulators found; aborting.

I've also tried dpkg-reconfigure xserver-xorg to reconfigure the options but still getting the error and it doesn't load the GUI login page.

Just for curiousity, I installed the latest snapshot of Debian netinstall CD and did a clean installation. "aptitude install x-window-system followed by aptitude install fluxbox" works perfectly and drop me into fluxbox GUI after rebooting.

Are there things that x-window-system installs and x-window-system-core doesn't? 

Thanks for the help !

---

### Post by No-Brain on 2006-01-28
I don't know.  I am fairly new to this myself.  The only thing I can think od is you have to install WDM or GDM as well.  Maybe someone else who is more knowledgeable can jump in here.

Roger

---

### Post by Akhran on 2006-01-29
Any help would be greatly appreciated!

Thanks !

---

### Post by christhemonkey on 2006-01-29
create a file in your home directory called .xsessions and insert the line exec fluxbox

sudo vi /home/your_user_name/.xsessions
and the line
exec fluxbox

type ZZ to quit and save

then

sudo /etc/init.d/gdm restart

Let me know!

---

### Post by Akhran on 2006-01-30
The only display manager I installed was xdm. Restarting the system gives me the same error; the GUI login page doesn't display.

Would be great if anyone would update what happens to the x-window-system package in ubuntu depositaries, cos the package works fine in debian installation.

Thanks !

[QUOTE=christhemonkey]create a file in your home directory called .xsessions and insert the line exec fluxbox

sudo vi /home/your_user_name/.xsessions
and the line
exec fluxbox

type ZZ to quit and save

then

sudo /etc/init.d/gdm restart

Let me know![/QUOTE]

---

### Post by benplaut on 2006-01-30
```
sudo apt-get install x-window-system-core fluxbox xterm aterm
sudo dpkg-reconfigure xserver-xorg
echo "exec fluxbox" > ~/.xsessions
```

see if that works, then report back

---

### Post by ecto on 2006-01-30
You should try making an .xinitrc script instead of an .xsession (that will most likely work.) try this
> sudo vi ~/.xinitrc
              exec fluxbox
also have you tried getting xserver-xorg package?

---

### Post by Akhran on 2006-01-30
Did all that and when I reboot the system, it drops me at the text console login. When I did a manual 'startx', the following error message pop up:

Xsession: unable to start X session --- no "/home/john/.xsession" file, no "/home/john/.Xsession" file, no session managers, no window managers, and no terminal emulators found; aborting.

Thanks.



[QUOTE=benplaut]```
sudo apt-get install x-window-system-core fluxbox xterm aterm
sudo dpkg-reconfigure xserver-xorg
echo "exec fluxbox" > ~/.xsessions
```

see if that works, then report back[/QUOTE]

---

### Post by Akhran on 2006-02-01
Tried that too, but I'm still getting the same error as above. I think the xserver-xorg package comes with x-window-system-core. so yes :)

Thanks.

[QUOTE=ecto]You should try making an .xinitrc script instead of an .xsession (that will most likely work.) try this

also have you tried getting xserver-xorg package?[/QUOTE]

---

