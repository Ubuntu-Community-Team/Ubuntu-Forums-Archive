---
title: "[SOLVED] How To Enable Right Click GUI Virus Scanning With Avast"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by randy78 on 2008-02-02
I like to scan what I download so I don't pass on a potentially infected file to a friend.
Here's how to do that with ease ;)

*Note that this won't scan folders, only single files

Download Avast for Linux:
[http://avast.com/eng/download-avast-for-linux-edition.html]("http://avast.com/eng/download-avast-for-linux-edition.html") (Deb package for Ubuntu)

Register and check email for license key, paste into a text editor for later use
[http://avast.com/eng/home-registration.php]("http://avast.com/eng/home-registration.php")

Double click .deb and install

Open a terminal and type: avastgui

Enter product key at prompt

Install Nautilus-Actions menu configuration editor:
sudo apt-get install nautilus-actions

Open nautilus actions configuration
Menu>System>Preferences>Nautilus Actions Configuration

Click ADD

Label: Scan For Viruses
Tooltip: Avast For Linux
Icon: I searched Google Images for "Avast Icon"
Path: /usr/bin/avastgui
Parameters: --scan-dir=%M (enter exactly as shown)

Restart X (CTRL+ALT+BACKSPACE) or Log Out and Log In

Right click on the file (not folder) of your choosing and click Scan For Viruses, or if you want to see Avast in serious action, Search Google for Virus Test File (Eicar) and scan that one.

I hope this helped some people out and even though we are VERY safe just by using Ubuntu alone, you will now have the option to scan whatever you please ;)

---

### Post by bill_greene on 2008-02-02
Excellent how to.

                                  Thanks Randy.

---

### Post by randy78 on 2008-02-02
Thanx!

I just marked it as Solved so others might be able to use it...

I wonder if I can have it moved into the Tutorials section?

:popcorn:

---

### Post by rhomany on 2008-06-25
Exactly what I came here looking for. Thanks

---

