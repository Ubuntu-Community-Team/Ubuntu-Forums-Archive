---
title: "gksudo not found"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by dhawald3 on 2006-11-17
I am using kubunutu 6.06

I installed grubed,but when I try to run it
the following error comes.

gksudo GrubEd
bash: gksudo: command not found

please help

---

### Post by Bachstelze on 2006-11-17
In KDE, you use *kdesu* instead of *gksudo*.

---

### Post by earobinson on 2006-11-17
The kde version of gksudo is 'kdesu'
source: [https://launchpad.net/distros/ubuntu/+ticket/1983](https://launchpad.net/distros/ubuntu/+ticket/1983)

---

### Post by dhawald3 on 2006-11-17
now the following error comes

X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
qstring_to_xtp result code -2
qstring_to_xtp result code -2
/usr/bin/GrubEd: line 26: zenity: command not found

---

### Post by earobinson on 2006-11-17
can you tell us what you did to get those errors?

---

### Post by Bachstelze on 2006-11-17
My guess is that you need to install a package called *zenity* but I'm not 100% sure since I don't know that app.

---

### Post by dhawald3 on 2006-11-17
> **earobinson said:**
> can you tell us what you did to get those errors?

I just entered the terminal and typed

kdesu grubed

---

### Post by Bachstelze on 2006-11-17
(Almost) all the messages you get are normal. The real problem is the last line, telling you that your 'grubed' app cannot find another one called 'zenity', so if I were you, I'd try to install that one too.

---

### Post by dhawald3 on 2006-11-17
> **HymnToLife said:**
> (Almost) all the messages you get are normal. The real problem is the last line, telling you that your 'grubed' app cannot find another one called 'zenity', so if I were you, I'd try to install that one too.

It ran!!

here's some info about zenity
zinity 
Displays graphical dialog boxes from shell scripts
Zenity allows you to display GTK+ dialogs from shell scripts; it is a rewrite of the `gdialog' command from GNOME 1.
Zenity includes a gdialog wrapper script so that it can be used with legacy scripts.

---

### Post by ajgreeny on 2006-11-17
All the error bit of your message

X Error: BadDevice, invalid or uninitialized input device 168
Major opcode: 145
Minor opcode: 3
Resource id: 0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
Major opcode: 145
Minor opcode: 3
Resource id: 0x0

 are due to invalid entries in your */etc/X11/xorg.conf* file.  You need to comment out with # at the beginning any lines related to wacom devices you don't have.

For example in my xorg.conf file I have the following lines all commented out
#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "stylus"
#  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
#  Option        "Type"          "stylus"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "eraser"
#  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
#  Option        "Type"          "eraser"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "cursor"
#  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
#  Option        "Type"          "cursor"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection

and then at the bottom of the file the following three lines also

#    InputDevice     "stylus" "SendCoreEvents"
#    InputDevice     "cursor" "SendCoreEvents"
#    InputDevice     "eraser" "SendCoreEvents"

This should remove the errors from terminal starts of most applications.  If you have one of there devices (I note only two sets of the error, not three as I had) you will need to leave that one uncommented.

---

### Post by earobinson on 2006-11-17
> **dhawald3 said:**
> It ran!!

here's some info about zenity
zinity 
Displays graphical dialog boxes from shell scripts
Zenity allows you to display GTK+ dialogs from shell scripts; it is a rewrite of the `gdialog' command from GNOME 1.
Zenity includes a gdialog wrapper script so that it can be used with legacy scripts.
well if everything is resolved do us a favor, edit the original post, click advanced, and mark this thread as resolved

---

