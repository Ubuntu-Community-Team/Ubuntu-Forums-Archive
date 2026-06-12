---
title: "Kubuntu help"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by 141N on 2007-11-19
Hey all, I just upgraded to Kubuntu Gutsy after using Ubuntu since Dapper release. Anyway, theres a few things that I can't seem to get the hang of, and its beginning to get annoying because I am really liking the looks of Kubuntu.

Anyway, I setup my msn on Kopete, and I chose remember password, so it adds it into a 'KWallet'. OK, fair enough I think, and proceed to log in to Kopete, which results in a KDE Crash, and always does. So I uninstall it and go to reinstall, but cannot reinstall (the check box does not 'check' to show it is selected for installation). I checked out the Kubuntu Docs and it says to press Alt+F2 and type 'kdesu adept' to run adept as root, but this just comes back with the error "Command not found!"

Can anyone help, please?

Thanks in advance, Iain

---

### Post by disturbedite on 2007-11-19
if you're on gutsy, its kdesudo *not* kdesu.  with gutsy, kdesu was replaced with kdesudo.

---

### Post by cookies on 2007-11-19
kdesudo has a symbolic link to *kdesu* for backwards compatibility.

The command is
```
kdesu adept_manager
``` 

And there was a critical update to fix the crashing issue, have you updated?

---

### Post by 141N on 2007-11-19
thanks, I typed kdesudo adept_installer (turns out thats the command from the KMenu) but that still shows some stuff 'greyed-out' and I can't check Kopete to reinstall.

I tried KMenu > Right Click 'Add/Remove Programs' > Put Into Run Dialog > Options > Run As Different User (User: root; Password: //my password) but it still does not allow me to install any new packages.

Sorry if this seems so trivial but is really beginning to spoil Kubuntu for me with something like this =/

---

### Post by 141N on 2007-11-19
Thanks for that - you reminded me that during the install I got an alert saying that because I wasn't connected to the internet then I wasn't getting the updates and to uncomment the lines in /etc/apt/sources.list

So, I enabled everything other than the backports deb's and updated in Adept Manager, however, it keeps crashing aswell, I installed Kopete and Firefox (God knows how because they both came up saying "Could not commit to download") so I restarted and they both worked. Then I tried to open Adept Manager again same way as before and I get the same problem? What gives?

I used SuSE 10.1 for a while before going to Ubuntu Dapper and never had these issues in KDE so they're all very foreign to me =P

Any help would be appreciated - Thanks again!

---

