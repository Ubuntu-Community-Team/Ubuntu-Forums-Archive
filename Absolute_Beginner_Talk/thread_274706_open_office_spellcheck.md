---
title: "open office spellcheck"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by cmaranhao on 2006-10-10
currently i only have english spellcheck.. and i have two problems:

1)when i wrote mispelled words, and after i tried to correct the grammar errors, it said everything was ok, it did not correct the words, even with the english spell installed..what should i do?

2)how can i add a portuguese (from portugal and not brazil) spellcheck?

edit: i found this package for the PT spellcheck but it says this:

"error: conflicts with the installed package "open-office.org-core""

[http://packages.debian.org/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Fo%2Fopenoffice.org%2Fopenoffice.org-l10n-pt_2.0.4~rc3-1_all.deb&md5sum=6c147ca9c652969ee47dc1397b8be13b&arch=all&type=main](http://packages.debian.org/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Fo%2Fopenoffice.org%2Fopenoffice.org-l10n-pt_2.0.4~rc3-1_all.deb&md5sum=6c147ca9c652969ee47dc1397b8be13b&arch=all&type=main)

many thanks

---

### Post by cmaranhao on 2006-10-10
bump

---

### Post by nocturn on 2006-10-11
It does not work for me either.
Both Dutch and English.

OO on Windows (at work) works fine!

Anyone?

---

### Post by nocturn on 2006-10-11
I filed a bugreport on this: #65318

---

### Post by alecjw on 2007-07-06
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/65318](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/65318) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				You have to install myspell-YOUR_LANGUAGE eg myspell-en-gb. I don't know why it isnt installed by default, and i have commented on this in the bug report.

---

### Post by Jimmyfj on 2007-07-06
> **cmaranhao said:**
> currently i only have english spellcheck.. and i have two problems:

1)when i wrote mispelled words, and after i tried to correct the grammar errors, it said everything was ok, it did not correct the words, even with the english spell installed..what should i do?

2)how can i add a portuguese (from portugal and not brazil) spellcheck?

edit: i found this package for the PT spellcheck but it says this:

"error: conflicts with the installed package "open-office.org-core""

[http://packages.debian.org/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Fo%2Fopenoffice.org%2Fopenoffice.org-l10n-pt_2.0.4~rc3-1_all.deb&md5sum=6c147ca9c652969ee47dc1397b8be13b&arch=all&type=main](http://packages.debian.org/cgi-bin/download.pl?arch=all&file=pool%2Fmain%2Fo%2Fopenoffice.org%2Fopenoffice.org-l10n-pt_2.0.4~rc3-1_all.deb&md5sum=6c147ca9c652969ee47dc1397b8be13b&arch=all&type=main)

many thanks

Try and go to Synaptic>text editing and look for the English  language packets, mark them up and install the packets needed. 
Then startup the OpenOffice.org Writer and go to Functions/Settings/Language settings - Here you have two type of settings from which you can set both language and spelling aids.

---

### Post by tremoloqui on 2008-07-14
> **cmaranhao said:**
> 
1)when i wrote mispelled words, and after i tried to correct the grammar errors, it said everything was ok, it did not correct the words, even with the english spell installed..what should i do?


I was having issues with this and solved them by selecting the language of the document with the "Tools > Language > For All Text" menu.  In my case, I have the language set to English(Canada) in Kubuntu but the installed dictionaries are English(US) and English(UK).

This should be automatic, particularly when the dictionary and the regional language are different. (i.e. Canada uses UK english.) 

I hope this helps,

Cheers!

---

### Post by Hagar Delest on 2008-07-16
Does it help: [[Tutorial] Spell check and Language configuration](http://user.services.openoffice.org/en/forum/viewtopic.php?f=7&t=67)?

---

