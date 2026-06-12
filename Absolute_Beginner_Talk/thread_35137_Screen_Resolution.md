---
title: "Screen Resolution"
date: 2005-05-17
forum: Absolute Beginner Talk
---

### Post by roba1 on 2005-05-17
My first install of a linux distro.

Every thing went just great, but.

My screen resolution is 640x480, and the only other option I have in the control panel is 300x200?
How come there is not more choices. I have a 17" monitor and am capable of higher resolutions....would like to be at 1024x768.

Do I have to install drivers for my Viewsonic E771 monitor?
Or is there something I missed in the original install?

I installed to the entire 10gig drive, no other os running.
Just pressed return at the install prompt.

My system is a 400mgz Intel chip, voodoo3 graphics card and sound blaster live! card.

Ty in advance for any help

---

### Post by Xian on 2005-05-17
I would first make sure that you have the proper sync rates for you monitor listed in the /etc/X11/xorg.conf file. The section listed below is what you are looking for, and I have included my actual specs. Do you have the lines "HorizSync" & "VertRefresh"?

```
Section "Monitor"
	Identifier	"COMPAQ 7500"
	Option		"DPMS"
        HorizSync       30-70
        VertRefresh     50-140
EndSection
```

---

### Post by roba1 on 2005-05-17
Ok....found the file you where talking about.

No it does not have those lines in the file...ie......horizsync...vertrefresh.
I tried to insert the lines but could not save the file.

What am I doing wrong.....lol

---

### Post by TravisNewman on 2005-05-17
you have to edit it as superuser, for example, type "sudo nano /etc/X11/xorg.conf"

---

### Post by roba1 on 2005-05-17
lol.....as the topic of this thread says......absolute new user....that's me.

Where do I type  sudo...ect......               lol

---

### Post by TravisNewman on 2005-05-17
[QUOTE=roba1]lol.....as the topic of this thread says......absolute new user....that's me.

Where do I type  sudo...ect......               lol[/QUOTE]
 in a terminal. You can get one by right clicking the desktop and choosing "open terminal," or by clicking on it's icon in the system tools section of the menu.

---

### Post by roba1 on 2005-05-17
ok....have been trying to do as you suggested but I keep getting a black screen with no writing, thought that that command would load the xorg.conf file?
Seems to me that I would be creating a new  file so have just closed the konsole
and did not save.

---

### Post by Xian on 2005-05-17
[QUOTE=roba1]ok....have been trying to do as you suggested but I keep getting a black screen with no writing, thought that that command would load the xorg.conf file?[/QUOTE]
The path must be improper.
Just open a terminal as previously described, enter the text listed below, and then just navigate to the file and make needed changes.

```
$ sudo gedit
```

If you are in KDE then do this:

KDE Start Menu Icon > Run Command > kdesu kwrite

Or you can enter this in the Konsole:
```
sudo kwrite /etc/X11/xorg.conf
```

---

### Post by momo66 on 2005-05-17
[QUOTE=roba1]ok....have been trying to do as you suggested but I keep getting a black screen with no writing, thought that that command would load the xorg.conf file?
Seems to me that I would be creating a new  file so have just closed the konsole
and did not save.[/QUOTE]


 Make sure you are using caps 

/etc/X11/xorg.conf

X in X11 is capitalized.  

the command at the terminal prompt should be 

```
sudo gedit /etc/X11/xorg.conf
```

Cut and paste the code mentioned in the previous post for your Horizontal and Vertical Sync.  Then restart your X session.

---

### Post by roba1 on 2005-05-17
ok...do not think i have any of these editors installed...gedit...kwrite...

Just did a default install of Kubuntu......kate is there but I just get an error when trying to open the file using kate

Where do I go to install other packages ..ie.. gedit and kwrite?

---

### Post by roba1 on 2005-05-17
OK.....It just started to work....go figure....got nano to read the file...made the changes as instructed
but now I am at a loss as to how to save my changes......can't find a "save" or "save as" command.......
boy these new users.........lol

---

### Post by roba1 on 2005-05-17
Got it to work...ty all for your help......but as Arnie says..
I'll be back!

---

### Post by momo66 on 2005-05-19
[QUOTE=roba1]ok...do not think i have any of these editors installed...gedit...kwrite...

Just did a default install of Kubuntu......kate is there but I just get an error when trying to open the file using kate

Where do I go to install other packages ..ie.. gedit and kwrite?[/QUOTE]

go to a terminal prompt and type

```
sudo apt-get install kwrite
``` 

that should install kwrite.  

now you can use the command

```
sudo kwrite /etc/X11/xorg.conf
```

to edit your xorg.conf as mentioned before.

---

### Post by wolfsta on 2007-09-15
Thank you Xian for posting your settings..

I've been trying to find the sync ranges for my compaq 7500 for ages.. works perfectly now :)

Wolfsta

---

