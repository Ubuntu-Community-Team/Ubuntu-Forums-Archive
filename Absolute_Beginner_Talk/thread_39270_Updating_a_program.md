---
title: "Updating a program"
date: 2005-06-04
forum: Absolute Beginner Talk
---

### Post by Zaare on 2005-06-04
I'm probably as new to Linux as one could be, I installed Ubuntu just yesterday.
Anyway, here's the problem:

When I installed Ubuntu, it automatically installed certain programs, for example firefox. Now I want to upgrade firefox. I downloaded the linux version of the installer and found the folder where firefox is installed (/usr/lib/mozilla-firefox). When I tried to install the new version there, I got the message: Choose another directory because you do not have permission to install to /usr/lib/mozilla-firefox.
First I thought it was because I didn't have administrative rights, so I created an administrator account, but even when I log in with the administrator account I recieve the same message.

Any help would be appreciated.

---------- Edit --------------
I found the instructions on how to install updates in another thread nad was able to update firefox, but I still wonder why I recieved the message about not having permission to install.

---

### Post by Moobert on 2005-06-04
For a start a root 'administrator' account is made on the ubuntu install (as with most linux). So type...

sudo <program name>

to run the app with root premissions

or

sudo -s

to login a root with that terminal

Logining into X as root is bad, as it removes the protection you get from a muiltuser system.

The best way atm to update firefox is to use the backports to the apt-get system, see:
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

more info on backport:
[http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/)

---

### Post by Moobert on 2005-06-04
[QUOTE=Zaare]
ions on how to install updates in another thread nad was able to update firefox, but I still wonder why I recieved the message about not having permission to install.[/QUOTE]

as the normal user to only have read access to everything on your system, plus write access to /home/<username>. The root account as full read/write to all your system and it allow you to make major changes. So run most apps as a normal user so they can't do bad things to your system.

---

### Post by Zaare on 2005-06-04
Oh, I see. Thanks. I have another problem with this though:

It seems the version number is not updated in the Ubuntu update of firefox so I can't access the addons at firefox homepage. This is supposed to get me around the problem:
Setting general.useragent.vendorSub to 1.0.4 in about:config seems to let me
access addons.mozilla.org
but I don't understand how to do this.

---

### Post by Knome_fan on 2005-06-04
Just type about:config in the location bar (where you normally type the addresses of web pages).

Then search for general.useragent.vendorSub and change its value to 1.0.4 (I think you have to double-click on the value).

---

### Post by Zaare on 2005-06-04
Thanks a lot for the help guys, but I have one more question:
If I log in with an administrator account (the one you can create under "users and groups"), does that mean I have logged in as root? Which type of account should I have for "normal" use? Default, Desktop or Administrator?

---

### Post by poofyhairguy on 2005-06-04
[QUOTE=Zaare]Thanks a lot for the help guys, but I have one more question:
If I log in with an administrator account (the one you can create under "users and groups"), does that mean I have logged in as root? Which type of account should I have for "normal" use? Default, Desktop or Administrator?[/QUOTE]

Yep. Thats bad. Whats why some many Window's machines are screwed. Go with the default account. 

If you need to use a GUI application in root, use this command:

gksudo app.

(replace app. with name of application).

---

### Post by Zaare on 2005-06-05
Ok, I created a Default account and logged in. Now it seems I can't do anything that requires a password like "sudo", Synaptic, Firestarter and so on.
When I type "sudo -s" I get the message that I'm "not in the sudoers file" and when I try to launch firestarter with "gksudo" I get the message that I'm "not in".

---

### Post by Knome_fan on 2005-06-05
No, I think poofhairyguy meant that you should stay with the account you created on installation. This accout gets set up to be able to use sudo.

If you want further accounts to be able to use sudo, open up a root terminal and type visudo.
At the bottom you'll find a sudo line for the first user created during installation, now just add other users you want to be able to use sudo.

Of course it's best to simply stick with the initial user.

What exactly are you trying to do anyway?

---

### Post by Zaare on 2005-06-05
Well, I started this thread because I needed help updating firefox, and worked out. But Moobert said that, from a safty point of view, it's a bad idea to use an administrator account for general usage, so I created a new account (Default) which I didn't put in sudoers-group (did not know about that at the time).
And since I thought the root-account which is created automatically when installing Ubuntu will have the same password as the first "normal account" I deleted my administrator account. But when I try to log in as root with the mensioned password, I get the message that the password is wrong.
So basically I have locked my self out of the system. Very pathetic, I know :)
I think I have to re-install Ubuntu...

---

### Post by Gtaylor on 2005-06-05
If your new account is not in the sudoers list and you deleted your old regular user account, you probably have in fact locked yourself out. I believe there's a way to get back in via a rescue boot or something, you'll have go Google something like 'lost root password + Debian'.

And I believe you mis-understood what was said about security :) Just stick with the initial account you created with Ubuntu, what was said earlier was about people using the root account to surf the web or on Windows, the Administrator account. You definitely never want to use those for day-to-day stuff.

---

