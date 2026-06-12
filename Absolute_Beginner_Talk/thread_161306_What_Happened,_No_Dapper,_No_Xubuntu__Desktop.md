---
title: "What Happened, No Dapper, No Xubuntu_ Desktop"
date: 2006-04-16
forum: Absolute Beginner Talk
---

### Post by Topaz on 2006-04-16
I did the changes, change breeezy to dapper, It went through all the downloads, did install, rebooted and there is no change, still kubuntu 5.10. I believe that computers no matter what os do not like me and refuse to cooperate.

---

### Post by Jagot on 2006-04-16
Can you post your /etc/apt/sources.list please.

Also what commands did you issue?

Should be for upgrading to Dapper:

sudo apt-get update
sudo apt-get dist-upgrade

And for installing Xubuntu:

sudo apt-get install xubuntu-desktop

---

### Post by Topaz on 2006-04-16
[QUOTE=Jagot]Can you post your /etc/apt/sources.list please.

Also what commands did you issue?

Should be:

sudo apt-get update
sudo apt-get dist-upgrade[/QUOTE]

Error snapshot:

---

### Post by Topaz on 2006-04-16
[QUOTE=Topaz]Error snapshot:[/QUOTE]

~$ sudo apt-get install xubuntu-desktop
Password:
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  xubuntu-desktop: Depends: orage but it is not going to be installed
                   Depends: thunar but it is not going to be installed
                   Depends: xfce4-mailwatch-plugin but it is not going to be installed
                   Depends: xfce4-mixer-alsa but it is not going to be installedE: Broken packages

---

### Post by Jagot on 2006-04-16
Ok, with regards to Xubuntu, have you activated the universe repository, because I believe that is where the xubuntu-desktop package lives?

---

### Post by Topaz on 2006-04-16
[COLOR="SeaGreen"]** Newest Error           **
[/COLOR]



:~$ /etc/apt/sources.list
bash: /etc/apt/sources.list: Permission denied

:~$ sudo /etc/apt/sources.list
Password:
sudo: /etc/apt/sources.list: command not found
:~$ sudo edit /etc/apt/sources.list
Warning: unknown mime-type for "/etc/apt/sources.list" -- using "application/*"
Error: no "edit" mailcap rules found for type "application/*"

---

### Post by red_Marvin on 2006-04-16
/etc/apt/sources.list is a file not a command, hence the error.
If you want to edit it then:
A console editor
sudo nano /etc/apt/sources.list
A gui editor:
sudo gedit /etc/apt/sources.list

---

### Post by Jagot on 2006-04-16
Try:

sudo kate /etc/apt/sources.list

---

### Post by Topaz on 2006-04-16
[QUOTE=Jagot]Try:

sudo kate /etc/apt/sources.list[/QUOTE]
Here it is.

---

