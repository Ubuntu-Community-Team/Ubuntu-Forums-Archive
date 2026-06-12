---
title: "After installing a application from a .deb file, where does the application go?"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by ahuman on 2008-02-21
[B][COLOR="SeaGreen"]If you downloaded a program like [Mercury Messenger for Ubuntu](http://thebachman.info/images/stories/Mercury/Versions/mercury-messenger-1.9.deb): (which needs to be extracted from a .deb file), how would you launch it, or get that program to drop it's icon on your desktop, as programs tend to do for users on Windows & Mac?

When I download applications from .deb files, I don't know where to find them on my computer. It seems to be hidden. After I downloaded  & installed Mercury messenger, I looked for it with the Ubuntu Search-engine, but I couldn't find the actual application on my computer.

It's in my Synaptic Package Manager (System>Administrator>Synaptic Package Manager), as you can see:[/COLOR][/B]

[img]http://img50.imageshack.us/img50/7562/screenshotsynapticpackalk9.png[/img]

**[COLOR="SeaGreen"]But the actual program icon & application doesn't appear when I look for it via the Ubuntu search-engine; *here's a shot of it*:[/COLOR]**

[img]http://img141.imageshack.us/img141/563/screenshot2filesfoundselq2.png[/img]

---

### Post by ubuntu27 on 2008-02-21
Always try to get the software from the repositories using Synaptic Package Manager. If the software you desire is not in the repository, then get it from it's official website (unless you trust its source). Its a common security practice ;)

[Mercury Messenger's HomePage]("http://www.mercury.im/")

All the programs executable are usually places in a directory with the name "bin"

Open Synaptic Package Manager, search for mercury.
When you found the package, click on Properties.
Now lick on "Installed Files"

See what files that packaged installed. Try to look for any name with "bin"

Also see this How-to.  I just installed an package, [Where did my program go?]("http://monkeyblog.org/ubuntu/installing/#where_did_it_go")

---

### Post by hyper_ch on 2008-02-21
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

If it is a gui based messenger then you should have an entry in the internet section. If not, you need to call it from the command line (probably mercury-messenger).

The search can't find it as it is not indexed yet. You have basically two search options:

locate (slocate database) --> this one indexes and stores the found files. It is quicker - if the stuff is indexed

find --> this one will do an active search on the system. It offers a lot more options than locate

I assume the search engine in ubuntu uses the slocate database. you can manually update the index by running:
```

sudo updatedb

```

---

### Post by ahuman on 2008-02-21
[COLOR="Magenta"][COLOR="Magenta"]Thanks for helping me, again. Would you or anyone else please tell me how I could get a program's icon (such as Mercury messenger's icon) to appear on my top panel (in Ubuntu 7.10)?[/COLOR][/COLOR]

---

### Post by hyper_ch on 2008-02-21
it is not in any of the menu categories?

---

### Post by kathryn on 2008-02-21
If the program has been added to the Applications drop-down menu somewhere (e.g. in "Internet"), you can drag and drop the desired program to the panel (the mouse pointer should include a plus sign with the icon of the program).

Otherwise...

Right-click with your mouse on the panel that you want to add a launcher/icon to.

Choose "Add to panel..."

Find the button (near the top of the subsequent window that appears) that says "Custom Application Launcher".  This opens another window.

Name field: Type in the desired name/title of the icon
Command field: Type in the path/location of the file you want to launch (assuming you know it)
Comment field: Optional, you can type in a description.

Click the icon at the top left of the window to choose another icon.

Hope that helps.

---

### Post by ahuman on 2008-02-21
> **hyper_ch said:**
> it is not in any of the menu categories?
[COLOR="DarkRed"]No. Is there a way for me to put that application's icon in the menu-categories, which you mentioned?[/COLOR]
> **kathryn said:**
> If the program has been added to the Applications drop-down menu somewhere (e.g. in "Internet"), you can drag and drop the desired program to the panel (the mouse pointer should include a plus sign with the icon of the program).

Otherwise...

Right-click with your mouse on the panel that you want to add a launcher/icon to.

Choose "Add to panel..."

Find the button (near the top of the subsequent window that appears) that says "Custom Application Launcher".  This opens another window.

Name field: Type in the desired name/title of the icon
Command field: Type in the path/location of the file you want to launch (assuming you know it)
Comment field: Optional, you can type in a description.

Click the icon at the top left of the window to choose another icon.

Hope that helps.
**[COLOR="Magenta"]Thanks for helping me. I appreciate your kindness & patience. Do you or anyone else know where most application-icons can be found in Ubuntu 7,10?**[/COLOR]

---

### Post by FrozenFox on 2008-02-21
Most well-made debs should put the file into a category in your start menu, like those from official ubuntu sources. It is best to use synaptic to install everything possible, because it is from a trusted source and pretty much always installs start menu entires for programs with a GUI that are meant to be run (obviously, there won't be entries for drivers, decorative stuff, etc). For those that don't, you can open the .deb (the program that opens the deb to show you info about it and allow you to install it upon double click is called GDebi) and look under the tab 'installed files' and see exactly what that .deb uses and/or installs. You are typically looking for the entry that says the location of your program, which is usually in the folder /usr/bin (user binaries) or occasionally /usr/sbin (super user binaries?).. it will have the name right after, and tell you exactly the name and location of your file.

For instance, I'd look for something along the lines of /usr/bin/mercurymsgr .. On your file, i scrolled down the 'installed files' list and found the last entry to be /usr/bin/mercury, which is clearly what we want, the user binary (program) called mercury. Thus, you can now open your menu editor (i think the command is alacarte on gnome. its probably in the place one of the users above said) and go to new item, give it a name and an icon and description and the command will be /usr/bin/mercury. If the box for it is checked, it will then be in your start menu. You should then be able to add it to your taskbar panel by right click --> add applet or whatnot as described by the others.

---

