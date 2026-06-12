---
title: "Installing Firefox Beta"
date: 2005-10-11
forum: Absolute Beginner Talk
---

### Post by Souljah on 2005-10-11
Yet another noob question, I did a search for it but it seem to bring up specific applications. Anyhow, I just downloaded the latest firefox 1.5 beta 2 download. The extension is tar.gz. Now, how do I install this and get this to work? I want it to update the original firefox that comes with ubuntu?

On a sidenote, where is the options menu in the firefox 1.0.6 that comes with ubuntu 5.10 preview release :???: 

Ryan

---

### Post by bdash on 2005-10-11
Hello.

When you launch the application installer, you have only applications that were selected by Ubuntu. Usually the most complete and popular application of each category.

If you want to choose from more applications, you can click on "advanced". This will be a little more complicated since you will see not applications but packages. Some of them are applications, others are just libraries (needed by applications).

About Firefox: Firefox 1.5 is still beta, thus not included in Ubuntu. If you want to install it anyway, then you are on your own. It will be installed independently of Ubuntu. If you are not very comfortable with manual installation, you should wait for the final version, and for a version in Ubuntu repository.

Anyway, if you are courageous:
```

tar -xzvf firefox-1.5b2.tar.gz
cd firefox
./run-mozilla

```

Or something like that. Be aware that you Firefox 1.0.7 profile may be broken then.

---

### Post by aysiu on 2005-10-11
You won't find Firefox Beta 1.5 in very many repositories. If you download the .tar.gz, all you have to do is [extract it](http://photobucket.com/albums/b337/psychocats/?action=view&current=b1485c53.png) and [double-click on firefox-installer](http://photobucket.com/albums/b337/psychocats/?action=view&current=a207e708.png) or firefox (depending on which version of the .tar.gz you get). That's it.

Oh, and the preferences are under Edit instead of Tools.

---

### Post by Souljah on 2005-10-11
[QUOTE=bdash]Hello.

When you launch the application installer, you have only applications that were selected by Ubuntu. Usually the most complete and popular application of each category.

If you want to choose from more applications, you can click on "advanced". This will be a little more complicated since you will see not applications but packages. Some of them are applications, others are just libraries (needed by applications).

About Firefox: Firefox 1.5 is still beta, thus not included in Ubuntu. If you want to install it anyway, then you are on your own. It will be installed independently of Ubuntu. If you are not very comfortable with manual installation, you should wait for the final version, and for a version in Ubuntu repository.

Anyway, if you are courageous:
```

tar -xzvf firefox-1.5b2.tar.gz
cd firefox
./run-mozilla

```

Or something like that. Be aware that you Firefox 1.0.7 profile may be broken then.[/QUOTE]

Where do you go to run those commands and what do those commands do?

In response to ayslu: When I double click on firefor it tells me it's an executable. It tells me to run, run in terminal, display, or cancel. When I do either run or run in terminal, nothing happens. It doesn't update, doesn't do anything. What am I doing wrong?

---

### Post by aysiu on 2005-10-11
[QUOTE=Souljah]
In response to ayslu: When I double click on firefor it tells me it's an executable. It tells me to run, run in terminal, display, or cancel. When I do either run or run in terminal, nothing happens. It doesn't update, doesn't do anything. What am I doing wrong?[/QUOTE] Did you extract the .tar.gz first, or just open it? After you open it, there should be an extract button. In Gnome, it's a big button that says "Extract." In KDE, it's a small purple arrow that points up.

After you extract it, there should be a regular folder (not a .tar.gz) somewhere. Mozilla distributes two versions of Firefox--one with an installer, one without. If yours has a file called *firefox-installer*, click on the file called *firefox-installer*. If not, click on the file called *firefox* (not to be confused with the file called *firefox-bin*.

The links in my last post were to screenshots, so you can see what to do--this can all be done graphically. You don't have to type in any commands.

---

### Post by Souljah on 2005-10-11
[QUOTE=aysiu]Did you extract the .tar.gz first, or just open it? After you open it, there should be an extract button. In Gnome, it's a big button that says "Extract." In KDE, it's a small purple arrow that points up.

After you extract it, there should be a regular folder (not a .tar.gz) somewhere. Mozilla distributes two versions of Firefox--one with an installer, one without. If yours has a file called *firefox-installer*, click on the file called *firefox-installer*. If not, click on the file called *firefox* (not to be confused with the file called *firefox-bin*.

The links in my last post were to screenshots, so you can see what to do--this can all be done graphically. You don't have to type in any commands.[/QUOTE]

I extracted it, onto the desktop. When I open the folder, I see some folders, files and so forth. I do see a file called "firefox" but when I click on it, like I said, those are the commands I get. I'll show you screenshots to these commands.

Here they are:

[[IMG]http://img413.imageshack.us/img413/7189/screenshot3yu.th.png[/IMG]](http://img413.imageshack.us/my.php?image=screenshot3yu.png)

[[IMG]http://img435.imageshack.us/img435/9485/screenshotrunordisplay1bb.png[/IMG]](http://imageshack.us)

---

### Post by aysiu on 2005-10-11
[QUOTE=Souljah]I do see a file called "firefox" but when I click on it, like I said, those are the commands I get. I'll show you screenshots to these commands.[/quote] Yes, please show the screenshot for the **Run** choice.

---

### Post by Souljah on 2005-10-11
Actually in my last post, those 2 were the only screenshots that came up. After I clicked on "Run", nothing happened so therefore I can't really show a screenshot.

But I HAVE A MAJOR problem now. I just rebooted and now I don't see my windows xp there. It's not there when I go to my boot menu in ubuntu. Omgosh I didn't delete it did I? I know when I was installing linux, I used two partitions and both were totalled to 10 gigabytes.

EDIT: Windows XP was there, but I don't know what I did, I guess I might have made a kernel change and now windows is not displaying anymore. Is there a system restore function on ubuntu like there is in windows xp?

---

### Post by Feirax on 2005-10-22
[QUOTE=Souljah]Actually in my last post, those 2 were the only screenshots that came up. After I clicked on "Run", nothing happened so therefore I can't really show a screenshot.

But I HAVE A MAJOR problem now. I just rebooted and now I don't see my windows xp there. It's not there when I go to my boot menu in ubuntu. Omgosh I didn't delete it did I? I know when I was installing linux, I used two partitions and both were totalled to 10 gigabytes.

EDIT: Windows XP was there, but I don't know what I did, I guess I might have made a kernel change and now windows is not displaying anymore. Is there a system restore function on ubuntu like there is in windows xp?[/QUOTE]

I had the same thing happened to me after I agreed to update my kernel.   What I did to fix it was modify the menu by 
```
sudo gedit  /boot/grub/menu.lst 
``` then look for ```
### BEGIN AUTOMAGIC KERNELS LIST
``` before that line add 

```

title		Windows XP
root		(hd0,0)
makeactive
chainloader	+1

```

You may have to modify the root (hd0,0) to indicate which drive and partition your windows is on.   I believe it's hd0->primary master, hd1->primary slave, hd2, secondary master, etc.  And for partitions, the first partition starts at 0.

Btw, I'm a noob so this may not be the ideal approach, but it's worked for me. :)

---

