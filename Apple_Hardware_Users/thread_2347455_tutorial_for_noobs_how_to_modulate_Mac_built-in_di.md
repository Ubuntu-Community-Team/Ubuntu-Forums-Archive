---
title: "tutorial for noobs: how to modulate Mac built-in display brightness comfortably"
date: 2016-12-25
forum: Apple Hardware Users
---

### Post by 1dono on 2016-12-25
I am a former Mac guy, but since I don't like the current look of OSX any more and Apple decided to build their devices even more compact (with no chance to replace anything), I switched to Linux. To be more precise: Elementary OS (-> nice)
And I have been rather happy with that decision, after I finally got my Magic Mouse and Apple Keyboard working (for the most part). But one thing was totally frustrating: I could not change the display brightness with my keyboard, but only by this single terminal command: ```
 sudo echo YOUR_BRIGHTNESS | tee -a /sys/class/backlight/radeon_bl0/brightness
```
And nothing is more punishing than a screen that roasts your eyes while you're failing to correctly type in your root password ...
Being a Linux noob I searched the internet for a script that could solve that, but I was not lucky. And therefore I unified all my computer knowledges to develop the following tutorial to help out all the helpless noobs out there in this dark world.

The following tutorial will get you either some scripts that let you modulate your screen brightness by keyboard shortcuts or by a simple GUI. For the GUI variant you will also create a dash (app launcher) shortcut that can be drawn into the Elementary OS dock for easy access. The keyboard shortcuts can also be hold down to repeatedly execute your scripts and thereby change your screen brightness fast.
This all was tested on a mid 2011 iMac 27 inch (iMac 12,2) with Elementary OS Loki (Ubuntu 16.04) installed. I guess it will also work for other Apple and none-Apple devices with some modifications. Of course: Use at your own risk!

**IMPORTANT**:
You will have to find out your driver for the display backlight in /sys/class/backlight at first. For the iMac 12,2 you should find /sys/class/backlight/radeon_bl0. Sometimes /sys/class/backlight/radeon_bl1 appears instead, for whatever reason. In this folder there are two files called 'brightness' and 'max_brightness'. 'max_brightness' will show you the maximum relative brightness (255) and 'brightness' the current screen brightness. It can vary from 0 to 255 in steps of one. You should not set the brightness to 0 before you have got your keyboard shortcuts working, because it is rather painful to read of your screen illuminating it with a flash. (Yep, LCD still works, only backlight is off.) In the GUI solution you are prevented from ever setting the value to 0. With the shortcuts working, there is no problem about that.

** VARIANT 1: CUSTOM KEYBOARD SHORTCUTS**

