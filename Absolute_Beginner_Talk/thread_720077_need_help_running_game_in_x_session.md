---
title: "need help running game in x session"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by linuxjerk on 2008-03-09
having trouble getting a game to run in it's own x session.

Here is a script I tried and some of the errors it generated.

I figured out I needed a "sudo" in the place where the x session is called.
 but then the x window opens and I don't know how to get out of it so I can't get
back to the console to see the errors generated.

I can see from the errors that a driver is not found and the display is not being set up properly.
I don't know what this means and I would appreciate all the help I can get.


dennis@dennis-desktop:~$ #!/bin/sh
dennis@dennis-desktop:~$ #uncomment if launching from console session
dennis@dennis-desktop:~$ #sudo /etc/init.d/gdm stop
dennis@dennis-desktop:~$ #KDE use this instead
dennis@dennis-desktop:~$ #sudo /etc/init.d/kdm stop
dennis@dennis-desktop:~$
dennis@dennis-desktop:~$ # Launches a new X session on display 3. If you don't have an Nvidia card
dennis@dennis-desktop:~$ # take out the "& nvidia-settings --load-config-only" part
dennis@dennis-desktop:~$ X :3 -ac
X: user not authorized to run the X server, aborting.
dennis@dennis-desktop:~$
dennis@dennis-desktop:~$ # Goto game dir (modify as needed)
dennis@dennis-desktop:~$ cd "$HOME/.wine/drive_c/Program Files/DreamWorks Interactive/Trespasser/"
[email]dennis@dennis-desktop:~/.wine[/email]/drive_c/Program Files/DreamWorks Interactive/Trespasser$
[email]dennis@dennis-desktop:~/.wine[/email]/drive_c/Program Files/DreamWorks Interactive/Trespasser$ # Forces the system to have a break for 2 seconds, X doesn't launch instantly
[email]dennis@dennis-desktop:~/.wine[/email]/drive_c/Program Files/DreamWorks Interactive/Trespasser$ sleep 2
[email]dennis@dennis-desktop:~/.wine[/email]/drive_c/Program Files/DreamWorks Interactive/Trespasser$
[email]dennis@dennis-desktop:~/.wine[/email]/drive_c/Program Files/DreamWorks Interactive/Trespasser$ # Launches game (modify as needed)
[email]dennis@dennis-desktop:~/.wine[/email]/drive_c/Program Files/DreamWorks Interactive/Trespasser$ DISPLAY=:3 WINEDEBUG=-all wine "C:/Program Files/DreamWorks Interactive/Trespasser/Trespass.exe"
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
[email]dennis@dennis-desktop:~/.wine[/email]/drive_c/Program Files/DreamWorks Interactive/Trespasser$ Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
__________________

---

### Post by Oldsoldier2003 on 2008-03-09
> **linuxjerk said:**
> having trouble getting a game to run in it's own x session.

Here is a script I tried and some of the errors it generated.

I figured out I needed a "sudo" in the place where the x session is called.
 but then the x window opens and I don't know how to get out of it so I can't get
back to the console to see the errors generated.

I can see from the errors that a driver is not found and the display is not being set up properly.
I don't know what this means and I would appreciate all the help I can get.


