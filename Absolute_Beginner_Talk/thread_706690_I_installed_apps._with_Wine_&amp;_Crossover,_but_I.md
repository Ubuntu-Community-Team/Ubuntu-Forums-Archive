---
title: "I installed apps. with Wine &amp; Crossover, but I cannot find their icons &amp; ect."
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by ahuman on 2008-02-24
**[COLOR="Green"]I installed Apple iTunes & Quicktime (the Windows-versions) with these 2 windows-emulators: Wine & Crossover, but I cannot find the iTunes- & Quicktime-* icons* (.a.k.a. xpm-files) and the folders that contain the windows programs (a.k.a. .exe-files)**[/COLOR]

[COLOR="DarkRed"]**Question 1. Would any of you please tell me how to find all of the .exe-files on my computer when the default search tools on Ubuntu isn't showing them, and Wine & Crossover for Linux aren't inserting the programs' icons on my desktop, after I've installed them?:[/COLOR]**

[COLOR="Green"][B]I have a mini iTunes-icon on my desktop panel (the top panel), but I don't have a _full-size_ icon of iTunes on my desktop or any of the folders I've explored via the main Ubuntu search tools:

Search tool #1:Tracker Search Tool
Location:[/COLOR][/B] Applications>Accessories>Tracker Tool

[B][COLOR="Green"]Search Tool #2: Search for Files...
Location:[/COLOR][/B] Places>Search for Files...

By following these steps I *can* find the iTunes icon (and other .xpm-files) via the options that are available in the top Ubuntu desktop-panel:

1. Right-click on the iTunes icon (located in top desktop panel).
2. Click on "Properties", which makes this window appear:

[img]http://img146.imageshack.us/img146/636/screenshotlauncherpropekw3.png[/img]

3. Click on the icon shown in the top right-hand corner of the *Properties*-window, then wait until this window appears:

[img]http://img225.imageshack.us/img225/1329/screenshotbrowseicons1ty6.png[/img]

[COLOR="Green"]**Those are easy steps to follow when anyone needs to have the correct-icon for a program appear in the top desktop-panel on Ubuntu, but  I need to find & change the icons that are located in my home folders (such as my desktop folder).**[/COLOR]

**[COLOR="DarkRed"]Question 2:Would any of you please tell me how do you find the .xpm-files (icons) for programs, when they're not as easy to find as the icons for the desktop-panel?[/COLOR]**

[COLOR="Green"][B]As you may see in the following screenshot, the incorrect icons are being used for 2 iTunes programs: iTunes.exe & iTunesHelper.exe. I tried to access the "Browse Icons" window to change those icons to the icon that is used in my desktop panel, but that's not possible.

My home folders don't display the correct icons even when I follow similar steps, which I listed above to find the .xpm-files/program-icon):[/COLOR][/B]

1. Right-click on iTunes.exe (non-native icon)

[img]http://img238.imageshack.us/img238/8918/itunesexewx5.png[/img]

2. Select/Click on "Properties" in the context-menu (afterwards the following window opens):

[IMG]http://img401.imageshack.us/img401/925/screenshotitunesexepropim7.png[/IMG]

3. After I click on the icon shown in the top right-hand corner of the *Properties*-window,  the "Select Custom Icon"-window appears (as you can see in that screenshot there aren't any icons displayed in it, like there was in the window that appeared after I clicked on the iTunes-icon in the *Properties*-window, about which I mentioned at the top portion of this message):

[IMG]http://img125.imageshack.us/img125/3259/screenshotselectcustomimg6.png[/IMG]

[COLOR="DarkRed"]**Question 3 (my final question): Would any of you please give me step-by-step instructions about how to change those default icons to the correct icons, like the icons can be changed in the desktop-panel?**[/COLOR]

---

### Post by Crooksey on 2008-02-24
They will probably be found in...

```

~/.wine/C_Dirve/Program_Files/iTunes/iTunes.exe
``` or something..

```

$ sudo updatedb
$ locate *.exe
```

---

### Post by ahuman on 2008-02-24
Question 3 (my final question): > Would any of you please give me step-by-step instructions about how to change those default icons to the correct icons, like the icons can be changed in the desktop-panel?

For example: This icon is not the correct icon for iTunes:

[img]http://img238.imageshack.us/img238/8918/itunesexewx5.png[/img]

---

### Post by Crooksey on 2008-02-25
Check your other post, replies there.

Dont' make two posts, it just isnt polite.

---

