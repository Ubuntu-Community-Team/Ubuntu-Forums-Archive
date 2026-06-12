---
title: "Task bars have disappeared on XFCE"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by Jored on 2007-08-02
I'm running Xubuntu with Xfce. On booting, both the top and bottom toolbars had disappeared. I right clicked on the desktop and got a popup window where I could select any application or system tool. I messed around with the various windows and desktop settings to get the toolbars back and when I rebooted all I got was a blue screen, with no toolbars and no desktop. Right or left clicking on any part of the screen has no effect.

What should I do to get Xfce to start in default mode or get back to the "normal" desktop?

---

### Post by ugm6hr on 2007-08-02
Try Alt+F2: **xfce-setting-show backdrop**

Then tick the "Allow XFCE to manage the desktop" button.

If the panels aren't there:

Alt+F2: **xfce4-panel &**

---

### Post by Jored on 2007-08-02
> **ugm6hr said:**
> Try Alt+F2: **xfce-setting-show backdrop**

[B]I got the following message back:

(xfce-setting-show:5340) : Gtk-WARNING ** : cannot open display[/B]

Then tick the "Allow XFCE to manage the desktop" button.

If the panels aren't there:

Alt+F2: **xfce4-panel &**

So I tried this and got back:

(xfce-panel:5276) : Gtk-WARNING ** : cannot open display xfce-panel

It looks like XFCE has somehow been corrupted. Should I uninstall and reinstall XFCE? How?

Would booting from the LiveCD fix the problem?

---

### Post by Jored on 2007-08-02
I'm sorry, I garbled my reply.

Repeat:

I tried Alt+F2: xfce-setting-show backdrop and got the following message back:

**(xfce-setting-show:5340) : Gtk-WARNING ** : cannot open display**

I then tried Alt+F2: xfce4-panel & and got back:

**(xfce-panel:5276) : Gtk-WARNING ** : cannot open display xfce-panel**

It looks like XFCE has somehow been corrupted. Should I uninstall and reinstall XFCE? How?

Would booting from the LiveCD fix the problem?

---

### Post by ugm6hr on 2007-08-02
Alt+F2: **gksu usr/bin/synaptic**

This will load Synaptic.  It should tell you if any of the packages are "broken" along the bottom of the window.

I have never encountered this, but it would be safe to try repairing any broken packages.  If that didn't help (or there were none), maybe try reinstalling *xubuntu-default-settings*, *xfdesktop4*, *xfce4-panel* packages (and perhaps others related to xfce.

---

### Post by Jored on 2007-08-02
It's strange. I ran Synaptic and it showed no broken packages. I then booted in Recovery Mode as root and Xfce ran OK, with all panels and task bars visible. I then rebooted and logged in normally and got the plain blue screen and just the cursor, as before.

I'm now logging in safe graphic mode from the LiveCD to see if there is a repair function in there. 

If booting from the recovery Grub entry allows me to work with a fully functional Xfce desktop as root, how can it be that when I login as a normal user, I get no desktop?

I'm really lost on this one and wouldn't like to completely reinstall Xubuntu.

I still have to try the steps you suggest at the bottom of your post.

---

### Post by Jored on 2007-08-02
No luck.

When I booted from the live CD I only got a desktop with the disc volumes, home folder, trash icon, install icon, etc but no toolbars either at the top or the bottom.

Right clicking only gave options to create folder, url, etc, but no Applications, System or anything like it.

I didn't want to reinstall since I haven't given up yet. 

When I login as root from recovery mode, it's all there and the Xfce desktop works fine. I tried to get around the problem by creating a brand new user, but it returned a message saying that I didn't have the attributes to do so (as root? Strange).

So back where I started.

Anyone else got any ideas?

---

### Post by Jored on 2007-08-03
Nobody seems interested in this problem.

However, for others who may encounter it, this is how a newbie like me worked around it to get a working laptop without having to reinstall Xubuntu and waste even more time.

I created a new user by getting into the terminal from the broken desktop (Ctrl+Alt+F2). 

sudo adduser <new_username>

It will ask you for your old password and then for a new one for the new user.

I rebooted with the the new user and confirmed it worked. No problem, except that the new user had no admin priviledges.

I then rebooted in recovery mode and when I got the root prompt (#), I typed:

adduser <user_name> admin

Then:

reboot

And I got the new user with admin priviledges. From here on it was a matter of repersonalising the new account,  (Foxmarks made recovering bookmarks a no brainer) and, strangely enough, all Firefox plugins were still installed and I only had to reinstall the addons like flash, Foxmarks, Googlebar, etc).

I'm sure there may be better ways, but this has worked for me.

---

### Post by NemoFox on 2008-03-01
I had the same problem and fixed it deleting the $HOME/.cache directory, after this everything was fine....

---

### Post by Oldsoldier2003 on 2008-03-01
> **NemoFox said:**
> I had the same problem and fixed it deleting the $HOME/.cache directory, after this everything was fine....

or just create a launcher and run xfce-panel then save your session.

---

### Post by munkymac on 2008-05-13
I had this happen last night, and I did mostly the same thing as NemoFox to fix it. Creating a launcher to run the panel seems counterintuitive, since the panel is supposed to automatically launch (assuming you have the panel checked in the panels menu in the settings dialogue). 

If the panel disappears, the best bet is to do the following:

1. Open Thunar
2. In the navbar, enter this text: ```
/home/<username>/.cache/
``` 
3. Delete the "sessions" folder
4. Log out

Chances are, you'll be back to normal. If not, then create the launcher for xcfe-panel (as a stopgap solution) and do some more searching

---

