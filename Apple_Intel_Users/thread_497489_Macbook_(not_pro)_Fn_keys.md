---
title: "Macbook (not pro) Fn keys"
date: 2007-07-10
forum: Apple Intel Users
---

### Post by Kaltas on 2007-07-10
Hello everyone (yay my first post! :) )...

After reading a lots of resources I managed to get up and running almost everything on my shiny new Macbook (new one - Core 2 Duo). Unfortunately two last things refuse to work.

1. Mute button - if I press Fn+f3 - it does pop-up a message Mute On / Mute Off which is pretty good, but it does not affect sound at all - it still keeps playing (KMix icon is crossed all the time so I suppose it thinks the sound is muted). Volume control (Fn+f4 & Fn+f5) works great.

2. Brightness control (Fn+f1 & Fn+f2) doesn't do anything. I managed to get macbook-backlight -xx and macbook-backlight +xx commands working so I can change the brightness from the console, but I would like to use my Fn keys too.

Please ask if you need to know some more information.

If anyone knows what to do I will be very grateful for any help or directions where to find it.

---

### Post by benanzo on 2007-07-10
I don't know about the brightness keys - it Just Works on my first-gen MacBook.  But for the volume keys I think you need to tell KMix which ALSA channel to control.

Right now it is most likely set to control something like Front or Master, when it should be controlling PCM.  I don't know how to change it in KDE but in GNOME go to **System -> Preferences -> Sound** then under **Default Mixer Tracks** make sure that **PCM** is highlighted.  Now open volume control and turn both Front and Master up as far as they go.  You'll use the PCM channel to control all output volume.  Now the keyboard keys will work as expected.  There should be a similar way to do it in KDE.

Note:  I have sometimes experienced crackling and distortion if the Master channel is set to max volume even while using PCM to control the output.  If you experience this just set Master to about 50-75%.  It doesn't seem to affect anything other than that.

Good Luck!

---

### Post by ronocdh on 2007-07-10
I just wanted to mention that I have a MBP (2nd gen), and Benanzo's advice is applicable to them, too. Each time I reinstall, the volume buttons have a GUI overlay response, but the volume doesn't change. Setting the **Front** channel does solve the problem on my MBP (SigmaTel Audio card, don't know whether that's different from the MBs). Also, be aware there are separate settings for **Speakers** and **Headphones**, much as I'm sure you've noticed different volumes in OS X when plugging in headphones.

BTW, in Feisty I just hit the F-keys without holding Fn. Are the MBs usually set up to require Fn depressed as well, or is this a personal configuration by Kaltas?

---

### Post by Kaltas on 2007-07-10
Thank you for your quick replies guys, I really appriciate it!

Maybe I didn't explain my problem very well - sound control Fn+f4/f5 (-volume and +volume) works well, the only Fn+fX combinations that don't work are Fn+f1, Fn+f2 (backlight control) and Fn+f3 (mute).

After fresh installation (Kubuntu 7.04 Feisty) none of the keys worked (with or without Fn if I remember correctly). After I installed sysfsutils package volume control started working, but Mute key only popups a message about Mute On/Off but doesn't really mute the sound and Brightness keys don't do nothing at all...

I think (and I might be wrong) that I only need to map Fn+f1/2/3 to some shell command (like macbook-backlight -10 and +10 or so) somewhere but I really can't figure out where.

benanzo: the setting you are describing can be set in KMix in "Select master channel" window - just writing this here for other KDE users who may find it useful

EDIT:
In one guide I found these commands that probably do the trick for Gnome, but I can't figure out the KDE alternative.

```

wget http://ubuntu.desrt.ca/macbook-backlight_0.0-1_i386.deb
gdebi-gtk macbook-backlight_0.0-1_i386.deb
sudo chmod u+s /usr/bin/macbook-backlight
gconftool-2 --type string --set /apps/metacity/global_keybindings/run_command_1 "0x65"
gconftool-2 --type string --set /apps/metacity/global_keybindings/run_command_2 "0xd4"
gconftool-2 --type string --set /apps/metacity/keybinding_commands/command_1 "/usr/bin/macbook-backlight -10"
gconftool-2 --type string --set /apps/metacity/keybinding_commands/command_2 "/usr/bin/macbook-backlight +10"

```

---

### Post by Wittiga on 2007-07-12
Ive just installed kubuntu feisty on my new macbook and the Fn(n=1,2,3,...) keys work just fine, no need of using fn. But i have a problem, normally f5 used to reload firefox for example, but now it will turn up the volume. And alt+f4 will not close a window but turn the volume down. All the Fn keys work like they do on mac, and i dont know how to make them work the other way around. Crtl+alt+f2 will not take me to console mode, it will change brightness. I think this is because i chose mac keyboard during installation, which is good, but i miss those other "normal" uses of the Fn keys. Other thing that my macbook lacks is the del key, i have to use the mouse whenever i want to delete a file. Do i have to manually edit some configuration file to fix this? Or am i missing something?

Thanx

Edit: glupie me. Just have to use the fn key to use the Fn. And brightness wont change :(

---

### Post by Kaltas on 2007-07-13
We share the same problem although we have different goals ... Hope someone will help.

---

