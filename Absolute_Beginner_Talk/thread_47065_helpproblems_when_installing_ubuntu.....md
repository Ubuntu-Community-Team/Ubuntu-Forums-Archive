---
title: "help:problems when installing ubuntu...."
date: 2005-07-07
forum: Absolute Beginner Talk
---

### Post by lucaflea on 2005-07-07
hi! i've already installed this version of ubuntu (ubuntu-5.04-install-amd64). the problem is when i finish the installation and reboot my pc. ubuntu loads but when i get into the OS the screen becomes black with some "graphic noises" in the middle of it and only the mouse is visible....

why??
what can i do???

---

### Post by Lunde on 2005-07-07
[QUOTE=lucaflea]hi! i've already installed this version of ubuntu (ubuntu-5.04-install-amd64). the problem is when i finish the installation and reboot my pc. ubuntu loads but when i get into the OS the screen becomes black with some "graphic noises" in the middle of it and only the mouse is visible....

why??
what can i do???[/QUOTE]
 There may be that you have a special graphic card that is not supported.

Can you post the Graphic card info?

Also, can you press at the black screen:

**Alt+Ctrl+F1** 

Login with your username and type:

**Pico /etc/X11/xorg.conf**

And use the arrows to scroll down to the 
**Section "Device"**
and post the post the output here

---

### Post by lucaflea on 2005-07-07
the graphic card is:

SAPPHIRE RADEON 9200SE ATLANTIS 128mb....


i 'will try what you said as soon as possible...

thanx for now.

may i t depend on the screen resolution i chose during the installation process???

---

### Post by Lunde on 2005-07-07
[QUOTE=lucaflea]the graphic card is:

SAPPHIRE RADEON 9200SE ATLANTIS 128mb....


i 'will try what you said as soon as possible...

thanx for now.

may i t depend on the screen resolution i chose during the installation process???[/QUOTE]
 Your card will not work by default installation, but 

