---
title: "Ctrl-Alt-F7 doesnt returns the GUI"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by buntutur on 2007-07-17
Hi friends,

I was trying to set up the dual monitor on my PC.i was just following some procedure to do so, i went into terminal mode after pressiing Ctrl-Alt-F1.

But now i cannot return back to GUI (desktop mode).I have tried using Ctrl-Alt-F7, but to no avail.

Please help me....

---

### Post by overdrank on 2007-07-17
> **buntutur said:**
> Hi friends,

I was trying to set up the dual monitor on my PC.i was just following some procedure to do so, i went into terminal mode after pressiing Ctrl-Alt-F1.

But now i cannot return back to GUI (desktop mode).I have tried using Ctrl-Alt-F7, but to no avail.

Please help me....

HI I had this happen on another keyboard try the F6 instead of the F7.:(

---

### Post by hannulan on 2007-07-17
Had the GUI started at first? Ctrl-Alt-F? makes you go to another "desktop" (I don't know the name of it, it is not desktop). 

Login in the consol and try to start the Xserver instead. This is done by typing "sudo /etc/init.d/gdm restart" in the consol.

---

### Post by buntutur on 2007-07-17
thanks for the help, but none of it works,,while pressing F6 shows console a tty5 and sudo /etc............ is not accepted ...

GUI was working fine before i changed some xorg file.....

---

### Post by overdrank on 2007-07-17
> **buntutur said:**
> thanks for the help, but none of it works,,while pressing F6 shows console a tty5 and sudo /etc............ is not accepted ...

GUI was working fine before i changed some xorg file.....

Hi if you changed settings in the xorg you need to reboot first.

---

### Post by buntutur on 2007-07-17
Danke...u were right....its OK now...but the screen waves as i scroll down...any guesses what mite be the problem..

---

### Post by overdrank on 2007-07-17
> **buntutur said:**
> Danke...u were right....its OK now...but the screen waves as i scroll down...any guesses what mite be the problem..

It would be my fist concern the graphics driver. What changes did you make in the xorg?

---

### Post by buntutur on 2007-07-17
> **overdrank said:**
> It would be my fist concern the graphics driver. What changes did you make in the xorg?

i am not sure what changes i made as i was just following the procedure posted by somebody.

what should i do to check the graphic drivers..

---

### Post by overdrank on 2007-07-17
> **buntutur said:**
> i am not sure what changes i made as i was just following the procedure posted by somebody.

what should i do to check the graphic drivers..

**Do you have a link for the page? **You can view your xorg and it will be under device. Here is mine
```
Section "Device"
	Identifier	"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection
```
Use this command in the terminal 
```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by hannulan on 2007-07-17
I'm not sure what you mean with "the screen waves as i scroll down". Is the picture moving as it is not suppose to do. 

In that case it *can* be the updating frequency. In the xorg.configrue file look for the Section "Monitor" and then the entries HorizSync and VertRefresh and see if they are compatible with your monitor.

---

### Post by buntutur on 2007-07-17
> **overdrank said:**
> **Do you have a link for the page? **You can view your xorg and it will be under device. Here is mine
```
Section "Device"
	Identifier	"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection
```
Use this command in the terminal 
```
gksudo gedit /etc/X11/xorg.conf
```

It sayz command not found......

However i got following result >

bash: gksudo: command not found
@buntu-desktop:~$ sudo gedit /etc/X11/xorg.conf
Password:
X Error: BadDevice, invalid or uninitialized input device 154
  Major opcode:  143
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 154
  Major opcode:  143
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Traceback (most recent call last):
  File "/usr/lib/gedit-2/plugins/modelines.py", line 23, in ?
    import gconf
ImportError: No module named gconf

** (gedit:8502): WARNING **: Could not load python module modelines


** (gedit:8502): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN
 (plugin)' failed

** (gedit:8502): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN                                                               (plugin)' failed

** (gedit:8502): WARNING **: Throbber rest icon not found
/bin/sh: /usr/bin/esd: not found

** (gedit:8502): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN                                                               (plugin)' failed

** (gedit:8502): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN                                                               (plugin)' failed

** (gedit:8502): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN                                                               (plugin)' failed

** (gedit:8502): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN                                                               (plugin)' failed

** (gedit:8502): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN                                                               (plugin)' failed

** (gedit:8502): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN                                                               (plugin)' failed


.............................

Screen wavers mean, when i scroll down down a page..the screen waves ....normally this should not happen.
How do i look in xconfig file..can zou plz let me know the command


Thanx

---

