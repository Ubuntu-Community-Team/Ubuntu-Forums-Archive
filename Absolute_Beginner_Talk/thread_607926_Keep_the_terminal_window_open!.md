---
title: "Keep the terminal window open!"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by TJ-Tigger on 2007-11-09
I have created a drawer on a panel in GNOME and in that drawer I have placed some command line commands to launch vpnc using different scripts to connect to my customers sites.  I would like for the launched terminal window to stay open after it executes the command.  How do I do this?  Here is what I have in the command window.  

sudo /usr/sbin/vpnc /etc/vpnc/customer1.conf

This launches the terminal and asks for my sudo password and then asks for the VPN password after which it connects and I can work on the customers network.  I would like to force the window to stay open after it connects.  Any suggestions on how to make this happen?

Thanks for the help.

---

### Post by duruttye on 2007-11-10
Hey, maybe you can make a new tab for every command, then that can be closed, after it starts.
But you will have to open a new tab every time. 
Cannot think at something else:)

---

### Post by kyphi on 2007-11-10
Have you tried a right click on the title bar and selecting 'On Top' from the dropdown menu.

---

### Post by TJ-Tigger on 2007-11-12
I have not tried that.  maybe I will try to open the command in another tab to see if the terminal will stay open.  I may just try gvpnc instead and launch the gui from the panel.

---

### Post by Dr Small on 2007-11-12
Have you tried "gksudo" ?

---

### Post by spupy on 2007-11-12
I'm not sure if I understand what you mean: If you use gnome-terminal, go to Edit -> Current Profile -> Tab "Title & Command" -> At the bottom it says "When command exits" -> choose  "Hold the terminal open". Is that what you are looking for?

---

### Post by TJ-Tigger on 2007-11-12
> **spupy said:**
> I'm not sure if I understand what you mean: If you use gnome-terminal, go to Edit -> Current Profile -> Tab "Title & Command" -> At the bottom it says "When command exits" -> choose  "Hold the terminal open". Is that what you are looking for?

I have not checked that.  I will give it a shot.

---

### Post by TJ-Tigger on 2007-11-12
If I didn't explain very well, I am trying to add shortcuts to vpnc and profiles to a drawer on my panel in Gnome.  I have it so that it will launch the command I mentioned above as Application in Terminal.  When I do this it works and asks for my sudo password as well as the vpnc password and then the terminal exits after I enter these passwords.  When I do an ifconfig in another terminal it shows as connected so all is good.  I was just hoping to find a way to keep the terminal open when I click on the shortcut from the panel. 

Tigg

---

### Post by mali2297 on 2007-11-12
With xterm, you can use
```

xterm -hold -e your_command

```
This will however just leave the window open, you will not be able to interact with it after your_command has finished.

A better solution:
```

xterm -e "your_command ; bash"

```
With this, you will get to a familiar bash prompt when your_command has finished.

I don't have gnome-terminal, but I'm sure that it has corresponding options. Check
```

man gnome-terminal

```

---