dennis@dennis-desktop:~$ #!/bin/sh
dennis@dennis-desktop:~$ #uncomment if launching from console session
dennis@dennis-desktop:~$ #sudo /etc/init.d/gdm stop
dennis@dennis-desktop:~$ #KDE use this instead
dennis@dennis-desktop:~$ #sudo /etc/init.d/kdm stop
dennis@dennis-desktop:~$
dennis@dennis-desktop:~$ # Launches a new X session on display 3. If you don't have an Nvidia card
dennis@dennis-desktop:~$ # take out the "& nvidia-settings --load-config-only" part
dennis@dennis-desktop:~$ X :3 -ac
X: user not authorized to run the X server, aborting.
dennis@dennis-desktop:~$
dennis@dennis-desktop:~$ # Goto game dir (modify as needed)
dennis@dennis-desktop:~$ cd "$HOME/.wine/drive_c/Program Files/DreamWorks Interactive/Trespasser/"
[email]dennis@dennis-desktop:~/.wine[/email]/drive_c/Program Files/DreamWorks Interactive/Trespasser$
[email]dennis@dennis-desktop:~/.wine[/email]/drive_c/Program Files/DreamWorks Interactive/Trespasser$ # Forces the system to have a break for 2 seconds, X doesn't launch instantly
[email]dennis@dennis-desktop:~/.wine[/email]/drive_c/Program Files/DreamWorks Interactive/Trespasser$ sleep 2
[email]dennis@dennis-desktop:~/.wine[/email]/drive_c/Program Files/DreamWorks Interactive/Trespasser$
[email]dennis@dennis-desktop:~/.wine[/email]/drive_c/Program Files/DreamWorks Interactive/Trespasser$ # Launches game (modify as needed)
[email]dennis@dennis-desktop:~/.wine[/email]/drive_c/Program Files/DreamWorks Interactive/Trespasser$ DISPLAY=:3 WINEDEBUG=-all wine "C:/Program Files/DreamWorks Interactive/Trespasser/Trespass.exe"
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
[email]dennis@dennis-desktop:~/.wine[/email]/drive_c/Program Files/DreamWorks Interactive/Trespasser$ Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
__________________

this needs to be saved into a file then the script needs to be run, not entered from the terminal. paste the example code form the tutorial into a text editor, save the file and chmod it as in the tutorial. you will need to adjust the paths and uncomment the lines for the window manager you are using.

---

### Post by linuxjerk on 2008-03-09
You are right. I need to go back and read the tutorial more carefuly. But there are still some things about the chmod thing and getting the file saved properly that are puzzling me.
I have the file saved as a text file but I'm not sure I have things setup properly.
I'll have ttomorrow it's getting late. But thanks for replying

---

### Post by linuxjerk on 2008-03-10
I feel like such a lame bone head.

I'm afraid I don't even know what a window manager is?
I tried the chmod thing and the first time all I got was a grey screen with an X in the middle.
The next time I tried it with this uncommented "#sudo /etc/init.d/gdm stop" and the whole system crashed.
When I paste this stuff into "nano" alot of the stuff disappears. Is this normal?
I'm afraid this is getting too much like programming, and I'm no programmer.

Someone will have to walk me through this.
This is a listing of what I have so far.
Help!

#!/bin/sh
#uncomment if launching from console session
#sudo /etc/init.d/gdm stop
#KDE use this instead
#sudo /etc/init.d/kdm stop

# Launches a new X session on display 3. If you don't have an Nvidia card
# take out the "& nvidia-settings --load-config-only" part
X :3 -ac

# Goto game dir (modify as needed)
cd "$HOME/.wine/drive_c/Program Files/DreamWorks Interactive/Trespasser/"

# Forces the system to have a break for 2 seconds, X doesn't launch instantly 
sleep 2

# Launches game (modify as needed)
DISPLAY=:3 WINEDEBUG=-all wine "C:/Program Files/DreamWorks Interactive/Trespasser/Trespass.exe"

---

### Post by linuxjerk on 2008-03-10
Can anyone help with this? I really don't know what I'm doing on this one.

---

### Post by linuxjerk on 2008-03-10
I don't know if this is a problem but I did install directx

---

### Post by RequinB4 on 2008-03-10
Go to applications - acessories - text editor.

Copy and paste the script into the text editor.

Go to file - save as, then save as scriptname.sh on your Desktop

Go to applications - acessories - terminal and run the following 

```

cd ~/Desktop
sh scriptname.sh

```

Be sure to keep that line uncommented, as you noticed, it doesn't like it when you stop your Graphical interface.  It should not ask you for your password.  If you installed Tresspasser into a different WINE directory, place that directory instead of Program Files/DreamWorks Interactive/Trespasser.

If that doesn't work, try replacing all the / in the last line of code with the character \

And good luck

---

### Post by linuxjerk on 2008-03-10
Well this is exactly as I ran it. Except I had to put a "sudo" in here "sudo X :3 -ac" because I got don't have authorization to run xserver error without it.

