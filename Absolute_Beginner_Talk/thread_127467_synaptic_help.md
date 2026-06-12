---
title: "synaptic help"
date: 2006-02-09
forum: Absolute Beginner Talk
---

### Post by andy127 on 2006-02-09
hello all, i am getting starting using linux and would like some help. The install went fine with dual boot on my machine, but when i tried updating packages, using synaptic package manager, it prompts me for a root passwd. I have entered the passwd i created using 'sudo passwd root'. Then the package manager does nothing, nothing pops up on screen. The same happens when i try and start the 'users and groups' from the system->admin->users and groups. It says starting service then nothing happens. I have downloaded the automatix and ran it, but after the completion of automatix, i reboot and nothing is different(i am assuming the packages should be installed after a reboot and the applications should be present). I appreciate any help, been looking around the forums for two days and have tried several things with no success. Just stuck and thought i would ask, thanks.

---

### Post by r4ik on 2006-02-09
Try reinstall synaptic by

sudo apt-get update
sudo apt-get install synaptic

In a Terminal.
See what it does.
When promted to run as root use the "sudo su"  command (without the ") type your paswrd and try again.
Good luck!
Could find anything on usr and groups  sorry.

---

### Post by bscbrit on 2006-02-09
There is no default 'root' account in Ubuntu, well not one that you should use frequently.  Ubuntu uses 'sudo' instead which, now that I am used to it, is in my opinion a much better solution:

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by Sokraates on 2006-02-09
Actually, the solution is very simple:

When asked for the "root"-password, simply type your user-password (the one you use to login to your account). That's the power of sudo. ;)

---

### Post by andy127 on 2006-02-09
thanks for your help, i did as you said and this is what happened.
_______________________________________
root@Gus:/home/andy# sudo apt-get install synaptic
Reading package lists... Done
Building dependency tree... Done
synaptic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
________________________________________
so then i tried clicking on synaptic package manager again, it prompted me for my passwd, which i entered, and then nothing, no response. i'll keep playing with it, thanks for all your help so far.

---

### Post by bscbrit on 2006-02-09
Try typing the following at the command line:

sudo synaptic

That way you might get to see the error message. :D

---

### Post by andy127 on 2006-02-09
That did it! from the terminal window, this came up:

---------------------------------------------------------------
(synaptic:7209): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(synaptic:7209): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed
--------------------------------------------------------------
but then the package manager opened in the xwindows. I have no idea what all that means, but thanks to everyone for helping me out.

---

### Post by bscbrit on 2006-02-09
Does it now open from the menu as well?

---

### Post by andy127 on 2006-02-09
no, it doesnt open from the menu now....i dont know whats going on....i had left the synaptic window open all day while i was gone as well as my terminal window. This is what was being displayed while i was gone(in the terminal window)

(synaptic:7209): Gtk-CRITICAL **: gtk_tree_view_unref_tree_helper: assertion `node != NULL' failed

any idea what this means?

---

### Post by aysiu on 2006-02-09
Create a launcher with the command: ```
gksudo synaptic
```

*sudo* is for terminal commands.
*gksudo* is for graphical Gnome apps and *kdesu* is for graphical KDE apps.

---

### Post by andy127 on 2006-02-09
i'll give it a try and see what happens, do you think that whatever is causing this would also be causing automatix to run, but when it says it is done, fininshed installing, all the programs i selected to install are all running in the background, constantly trying to install, then when i click <ok> to complete installation, they all disappear and nothing gets installed.

---

### Post by andy127 on 2006-02-09
ok, i just tried typing  gksudo synaptic and the same thing occurred, it opened the package manager, but then i tried to open it from the menu, it didnt work....i am gonna get it sooner or later!

---

### Post by Sokraates on 2006-02-10
I'm no GNOME-user so maybe some details are wrong, but here it goes:

As far as I understand, you always started synaptic through a terminal, either through "sudo" or "gksudo".

Now if you want to have a menu-item that starts synaptic as root, you have to edit the command executed when clicking on this item.

I don't know if you can edit shortcuts by rightclicking on the menu-item, but in the end the command should look like this:
```
gksudo synaptic
``` Now everytime you click on the button, a window will appear, asking for the root-password. Enter your user password. Then synaptic will start with all the necessary rights. :D

By the way: the command should be "gksudo synaptic" per default, so I don't know what went wrong on your system.

---

