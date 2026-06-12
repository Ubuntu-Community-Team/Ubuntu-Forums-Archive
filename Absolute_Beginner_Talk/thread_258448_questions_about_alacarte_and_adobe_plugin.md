---
title: "questions about alacarte and adobe plugin"
date: 2006-09-15
forum: Absolute Beginner Talk
---

### Post by frprinterwiz on 2006-09-15
have two things I would like to know about, get some assistance with.

A) Can I use a terminal command or another utility to remove access to the Alacarte menu editor without undoing the changes it has made? Or password protect that utility? It's pointless to remove access to certain programs for a user if they can just go back in and turn them on again.

B) Adobe plugin for firefox - can open pdf files under my user account but in the guest account it forces you to save them and then open them. In the install directory I do not have the browser plug-in directory. I've tried reinstalling the adobe pdf app but no luck (just wound up with multiple instances of adobe in the office menu and still no browser plug-in directory). I tried the Package Manager install and a manual install of  the the gz.tar files. On my usr account the gz.tar files worked fine. Is there a way to get the plug-in to work using the files from my usr directory?

TIA

Frprinterwiz

---

### Post by oedipuss on 2006-09-16
About A, you could remove the menu entry of Alacarte from alacarte itself, If that's what you're looking for. A user would still be able to run it from a terminal though, but it wouldn't be as readily available. 


The plugins for firefox are located either in /home/username/.mozilla/plugins or in /usr/lib/mozilla/plugins (or /usr/lib/mozilla-firefox/plugins, I'm not sure which of the last two takes precedence) . Having a plugin in your home folder means that only you can use it. Try installing it in usr, and removing the home plugin files to see if the ones in usr work (don't delete them ofcourse, just rename the directory :D) Other than that I'm not sure.

---

### Post by frprinterwiz on 2006-09-17
Doh - I missed the entry for alacarte itself LOL, my bad

Will give the plug in idea a whirl when I get the chance.  Somehow I don't think it's going to be an issue as Jr was not happy with the new way of accessing the internet.  He's going to be even more pissed when he sees all of the music he dl'd is gone too LOL

---

