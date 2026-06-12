---
title: "Running netowork manager in xfce"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by gustavocm on 2007-06-20
Hello, 
i started downloading xfce with synaptic...
when i run nm-applet from the terminal nothing happens,
what can i do? where the nm icon should appear?

thank you

---

### Post by orb9220 on 2007-06-20
> where the nm icon should appear?


It should appear in the system tray or also called notification applet. 
Do you have a notification applet on the panel?

---

### Post by gustavocm on 2007-06-20
that's it!
thank for your help!! :D

---

### Post by gustavocm on 2007-06-22
now network manager is being open 5 times i'm with 5 icons in  the system tray.

why it happens? how can i fix it?

---

### Post by diatribe on 2007-06-22
right-click on them and select close?  every time you open the program it sends an icon to the system tray; it has 5 instances open

---

### Post by gustavocm on 2007-06-22
i didn't open the program 5 times... it happens automatically on startup. i don't know why.

---

### Post by kadath on 2007-06-23
> **gustavocm said:**
> i didn't open the program 5 times... it happens automatically on startup. i don't know why.

I think I may know how to fix this.

You need to add network-manager-gnome to your list of auto-started applications by using the session editor. Add the command "nm-applet --sm-disable" to the list, log out (or reboot), and then log back in.

If there is still more than one icon, you may need to uninstall and re-install network-manager-gnome, and then logout/reboot, and log in again.

---

### Post by gustavocm on 2007-06-23
It didn't works.... i uninstalled and re-installed it, log-out and log-back... now it is openning nm-applet 7 times. (I added "nm-applet --sm-disable" to the "Autostarted applications")

any other suggestion?

---

### Post by kadath on 2007-06-23
> **gustavocm said:**
> It didn't works.... i uninstalled and re-installed it, log-out and log-back... now it is openning nm-applet 7 times. (I added "nm-applet --sm-disable" to the "Autostarted applications")

any other suggestion?

[This post]("http://ubuntuforums.org/showpost.php?p=2689115&postcount=7") includes some steps that worked for the poster. He managed to go from 5 network-manager applets to just 1. Maybe it will work for you too?

---

### Post by __Alex__ on 2007-10-21
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/95064](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/95064) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi, I had exactly the same problem for Gutsy. I fixed it by following these steps :

0. menu->autostarted applications, uncheck network manager, close
1. killall nm-applet
2. rm -rf ~/.cache/sessions
3. log out (don't save session)
4. log in
5. now I don't have any nm-applet. Go to autostarted apps, add network manager
6. logout, save session
7. login -> I have one instance of nm-applet running fine.

---

