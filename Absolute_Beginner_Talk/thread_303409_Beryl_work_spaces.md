---
title: "Beryl work spaces"
date: 2006-11-20
forum: Absolute Beginner Talk
---

### Post by Bazzaah on 2006-11-20
had a quick look through search but couldn't find the answer to my question, which is this:

is there a way to use the top and bottom planes of the Beryl cube as work spaces? 4 is great to have but sometimes, i think it'd be nice to have access to the 6 sides that a cube has. So that way I could have Evolution, GIMP, NVU, Banshee, Open Office and Firefox all going at the same time.

Is this possible? If not any plans to make it so?

Also thought some of you might find this amusing - I went back into windows yesterday to play around on FS2004 and Windows crashed on me twice within 30 mins with the instability apparently caused by an upgrade (ahem) to windows installer being unable to install itself. I had to laugh. 

Thanks.

---

### Post by sethmahoney on 2006-11-20
No, you can't, and there are no plans that I'm aware of to make it so that you can.  You used to be able to make the "cube" have more than 6 sides, which would give you more workspaces, but it looks like they've removed that as well...

You might have a look at the Beryl forums (forum.beryl-project.org) just in case there's something I've missed, though.  There will also be more details on plans for future releases there.

---

### Post by CowzRule on 2006-11-20
In my version of Beryl, I'm able to add desktops to the cube by clicking the "Numeric Values" tab under "General Options" and adjusting the "Horizontal Virtual Size" slider.
One note...If you do adjust it to more or less than 4, you'll lose the top and bottom cube image.

---

### Post by sethmahoney on 2006-11-20
> **CowzRule said:**
> In my version of Beryl, I'm able to add desktops to the cube by clicking the "Numeric Values" tab under "General Options" and adjusting the "Horizontal Virtual Size" slider.
One note...If you do adjust it to more or less than 4, you'll lose the top and bottom cube image.

It looks like they removed that option for 0.1.2 - or, at least, its not appearing in my settings.

---

### Post by CowzRule on 2006-11-20
Sorry, guess I should have said I'm using the latest Beryl svn version. I just updated it yesterday. This is how I got it:
[http://www.ubuntuforums.org/showthread.php?t=279456]("http://www.ubuntuforums.org/showthread.php?t=279456")
Basically add this to your sources.list```
For Daper:
deb http://3v1n0.tuxfamily.org dapper beryl-svn

For Edgy:
deb http://3v1n0.tuxfamily.org edgy beryl-svn
```Add Key:```
KEY=81836EBF; gpg --keyserver subkeys.pgp.net --recv $KEY && gpg --export --armor $KEY | sudo apt-key add -
```Get needed dependencies:```
sudo apt-get install libc6 libice6 libpng12-0 libsm6 libstartup-notification0 libx11-6 libxcomposite1 libxdamage1 libxext6 libxfixes3 libxinerama1 libxrandr2 libglib2.0-0 libatk1.0-0 libcairo2 libfontconfig1 libgtk2.0-0 libpango1.0-0 libxcursor1 libxi6 libxrender1 librsvg2-2 libapr0 libdb4.3 libexpat1 libsvn0 libwnck18 libldap-2.3-0 #libdbus-1-2 libdbus-1-3
```Then:```
sudo apt-get update
sudo apt-get upgrade
```and rebooted.

---