The results were a blank grey screen with an X in the middle. Waited about 5 minutes and nothing. Did ctrl+alt+f7 to get back to the terminal. It was full of blanks. No error messages in the terminal.
I rechecked my paths to the game and all looks correct.
Don't know what to do???


#!/bin/sh
#uncomment if launching from console session
#sudo /etc/init.d/gdm stop
#KDE use this instead
#sudo /etc/init.d/kdm stop

# Launches a new X session on display 3. If you don't have an Nvidia card
# take out the "& nvidia-settings --load-config-only" part
sudo X :3 -ac

# Goto game dir (modify as needed)
cd "$HOME/.wine/drive_c/Program Files/DreamWorks Interactive/Trespasser/"

# Forces the system to have a break for 2 seconds, X doesn't launch instantly 
sleep 2

# Launches game (modify as needed)
DISPLAY=:3 WINEDEBUG=-all wine "C:/Program Files/DreamWorks Interactive/Trespasser/Trespass.exe"

---

### Post by Whiffle on 2008-03-10
You're gettings as far as the goto game dir part, but its failing because you've got spaces in your path name.  you need to put a \ before each space in the directory paths, like so:

cd "$HOME/.wine/drive_c/Program\ Files/DreamWorks\ Interactive/Trespasser/"

---

### Post by linuxjerk on 2008-03-10
ok here is the latest rendition. Are you sure about the back slashes? Were in wine I think?.
I get an error: can't cd to ......... on the line with the back slashes. Then the system crashes and I have to reboot.


#!/bin/sh
#uncomment if launching from console session
#sudo /etc/init.d/gdm stop
#KDE use this instead
#sudo /etc/init.d/kdm stop

# Launches a new X session on display 3. If you don't have an Nvidia card
# take out the "& nvidia-settings --load-config-only" part
sudo X :3 -ac

# Goto game dir (modify as needed)
cd "$HOME/.wine/drive_c/Program\ Files/DreamWorks\ Interactive/Trespasser/"

# Forces the system to have a break for 2 seconds, X doesn't launch instantly 
sleep 2

# Launches game (modify as needed)
DISPLAY=:3 WINEDEBUG=-all wine "C:/Program Files/DreamWorks Interactive/Trespasser/Trespass.exe"

---

### Post by soldats on 2008-03-10
i believe sometimes it needs \\ instead of just \

---

### Post by linuxjerk on 2008-03-11
ok I guess I'm confused here. Aren't these paths in wine? I understand that linux can't deal with spaces in the filename but aren't we in wine at this point???

Do I also need the \ or \\ on the path that executes the game lower down in the script?
thanks

---

### Post by linuxjerk on 2008-03-11
ok tried the double blackslash thing. Just pops up the grey screen with the X in the middle and sit's there.

ARE you sure I don't need the backslashed on the second line with paths?

We are in wine at this point aren't we? Why do I need the back slashes at all??

Or am I wrong???

How do I stop the xserver? I don't want to reboot all the time???

---

### Post by linuxjerk on 2008-03-12
so that's it? This will never work?

---

### Post by Whiffle on 2008-03-12
Oh it can work, it just takes some fiddling.  I messed with it a bit yesterday but didn't get real far, I kept running into the same problem you have.  

There may be some other options too (creating a new xsession so you can run your game from the login screen) but I'll have to boot into ubuntu to check them out.

---

### Post by linuxjerk on 2008-03-12
Hello thanks for trying. When I try to run it now the terminal console is just full of blanks. Pretty hard to fix something when there's no error messages.

---

### Post by Whiffle on 2008-03-12
I managed to get error messages by hitting Ctrl+alt+backspace in the blank xsession, and then after a bit I'd get some errors out of the terminal.

---

### Post by linuxjerk on 2008-03-12
Well I won't be doing anything with that for a while. 

I killed my gnome somehow. Can't even bring up a terminal from there anymore.

Any ideas on how I can reinstall the gnome desktop from the recovery terminal?

---

