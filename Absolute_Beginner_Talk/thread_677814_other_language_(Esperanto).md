---
title: "other language (Esperanto)"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by bengtgunnar on 2008-01-25
I elected Esperanto for installing and using Ubuntu and the installation process works fine in perfectly translated Esperanto. 
   The problem accurs when I reboot. Then I can elect between 14 varieties of English but not Esperanto (or Swedish, my mother toung). Sorry for bad spelling of English

---

### Post by Ub1476 on 2008-01-25
Have you tried to set your language in System>Administration>Language Support?

---

### Post by brokenhachi on 2008-01-25
so i have a similar problem. i would like to install japanese language support (so i can type english and japanese text and switch between them) but when i went to system>admin>language support  the only language on the list is english (like the guy above said, 15 different types)

are we missing some file?

---

### Post by brokenhachi on 2008-01-25
ok so i was looking in the add/remove programs menu and i notice under system tools there is 2 packs for language support.. one is installed and the other one says it cannot be installed on my computer.... is that the one with other languages in it?

---

### Post by Delkster on 2008-01-25
> **brokenhachi said:**
> when i went to system>admin>language support  the only language on the list is english (like the guy above said, 15 different types)

Which list? The language selector in **System > Admin** should have first a list of various languages, each with a checkbox. There you can select the languages for which you want support to be installed in the system. Look down the list for Japanese (or Esperanto). If the box next to it doesn't show a tick, click on it and then click on "**Apply**." Supply your password if necessary. Support for the language you selected should now be installed.

The drop-down menu below that allows you to choose which language should be the default one for new sessions you start. It only shows the languages that are currently installed on the system, so if it doesn't show Japanese (or Esperanto), use the other list to install your language first as described above.

Edit:
Humph... I tried it and I don't get Esperanto to appear in the default language selector either (Japanese is already there). On the other hand, right after installing support for Esperanto I got a message in the notification area saying that the system needs to be restarted for the changes to take effect. I've never seen that when installing language packs, but it might be that logging out and back in would actually help.

---

### Post by brokenhachi on 2008-01-25
> **Delkster said:**
> Which list? The language selector in **System > Admin** should have first a list of various languages, each with a checkbox. There you can select the languages for which you want support to be installed in the system. Look down the list for Japanese (or Esperanto). If the box next to it doesn't show a tick, click on it and then click on "**Apply**." Supply your password if necessary. Support for the language you selected should now be installed.

ok so the box with checks... the only thing there is english.


also would like to add, that it WAS there on the live CD... should i re-install?

---

### Post by brokenhachi on 2008-01-25
ok so i was having some problems with installing programs so i posted a new thread about that, and the fix that this guy (philinux) told me worked for the installing programs problem and for the language problem, now i have japanese on my list along with several other languages and i CAN see esperanto on my list, so why dont you give that a shot?

---

### Post by Delkster on 2008-01-26
> **brokenhachi said:**
> ok so i was having some problems with installing programs so i posted a new thread about that, and the fix that this guy (philinux) told me worked for the installing programs problem and for the language problem, now i have japanese on my list along with several other languages and i CAN see esperanto on my list, so why dont you give that a shot?

For reference, he probably means [this thread](http://ubuntuforums.org/showthread.php?t=677848).

---

### Post by brokenhachi on 2008-01-26
oops hehe looks like i forgot to link it.... thanks man.

---

### Post by bengtgunnar on 2008-02-07
> **brokenhachi said:**
> oops hehe looks like i forgot to link it.... thanks man.
Thanks, I did go to Language support and added Esperanto, it didn't help. So I removed English. Still, when I reboot there is only English. Ubuntu is supposed to be multilingual, is it not?

---

### Post by brokenhachi on 2008-02-08
did the language pack install completely during your setup? have you thought of reinstalling ubuntu..?

---

### Post by donmiguel on 2008-02-13
if you want to give it a shot by command line, try this (haven't tried myself)


```


# removes ALL language packages you have installed
sudo apt-get remove language-pack*
# install esperanto:
sudo apt-get install language-pack-eo
# language-pack-eo-base will automatically also be installed

```

if it wasn't clear to you how to do it in synaptic:

open system/administration/synaptic package manager

hit control+f and search for esperanto or just click on one element on the list and start typing "language-pack-eo" to find the esperanto packages
then click on the carré on the left and select the option that says something like: "mark for install" (marki por instalado) :)

both ways described are the ways to install/uninstall programs or program-components.

good luck!

---

