---
title: "update firefox"
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by zerod on 2006-07-26
is it ok to update firefox that way?:
download firefox 1.5.0.5 tar.gz
extract it
open nautilus as root
delete old firefox directory in usr/lib (backup plugins)
copy the extracted firefox 1.5.0.5
paste in usr/lib
copy plugins of firefox 1.5.0.4 in plugins folder of firefox 1.5.0.5

this is the way that I just did and everything works good..
what do you think?

---

### Post by Sef on 2006-07-26
> this is the way that I just did and everything works good..
what do you think?

If it works, that fine.

---

### Post by 3rdalbum on 2006-07-26
I'm impressed, I wouldn't have thought of doing that. Since it works, then more power to you, especially since the Firefox team don't provide instructions :-)

---

### Post by moma on 2006-07-26
Your method is OK.
I have even installed Firefox 2.0 Beta and Thunderbird 1.5 that way. Clever you took a copy of plugins.

Does the symbolic link point to right location and binary.
$ ls -l  /usr/bin/firefox 

BTW: Would you like to buy a $100 laptop?
[http://www.pledgebank.com/100laptop]("http://www.pledgebank.com/100laptop")


// moma
   [http://www.futuredesktop.com/ubuntu6.06.html]("http://www.futuredesktop.com/ubuntu6.06.html")

---

### Post by aysiu on 2006-07-26
[This script](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Firefox_1.5) (created by forum member *nanotube*) automatically installs the Mozilla (not Ubuntu) version of the latest Firefox and integrates it with Ubuntu's plugins through symlinking. And the Mozilla version of Firefox is self-updating.

---

### Post by whein on 2006-07-26
Forgive my ignorance, but I thought better to ask first rather than have to reinstall later.  I installed Ubuntu from the liveCD downloaded over the internet from work.  It put Firefox 1.5.0.3 on.  I downloaded the .deb for 1.5.0.4 from the repository, copied it over to a local directory (no internet access for my Ubuntu machine yet) and got as far as getting Synaptic to recognize it as a valid package.  However, when I go to upgrade using Synaptic I get a warning that it's going to uninstall the Ubuntu Desktop.  Ack!  That doesn't sound good!  Is this ok and can I ignore it or will this do Really Bad Things(tm)?

---

### Post by Metacarpal on 2006-07-26
> **whein said:**
> ...However, when I go to upgrade using Synaptic I get a warning that it's going to uninstall the Ubuntu Desktop.  Ack!  That doesn't sound good!  Is this ok and can I ignore it or will this do Really Bad Things(tm)?

The Ubuntu-Desktop package is what's called a "meta-package".  It doesn't actually do anything.  It's set up so that all of the standard Ubuntu (Gnome) packages are dependancies, so if someone tells their computer to install the Ubuntu-Desktop package, it installs everything that comes with it.

So the short answer is, no, it won't hurt anything to lose that package.

---

### Post by Freelance Physicist on 2006-07-26
Wouldn't it be easier to uninstall firefox from within Synaptic (or apt-get) and then install from the source downloaded at mozilla.com/firefox?  (Of course, making sure to back up bookmarks and all other important data.)

This way firefox would keep itself updated without having to wait for the ubuntu repositories to catch up.

---

### Post by hanexar on 2006-07-27
I know it is fun to have the new firefox the day it is out, but it usually show up quite quickly in the update manager. No need to rush for manual update ;)

---

### Post by aysiu on 2006-07-27
> **Freelance Physicist said:**
> Wouldn't it be easier to uninstall firefox from within Synaptic (or apt-get) and then install from the source downloaded at mozilla.com/firefox?  (Of course, making sure to back up bookmarks and all other important data.) Uninstalling Firefox might ruin your Gnome--just the way Ubuntu built it--the two are tightly integrated.

> This way firefox would keep itself updated without having to wait for the ubuntu repositories to catch up. But, yes, if having the new release the day of is important to you, use the script I linked to earlier to install the Mozilla version, which is self-updating.

> **hanexar said:**
> I know it is fun to have the new firefox the day it is out, but it usually show up quite quickly in the update manager. No need to rush for manual update ;) Also true. I believe the last update from 1.5.0.3 to 1.5.0.4 took about a week.

---

### Post by Nrvnqsr on 2006-07-27
seems to me that script is incomplete, if I understand this it should able to tell me the version number and language choice for me to choose but it doesn't. And I have no idea to go around it :(

Edit: ok, what I can see from the page, this script is only designed for firefox 1.0.8 not the 1.5.0.# :-&

---

### Post by aysiu on 2006-07-27
> **Nrvnqsr said:**
> seems to me that script is incomplete, if I understand this it should able to tell me the version number and language choice for me to choose but it doesn't. And I have no idea to go aroud it :(
Hm. Maybe you can send a private message to [the creator of that script](http://www.ubuntuforums.org/member.php?u=66474).

---

### Post by Freelance Physicist on 2006-07-27
> **aysiu said:**
> Uninstalling Firefox might ruin your Gnome--just the way Ubuntu built it--**the two are tightly integrated**.

Why does this sound so familiar?
;)

---

### Post by aysiu on 2006-07-27
> **Freelance Physicist said:**
> Why does this sound so familiar?
;)
Well, it's not *that* integrated. For example, you don't use Firefox to provide updates (security and otherwise) to Ubuntu or Gnome. But several Gnome applications use Firefox's rendering engine.

---

### Post by nemonullus on 2006-10-23
Just a quick update - I just updated my Firefox to 2.0 using Zerod's method (thanks Zerod). The script doesn't seem to recognize anything past 1.5.07 - probably because 2.0 is still beta.

Anyhow, if you want to get 2.0 on Dapper Drake, this is a great way to do it.

---

### Post by towsonu2003 on 2006-10-24
I didn't see this link trhown in here so... it's always to [check out documentation]("https://help.ubuntu.com/community/FirefoxNewVersion") :p (adjust it for the new version while putting in commands of course)

---

