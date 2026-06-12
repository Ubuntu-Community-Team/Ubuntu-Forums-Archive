---
title: "toolbars"
date: 2005-01-11
forum: Art &amp; Design
---

### Post by danip on 2005-01-11
Ive seen some screen shots of themes that have that macos like toolbar on the bottom anyone know the name and where i can get it?  Also I have seen some things on the desktop that display the weather.  How can I get this all I can get is the little one that displays on the top toolbar.

---

### Post by sobralense on 2005-01-12
It will be better if you know how to upgrade to Hoary Version of Ubuntu.
The application name is.. gdesklets  search a bit for this name here, some people didn't  know how to install and the application work "how it should" =)

gdesklets shows the "osx" like toolbar , the weather, etc..

some people having problems to see my shot, try it:
[http://sobralense.host.sk/screenshot1.png](http://sobralense.host.sk/screenshot1.png)

I think is this what you're looking for... to install, try:

"sudo apt-get install gdesklets-data"

 (it will install normal gdesklets package as a dependecy, the *-data packages is the "plugins-pack")

ok, good luck...

---

### Post by danip on 2005-01-12
Ive been very reluctant to upgrade to hoary because i fear it is not stable enough for me.  Can you tell me differently?


by the way i cant get to your screen shot it says i do not have permission

---

### Post by danip on 2005-01-12
I have every thing that apt will install when you tell it to install gdesklets.  Now i type gdesklets into the terminal and here is my output.

```
steve@blackbetty ~/Desktop/themes/starterbar-desklet-0.31.2 $ gdesklets
gDesklets 0.26.2
Copyright (C) 2003, 2004 The gDesklets Team

This software is licensed under the terms of the GNU GPL.

[/home/steve/Desktop/themes/starterbar-desklet-0.31.2/starterbar.display]
/usr/lib/python2.3/site-packages/gtk-2.0/gtk/__init__.py:90: GtkDeprecationWarning: gtk.mainiteration is deprecated, use gtk.main_iteration instead
  self.warn(message, DeprecationWarning)
cp /usr/share/gdesklets/Sensors/StarterBar/home.desktop /usr/share/gdesklets/Sensors/StarterBar/.order /home/steve/.gdesklets/MyStarters/1105559628980228254073092iconbar/

``` 

What does this mean?  Also I am now trying to install the starter bar.  I go to the folder the bin file is in and type sh 'filename' then i get this plus sign for my curser and nothing happens.  I click my mouse and this is the output.

```
steve@blackbetty ~/Desktop/themes/starterbar-desklet-0.31.2 $ sh Install_StarterBar_Sensor.bin
Install_StarterBar_Sensor.bin: line 18: ERROR_B64: command not found
Install_StarterBar_Sensor.bin: line 20: ERROR_TAR: command not found
Install_StarterBar_Sensor.bin: line 22: SUCCESS: command not found
Install_StarterBar_Sensor.bin: line 27: no_message: command not found
Install_StarterBar_Sensor.bin: line 28: list_only: command not found
Install_StarterBar_Sensor.bin: line 29: destination: command not found
Install_StarterBar_Sensor.bin: line 32: args: command not found
Install_StarterBar_Sensor.bin: line 34: syntax error near unexpected token `if'Install_StarterBar_Sensor.bin: line 34: `    if (p == "--nomsg"): no_message = 1 '

```

---

### Post by danip on 2005-01-12
NM i did alot of playing with gdesklets and I got it working.  Can anyone tell me how to get it to run on startup?

---

