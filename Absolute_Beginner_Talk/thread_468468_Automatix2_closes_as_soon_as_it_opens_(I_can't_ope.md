---
title: "Automatix2 closes as soon as it opens (I can't open the app)"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by swarup on 2007-06-08
I want to run Automatix2, because I've tried installing the various AUD-DVD codecs myself and things are not working right in my sound and video. So I want to try having Automatix2 do it for me and see what happens. But after installing the application, I found that each time I opened it, just as the final main window was about to open in full, it would disappear and the application would not finish opening. So I tried reinstalling it, but the same thing is happening. My computer is kind of old (celeron 433, 288 RAM), but I don't think that should stop the Automatix application from even opening. Everything else I downloaded for Ubuntu runs fine. So what's wrong? Why won't Automatix2 even open????

---

### Post by swarup on 2007-06-08
> **swarup said:**
> I want to run Automatix2...So what's wrong? Why won't Automatix2 even open????

I tried opening it (Automatix2) in Terminal. For those literate in this Terminal stuff, I think it may give an indication as to why the application is not opening. See below:

swarup@swarup-laptop:~$ automatix2
Loading simple Config module ...
Creating backend ...
Loading socket FrontEnd module ...
Starting SCIM as daemon ...
GTK Panel of SCIM 1.4.4

Starting
/usr/lib/automatix2/resin_ui.py:60: GtkWarning: gtk_menu_attach_to_widget(): menu already attached to GtkMenuItem
  self.show_apps.set_menu(self.view_menu);
/usr/lib/automatix2/tray.py:19: DeprecationWarning: the module egg.trayicon is deprecated; equivalent functionality can now be found in pygtk 2.10
TRAY ICON CREATED
  try: import egg.trayicon as trayicon
Traceback (most recent call last):
  File "/usr/bin/automatix.py", line 63, in <module>
    main = main_ui()
  File "/usr/lib/automatix2/main_interface.py", line 19, in __init__
    self.build_interface()
  File "/usr/lib/automatix2/main_interface.py", line 51, in build_interface
    self.generate_menus()
  File "/usr/lib/automatix2/main_interface.py", line 119, in generate_menus
    self.generate_catalog_model()
  File "/usr/lib/automatix2/main_interface.py", line 362, in generate_catalog_model
    icon= gtk.gdk.pixbuf_new_from_file(list.icon)
gobject.GError: Failed to open file '/usr/share/icons/Tango/24x24/apps/k3b.png': No such file or directory
swarup@swarup-laptop:~$

---

### Post by m0rph on 2007-06-08
Do you have the burning program K3b installed and if so is it working ok ?

---

### Post by swarup on 2007-06-08
> **m0rph said:**
> Do you have the burning program K3b installed and if so is it working ok ?

No, it is not installed. Why?

---

### Post by m0rph on 2007-06-08
k3b.png must be to do with K3b therefore i believe something is missing from a k3b install.

Have you tries installing k3b to see if this fixes this error ?

Also what flavor of Ubuntu are you running ?

---

### Post by swarup on 2007-06-08
> **m0rph said:**
> k3b.png must be to do with K3b therefore i believe something is missing from a k3b install.

Have you tries installing k3b to see if this fixes this error ?

Also what flavor of Ubuntu are you running ?

I'm running Ubuntu 7.04

Where would I find this k3b? Is it listed in the normal Add/Remove application of 7.04?

---

### Post by taurus on 2007-06-08
Not sure why you need automatix2 since everything you need for Feisty is here.

[http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by swarup on 2007-06-08
> **taurus said:**
> Not sure why you need automatix2 since everything you need for Feisty is here.

[http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Because I've already installed everything from the RestrictedFormats. I don't know what the other link is (I'll check and see) but I've installed all the AUD and DVD codecs I could find anywhere....all the lib's, the codec32, etc etc. And right now I don't even have any audio on my system. So I thought, let me try with Automatix2 and see if it helps.

---

### Post by taurus on 2007-06-08
The first question is does your soundcard work in Feisty at all?

---

### Post by m0rph on 2007-06-08
> **swarup said:**
> I'm running Ubuntu 7.04

Where would I find this k3b? Is it listed in the normal Add/Remove application of 7.04?

Yes k3b is in Add/Remove but further reading of your terminal output suggest to me that the original setup of Automatix2 failed due to a package not installed.

Did you install it buy downloading directly from the Automatix website
[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

If not maybe worth to uninstall and try again........ [-o<

---

### Post by arnieboy on 2007-06-08
I am not sure why the OP is double posting here.. but he also posted in the automatix forums and it appears that key files are missing from some of the packages on his fresh Ubuntu Feisty install. I asked him to reinstall these (both from Ubuntu main) and Automatix found both missing files and started up.. I have personally never seen this issue before in more than 2 years of experience with Ubuntu but missing files in key packages (without deliberate deletion) is a very serious issue.
For reference, the thread can be found here:
[http://www.getautomatix.com/forum/index.php?showtopic=1298&hl=](http://www.getautomatix.com/forum/index.php?showtopic=1298&hl=)

---

### Post by m0rph on 2007-06-09
Double Help, Very Strange......... :lol:

---

