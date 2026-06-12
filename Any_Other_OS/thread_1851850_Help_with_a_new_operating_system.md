---
title: "Help with a new operating system"
date: 2011-09-29
forum: Any Other OS
---

### Post by avi k on 2011-09-29
I have Linux Fedora + Gnome and I started working with the system today, when I open Firefox or any other window, I miss the two marks at the top of the window through which I can drop the window down bar, or enlarge the window, can someone tell me how I add them?.
 Attaching a screenshot, you can see the Web page up on the right, there is a sign that can be used to close the window but I miss the other two marks.

[ATTACH]203133[/ATTACH]

---

### Post by nothingspecial on 2011-09-29
Moved to other OS/Distro talk

---

### Post by Linux_junkie on 2011-09-29
I am assuming you mean displaying the minimize and maximize buttons in Gnome-shell.  By default Gnome-shell does not display these buttons but I believe you can display them through the gconf-editor application.  You can run this app by pressing ALT and F2 keys together and in the dialog box type gconf-editor

You will have to search the editor for the option I'm affraid because I cannot remember where it will be.  I'll log in to Gnome 3 later to remind myself where in the editor you need to look.

---

### Post by avi k on 2011-09-29
Thanks I managed to complete the missing signs.
 Now I have another problem, I try to install tcsh, it's for software that I need to install, but look what the console says


> [admin@localhost ~]$ sudo apt-get install tcsh
[sudo] password for admin: 
admin is not in the sudoers file.  This incident will be reported.
[admin@localhost ~]$ 

---

### Post by nothingspecial on 2011-09-29
Hi,

That's because Fedora doesn't come with sudo configured.

You either have to install packages as root or configure sudo.

You realise that this is Ubuntu Forums?

There's nothing stopping you asking your questions here, but you'd probably be better of asking in Fedora forums.

[http://fedoraforum.org/](http://fedoraforum.org/)

---

### Post by avi k on 2011-09-29
Thanks for your help, I did not know that there is a special forum to Fedora

---

### Post by jRdbRR on 2011-09-29
do this instead of sudo

su - 

it will then ask you for the root passwd

enter the passwd and then you're set.



edit: or add yourself to the /etc/sudoers file, tho i cannot remember the exact syntax



i've never had much luck on other forums, i find this one is the best

---

### Post by el_koraco on 2011-09-30
> **avi k said:**
> Thanks I managed to complete the missing signs.
 Now I have another problem, I try to install tcsh, it's for software that I need to install, but look what the console says

Oh, noez, sudo reported you to [Santa]("http://xkcd.com/838/")! 
FYI, Fedora doesn't use apt-get if you didn't install and configure it manually. The commands: 

```
su -
enter root password
yum install tsch
```

There's guarantee that tsch is available on Fedora, I know we don't have it in the Debian repos. Install Gnome Tweak Tool to sort out some of the problems with Gnome 3. Common yum commands: 

```
yum install (apt-get install)
yum uninstall (apt-get remove)
yum erase (apt-get purge)
yum update (apt-get update && apt-get upgrade)
yum search (apt-cache search)
yum list (apt-cache policy)
yum grouplist (lists all groups, they're kinda like metapackages)
yum groupinstall (install a group)
```+ [link]("http://www.fedorafaq.org/#installsoftware")
You can also run man yum for the more esoteric options.

---

### Post by coffeecat on 2011-10-01
> **avi k said:**
> Thanks for your help, I did not know that there is a special forum to Fedora

Hi, in case you haven't found them, here are a couple of links for you.

Fedora Forum:

[http://fedoraforum.org/forum/](http://fedoraforum.org/forum/)

They seem quite friendly and helpful. Also, I found this useful when running Fedora:

[http://www.mjmwired.net/resources/](http://www.mjmwired.net/resources/)

There are instructions for enabling sudo there.

---

