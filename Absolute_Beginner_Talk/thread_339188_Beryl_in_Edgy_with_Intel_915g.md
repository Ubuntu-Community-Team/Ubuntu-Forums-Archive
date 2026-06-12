---
title: "Beryl in Edgy with Intel 915g"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by remon_sherin on 2007-01-15
Hello everyone
   I need help in installing Beryl on Edgy, I tried to follow the instructions on the link
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX")

I'm an absolute beginner on ubuntu and linux in general. So, I found the instructions hard to follow](*,) . for example I don't know if I had to download beryl or it's already existing on ubuntu. And proposed lines of code, I don't know if they are terminal commands or lines to be written in a file. 
   PLZ. I would be very happy if anybody could simplify instructions to me.
   Thanks in advance.

---

### Post by kilou on 2007-01-15
This assumes your in GNOME. The bold text is what you need to type or add. I mentionned when you need to use the terminal.

1. In a terminal, type:
**sudo gedit /etc/apt/sources.list **
(enter your password if requested)

2. Go at the end of the document and copy the following:
**deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main**

3. Save the document and exit Gedit

4. In the terminal, type
**wget [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg) -O- | sudo apt-key add -**

5. In the terminal, type:
**sudo aptitude update**

6. In the terminal, type:
**sudo gedit /etc/X11/xorg.conf**

7. In the opened document, under the section "module" make sure the following lines are there (add these if they are missing):
[B]Load "dri"
Load "dbe"
Load "glx"[/B]

8. Under section "Device" add the following line:
**Option  "XAANoOffscreenPixmaps"**

9. Copy the following at the very end of the file:
[B]Section "DRI"
        Mode 0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection[/B]

10. Save the document and exit Gedit

11. Press Ctrl+Alt+Backspace, wait and log in again

12. In the terminal, type:
**sudo aptitude install beryl**

13. Go in System->Preferences->Sessions and choose Startup programs tab

14. Click add and type **beryl-manager**

15. Click add and type **beryl --replace**

16. Click add and type **emerald --replace**

17. Exit and reboot the computer. Beryl should start. You can customize it by right clicking on the red diamond icon in the taskbar.

Hope this helps.

---

### Post by remon_sherin on 2007-01-15
Woooooooooooow Beryl is awesome
Thanks kilou very much, your reply was extremly helpful.:-D

---

