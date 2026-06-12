---
title: "[SOLVED] Applications not listed in Menu ??"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by chrome307 on 2007-08-21
I can running WNE and am able to use my Newsgroup Reader.

However I can't find a shortcut for this in the Application Menu.

I do see WINE but under the application ' Grabit' - there is only an Uninstall and Read Me text file.

The only way I seem to be able to run this app, is if I reinstall each time as I cannot find it on my PC.

There's most probably a simple explanation to this :)

Your help would be appreciated

---

### Post by WebSiteGuru on 2007-08-21
Isnt it in the /home/username/.wine folder? and where ever you install it.. You might have to run it manually. from that folder or create a shortcut.

---

### Post by chrome307 on 2007-08-21
This sounds very pathetic on my part, but I can seem to find the WINE folder :(

---

### Post by wolfen69 on 2007-08-21
to add things to menu: go to system>preferences>main menu

---

### Post by WanderingKnight on 2007-08-21
Go to your home folder and press Ctrl+H. Scroll down until you find the .wine folder. After that it's just drive_c/*windows disk*.

To run via terminal:

```
cd ~/.wine/drive_c

/*Navigate till the folder where the application is located*/

wine application-executable.exe
```

---

### Post by WebSiteGuru on 2007-08-21
> **chrome307 said:**
> This sounds very pathetic on my part, but I can seem to find the WINE folder :(

.wine folder is a hidden folder you will have to unhidden all hidden file to see it.

---

### Post by chrome307 on 2007-08-21
Thank you both for your patience, I have located the folder now and have created a shortcut on my desktop to see if it's working

[IMG]http://1pix.org/out.php/i1919_Screenshot.png[/IMG]

---

