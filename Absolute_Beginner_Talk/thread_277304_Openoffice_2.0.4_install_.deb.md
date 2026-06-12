---
title: "Openoffice 2.0.4 install *.deb"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by lognok on 2006-10-14
Hi I'm trying to install the new OpenOffice 2.0.4, got the *.deb files but install is a bit tricky. What I got is a folder full off *.deb files and I cannot install any of them since they depend on each other, ie trying to install package01.deb results in error because it wants package02.deb, which is not installed, because it wants package01.deb to install. So I'm not able to install OpenOffice because I don't know the right command to give dpkg.
Is there any one who can tell me the right way to install these packages?.

By the way, openoffice 2.0.2 has been removed.

---

### Post by ariel on 2006-10-14
The way I could successfully install openoffice 2.0.4 from the official .tar.gz file follows below.

If you do it in this way you don't have to uninstall the previous version, and besides that all the file extension associations and firefox associations with openoffice are maintained. If you uninstalled the previous version, to recreate the associations it is probably easier to install the official old package from the repo, and then do the below.


       sudo apt-get install alien

       Open the new (2.0.4) .tar.gz in a temp folder; then open a terminal in the folder that contains the official .rpm's and do:

       sudo alien *.rpm                 (this takes a few minutes)
       sudo dpkg -i *.deb

       New installation will be done in: /opt/openoffice.org2.0
       sudo chown your_user_name:your_user_name /opt/openoffice.org2.0 -R
       Then: sudo gedit /usr/bin/ooo-wrapper
       And comment out the following two lines
          my $SystemInstallDir = '/usr/lib/openoffice2';
          my $OOO_BUILDVERSION = '2.0.1';
       and put instead:
          my $SystemInstallDir = '/opt/openoffice.org2.0';
          my $OOO_BUILDVERSION = '2.0.4';


Hope this helps!

---

### Post by lognok on 2006-10-15
Thanks for the guide ariel, but I figured an easier way to install.

sudo dpkg -i package01.deb package02.deb package03.deb ....and so on...

This sovled my little install problem, so Openoffice 2.0.4 is all good :D

---

### Post by slimdog360 on 2006-10-15
any differences from 2.02?

---

### Post by Gannin on 2006-10-17
lognock, where did you get an OpenOffice.org package that has .deb's in it?

---

### Post by mikeymikec on 2006-10-17
[QUOTE=ariel;1617513]The way I could successfully install openoffice 2.0.4 from the official .tar.gz file follows below.[quote]

I followed your instructions, however all the openoffice icons disappeared from the 'applications' ubuntu menu.  I've got a working installation of OO2.0.4, but I don't think Ubuntu is really aware of it.

---

### Post by lognok on 2006-10-17
Gannin
 I got the *.deb files from the danish openoffice site: [http://da.openoffice.org/](http://da.openoffice.org/)

slimdog360
 haven't been using it yet, but will have to write some pages for a report during this week, so I'll have a go at it.
  I don't expect it to differ from 2.0.2, since it worked very well for me (think it's under the bonnet stuff that's been fixed).

mikeymikec
 It happend for me as well, even though I didn't follow ariel's guide. I solved it by installing all the packages again and the icons were back in Applications -> Office -menu (hope it helps you out).

All other things aside I'm running Edgy now and ooo 2.0.4 is default package :p

---

### Post by Gannin on 2006-10-17
Thanks for the tip lognock.  The main OpenOffice.org website only has a package that has .rpm's in it, so it's very nice to see a package that has .deb's in it instead.

---

### Post by mikeymikec on 2006-10-18
> **lognok said:**
> mikeymikec
 It happend for me as well, even though I didn't follow ariel's guide. I solved it by installing all the packages again and the icons were back in Applications -> Office -menu (hope it helps you out).

All other things aside I'm running Edgy now and ooo 2.0.4 is default package :p

I tried something like this, but in 'add/remove programs', it had OpenOffice 2.0.4 (definitely mentioned that version), and I couldn't untick it.  I proceeded to remove it (selecting everything with 'openoffice' in the name) in the Synaptec Package Manager, which seemingly removed both instances from my system.  I then installed 2.0.2 through 'add/remove programs', and I don't have any ideas what to do from there.

OO 2.0.4 got installed into /opt/openoffice (definitely a folder inside /opt).  Thunderbird wasn't aware of it when I tried to open attachments.

---

### Post by RawMustard on 2006-10-18
I don't understand why such an important piece of software such as open office is not kept up to date by the ubuntu people?  This having to jump through hoops to upgrade to the latest version is just ridiculous.  A windows user just needs to download and double click a file and their old version is completely updated anytime a new version is available, why can't this be the same for ubuntu users also?

---

### Post by jincast90 on 2006-10-18
> **RawMustard said:**
> I don't understand why such an important piece of software such as open office is not kept up to date by the ubuntu people?  This having to jump through hoops to upgrade to the latest version is just ridiculous.  A windows user just needs to download and double click a file and their old version is completely updated anytime a new version is available, why can't this be the same for ubuntu users also?

Well I dont necessarily think It should be the same way. Like having to download the who install file again. But I think it should be updated every time a new version comes up via the update manager. Its the same with wine. I think the newest version is 9.16 or so. Although its much easier to update wine. (Just a line urself). But I think it is a place where they might wanna have a look.

---

### Post by Gannin on 2006-10-18
The latest version of Wine is 0.9.23, and there is a Debian package repository specifically for Wine, so if you add that to your package repositories, it gets updated automatically with the update manager.

I think it would be very useful to do something similar with OpenOffice.org.

---

### Post by theadventuresofanidealist on 2006-10-29
i have openoffice's latest version and my title bar is all messed up.
anyone know how to fix this?

---

