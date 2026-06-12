---
title: "how to install themes"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by Dark-Angel on 2007-04-29
hi,
  I've just downloaded this but can't work out how to install it. 
[http://www.gnome-look.org/content/show.php?content=44563&forumpage=0](http://www.gnome-look.org/content/show.php?content=44563&forumpage=0)

i'm using ubuntu 6.06

---

### Post by Vic_Astro on 2007-04-29
Download Synthesis-1.1.tar.gz in ~/.themes
tar -xvvzf Synthesis-1.1.tar.gz

---

### Post by viciouslime on 2007-04-29
OR, if you prefer a gui, you can just drag and drop the file on to the themes window. System/Preferences/Theme You can also use the install theme button too. The easiest way of all, is to drag the link from the webpage to the Theme Preferences window and it will download AND install it for you. Since you have already downloaded it though, just drag the downloaded file on to the window.

---

### Post by Dark-Angel on 2007-04-29
> **viciouslime said:**
> OR, if you prefer a gui, you can just drag and drop the file on to the themes window. System/Preferences/Theme You can also use the install theme button too. The easiest way of all, is to drag the link from the webpage to the Theme Preferences window and it will download AND install it for you. Since you have already downloaded it though, just drag the downloaded file on to the window.

Thanks for that but it is saying that it is an invalid file format. Any ideas on why?

---

### Post by viciouslime on 2007-04-29
> **Dark-Angel said:**
> Thanks for that but it is saying that it is an invalid file format. Any ideas on why?

It is probably packaged in a non-standard way. Open the downloaded file and see if it contains more zip files, or tar.gz files, if so extract it to any folder temporarily, your home folder will do, then drag those files on to the themes window.

If that fails let me know and I will have a look at your link and guide you through it.

---

### Post by Dark-Angel on 2007-04-29
> **viciouslime said:**
> It is probably packaged in a non-standard way. Open the downloaded file and see if it contains more zip files, or tar.gz files, if so extract it to any folder temporarily, your home folder will do, then drag those files on to the themes window.

If that fails let me know and I will have a look at your link and guide you through it.

hey thanks for the help. I tried that and still couldn't really work it out.

---

### Post by viciouslime on 2007-04-29
Ok, double click NovumOS-Suite.tar.gz and it should open in File Roller. You should see a folder inside the archive called "NovumOS-Suite" double click it and you will see a file inside called "NovumOS-gtk2.tar.gz" select this file by click it once so it is highlighted and then press extract, choose a folder to extract it to (your home folder will do) then go to your home folder in nautilus (the ubuntu file browser) and drag the file on to the theme preferences window. Press apply new theme when it asks, et voilà.

Let me know if you get stuck with any of the steps.

---

### Post by Dark-Angel on 2007-04-29
i copied it to the home folder but i go to find theme preferences but only got desktop and examples in there.

---

### Post by viciouslime on 2007-04-29
> **Dark-Angel said:**
> i copied it to the home folder but i go to find theme preferences but only got desktop and examples in there.

You mean you can't find the theme preferences window? Click on system, then go to preferences, then click on themes near the bottom of the list. Then drag the file I told you to extract on to the window that comes up.

---

### Post by Dark-Angel on 2007-04-29
thanks for all that it is on know:)

---

### Post by viciouslime on 2007-04-29
> **Dark-Angel said:**
> thanks for all that it is on know:)

No problem. If you want to install its matching GDM theme too (that's the screen where you login) then follow the steps as before, but extract the file "NovumOS-GDM.tar.gz" and install it by going to System/Administration/Login Window and clicking add on the right hand side of the Local tab. This will present you with an open dialogue box, navigate to the "NovumOS-GDM.tar.gz" file.

---

### Post by Dark-Angel on 2007-04-29
thanks. One other thing, do you know how to change the screen  before it comes up to login screen if it's possible

---

### Post by viciouslime on 2007-04-29
> **Dark-Angel said:**
> thanks. One other thing, do you know how to change the screen  before it comes up to login screen if it's possible

It is possible, I haven't ever done it though. I believe someone has made some sort of script, or gui for doing it but I can't remember where I saw that. The bit before GDM is called usplash. So i would search for "usplash themes" or something along those lines, once you've found some they will probably contain installation instructions. :)

---

