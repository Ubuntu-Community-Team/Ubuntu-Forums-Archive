---
title: "FluxBox Mayhem"
date: 2005-05-16
forum: Apple PPC Users
---

### Post by Xbot on 2005-05-16
How would I go about installing FluxBox? I want to make a Hoary install with so many session types my iMac will explode :)

However, I just keep getting errors, no matter what commadn I use.

Any ideas?

---

### Post by moleculardeconstruction on 2005-05-16
I installed fluxbox without any trouble.

What apt repositories are you using?

```
apt-get install fluxbox
``` 

That did it for me, using the universe repository.

---

### Post by Xbot on 2005-05-17
The error I get with that command is "Couldn't find package fluxbox."

---

### Post by moleculardeconstruction on 2005-05-17
It seems as if you need to enable the other repositories.

Open up the /etc/apt/sources.list file and uncomment the other repositories.

You should then be able to install fluxbox.

---

### Post by Xbot on 2005-05-17
[QUOTE=moleculardeconstruction]It seems as if you need to enable the other repositories.

Open up the /etc/apt/sources.list file and uncomment the other repositories.

You should then be able to install fluxbox.[/QUOTE]
 It says the file is read-only...?

---

### Post by Len on 2005-05-17
Open a "Root terminal" from the Gnome menu and type:

```
gedit /etc/apt/sources.list
```

Or just open a normal terminal and type:

```
sudo gedit /etc/apt/sources.list
```

This will open every file read-write in Gedit, an application with an easy GUI.

If you ever mess up and can't start Xorg (the GUI) use the command ```
sudo nano <filepath>
``` to open a friendly command line editor (vi and emacs aren't that straightforward...).

After you enabled the other repositories you can also use Synaptic to install FluxBox. It is a pain that FluxBox or IceWM aren't in the standard repositories yet... Not very friendly, but I guess this will be fixed in the future.

---

### Post by Xbot on 2005-05-18
Ahh. I did a copy operation instead. Good thing I watched as Ubuntu installed - you learn a lot about the sudo command then :).

---

### Post by Len on 2005-05-18
The 'sudo' command overrides nearly all security. It is crucial to remember it ;).

Here is a list with some standards for your convenience:

ls - lists the contents of a folder (directory) or the current folder
cd - changes the directory (cd /bin)
cp - copy a file (cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak)
rm - removes a file
rm -r - removes a directory with all its contents (rm -r /var/tmp)
sudo - gives you full access to nearly anything (sudo rm xorg.conf.bak)
nano - a straightforward command line text editor, nice for editing configuration files
startx - starts X11
man - shows help pages for a command if available (man sudo) (man nano).

The <tab> key is your best friend. If you type cd /h and press 'tab' it will automatically adds the missing letters (cd /home). This also works for commands; typing su and then pressing 'tab' will list su and sudo (and maybe others). Very handy.

---

### Post by Xbot on 2005-05-18
Yeah. The sudo command reminds me of a sudo chop, I guess that's how I remember it ;).

---

