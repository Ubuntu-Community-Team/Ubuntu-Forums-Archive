---
title: "1 install of Seamonkey, multiple users"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by RogerDavis on 2007-04-09
I've been trying without success to install Mozilla SeaMonkey.  Actually, I did get an earlier version installed about a month ago, but it's only available to my log-in, not hers.  So while trying to install the updated version:
1) How do I install an app into USR-LOCAL, so all can use it?
2) If I must install it into my log-in, how do I get it to be usable in hers?
3) Maybe I should make a third log-in, call it FAUXROOT, and install all unsupported apps here, and have separate log-ins for both of us to use the apps in the HOME-USR, and in the FAUXROOT account?
4) Or ?!?!?

---

### Post by Bachstelze on 2007-04-09
Whatever you do in your /home folder, do the same thing but in /usr/local as root, though if you want to follow the standards, you should do it in /opt instead.

---

### Post by kvonb on 2007-04-09
A correctly installed application will be available to ALL accounts.

How did you install it?  Was it a .deb file or did you compile it from source?

If you weren't asked for your password when installing, then it might be only installed "locally", ie only for the user that installed it.

A non-official Ubuntu repository provided application might not have installed all the menu icons, although it might still be available.

When logged in as the other user, press <ALT><F2> and type in: seamonkey to see if it will run.  If it does
, then it is merely the icon that is missing from the menu.  It can be added by right clicking on the desktop and creating a new launcher.

Hope that helps.

---

### Post by Bachstelze on 2007-04-09
kvonb > how do you define "correctly installed" ? Sorry to disappoint you but "the Ubuntu way" is not the only correct way to do things !

---

### Post by aysiu on 2007-04-09
Copy and paste these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
wget -c http://mozilla.mirrors.easynews.com/mozilla/seamonkey/releases/1.1.1/seamonkey-1.1.1.en-US.linux-i686.installer.tar.gz
tar -xvzf seamonkey-1.1.1.en-US.linux-i686.installer.tar.gz
cd seamonkey-installer
gksudo ./seamonkey-installer
``` Follow the installer, answering all the questions with the default. ```
sudo mv /usr/local/seamonkey/plugins /usr/local/seamonkey/plugins.bak
sudo ln -s /usr/lib/firefox/plugins /usr/local/seamonkey/plugins
sudo ln -s /usr/local/seamonkey/seamonkey /usr/bin/seamonkey
``` Now the command *seamonkey* should launch Seamonkey for all users.

---

### Post by medad on 2007-04-09
I was going to tell you to go to the following website for help ([http://www.mozilla.org/projects/seamonkey/releases/seamonkey1.1.1/installation.html#linux_install_multiuser]("http://www.mozilla.org/projects/seamonkey/releases/seamonkey1.1.1/installation.html#linux_install_multiuser")), but you should first try what aysiu states above.  It definitely would be a quicker process.  Good luck.

---

### Post by aysiu on 2007-04-09
I've also updated the Wiki page to reflect the instructions I gave here (before, its instructions were a bit scant):
[https://help.ubuntu.com/community/SeaMonkey](https://help.ubuntu.com/community/SeaMonkey)

---

### Post by RogerDavis on 2007-04-09
Got to here, got this error:

roger@roger-desktop:~/seamonkey-installer$ sudo mv /usr/local/seamonkey/plugins /usr/local/seamonkey/plugins.bak
mv: cannot stat `/usr/local/seamonkey/plugins': No such file or directory
roger@roger-desktop:~/seamonkey-installer$

---

### Post by RogerDavis on 2007-04-09
OOPS, this also...

roger@roger-desktop:~/seamonkey-installer$ gksudo seamonkey-installer
sudo: seamonkey-installer: command not found

---

### Post by aysiu on 2007-04-09
The commands have to be copied and pasted in that exact order, including the downloading of the seamonkey .tar.gz file.

If you want to use a file you've already downloaded, it must be in your home directory in order for those commands to work.

