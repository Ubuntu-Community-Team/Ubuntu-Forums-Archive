---
title: "Themes for Ubuntu"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by hackxxcrack on 2007-08-17
Hi , I Downloaded A clock theme from gnome-look.org and i dont know howto install it... could you help me? the file is *.tar.gz  

Thank you:guitar:

---

### Post by RomeReactor on 2007-08-17
Hi. Go to "System->Preferences->Theme". Then just drag and drop the tar.gz file onto it.

---

### Post by Lord Illidan on 2007-08-17
No, I think he meant the clock themes to be used with macslow's clock. Can you by any chance refer us to the URL please?

---

### Post by hackxxcrack on 2007-08-17
This is The URL:

[http://gnome-look.org/content/show.php/Ninjja-Slim-Clocks?content=64568](http://gnome-look.org/content/show.php/Ninjja-Slim-Clocks?content=64568)

Thank you

---

### Post by por100pre1 on 2007-08-17
Clock theme? It could be a cairo clock theme indeed. Extract the files and save the new folder in the /home/*your-user-name*/.cairo-clock/themes folder. Hope this helps. :)

EDIT: Yes, it is a Cairo Clock theme...

---

### Post by hackxxcrack on 2007-08-17
> **por100pre1 said:**
> Clock theme? It could be a cairo clock theme indeed. Extract the files and save the new folder in the /home/*your-user-name*/.cairo-clock/themes folder. Hope this helps. :)

EDIT: Yes, it is a Cairo Clock theme...

Mmm.. But i dunno have the folder, i think i have to install someting else, isnt it?

---

### Post by por100pre1 on 2007-08-17
> **hackxxcrack said:**
> Mmm.. But i dunno have the folder, i think i have to install someting else, isnt it?

Right click it to extract it. A new folder will appear. Let me know if it works or not.

---

### Post by Lord Illidan on 2007-08-17
Yes, you need to install Cairo Clock itself, the main program. Here is the website.

[http://macslow.thepimp.net/?page_id=23](http://macslow.thepimp.net/?page_id=23)

Here is a direct link to the deb.. [http://macslow.thepimp.net/projects/cairo-clock/cairo-clock_0.3.2-1_i386.deb](http://macslow.thepimp.net/projects/cairo-clock/cairo-clock_0.3.2-1_i386.deb)

It is further down the page. It is marked Ubuntu Dapper, but don't worry bout that.

---

### Post by RomeReactor on 2007-08-17
> **Lord Illidan said:**
> No, I think he meant the clock themes to be used with macslow's clock. Can you by any chance refer us to the URL please?

hrmmm... I should have read more carefully before hitting that reply button.

> **hackxxcrack said:**
> Mmm.. But i dunno have the folder, i think i have to install someting else, isnt it?

You need to have the cairo-clock. If you have it already, the folder **por100pre1** mentions is hidden in your home directory--all files and folders whose name starts with a dot are hidden. To view them in Nautilus, press CTRL+H; do the same to hide them again.

If you don't have cairo-clock installed:
```
sudo apt-get install cairo-clock
```

Maybe I'm being overly obvious here, but please note that the theme you downloaded is for a clock applet, not for your desktop.

---

### Post by por100pre1 on 2007-08-17
Put the downloaded file in your desktop and do this in a terminal window;

```
cd Desktop
```

```
tar -xvzf 64568-Ninjja-Slim-Clocks.tar.gz
```

Four folders will appear. Drag them to your the /home/your-user-name/.cairo-clock/themes folder.

---

### Post by hackxxcrack on 2007-08-17
Ok thank you all , i installed all things! 

:guitar:

---

### Post by por100pre1 on 2007-08-17
> **hackxxcrack said:**
> Ok thank you all , i installed all things! 

:guitar:

Glad to help, that theme is really nice looking. Enjoy!
:popcorn:

---

