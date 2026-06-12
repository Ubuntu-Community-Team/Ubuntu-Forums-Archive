---
title: "Gnome PPP trouble"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by sarum on 2006-11-29
Hi there. I've recently reinstalled Dapper; and whereas before GnomePPP (icon on the panel) worked well.
 Now I have to go to Networking (via system/admin:) to 'Activate pppmodem' - all this; after entering my password. I can then go to the icon on the panel and it works. It also starts from the Networking dialog, of course, which means the panel icon is a bit redundant and certainly not working as it should.
Before the above mentioned reinstall I made a note of all the settings, but I've obviousely done something wrong. Can anyone suggest how to get it dialing from the GnomePPP icon without haveing to go to Networking; before the reinstall I dont think that I had to give my password. Password isn't too important as I'm the only one here. Any help will, as always, be gratefully received from Sarum

---

### Post by nite owl on 2006-11-29
Hi actually maybe you could answer my quesition, Ive downloaded the gnome-ppp package. but its in a .fpm format which i have not encountered before?? How would i install this?

---

### Post by johnnymac on 2006-11-29
Do you mean .fpm or .rpm?  I ask because .fpm is a FoxPro startup file...and I don't think that's the case.  If it's a .rpm you need to do the following:

This will create a .deb file for you
```

sudo apt-get install alien

```

Then  do this...
```

cd /place-where-you-put-the-rpm
sudo dpkg -i whatever-the-file-is-called.deb

```

Good luck

---

### Post by kvonb on 2006-11-29
You might have to run "pppconf" or "pppoeconf" (if you use pppoe) from a terminal, that sets up your username/password/network etc'.

Then you use the pon/poff wrapper tool (icon) gpppon to dial/hang up.

---

### Post by sarum on 2006-11-30
Hi I hope Johnnymac has answered your question - sorry I can't help - Sarum.

---

### Post by unisol on 2006-11-30
the way i dialup using dapper is by right-clicking on the taskbar at top of screen and click add to panel then select modem icon and click add. then i right-click on the modem icon and select properties and fill in isp infi phone number, username ,password, modem port. when im done i right-click on modem app  and select activate. it works everytime. hope it works for you

---

### Post by JNowka on 2006-11-30
Hello, I had this problem myself.  And it took me 3 months on and off to finally figure it out.  It was so easy you wouldn't believe.

1)Goto System->Administration->Networking

2)Select Modem connection->Properties

3)Deselect Enable this connection.

4)Use the Modem tools of your choice.

Don't forget you may have to edit the config files to get the modem connection software to work properly.  The most I had to do is edit kppp's config file to have it noauth.  not the pppconfig file, but the kppp.  I kinda have a hybrid system :).

---

### Post by sarum on 2006-11-30
Hi thanks to kvonb,unisol and JNowka. unisol's answer seemed the easiest to try; and it worked. I'm not sure now why I bothered with GnomePPP, other than the fact that I'd used it before. Anyway, thanks to all of you. Sarum.

---

