---
title: "forcing script to run in terminal"
date: 2006-03-31
forum: Absolute Beginner Talk
---

### Post by jlhughes on 2006-03-31
I have a simple script for starting my vpn connection:

sudo /etc/init.d/vpnclient_init start
sudo vpnclient connect SBVPN

This is saved as an executable file on my desktop. 

When I double-click on it, it offers the choice to run as terminal, display, cancel or run.

Is there a line or option I can add that will always make double-clicking on the script run in terminal?

Thanks

---

### Post by aysiu on 2006-03-31
If you make it a launcher on the panel instead of an icon on your desktop, I believe you can check a box that says "run in terminal."

---

### Post by jlhughes on 2006-03-31
[QUOTE=aysiu]If you make it a launcher on the panel instead of an icon on your desktop, I believe you can check a box that says "run in terminal."[/QUOTE]

Please explain how to "make it a launcher on the panel..."  

I don't understand "panel" or "laucher"

---

### Post by GiantsFanMan11 on 2006-03-31
I have a similar launch icon for vpnc which I have told to run in the terminal.  My problem is that it executes the command and then closes the terminal which disconnects me from vpnc.  Is there a way to force the terminal to stay open?
-Steve

---

### Post by GiantsFanMan11 on 2006-03-31
You can right-click on the launch bar (top of desktop) and choose to add a new launch icon with a specified action.
-Steve

---

### Post by jlhughes on 2006-03-31
Thanks. This is what I was looking for.

As for keeping the terminal session open, I used the "custum application launcher" and selected by script. I then checked the run in terminal option. The terminal window stays open (maintaining the VPN connection).

---

### Post by GiantsFanMan11 on 2006-03-31
[QUOTE=jlhughes]Thanks. This is what I was looking for.

As for keeping the terminal session open, I used the "custum application launcher" and selected by script. I then checked the run in terminal option. The terminal window stays open (maintaining the VPN connection).[/QUOTE]

What do you mean by select by script?  Do you mean "Type" because there was no script option for me.
-Steve

---

### Post by jlhughes on 2006-03-31
[QUOTE=GiantsFanMan11]What do you mean by select by script? [/QUOTE]

Sorry, that's a typo. I used the Custom Application Launcher option. Browsed to find my script. Selected it. Checked the "run in terminal" option. Saved.  Works like a charm. 

I'm VERY new to Ubuntu and the desktop it installs. I was unaware of the customizable bar at the top. That's a very nice feature.

---

