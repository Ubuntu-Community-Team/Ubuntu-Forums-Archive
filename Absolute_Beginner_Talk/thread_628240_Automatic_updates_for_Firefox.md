---
title: "Automatic updates for Firefox"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by Dumpy Dumpster on 2007-12-01
Why is the 'automatic update' box Firefox greyed out.   The other two are active.
Current Firefox is 2.0.0.8 and OS is Feisty Fawn.

---

### Post by FuturePilot on 2007-12-01
That's the way Ubuntu works. The Firefox updates are handled by the package manager.

---

### Post by Dumpy Dumpster on 2007-12-01
Thanks FuturePilot, but exactly how do I get updated?  Absolute Beginner, don't forget!!

---

### Post by mcduck on 2007-12-01
> **Dumpy Dumpster said:**
> Thanks FuturePilot, but exactly how do I get updated?  Absolute Beginner, don't forget!!

It gets updated through the same way the rest of Ubuntu gets updates. When Ubuntu developers have created and tested a working package of the new Firefox version it's uploaded into Ubuntu's repositories, and you'll get a icon in the Notification Ar ea, next to the clock, telling you that you have new updates available..

---

### Post by SunnyRabbiera on 2007-12-01
or you can do it the hard way like I do:
download firefox from its main download page
move it to something simple, like your home folder
unzip it
after that you will need to do this:
open up synaptic
now what you will need is something called nautilus-open-terminal, as this will allow you to open a terminal inside your desired directory (for some odd reason this is not enabled in ubuntu, it honestly should be)
now after installing it you will have to restart your session... there is no real easy way to do this bit I am afraid.
now after restart go to whatever directory you put the firefox zip in and under "file" in the menu go to "open in terminal"
now after this type in
sudo nautilus
and type in your password
now here is the tricky part:
go to /usr/lib/firefox
now in the folder you unzipped firefox to (as i suggested put the file in your home directory so you dont clutter your desktop, the directory is /home/yournamehere/, the home directory will have the same name as you use to log in just in case you are confused, for example if your screen name is clive then it will be in /home/clive, or if it is janet then it will be home/janet and sofourth)
now the key here is to select everything except the plugins folder and drag them from where you extracted the zip to (you should have it in /home/yournamehere/firefox)
to the /usr/lib/firefox directory
now whatever you do DONT, I repeat DONT copy over the plugins folder, leave it be as if you do overwrite the plugins folder already given in the /usr/lib/firefox directory and that will be bad, ESPECIALLY if you have plugins installed.
after the move is complete firefox will be up to date...
but remember:
be careful when doing this

---

### Post by Dumpy Dumpster on 2007-12-01
Thanks all.  I have printed it all out and will work through it.  Regards and thanks again.

---

