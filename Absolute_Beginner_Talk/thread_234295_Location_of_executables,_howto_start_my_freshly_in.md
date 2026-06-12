---
title: "Location of executables, howto start my freshly installed applications"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by IronArjen on 2006-08-11
Being totally new to Ubuntu and Linux I run into several items that I cannot solve. Many of them are actually instances of the same problem: upon installation using the Synaptic I cannot find how or where to start my new application. Certain applicatiosn appear in the applications bar but others do not. Many of them might need additional work in order to get them to work in X but others certainly not. The most important instance here is the Gnome Commander. I installed it, rebooted and: zip, nada, nothing.

Where do I find the executable, how do I include this in a application menu bar?

Just to be sure I run Dapper 64 and use Gnome for my desktop

Related: I know that certain applications will only appear in the so-called Debian menu bar. The problem is that this Debian menu bar should appear as a button on my application bar but it doesnt.

Tx

---

### Post by louis_nichols on 2006-08-11
Well, unfortunatelly, not all packages have the script that adds a shortcut to the menu.

The Debian menu thing seems strange, though. try doing this: Open a terminal and run the command ```
update-menus && killall gnome-panel
```

You'll see the panel dissapear for a second, but that's alright. After this, you should have the debian menu there.

However, starting an app is easily done from the terminal. Just  write the name of the executable (if you're not sure, just write the first letters, then press TAB and it will show you the laternatives). This same command can also be manually entered in the menu with the application Alacarte menu editor.

---

### Post by zxee on 2006-08-11
You can get the debian menu by installing it with automatix.
Also see this thread: [http://www.ubuntuforums.org/showthread.php?t=233936&highlight=debian+menu+install](http://www.ubuntuforums.org/showthread.php?t=233936&highlight=debian+menu+install)
Applications are in /usr but where in usr? Try /usr/local or from the terminal do > whereis gnome commander
Hope that helps.

---

### Post by xpod on 2006-08-11
Im having a similar problem but not with my ubunto.I cant seem to Find the Apps...a couple of games etc...that ive installed with adept in kubunto.

L know that the add/remove way works and any apps i choose there show up in a menu but cant seem to figur these other "package managers"out.

Ive not really used synaptic in ubunto yet as add/remove and Automatix seem to have done me so far.....

Not always as straight-forward when the "user" dont work properly..:-)

---

### Post by davebgimp on 2006-08-11
> **xpod said:**
> Im having a similar problem but not with my ubunto.I cant seem to Find the Apps...a couple of games etc...that ive installed with adept in kubunto.

They should appear in your programs menu once the menu is refreshed. You could log out and back in, or easier, right click the menu icon in Kubuntu, select edit and just save it without changing anything and it will rebuild the list.

---

### Post by IronArjen on 2006-08-11
Thanks for all the clear help guys, I am getting further. Great Forum!

Regarding "Well, unfortunatelly, not all packages have the script that adds a shortcut to the menu." Is there a general way to script or to add this script? Probably this is made difficult by the fact that certain depend on GTK and others on Java?

---

### Post by Kaloma on 2006-08-11
I am not yet an Ubuntu user (I will be soon when I get the laptop I ordered), but I am a long time Debian user.

See if there is an app called Alacarte in the Ubuntu repositories.  It is a menu editor for GNOME. You can add/remove/modify launchers, reorganize, etc.

Matthew

---

### Post by mostwanted on 2006-08-11
> **Kaloma said:**
> I am not yet an Ubuntu user (I will be soon when I get the laptop I ordered), but I am a long time Debian user.

See if there is an app called Alacarte in the Ubuntu repositories.  It is a menu editor for GNOME. You can add/remove/modify launchers, reorganize, etc.

Matthew

It's already installed. You just need to right-click on the menu and select the edit option.

---