1.) The be able to later reach a brightness of 0 (turn off screen), you set the brightness to a mulitple of 5, for example:
       ```
 sudo echo 50 | tee -a /sys/class/backlight/radeon_bl0/brightness
```
2.) For incrementing the brightness you create a new shell script in /usr/local/bin
        ```
sudo gedit /usr/local/bin/increment_brightness.sh
```
and paste in and save the following:
        ```
#!/bin/bash

      # A little script to set the keyboard backlight
      # Note: needs to be called as root (with gksu or sudo) because
      # of writing to /sys. Use "sudo visudo" to edit the /etc/sudoers file
      # if you want to allow non-admin users to change this value, possibly
      # without having to enter a password. Read "man sudoers" and, e.g., use
      # ALL ALL = NOPASSWD:/usr/local/bin/display-backlight
      # to allow all users to execute this command on all hosts without
      # a password.

      if [ -e /sys/class/backlight/radeon_bl0/brightness ]
        then BACKLIGHT=$(cat /sys/class/backlight/radeon_bl0/brightness)
             BACKLIGHT=$(($BACKLIGHT + 5))             #choose increment size here
             echo $BACKLIGHT | tee -a /sys/class/backlight/radeon_bl0/brightness
             exit 0
      elif [ -e /sys/class/backlight/radeon_bl1/brightness ]
        then BACKLIGHT=$(cat /sys/class/backlight/radeon_bl1/brightness)
             BACKLIGHT=$(($BACKLIGHT + 5))            #choose increment size here
             echo $BACKLIGHT | tee -a /sys/class/backlight/radeon_bl1/brightness
            exit 0
      else
       exit 0
      fi
```
To execute the script, you have to set the file permissions correctly:
        ```
sudo chmod +x /usr/local/bin/increment_brightness.sh
```
3.) For the decrement-brightness-script you create this file and save it:
        ```
sudo gedit /usr/local/bin/decrement_brightness.sh
```
```
#!/bin/bash

      # A little script to set the keyboard backlight
      # Note: needs to be called as root (with gksu or sudo) because
      # of writing to /sys. Use "sudo visudo" to edit the /etc/sudoers file
      # if you want to allow non-admin users to change this value, possibly
      # without having to enter a password. Read "man sudoers" and, e.g., use
      # ALL ALL = NOPASSWD:/usr/local/bin/display-backlight
      # to allow all users to execute this command on all hosts without
      # a password.

      if [ -e /sys/class/backlight/radeon_bl0/brightness ]
        then BACKLIGHT=$(cat /sys/class/backlight/radeon_bl0/brightness)
             BACKLIGHT=$(($BACKLIGHT - 5))            #choose decrement size here
             echo $BACKLIGHT | tee -a /sys/class/backlight/radeon_bl0/brightness
             exit 0
      elif [ -e /sys/class/backlight/radeon_bl1/brightness ]
        then BACKLIGHT=$(cat /sys/class/backlight/radeon_bl1/brightness)
             BACKLIGHT=$(($BACKLIGHT - 5))            #choose decrement size here
             echo $BACKLIGHT | tee -a /sys/class/backlight/radeon_bl1/brightness
             exit 0
      else
       exit 0
      fi  

```
As already shown above, you will have to make this file executable too:
```
         sudo chmod +x /usr/local/bin/decrement_brightness.sh
```
4.) There is one more problem: You will launch your scripts as a normal user, but they need to write to a file that belongs to root. So the easy approach is to alter the access permissions of /sys/class/backlight/radeon_bl0/brightness. That could be done by
```
                 sudo chmod a+rw /sys/class/backlight/radeon_bl0/brightness
```
Unfortunately the files in /sys/ will be deleted and created new on every startup. So you would have to type in this command after every bootup, which I did for a while (-> dumb).
The more intelligent solution is to create yet another script that will do that for you. 
```
         sudo gedit /usr/local/bin/backlight_file_permissions.sh
```
    ```
#!/bin/bash

      #Little script that makes the file /sys/class/backlight/radeon_bl0/brightness
      #(or same with radeon_bl1) editable to all users. Needed to change
      #display backlight brightness via "echo $BACKLIGHT | tee -a #/sys/class/backlight/radeon_bl0/brightness". Launch in rc.local to
      #ensure that the file permissions are updated on every startup.
      #Files in /sys/class/ loose their modified permissions after
      #shutdown.

      if [ -e /sys/class/backlight/radeon_bl0/brightness ]
        then sudo chmod a+rw /sys/class/backlight/radeon_bl0/brightness
             exit 0
      elif [ -e /sys/class/backlight/radeon_bl1/brightness ]
        then sudo chmod a+rw /sys/class/backlight/radeon_bl1/brightness
             exit 0
      else
       exit 0
      fi
```
This will automatically give read and write permissions on the 'brightness' file to every user if it is made executable
```
         sudo chmod +x /usr/local/bin/backlight_file_permissions.sh
```
and is copied into /etc/rc.local. rc.local is a system script which will be launched on every startup and can be used to launch 
your own scripts with root permissions. It should be modified like this:
```
#!/bin/sh -e
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
    
    #that's it:
    /usr/local/bin/backlight_file_permissions.sh
    
exit 0
```
5.) Now you just have to set up your own shortcuts for launching your scripts. This can be done easily with the systems settings 'keyboard', where you should find a section called 'shortcuts' with another subsection named 'custom'. Add a new custom shortcut of your choice (e.g. crtl + F1) and paste in '/usr/local/bin/decrement_brightness.sh' as command. Do the same for your increment shortcut, reboot and feel the magic.


** VARIANT 2: GUI**

1.)
Create new script in usr/local/bin:
        ```
sudo gedit /usr/local/bin/display-backlight.sh
```
2.) Paste in and save the following:    
    ```
#!/bin/bash

      # A little script to set the keyboard backlight
      # Note: clicking "Cancel" in the dialog sets the backlight to 0.
      # Note: needs to be called as root (with gksu or sudo) because
      # of writing to /sys. Use "sudo visudo" to edit the /etc/sudoers file
      # if you want to allow non-admin users to change this value, possibly
      # without having to enter a password. Read "man sudoers" and, e.g., use
      # ALL ALL = NOPASSWD:/usr/local/bin/display-backlight
      # to allow all users to execute this command on all hosts without
      # a password.

      # Read current value
      BACKLIGHT=$(cat /sys/class/backlight/radeon_bl0/brightness)

      BACKLIGHT=$(zenity \
                --title "display-backlight" \
                --scale \
                --text="Adjust the display backlight" \
                --value="$BACKLIGHT" \
                --min-value="1" \
                --max-value="255")

      echo $BACKLIGHT | tee -a /sys/class/backlight/radeon_bl0/brightness
      exit 0
```
3.) Make the script executable:
```
         sudo chmod +x /usr/local/bin/display-backlight.sh
```
4.) Now create a new empty file, paste in the following and move it into /usr/share/applications:
    ```
[Desktop Entry]
    Encoding=UTF-8
    Name=display brightness
    Comment=modulate display brightness via simple GUI
    Exec= "/usr/local/bin/display-backlight.sh"
    Icon=system-lock-screen
    Terminal=true

    Type=Application
    Categories=System
    StartupNotify=false
```
You can choose the category on your own, as well as the icon that will appear in the dash etc. You can find out the names of nice icons by opening other files in /usr/share/applications in a text editor.
5.) To get your GUI working for normal users (not only root) you will need to set read and 
write permissions to the 'brightness' file:
```
         sudo chmod a+rw /sys/class/backlight/radeon_bl0/brightness
```
Just like in variant one, a clever guy will create a script in rc.local for this.



sources:
general ideas for scripts: [https://help.ubuntu.com/community/MacBookPro5-5/Maverick#Keyboard_Functions](https://help.ubuntu.com/community/MacBookPro5-5/Maverick#Keyboard_Functions)
file permissions: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

