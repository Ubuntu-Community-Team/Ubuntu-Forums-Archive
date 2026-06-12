---
title: "Language selector"
date: 2005-09-28
forum: Absolute Beginner Talk
---

### Post by The Hedgehog on 2005-09-28
How can I add extra languages?
I now have Dutch installed(my choice during the installation), it also automatically installed English. But now I want to add 1 more.
I have used Synaptic to download all the necessary language packages.
And when I open my language selector the language is checked in the " languages available to people using this system" 
But at the log in screen, the new language doesn't show up in the language menu. I can only choose between the different variants of Dutch and English.

---

### Post by Wolki on 2005-09-28
[QUOTE=The Hedgehog]How can I add extra languages?[/QUOTE]

I'm soory, I don't know for Hoary. But there is a language adding gui tool in Breezy. :)

---

### Post by The Hedgehog on 2005-09-29
I have Breezy

---

### Post by Wolki on 2005-09-29
[QUOTE=The Hedgehog]I have Breezy[/QUOTE]

Hmm, installing languages with that worked for me... Maybe it's a bug, I sometimes gat strange localisation things on Breezy. You might want to file a bug though.

---

### Post by adrian440 on 2005-09-29
Open a terminal and type:
sudo dpkg-reconfigure locales

Pick some languages, when there are multiple choices, pick the ones with utf8 at the end. Reboot, and they should appear as language choices in the login. For firefox/openoffice, you'll probably need to get the official language packs, they can be found in the synaptic package manager.

---

### Post by The Hedgehog on 2005-09-29
The problem is solved when I reboot.
Thank you very much.

---

### Post by mcclane on 2005-10-13
Whats the language selector tool called in synaptic ? 

actually what r all the new tools called ? They don't install automatically from a dist upgrade.

---

### Post by Wolki on 2005-10-13
[QUOTE=mcclane]
actually what r all the new tools called ? They don't install automatically from a dist upgrade.[/QUOTE]

Always install ubuntu-desktop again (if you removed it) when upgrading  from one ubuntu release to the next. It makes sure all new things ubuntu installs by default are included in a dist-upgrade.

You can remove it again afterwards.

---

