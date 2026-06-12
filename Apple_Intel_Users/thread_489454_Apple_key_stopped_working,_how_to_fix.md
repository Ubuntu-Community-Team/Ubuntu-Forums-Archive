---
title: "Apple key stopped working, how to fix?"
date: 2007-07-01
forum: Apple Intel Users
---

### Post by Torajima on 2007-07-01
I have a macbook, and my right apple key has been remapped to 'right click'. It worked flawlessly until yesterday, now it's not working at all.

Here is my .xmodmap:

```
keycode 116 = Pointer_Button3
keycode 108 = Delete
```

The crazy thing is, the Delete key (mapped to 'enter') is still working... so it can't be a problem with xmodmap. And the apple key works fine on OSX and Windows.

Anyone have any ideas? I'm stumped...

---

### Post by ivesjd on 2007-07-01
Have you tried rerunning your .xmodmap?

---

### Post by Torajima on 2007-07-01
> **ivesjd said:**
> Have you tried rerunning your .xmodmap?

I'm not sure what you mean. I've rebooted, if that's what you're asking.

---

### Post by ivesjd on 2007-07-01
Sometimes when I reboot my xmodmap script doesn't work. So I just run it again and everything works again.

---

### Post by Torajima on 2007-07-05
Just in case anyone else has a similar problem, my key started working again after I plugged in and then removed an external USB mouse.

---

### Post by benanzo on 2007-07-06
I'm not certain why **.xmodmap** would flake out.

I use **xkbset** for my keyboard settings.  You might try what I've done to see if it works.

```

#!/bin/bash
#
# Configures Macbook's right apple key to be right mouse-click
# and lower enter key to be delete.
# Install xkbset (sudo apt-get install xkbset).
# Copy this script to ${HOME}/bin/macbook (or wherever you keep your scripts)
# Make it executable:
# ( Right-click -> Properties - > Permissions -> "Allow executing file as Program"
# set GNOME to run it at login ( System -> Preferences -> Sessions )

xmodmap -e 'keycode 116 = Pointer_Button3'
xmodmap -e 'keycode 108 = Delete'
xkbset m

# Disable touchpad for 2 seconds after last key press
# to prevent accidental touchpad activation while typing.

/usr/bin/syndaemon -d -t -i 2

```

Good Luck!

---

### Post by ThinkBuntu on 2007-07-07
Could you please post a little info as to how you use xkbset to remap keys? I'm trying to actually switch my Alt and Ctrl keys on a ThinkPad, but am not sure where to start. I'm doing it because I'm very used to the location of the "Apple" key on a mac, and I want my Control key to be in that spot.

---

### Post by benanzo on 2007-07-07
I only use **xkbset** to allow mouse button emulation from a keyboard key.  For remapping keyboard keys with other keyboard keys you can just use **xmodmap**.

First you'll need to find out what keycodes the Alt and Ctrl keys use.  Open a terminal and do:
```
xev
```
This will pop up a window that captures all keyboard/mouse data and prints it in the terminal.
For instance, when I press my left Alt key it shows:
```

KeyPress event, serial 31, synthetic NO, window 0x3400001,
    root 0x5d, subw 0x0, time 63988728, (-165,324), root:(498,374),
    state 0x0, **keycode 64** (keysym 0xffe9, **Alt_L**), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 31, synthetic NO, window 0x3400001,
    root 0x5d, subw 0x0, time 63988792, (-165,324), root:(498,374),
    state 0x8, **keycode 64** (keysym 0xffe9, **Alt_L**), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```
Notice that there are two events generated, one when the key is pressed and one when it is released.  Be careful though because if you're moving your mouse around a lot the data will scroll by pretty fast.

If I were to remap the Ctrl and Alt keys on my keyboard it would look like this:
```

# The original mapping according to *xev*:
# Control_L = keycode 37
# Alt_L = keycode 64

# swap them to remap the keys:
xmodmap -e 'keycode 64 = Control_L'
xmodmap -e 'keycode 37 = Alt_L'

```
You can either put this info in the **.xmodmap** file in your home directory or you can make it into a separate script like I did above.

Good Luck!

---

### Post by zmike1 on 2007-07-08
>  .... 

If I were to remap the Ctrl and Alt keys on my keyboard it would look like this:
```

# The original mapping according to *xev*:
# Control_L = keycode 37
# Alt_L = keycode 64

# swap them to remap the keys:
xmodmap -e 'keycode 64 = Control_L'
xmodmap -e 'keycode 37 = Alt_L'

```
You can either put this info in the **.xmodmap** file in your home directory or you can make it into a separate script like I did above.

Good Luck!

...jumping in...
Where would I put the script??  Where is the .xmodmap file located ?
My home directory appears to be completely empty?

---

### Post by benanzo on 2007-07-08
When people make scripts that they use for a specific purpose such as this they usually put it in a directory called **bin** in their /home/<username> directory.  You will usually have to create this directory yourself first.
```
mkdir ${HOME}/bin
```
(the term ${HOME} or sometimes $HOME refers to a variable that Ubuntu recognizes as the current user's /home/<username> directory.  You can interchange ${HOME} with /home/<username>.)

Now copy that script into a file called **keyboard.sh** (or whatever you want) and move it into that directory.  You will need to allow that script to run as a program by right-clicking it then selecting **Properties** -> **Permissions** then check the box next to **Allow executing file as program**.

Now to have it run whenever you start your desktop session go to **System -> Preferences -> Sessions** then under the **Startup Programs** tab select **New**.  You can give it any name you want such as "Keyboard Settings" - for the **Command** box click **Browse** and go to the **${HOME}/bin** directory you created and select your keyboard script.

The **.xmodmap** file is actually a hidden file in your ${HOME} directory.  If you open the file manager (Nautilus) and hit CTRL-H it will show all the hidden files and directories.  Those files and directories have a **.** (period) in front of the name to indicate that they're hidden.  If you go to **System -> Help and Support ** then search for **xmodmap** you can read about what it does.

If you do:
```
gedit ${HOME}/.xmodmap
``` in a terminal it will open that file for editing without having to find it in Nautilus.

Good Luck!

---

### Post by Torajima on 2007-07-08
> **benanzo said:**
> When people make scripts that they use for a specific purpose such as this they usually put it in a directory called **bin** in their /home/<username> directory.  You will usually have to create this directory yourself first.

Any reason not to just stick it in the existing /usr/bin?

---

### Post by cyberdork33 on 2007-07-08
/usr/bin is appropriate if several users need to access it.

---

### Post by benanzo on 2007-07-08
it doesn't matter.  They're both part of your ${PATH}.  Many people (including me) prefer to keep personal scripts organized in ${HOME}/bin instead of sticking them in /usr/bin or /usr/local/bin.  

It's easier for new people to manage scripts like these (and not forget about them) if they're in ${HOME}/bin.

---

