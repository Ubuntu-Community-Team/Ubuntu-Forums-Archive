---
title: "Stuck computer"
date: 2013-11-19
forum: Art &amp; Design
---

### Post by luxlumini on 2013-11-19
Hi everyone,
I hope you could help...
My wife was trying to install brushes on GIMP so she had to access the System Files. She was  trying to unlock ROOT .
The first command she (read in Ask Ubuntu that  had to be entered) in  was :
-"press ALT+F2"
- type in the command "gksu nautilus" and press ENTER
Howevere the ROOT kept on staying locked.
So the next one she tried was "sudo passwd"- this is where the Hard disc started getting filled up by its 45g space. Afterwards whatever she was trying to do it just kept on doing the same thing, saying that there is a an Error in copying a file that I can't remember the name of.
So basicly now when we switch it on -this is what comes on the screen:
1:! Mark
THE SYSTEM IS RUNNING IN LOW-GRAPHICS MODE

Your screen, graphics card, and input device settings could not be detected correctly. You will need to configure these yourself.
 ^click OK

2:Next screen: 
WHAT WOULD YOU LIKE TO DO?
-Run in low-graphic mode fore just one session
-Reconfigure graphics
-Troubleshoot the error
-Exit to console login

         -Cancel    ^ OK (options at the bottom right corner)

AND WHATEVER WE CHOOSE IT TAKES US TO AN OLD SCHOOL DARK PAGE WITH SIGNS LIKE:
*Stopping system V runlevel compatibility
.........

So from here unless we switch if off from its main button nothing else happens or at least we dont know what to do.
Please let me know what we need to do in order to bring it back to life!

---

### Post by papibe on 2013-11-19
Hi luxlumini. Welcome to the forum ):P

Try pressing Ctrl+Alt+F1 to get into text mode. Then login as the normal user (the one that can run sudo), and run this commands to free some space:
```
sudo apt-get clean

sudo apt-get autoclean

sudo apt-get autoremove
```
Then reboot by runing:
```
sudo reboot
```
Hope that helps. Let us know how it went.
Regards.

BTW: you don't need to unlock root to run a graphic application as super user, instead of gksu, use the command gksudo, which is just like sudo for GUI apps.

---

### Post by luxlumini on 2013-11-19
Hi and thanks for the fast reply!

Just tried it:
Control+Alt+F1 did work and we logged in as user.
Unfortunately  the three sudo apt... options didn't bring much luck.
It keep saying /usr/lib/sudo/sudoers.so must only be writable by owner
sudo:fatal error, unable to load plug-ins


Please let us know if anything else comes to mind!

And thanks for welcoming too!!

---

### Post by papibe on 2013-11-19
It looks like your user lost the ability to 'sudo'.

Try this:

Boot into recovery mode. You'll boot into text mode and presented with a menu. Select 'root prompt', and you'll be on a text mode terminal session with a root prompt (#).

There execute the commands without sudo (you are already root):
```
apt-get clean

apt-get autoclean

apt-get autoremove

reboot
```
Let us know how it goes.
Regards.

---

### Post by luxlumini on 2013-11-19
Hi again,

it is not really working out,
we can only switch on and off from the main button,as soon as we switch on it says "press enter to boot the selected OS, "e" to edit the commands before booting or "c"for command line.
But when we press Enter again it says the "System is running in low-graphics mode"
And again that closed circle I described earlier...
Sorry if I sound a bit.silly-just no experience with such issues before.

---

### Post by papibe on 2013-11-19
Hold the shift key while the computer is powering on, so you get into the grub menu instead of booting the OS.

[Here]("http://www.youtube.com/watch?v=iQfTW_HbhMc")'s a related video tutorial that describes how to get there.

Regards.

---

### Post by luxlumini on 2013-11-19
In fact is there no more simple way, like re-installing the program(i am not quite sure how that can be done though) that would keep all the files that we have on it already?

---

### Post by papibe on 2013-11-19
So far, I've been trying to clean/remove some files, in case that is the reason of not able to boot in full resolution.

At this moment, I don't know the extend of the problem beyond:
[LIST]
[*]Full disk.
[*]Lost sudo.
[*]Set password to root.
[/LIST]
Also I would guess that when you run 'gksu', it may have change ownership to some files on your home directory, but you need first to have sudo working to fix that.

In order to release some space on your disk you need either:
[LIST]
[*]Use sudo, or
[*]Boot into recovery mode, and run as root.
[/LIST]

An alternative would be to fix sudo first. If you want to attempt this, you would also need to boot into recovery mode. Here's how to do it: [Fix Broken sudo]("http://www.psychocats.net/ubuntu/fixsudo").

I hope I could give you more pointers, but this is the process that I would follow to repair my own computer.
Regards.

---

### Post by luxlumini on 2013-11-19
Hi,
So we managed to get to the root prompt and did all the commands(before that goes to recovery mode) but nothing happens -again it restarts itself and this time ony it gives option to keep on back -up or default configuration; but whatever we choose it stays frozen...

---

### Post by luxlumini on 2013-11-19
Just saw you reply-will give it a try, thanks!

---

### Post by ofnuts on 2013-11-22
Just noticed this.... there is normally no need to use root privs to add things to Gimp. Add-ons such as brushes, patterns, gradients, etc.. should go in the user's Gimp profile (~/.gimp-2.8/..., note the leading dot that makes it hidden by default).

---

