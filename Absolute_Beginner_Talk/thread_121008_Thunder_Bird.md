---
title: "Thunder Bird"
date: 2006-01-24
forum: Absolute Beginner Talk
---

### Post by utab on 2006-01-24
Hi,

I would like to uninstall Mozilla-Thunderbird(not the mails and addresses in it just the program) and install Thunderbird only? How can I do this? I appreciate If you could give me with the complete steps (I looked at wiki but some of the steps have been skipped especially the ones about the Gnome Launcher menus.)

Thx.

---

### Post by manicka on 2006-01-24
If you have the Mozilla-Thunderbird package installed then that is Thunderbird.
They are the same thing. 

What page are you looking at on the wiki?

---

### Post by miahfost on 2006-01-24
I am not sure it is necessary to uninstall Mozilla-Thnuderbird so that you can install Thunderbird, but if that what you really want to do, here's how.

If you want to remove a program you can select System --> Administration --> Synaptic Package Manager. Once you give your password, Synaptic opens up giving you a list of installed software on your system. Do a search for thunder which should bring up all the Mozilla-Thunderbird packages. Click on the empty box just before the name Mozilla-Thnuderbird and then click "remove" when a dialog pops up. 

Note this assumes you installed Mozilla-thunderbird through your Ubunut system and not downloaded directly from the internet. If you downloaded it directly from the internet you will have to use a different method to uninstall.

---

### Post by utab on 2006-01-24
Hi 

Since Ubuntu installs Mozilla-T... 1.0.7 it has a bug with multiple SMTP servers so I can not manage two or more accounts at the same time. This is why I want to uninstall Mozilla-T. and why I want to upgrade to Thunderbird 1.5 which is said to overcome this bug.

thx.

---

### Post by manicka on 2006-01-24
[QUOTE=utab]Hi 

Since Ubuntu installs Mozilla-T... 1.0.7 it has a bug with multiple SMTP servers so I can not manage two or more accounts at the same time. This is why I want to uninstall Mozilla-T. and why I want to upgrade to Thunderbird 1.5 which is said to overcome this bug.
[/QUOTE]

Ah ok, that makes more sense. Is this the wiki page you were referring to? What problems are you having with the intructions?

[https://wiki.ubuntu.com/ThunderbirdNewVersion](https://wiki.ubuntu.com/ThunderbirdNewVersion)

---

### Post by utab on 2006-01-24
Hi sorry I copied the whole instructions,

sudo mv thunderbird-1.5rc1.tar.gz /opt/
sudo tar xzvf /opt/thunderbird-1.5rc1.tar.gz

[COLOR="red"]+ To put it in your home direcory do basically the same thing, but change /opt/ to ~ and you can leave out the sudo's (why do we need this and how?)[/COLOR]

Almost done - to be able switch off between running either the older package you might have installed and the new version, add a new symbolic link: 

sudo ln -s /opt/thunderbird/thunderbird /usr/bin/thunderbird
As the older version will be installed as /usr/bin/mozilla-thunderbird, this will allow you to run that one as mozilla-thunderbird and the new one with thunderbird. To avoid confusion or get rid of the old link altogether just do: 

sudo mv /usr/bin/mozilla-thunderbird /usr/bin/mozilla-thunderbird-old
sudo ln -s /opt/thunderbird/thunderbird /usr/bin/mozilla-thunderbird

You can now launch the new version with your old profile from the command-line. If you decided to use thunderbird from the command line, you may need to adjust the properties of your Gnome panel & menu launchers accordingly.

[COLOR="Red"]+ This is  a problem I can not find sth like this, when I right click on the panel or maybe I am at the wrong place [/COLOR]

To modify Gnome panel launchers right click and select Properties. Then change the old command to the new command if you changed it from mozilla-thunderbird to thunderbird. To change your link in the Applications menu, use Applications > System Tools > Application Menu Editor. This lets you use the official icons if you've gone throught the trouble of updating them (see the  Unofficial Ubuntu Guide). 

[COLOR="red"]+ This one is also related with the above I guess[/COLOR]

Should you need it, the Thunderbird profile manager can still be accessed via: 

thunderbird -P

---

### Post by manicka on 2006-01-24
From what I can make out from the above

1. Yopu don't need to install thunderbird into your home directory. You are right, this part is not necessary.

2. Once you've run these commands

sudo mv /usr/bin/mozilla-thunderbird /usr/bin/mozilla-thunderbird-old
sudo ln -s /opt/thunderbird/thunderbird /usr/bin/mozilla-thunderbird

You should be able tu sue your existing thunderbird icons to launch the new version. This is assuming that you haven't uninstalled the 1.07 version and still have it there. Both versions should exist quite ahppily together on your system.

---

