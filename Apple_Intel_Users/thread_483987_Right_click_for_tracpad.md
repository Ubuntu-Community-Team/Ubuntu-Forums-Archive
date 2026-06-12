---
title: "Right click for tracpad"
date: 2007-06-25
forum: Apple Intel Users
---

### Post by hjel on 2007-06-25
how can i setup the right click on my tracpad

---

### Post by ivesjd on 2007-06-25
I have heard that three finger tap is supposed to work out of the box. But since I don't like tapping I use this code in rc.local (so its enabled on boot)
```

#makes right cmd right click
xmodmap -e 'keycode 116 = Pointer_Button3' 
# Disable touchpad for 1 seconds after last key press 
# to prevent accidental touchpad activation while typing. 
syndaemon -d -k -K -i 1

```
put that other code in there figured you might like it too. The right cmd button is the right apple button FYI.

---

### Post by kzm. on 2007-06-25
this works for me, too. i have the default three finger tap = right mouse working out of the box. 
but to have some real buttons i can keep pressed i use a solution like ivesjd

i have the lower enter key as right and the right option as middle.. wondering where i have my alt-gr now.. :roll:

    sudo mkdir /bin/scripts
    sudo gedit /bin/scripts/keys_mouse_mac_fix
    add:
    #makes lower enter key right click.
    xmodmap -e 'keycode 108 = Pointer_Button3'
    #makes right apple key middle click.
    xmodmap -e 'keycode 116 = Pointer_Button2'
    
    sudo nautilus
    go /bin/scripts/ select keys_mouse_mac_fix set under permission "executable"
    go System > Preferences > Session 
    add "mac mouse fix" : /bin/scripts/keys_mouse_mac_fix

---

### Post by wigglydiggly on 2007-06-26
> **ivesjd said:**
> I have heard that three finger tap is supposed to work out of the box. But since I don't like tapping I use this code in rc.local (so its enabled on boot)
```

#makes right cmd right click
xmodmap -e 'keycode 116 = Pointer_Button3' 
# Disable touchpad for 1 seconds after last key press 
# to prevent accidental touchpad activation while typing. 
syndaemon -d -k -K -i 1

```
put that other code in there figured you might like it too. The right cmd button is the right apple button FYI.

I tried your code but it didn't work.  Here's my rc.local:

!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

#makes right cmd right click
xmodmap -e 'keycode 116 = Pointer_Button3' 
# Disable touchpad for 1 seconds after last key press 
# to prevent accidental touchpad activation while typing. 
syndaemon -d -k -K -i 1

exit 0

Running on C2D Macbook.

Thanks in advance for you time.

---

### Post by ivesjd on 2007-06-27
Sorry, I had not tried putting that code in the rc.local. But thought it would work. I tried it as well and it didn't work. So what you need to do is put the code into a file. Then right click the file and go to permissions and check the executible box. I have mine in /bin/scripts/xmodmap and then go to system>preferences>sessions and create a new entry. Name it xmodmap and put in /bin/scripts/xmodmap and itll work. Also you can just double click the file/script and itll run without you having to reboot. I sometime find it doesnt work so I just run it manually when need be.

---

