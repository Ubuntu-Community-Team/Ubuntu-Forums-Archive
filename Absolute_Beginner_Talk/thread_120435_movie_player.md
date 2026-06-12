---
title: "movie player"
date: 2006-01-21
forum: Absolute Beginner Talk
---

### Post by raul99 on 2006-01-21
I recently installed ubuntu 5.10 which has included the Mozilla Firefox browser.
How do I install the Totem movie player?  Thanks

---

### Post by ubuntuuser on 2006-01-21
Ubuntu comes with Totem as default media player installed, so you don't have to install it. If you want to have the Firefox plugin just type ```
sudo apt-get install totem-gstreamer-firefox-plugin
``` or ```
sudo apt-get install totem-xine-firefox-plugin
```, depending on what kind of player engine you use. I think gstreamer is default, so if you didn't change anything, use that.

---

### Post by raul99 on 2006-01-21
I tried both player engines and got two error messages;
E: Couldn't find package totem-gstreamer-firefox-plugin
E: Couldn't find package totem-xine-firefox-plugin
Anything other to try?

---

### Post by ubuntuuser on 2006-01-21
You have to enable additional repositories. In synaptic, there is a menu option for that. I don't use the English ubuntu, so I'm not gonna translate that, but it's easy to find.

---

### Post by raul99 on 2006-01-22
I am trying to obtain the Totem movie player, I have been advised to "enable the additional repositories" in synaptic. I have never used synaptic, I found the website on Google, what part of it do I download and how do I get it into ubuntu?

---

### Post by ubuntuuser on 2006-01-23
Start synaptic, then select sth like Preferences or maybe Setup. There must be a "Repositories" option. Click on that, then click "add" and select what you need.

---

### Post by DonQuixote on 2006-01-23
If you have the standard installation, at the top of the screen is a bar that reads "Applications", "Places", and "System".

Follow this menu link, "System->Administration->Synaptic Package Manager"

Enter your password when prompted.

When Synaptic starts you may get a few errors... just click through them, then at the menu bar select "Settings->Repositories"

The screen titled "Software Preferences" will be displayed.

Click on the "+Add" button

The screen titled "Edit Repository..."

Select the additional repositories you'd like to search

---

