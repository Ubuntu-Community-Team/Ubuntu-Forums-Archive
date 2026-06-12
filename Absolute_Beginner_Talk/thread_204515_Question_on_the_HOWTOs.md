---
title: "Question on the HOWTOs"
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by IDontKnow9998 on 2006-06-27
[http://www.ubuntuforums.org/showthread.php?t=125752](http://www.ubuntuforums.org/showthread.php?t=125752)

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo gedit /etc/X11/xorg.conf
```

What does that mean?

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"Protocol"		"evdev"
	Option       	"Dev Name"		"Logitech USB Receiver"
	Option		"Device"		"/dev/input/mice"
	Option		"Buttons"		"8"
	Option		"ZAxisMapping"		"4 5 7 8"
EndSection
```

I found the xorg.cong file with the search. But when I try to replace that with the current mouse thing I get some sort of error about the file being in used.

---

### Post by woedend on 2006-06-27
[QUOTE=IDontKnow9998][http://www.ubuntuforums.org/showthread.php?t=125752](http://www.ubuntuforums.org/showthread.php?t=125752)

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo gedit /etc/X11/xorg.conf
```

What does that mean?
[/QUOTE]

sudo is the command to give you root priveleges.  You need root privelege to make changes to important files, like xorg.conf.  cp means copy.  Copy uses two "arguments",separated with a space.  The first argument is the file to be copied.  The second is where to copy the file.  Put together, we have
With root privelege, copy /etc/X11/xorg.conf to /etc/X11/xorg.conf_backup
this way, if when you reboot things dont work, you can easily put back xorg.conf by reversing the two

gedit is the program similar to notepad, to edit text files.  it means
with root priveleges, allow me to edit by hand xorg.conf

[QUOTE=IDontKnow9998]
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"Protocol"		"evdev"
	Option       	"Dev Name"		"Logitech USB Receiver"
	Option		"Device"		"/dev/input/mice"
	Option		"Buttons"		"8"
	Option		"ZAxisMapping"		"4 5 7 8"
EndSection
```

I found the xorg.cong file with the search. But when I try to replace that with the current mouse thing I get some sort of error about the file being in used.[/QUOTE]

I will be perfectly honest with you...I did not like this Howto.  No offense to the author or any it has helped, but I found that it simply did not work for me, nor would it have added any features over explorer.

---

### Post by matrooswolf on 2006-06-27
I don't really understand what your problem is, but:
go to the terminal:
it is in the menu:
Applications > Accessories > Terminal

then copy the first two commands (one by one) and paste them in the terminal.

The second command will open a new window with the xorg.conf open in it.

Scroll down till you find the section "inputdevice" and replace it with 
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"Protocol"		"evdev"
	Option       	"Dev Name"		"Logitech USB Receiver"
	Option		"Device"		"/dev/input/mice"
	Option		"Buttons"		"8"
	Option		"ZAxisMapping"		"4 5 7 8"
EndSection
```
save and exit ...

Then logout and log back in, that should do the trick ...

Edit: woedend beat me, and better ... (btw woedend, did you know that woedend means very enraged in dutch?)

---

### Post by adam.tropics on 2006-06-27
The first line copies (cp) for backup, the xorg.conf file (when you hit return), and the second opens the file in a text editor (in this case gedit)

If you did this, then a search, the file will show as in use by the above command I imagine, in the terminal where you entered the above command it will have asked for your password. Enter it and it will open the files with permission needed to edit it.

Also, I had a quick look at the guide you are using. Its fine but I should mention that with Logitech hardware, there is a tendancy on model changeovers to change capitalisation on the name. Just to be safe, 
In a terminal type

```
cat /proc/bus/input/devices
```

then <enter>

The output will have a section related to the Logitech USB Receiver. You need to just check how it is written. For me for example it is Logitech USB RECEIVER. Whilst only a capitalisation thing it is enough to be an issue. If this is the case just adjust the guide you are using accordingly.

Good luck

---

### Post by adam.tropics on 2006-06-27
matrooswolf, are you using this setup yourself successfully? 

On a little further investigation, it is not gonna work without the older evdev package, and also, evdev has become a driver rather than protocol. I'm sorry but it isn't gonna work i fear. you would perhaps do well to sort of 'tweak' [this one....]("http://ubuntuforums.org/showthread.php?t=188302&highlight=mx1000+adam.tropics")sorry for the earlier error on my part.

---

### Post by matrooswolf on 2006-06-27
[QUOTE=adam.tropics]matrooswolf, are you using this setup yourself successfully? 

On a little further investigation, it is not gonna work without the older evdev package, and also, evdev has become a driver rather than protocol. I'm sorry but it isn't gonna work i fear. you would perhaps do well to sort of 'tweak' [this one....]("http://ubuntuforums.org/showthread.php?t=188302&highlight=mx1000+adam.tropics")sorry for the earlier error on my part.[/QUOTE]
HI adam.tropics.
No, I'm not, I just tried to reply to IDontKnow9998 (see his first post).  And I think I am way out of line here, I don't even know what evdev is.

But on the other hand, I'm interested by your remark, I have a MX1000 myself and never set it up right (it is still on my todo list ;)

If have had a quick look at your link, and I will look into it when I have more time, (but it says "not for the faint of heart", that's bad news, because that describes my category quite accurately ;))

---

### Post by IDontKnow9998 on 2006-06-27
yeah tnx for the reply... but it also did not work with me :(

Nothing I try on Linux works :P

Took me 6 attempts and two formats to get it 2 work.... and even after all that grub is on the wrong hdd that im getting rid of in 2 months max :\ (have 2 tell my bios 2 boot from a other HDD that does not have win xp / Linux :\)

---

