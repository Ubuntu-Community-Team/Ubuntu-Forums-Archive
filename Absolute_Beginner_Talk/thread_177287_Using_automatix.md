---
title: "Using automatix"
date: 2006-05-16
forum: Absolute Beginner Talk
---

### Post by keheikev on 2006-05-16
I used automatix to install thunderbird 1.5 now it has at the header just mail/news not thunderbird or in the help does not open when I click on the menu bar for the application I did it this way  as the previous version that you may install with synaptic has the flaw at least when I downloaded it of not opening links in a browser when clicked in a message.
 I manually edited the prefs.js file and that had no effect but I got impatient and did not add a user.js file in the mozilla folder. How do I install a correct version of 1.5 thunderbird at their website for mozilla they just say extract the archive and type thunderbird at the console.  :-? 
Keheikev

---

### Post by keheikev on 2006-05-16
Btw the help menu doesnt work and just like before...I tried to find an extension called about:config but that didnt turn up for linux versions of thunderbird. I really wih I knew what was wrong with the correct display and not being able to click on links  to  open browser windows.
Kevin:)

---

### Post by mostwanted on 2006-05-16
If you're just a single user:

1) Download archive from mozilla.org
2) Unextract somewhere in your home folder
3) There should be a file called thunderbird (or similar) - this is the executable and you can run Thunderbird by clicking on it (you might need to set permissions to "executable"; right-click, properties).

Remove Thunderbird using Synaptic and type this into the terminal (don't press enter and remember the space after /usr/bin/thunderbird):
```

sudo ln -s /usr/bin/thunderbird 
```

Then drag and drop the executable into the terminal and press enter. This creates a symbolic link (a shortcut in the directory where all the Ubuntu commands reside) to your executable. Now Thunderbird should run with the command "thunderbird". You can make launchers and menu entries that link to this command if you'd like.

The easier way:

1) Upgrade to Dapper :)
```

gksudo "update-manager -d"
```

warning: upgrades your entire operating system.

---