Ati drivers Howto:
[http://www.ubuntuforums.org/showthread.php?t=24557](http://www.ubuntuforums.org/showthread.php?t=24557)

Some other links:
[http://ubuntuforums.org/showthread.php?t=24913](http://ubuntuforums.org/showthread.php?t=24913)
[http://ubuntuforums.org/showthread.php?t=22412](http://ubuntuforums.org/showthread.php?t=22412)

---

### Post by lucaflea on 2005-07-07
Pico /etc/X11/xorg.conf


pico stands for....????

---

### Post by nocturn on 2005-07-07
[QUOTE=lucaflea]Pico /etc/X11/xorg.conf


pico stands for....????[/QUOTE]

It's a text editor.

---

### Post by Lord Illidan on 2005-07-07
pico is a text editor...

Run it as pico, not Pico..because Linux is case sensitive..

---

### Post by Lunde on 2005-07-07
[QUOTE=Lunde]
**Pico /etc/X11/xorg.conf**
[/QUOTE]
Sorry, I typed a bit fast..

---

### Post by lucaflea on 2005-07-07
thanx guys....
i entered the text editor mode but....how can i save and exit?????

 ](*,) 

if changing to 15 the default depht won't work...what can i do????

---

### Post by Lord Illidan on 2005-07-07
I think you should use vi..here is a tutorial on how to use it effectively..

[http://docs.freebsd.org/44doc/usd/12.vi/paper.html](http://docs.freebsd.org/44doc/usd/12.vi/paper.html)

Edit : sorry...I should have told you..>

vi /etc/X11/xorg.conf

---

### Post by Lunde on 2005-07-07
[QUOTE=lucaflea]thanx guys....
i entered the text editor mode but....how can i save and exit?????

 ](*,) 

if changing to 15 the default depht won't work...what can i do????[/QUOTE]
 All the commands are explained at the bottom when you open the pico editor.

**Ctrl+o** =overwrite 
Then press **Enter **so confirm the overwrite, and last press
**Ctrl+X** = Exit

But are you sure about the changes you have done?

---

### Post by nocturn on 2005-07-07
[QUOTE=Lunde]All the commands are explained at the bottom when you open the pico editor.

**Ctrl+o** =overwrite 
Then press **Enter **so confirm the overwrite, and last press
**Ctrl+X** = Exit

But are you sure about the changes you have done?[/QUOTE]

I would take a backup of the file first.
cp xorg.conf xorg.conf.o
pico xorg.conf

Move the backup back by
mv xorg.conf.0 xorg.conf

---

### Post by Lunde on 2005-07-07
[QUOTE=nocturn]I would take a backup of the file first.
cp xorg.conf xorg.conf.o
pico xorg.conf

Move the backup back by
mv xorg.conf.0 xorg.conf[/QUOTE]
 Agree, but eather: **cd /etc/X11** or use full paths 
**cp /etc/X11/xorg.conf /etc/X11/xorg.conf.o**

---

### Post by lucaflea on 2005-07-07
guys, i got it!!!

ubuntu works!!!!!!

thanx to all of you!!

and now...where can i get some hits about how to conifgure my adsl speedtouch modem....  :roll:

---

### Post by Lunde on 2005-07-07
[QUOTE=lucaflea]guys, i got it!!!

ubuntu works!!!!!!

thanx to all of you!!

and now...where can i get some hits about how to conifgure my adsl speedtouch modem....  :roll:[/QUOTE]
 Glad it worked out for you.

Here's a howto for Speedtouch USB.. 
[http://ubuntuforums.org/showthread.php?t=26017](http://ubuntuforums.org/showthread.php?t=26017)

---

### Post by lucaflea on 2005-07-07
no way....I CAN'T DO IT....
i suck... there's a simple way to configure my modem?? i've tried all the possibilities but.... i suck....

someone help me please...  :?

---

### Post by poofyhairguy on 2005-07-07
[QUOTE=lucaflea]no way....I CAN'T DO IT....
i suck... there's a simple way to configure my modem?? i've tried all the possibilities but.... i suck....

someone help me please...  :?[/QUOTE]

Where did you fail? At what point? There is unsually only one way to do things....we can only help you through it.

---

### Post by lucaflea on 2005-07-07
for example.... when i write "sudo gedit /etc/hotplug/usb/speedtouch" it should return me a list of things but it returns me only a white page....why?

---

### Post by Lunde on 2005-07-07
[QUOTE=lucaflea]for example.... when i write "sudo gedit /etc/hotplug/usb/speedtouch" it should return me a list of things but it returns me only a white page....why?[/QUOTE]
 gedit is a text editor, if the file does'nt exist it will open a new file. Is it the howto I posted a link to that will not work? 

Where does it stop? How far did you get?
What's the full name of yur modem? and is it USB or Network

---

### Post by lucaflea on 2005-07-08
my modem is "adsl speedtouch 330 usb". i can go so far as i wrote yesterday: the tell me:

"Let's get started by downloading the speedtouch-suite from [http://s1x.homelinux.net/projects/speedtouch_suite](http://s1x.homelinux.net/projects/speedtouch_suite).
Follow the instructions in that website, namely the ones about downloading the firmware.
**Once you've installed that one**, you'll have to edit the file /etc/hotplug/usb/speedtouch by executing the command:....."

the problem is that i download that file but i can't insall it. where do i install it? how do i do it?? maybe this is why when i write "sudo gedit /etc/hotplug/usb/speedtouch " it returns me a blank page...

it would be easier for newbies to have a simple "auto installer" package...

---

### Post by Lunde on 2005-07-08
[QUOTE=lucaflea]my modem is "adsl speedtouch 330 usb". i can go so far as i wrote yesterday: the tell me:

"Let's get started by downloading the speedtouch-suite from [http://s1x.homelinux.net/projects/speedtouch_suite](http://s1x.homelinux.net/projects/speedtouch_suite).
Follow the instructions in that website, namely the ones about downloading the firmware.
**Once you've installed that one**, you'll have to edit the file /etc/hotplug/usb/speedtouch by executing the command:....."

the problem is that i download that file but i can't insall it. where do i install it? how do i do it?? maybe this is why when i write "sudo gedit /etc/hotplug/usb/speedtouch " it returns me a blank page...

it would be easier for newbies to have a simple "auto installer" package...[/QUOTE]
 OK, I've never installed the Speedtouch drivers myself, but I'm pretty sure that you need to do the following:

1.) Download the **firmware** and **speedtouch-suite-gen-0.4.sh** into your /home directory or some subfolder. I would create a directory named **speedtouch_drivers** by typing this command in the terminal:
**$ mkdir ~/speedtouch_drivers**
then place the downloaded files into that directory

2.) Still in the terminal:
**$ chmod 775 ~/speedtouch_drivers/speedtouch-suite-gen-0.4.sh**
change the directory name in the command above if you chose a different name.

3.) Run the installer by typing:
**$ sudo ~/speedtouch_drivers/speedtouch-suite-gen-0.4.sh**

I've never installed this, but I guess you will be guided through the process by the installer.

4.) change the settings in the** speedtouch-suite.conf** file by:
**$ sudo gedit /etc/speedtouch/speedtouch-suite.conf **
and continu as described in the howto here:
[http://ubuntuforums.org/showthread.php?t=26017](http://ubuntuforums.org/showthread.php?t=26017)

Let me know if you get problems

---

