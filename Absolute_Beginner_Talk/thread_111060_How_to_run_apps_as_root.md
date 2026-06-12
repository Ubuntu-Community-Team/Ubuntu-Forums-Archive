---
title: "How to run apps as root?"
date: 2006-01-01
forum: Absolute Beginner Talk
---

### Post by seekyrr on 2006-01-01
I can launch some apps from the terminal with sudo, but other apps that are graphical don't give me that option.

Is there a way to give the account root access for the entire session?

Thanks

Seek

---

### Post by Mustard on 2006-01-01
What applications of a graphical nature do you need to run?

Ideally you would use sudo or even use sudo to temporarily log in as root using the sudo -i command.  Some applications can be launched using the gksudo command so that a graphical prompt is presented for entering the sudo password.

If you really want to log in as root permanently for the session, which is not advisable, you could go to your System>>Administration>>Login Screen Setup menu choice and then go to the security tab and tick the box allowing a root login.  Then you would need to set up a root password using the command sudo passwd root.  To then disable your root password, for security purposes after you have finished doing whatever you are doing,  you would need to do a sudo passwd -l root command.

For further information visit this wiki page...
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by pbb on 2006-01-01
You need to start the graphical apps in the same way as the terminal apps, like this:

sudo gedit

This starts the graphical editor, in sudo mode...

---

### Post by earobinson on 2006-01-01
you should be able to start anything with sudo, if not tell us what app it is and we will try and help. the link Mustard provided will let u enable the root account

---

### Post by aysiu on 2006-01-01
If it's a graphical application, start it with gksudo.
For example, ```
gksudo synaptic
```

---

### Post by Lord Illidan on 2006-01-01
[quote=aysiu]If it's a graphical application, start it with gksudo.
For example, ```
gksudo synaptic
```[/quote]

Don't want to hijack this thread, but why use gksudo?

```
sudo synaptic

(synaptic:26583): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(synaptic:26583): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

``` 
Always worked for me, both in Gnome and in KDE. In KDE it throws up these errors, but it loads and runs perfectly then.

---

### Post by qferret on 2006-01-01
If you insist on running apps as root, the following command will come in handy someday.

chown <user> /home/<user>/.Xauthority

When running certain apps as root, the app "accidentally" changes the ownership of the .xauthority file in your home directory to root. After this happens, you will receive .Xauthority errors on just about everything else you try to run until you change the ownership back.

---

### Post by seekyrr on 2006-01-01
Edit.

Appears I made the folder as root and didnt give my non root account access..DOH.

I would have needed the other info soon or later..appreciate the help.

Seek


I was trying to run BitTorrent.

If I just launch it off the app menu, it doesn't seem to have the permissions to make a folder to store the download.

I tried gksudo but it failed to launch app.

Seek

---

### Post by Omnios on 2006-01-01
I had a similar problem about a year ago with never Winter Nights posted back in 5.04 and the solution was to I had was to make a shell script to launch the game this is nice because you can point a menu entry to the shell script to launch it as root.

---

### Post by earobinson on 2006-01-01
[QUOTE=Lord Illidan]Don't want to hijack this thread, but why use gksudo?

```
sudo synaptic

(synaptic:26583): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(synaptic:26583): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

``` 
Always worked for me, both in Gnome and in KDE. In KDE it throws up these errors, but it loads and runs perfectly then.[/QUOTE]
gksudo is a way to keep it graphical there is no real reason to use it in the terminal however apps like synaptic use gksudo to launch if you look at the launch command of synaptic in the system menu its gksudo synaptic as to avoid the terminal and not scair any novice users.

---

### Post by poofyhairguy on 2006-01-02
[QUOTE=Lord Illidan]Don't want to hijack this thread, but why use gksudo?
[/QUOTE]

Its important to use gksudo for all graphical apps that are not gedit because otherwise you might screw up your .ICEauthority file. Then you can't log into Gnome.

I have a lot before I learned- use gksudo.

---

