---
title: "superkaramba  anyone"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by HdK on 2006-09-01
I have downloaded superkaramba I have no idea how to install  please help!

---

### Post by andlinux21 on 2006-09-01
I take it you are using kubuntu?  Can you give us a little info about what your running?

---

### Post by msak007 on 2006-09-01
If by "download" you mean you downloaded a file from a web site, there's no reason to - superkaramba is in the repositories. Open Konsole and type
```
sudo aptitude install superkaramba
```
Once you do, superkaramba should show up in your KMenu under the "Utilities" submenu. Installing themes is a simple as launching superkaramba, downloading the theme file (usually in a .skz compressed format), clicking on "Open Local Theme" and pointing it to the file you just downloaded. Alternatively, superakaramba also has a "Get New Stuff" button which will show you the most popular / most downloaded themes from KDE-Look.org and let you install them with one click.

---

### Post by HdK on 2006-09-02
Thanks alot that worked

---

### Post by HdK on 2006-09-02
Hey, when i install the apps , and then try to open them, where do they install by default I cant find them on my system

---

### Post by jordanmthomas on 2006-09-02
Usually, you can find programs in   /usr/bin

To run one, you can press Alt + F2 and then type it.   eg.  superkaramba

If you are on a command line, you can type the first couple of letters and then press tab to see all possibilities.

Oh, and sometimes they will be in your applications menu.

---

### Post by HdK on 2006-09-02
OK im trying to run DI-Radio-Calendar and I cant reinstall using the supperkaramba prog once it has been installed, It is not in the usr/bin file is the any commands that i can run in a terminal to get it to run

---

### Post by msak007 on 2006-09-02
superkaramba is the app that runs the plugins, such as [DI-Radio-Calendar]("http://www.kde-look.org/content/show.php?content=43754"). Once it's installed you use it to install the themes / add-ons. KDE-Look.org has [install instructions]("http://www.kde-look.org/help/index.php?type=38") for the theme. Basically once superkaramba is started, if you don't see it right away the icon for it should be in your System Tray by the clock. Download the theme if you haven't done so already, extract it to a folder (~/.superkaramba is the ideal location), click on the superkaramba System Tray icon once to open it back up, click on "Open Local Theme", then point it to the folder where you just extracted the theme. You should see a file called "di-radio.theme" - once you've chosen this file, the theme will load on your Desktop. Normally superkaramba themes are in a format of "<filename>.skz, and all you have to do is download the file and open the .skz file.

---

### Post by HdK on 2006-09-02
Ok I downloaded the dj program to my desktop , I am having a hard time unzipping the files when I double click on icon it asks me which program to open up with. How do I extract in into a different folder

---

