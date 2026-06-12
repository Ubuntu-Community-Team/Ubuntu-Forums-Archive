---
title: "Flash plugin for Opera"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by futureal2032 on 2007-05-21
hey i am using Opera on my Ubuntu..
when i start opera ...a window pops up saying i need to install latest flash plugin..
when i click "ok" it takes me to a page for downloading the flash plugin...
the page lets me select my Ubuntu version for the plugin download..
the plugin is for mozilla/firefox..
and good detailed instructions have been given on what to do after download..
it says that the plugin installs in ./Mozilla folder in my /home directory ..so i ahve to point my Opra plugin destination path to ./Mozilla directory to the plugin file.

so far so fine...
i downloaded the file... followed the instructions..started the installation... it asks me "if i want to install. yes/no" option..i said yes..then a msg came ""installation comlete"
then i started Opera.. and went to preferences and plugins folder..and tried to give it the path as stated above.Problem is i dont have any ./Mozilla directory in my home folder... i browsed everything..and could not find it...so could not find the plugin...

can anyone help me out here... where does the plugin go if it installed but there is no default ./mozilla directory created?

---

### Post by Obor on 2007-05-21
This is what I have in plugin path in Opera:
```
/usr/lib/opera/plugins:/usr/lib/flashplugin-nonfree:/usr/lib/mozilla/plugins:/usr/lib/firefox/plugins:/usr/lib/netscape/plugins-libc6
```

It looks like the flash is pointing to /usr/lib/flashplugin-nonfree
at least on my install. Hope it helps

Edit:
If it doesn't work you could also try
/usr/lib/firefox/plugins
or
/usr/lib/mozilla/plugins

---

### Post by futureal2032 on 2007-05-21
thanx ... when i manually typed the possible plugins folder paths...it worked...

thanx

---

