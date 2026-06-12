---
title: "Help with Wine Please?????"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by ianb72 on 2007-05-01
I am using WINE in Ubuntu 7.04 (fiesty) I have installed wine 3 ways,
throught the Terminal and through Synaptics, and removed it by "sudo
apt-get remove --purge wine" and also "sudo apt-get autoremove wine"
and then through synaptics.

All completely remove wine but under the "Applications" drop down menu
wine is listed with the software that was installed, even when I had
uninstalled it using the "uninstaller" command.
I have tried re-installing wine and the software, but one bit of
software I try to re-install just wont re-install, thats echolink.

How do I get rid of these software from the wine list?

I have been told on the Wine forum this 

The menu entries are located (for Gnome at least) in:
[HTML] ~/.config/menus/applications-merged[/HTML]

You may have to restart Gnome to update the menu
But being new and a bit stupid I am not sure what the guy means can anyone help

Regards
Ian

---

### Post by xboxbman on 2007-05-01
it means you should restart your PC and the changes should be made.  If not, you can edit the menus with System>Preferences>Main Menu.  You can manually edit the menus there.

---

### Post by ianb72 on 2007-05-01
Thanks, that worked great in Fiesty.

How can I do that on my 6.06 Dapper pc??

Ian

---

### Post by outphase on 2007-05-18
Is there anyway to restore the Start Menu in Applications? Mine disappeared and new apps don't show up.

---

### Post by tompickles on 2007-05-18
Ctrl+Alt+BackSpace will restart Gnome. Fast than a complete reboot!

---

### Post by zvacet on 2007-05-18
home folder>view>hidden files and see if .wine folder is still there.If it is delete it.

---

### Post by outphase on 2007-05-29
I've deleted the .wine folder in home and reinstalled wine. My applications menu for wine just doesn't come back. Any thoughts on how to completely restore the fake start menu?

---

### Post by SoulinEther on 2007-05-29
Start installing new applications? I myself had a difficult time with that Wine menu... it doesn't really work 100% in my experience.

---