Let me explain what each command does: ```
wget -c http://mozilla.mirrors.easynews.com/mozilla/seamonkey/releases/1.1.1/seamonkey-1.1.1.en-US.linux-i686.installer.tar.gz
``` This command downloads Seamonkey from the Mozilla website. ```
tar -xvzf seamonkey-1.1.1.en-US.linux-i686.installer.tar.gz
``` This command unzips (or extracts) the file into its multiple parts. ```
cd seamonkey-installer
``` This command changes the current directory to the newly created *seamonkey-installer* directory. If you are not in this new directory, none of the subsequent commands will work. ```
gksudo ./seamonkey-installer
``` Launches the installer wizard with root privileges (allowing you to make system-wide changes for all users) ```
sudo mv /usr/local/seamonkey/plugins /usr/local/seamonkey/plugins.bak
``` Makes a backup copy of the standard Seamonkey plugins folder. ```
sudo ln -s /usr/lib/firefox/plugins /usr/local/seamonkey/plugins
``` Creates a link from your regular plugins folder to the Seamonkey plugins folder so Seamonkey can share all the other plugins you've already installed. ```
sudo ln -s /usr/local/seamonkey/seamonkey /usr/bin/seamonkey
``` Links the Seamonkey executable to the normal path where you can launch applications from.

---

### Post by kvonb on 2007-04-09
> **HymnToLife said:**
> kvonb > how do you define "correctly installed" ? Sorry to disappoint you but "the Ubuntu way" is not the only correct way to do things !

I don't recall any reference to "the Ubuntu way" in my post.

"A correctly installed application will be available to ALL accounts" seems quite straightforward to me, ie if the installation went well and it adhered to standard Linux conventions, then it will be available to all user accounts, unless a certain user is specifically banned from using it.

In this case "correctly installed application" was referring to the application itself, NOT the person that installed it.  It is a modern "phenomenon" that people instantly take everything to refer to themselves personally, whereas the actual sentence refers to the third party, in this case the actual installation process, NOT the installer!

Ergo if you were assuming that I was blaming RogerDavis for not correctly installing seamonkey, then you are mistaken.  Also if you were assuming that I was stating that the "Ubuntu way" is the "Correct and only way" to install applications, again you got the wrong end of the stick!

And you are not disappointing me, the only way I am disappointed is when people read more into a sentence than is offered, and make assumptions rather than stick to facts.

Regards, Kev :)

---

### Post by RogerDavis on 2007-04-09
OK, I got farther this time, It went through some motions as though installing, but the elapsed time was something like 5 to 10 seconds, much shorter than Windoze.  When I restarted Seamonkey, it still showed version 1.1, not 1.1.1 .  

Log below:

roger@roger-desktop:~$ wget -c [http://mozilla.mirrors.easynews.com/mozilla/seamonkey/releases/1.1.1/seamonkey-1.1.1.en-US.linux-i686.installer.tar.gz](http://mozilla.mirrors.easynews.com/mozilla/seamonkey/releases/1.1.1/seamonkey-1.1.1.en-US.linux-i686.installer.tar.gz)
--07:37:57--  [http://mozilla.mirrors.easynews.com/mozilla/seamonkey/releases/1.1.1/seamonkey-1.1.1.en-US.linux-i686.installer.tar.gz](http://mozilla.mirrors.easynews.com/mozilla/seamonkey/releases/1.1.1/seamonkey-1.1.1.en-US.linux-i686.installer.tar.gz)
           => `seamonkey-1.1.1.en-US.linux-i686.installer.tar.gz'
Resolving mozilla.mirrors.easynews.com... 69.16.168.244
Connecting to mozilla.mirrors.easynews.com|69.16.168.244|:80... connected.
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable

    The file is already fully retrieved; nothing to do.

roger@roger-desktop:~$ tar -xvzf seamonkey-1.1.1.en-US.linux-i686.installer.tar.gz
./seamonkey-installer/
./seamonkey-installer/xpi/
./seamonkey-installer/xpi/spellcheck.xpi
./seamonkey-installer/xpi/regus.xpi
./seamonkey-installer/xpi/deflenus.xpi
./seamonkey-installer/xpi/inspector.xpi
./seamonkey-installer/xpi/chatzilla.xpi
./seamonkey-installer/xpi/langenus.xpi
./seamonkey-installer/xpi/mail.xpi
./seamonkey-installer/xpi/talkback.xpi
./seamonkey-installer/xpi/xpcom.xpi
./seamonkey-installer/xpi/venkman.xpi
./seamonkey-installer/xpi/reporter.xpi
./seamonkey-installer/xpi/psm.xpi
./seamonkey-installer/xpi/browser.xpi
./seamonkey-installer/README
./seamonkey-installer/config.ini
./seamonkey-installer/seamonkey-installer-bin
./seamonkey-installer/installer.ini
./seamonkey-installer/seamonkey-installer
./seamonkey-installer/MPL-1.1.txt
roger@roger-desktop:~$ cd seamonkey-installer
roger@roger-desktop:~/seamonkey-installer$ gksudo ./seamonkey-installer
roger@roger-desktop:~/seamonkey-installer$ gksudo ./seamonkey-installer
roger@roger-desktop:~/seamonkey-installer$ sudo mv /usr/local/seamonkey/plugins /usr/local/seamonkey/plugins.bak
roger@roger-desktop:~/seamonkey-installer$ sudo ln -s /usr/lib/firefox/plugins /usr/local/seamonkey/plugins
roger@roger-desktop:~/seamonkey-installer$ sudo ln -s /usr/local/seamonkey/seamonkey /usr/bin/seamonkey
ln: creating symbolic link `/usr/bin/seamonkey' to `/usr/local/seamonkey/seamonkey': File exists
roger@roger-desktop:~/seamonkey-installer$
roger@roger-desktop:~/seamonkey-installer$

HELP?!?

---

### Post by aysiu on 2007-04-09
The output actually looks pretty good. For some reason, /usr/bin/seamonkey already exists, so try ```
sudo rm /usr/bin/seamonkey
sudo ln -s /usr/local/seamonkey/seamonkey /usr/bin/seamonkey
```

---

### Post by RogerDavis on 2007-04-10
SUCCESS - KINDA...
I ran the lines above, no good
went back and repeated the first batch, no new icon on screen, old one still launches from original icon.  Went into "home-usr-local", found the new files, looked ok.  Found executable, ran it, correct one.  Made a launcher, could not get correct icon, even in the "icons" directory of Seamonkey.  Used another, works, but bogus icon.

So now:

1) How do I get correct Icon?
2) Can I just delete the first installation (1.1) in Roger-Seamonkey directory?  Or will that kill all my bookmarks?  I can't find and "uninstall" file, maybe it's not necessary?

Thanks!!!

---

