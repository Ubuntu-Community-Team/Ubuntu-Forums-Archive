---
title: "Upgrade 4.10 to 5.04?"
date: 2005-06-28
forum: Absolute Beginner Talk
---

### Post by gammyhand on 2005-06-28
I have 4.10 CD's in 64 bit flavour and 32 bit flavour.  I am using 64 bit flavour and tonight I am either going to do the "nerd" upgrade to get the 32 bit packages or re-install with the 32 bit version. Either way, is it possible to upgrade 4.10 to 5.04?

---

### Post by jasmuz on 2005-06-28
[QUOTE=gammyhand]I have 4.10 CD's in 64 bit flavour and 32 bit flavour.  I am using 64 bit flavour and tonight I am either going to do the "nerd" upgrade to get the 32 bit packages or re-install with the 32 bit version. Either way, is it possible to upgrade 4.10 to 5.04?[/QUOTE]
 To upgrade form 4.10 to 5.04 its easily done, if all packages are for the x86 32 bit architecture.

Just go to synaptic, in the edit menu--> Add CDROM, afterwards you must update your list and select mark all upgrades..

That would be it.

---

### Post by gammyhand on 2005-06-28
[QUOTE=jasmuz]To upgrade form 4.10 to 5.04 its easily done, if all packages are for the x86 32 bit architecture.

Just go to synaptic, in the edit menu--> Add CDROM, afterwards you must update your list and select mark all upgrades..

That would be it.[/QUOTE]
 If I re-install with the 32-bit install CD then Add CDROM...I don't have a 5.04 cd? I want to know if I can update my 4.10 install to 5.04 through synaptic or if it is only possible with a complete re-install. Thanks :)

---

### Post by gammyhand on 2005-06-29
[QUOTE=gammyhand]If I re-install with the 32-bit install CD then Add CDROM...I don't have a 5.04 cd? I want to know if I can update my 4.10 install to 5.04 through synaptic or if it is only possible with a complete re-install. Thanks :)[/QUOTE]
 Anyone got an answer on this? I want to reinstall tonight :)

---

### Post by poofyhairguy on 2005-06-29
[QUOTE=gammyhand]If I re-install with the 32-bit install CD then Add CDROM...I don't have a 5.04 cd? I want to know if I can update my 4.10 install to 5.04 through synaptic or if it is only possible with a complete re-install. Thanks :)[/QUOTE]

Sorry...I dropped the ball on you. I apologize. You can update Ubuntu through synaptic. 32 bit version to 32 bit version, 64 to 64 and so forth (one kind can't upgrade to the other kind).

In order to do it, enter this command in a normal terminal:

sudo gedit /etc/apt/sources.list

a text file will pop up with stuff in it. Delete that stuff. Everything. Copy and paste in these lines instead:

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

save it and exit. Open synaptic. Hit reload. Then do "mark all upgrades." Hit apply. You will upgrade to the Hoary and the newest apps we have (that are stable). It will download a lot to do it....like 500+mb...and you might have to hit enter a few times (for every question asked...just hit enter....the defaults are great).

Sorry I missed your question before. This is kinda my part of the world and I slipped.

---

### Post by gammyhand on 2005-06-29
[QUOTE=poofyhairguy]Sorry...I dropped the ball on you. I apologize. You can update Ubuntu through synaptic. 32 bit version to 32 bit version, 64 to 64 and so forth (one kind can't upgrade to the other kind).

In order to do it, enter this command in a normal terminal:

sudo gedit /etc/apt/sources.list

a text file will pop up with stuff in it. Delete that stuff. Everything. Copy and paste in these lines instead:

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

save it and exit. Open synaptic. Hit reload. Then do "mark all upgrades." Hit apply. You will upgrade to the Hoary and the newest apps we have (that are stable). It will download a lot to do it....like 500+mb...and you might have to hit enter a few times (for every question asked...just hit enter....the defaults are great).

Sorry I missed your question before. This is kinda my part of the world and I slipped.[/QUOTE]
 Much appreciated. Don't worry about the delay replying. It's just good people are willing to help at all.

Edit: Is it possible to get it to automatically accept the defaults rather than needing an enter key press? I want to leave this upgrade going while I go to work tomorrow.

---

### Post by UbuWu on 2005-06-29
[QUOTE=gammyhand]
Edit: Is it possible to get it to automatically accept the defaults rather than needing an enter key press? I want to leave this upgrade going while I go to work tomorrow.[/QUOTE]

Don't know if it is possible in synaptic, but it is possible if you use the command-line. Enter the following commands:

sudo apt-get update
sudo apt-get dist-upgrade -y

This will assume a yes on all questions.

---

