---
title: "installed wine via automatix, now where is it???"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by bishop9226 on 2007-05-29
i installed it via automatix, it brought up the tabs and everything to configure it so i clicked OK.  now i remember someone saying once they did that they could right click on EXE files and do "open with" wine, but wine isnt listed there and it didnt even put it under my "applications" like it should have.  what is wrong here?  like, how am i supposed to open up wine to configure it if it doesnt make an icon?  how do i get it to show up as an app so i can right click things and go "open with wine"


thanks

quick addendum

using latest version, 0.9.37, and i can get the config window up by going to terminal and typing "winecfg" 

but i want to know why it didnt add itself under "applications" like it does for everyone else and why i cant right click on exe files and do "open with wine"

---

### Post by bodhi.zazen on 2007-05-29
Log out and back in

Otherwise, I use wine from the command line

```
wine /path/to/program.exe
```It is not soo bad, use tab completion

Your path is likey ~/.wine/c/Program\ Files/Program.exe

Once the program is running from the command line I add a launcher.

---

### Post by bishop9226 on 2007-05-29
ok i logged out, did ctrl+alt + backspace and then logged back in.  STILL NO WINE! so now what

i want to be able to do what this guy did

> "It was very easy to make it work. Actually i didn't do anything

I don't know if this is the bet way to do this, but i tell you what i did.

I installed wine using Automatix, so maybe that's the right path.

Then i went in my windows partition with Krusader (a file manager), right clicked on uTorrent, which was alredy installed in my windows xp, and selected Wine in the "open with..." menu.

That's it. It simply worked. "



i installed wine the same way yet i didnt get a menu thing or any option to use it with "open with"

i just want to use photoshop in peace.  i copied my adobe folder to /.wine/drive_c/program files/adobe/

so now i have the exe in there but when i click on it it says

> Cannot open /home/art/.wine/drive_c/Prog...e Photoshop CS2/Photoshop.exe: No application suitable for automatic installation is available for handling this kind of file.

so i know i need to open it WITH wine but how do i do that???

---

### Post by Ek0nomik on 2007-05-29
You have to install programs with wine too, I don't think you can simply copy a directory over.

Do you have an executable file for installing Photoshop?

---

### Post by bishop9226 on 2007-05-29
apparently the guy above me didnt install anything to use utorrent, though that doesnt have an install, just an executable so you may be right.  but why is it that i installed wine and it isnt on my apps or anything but it was for that guy?  that discrepancy is making me mad.

---

### Post by hasimir44 on 2007-05-29
are you sure that wine was actually installed? 

if so, then this should give you the path to wine: 

```
which wine
```

the last time I used wine, I just double clicked on an exe (scite.exe) on my usb stick and wine popped up like a wrapper and ran it. I didn't need to install the exe from wine...

---

### Post by bishop9226 on 2007-05-29
yes i have an executable install, but i cant open any .exe's even though i installed wine already.  i just get the same message i pasted above.

> Cannot open /media/sda1/utorrent.exe: No application suitable for automatic installation is available for handling this kind of file.

howcome i cant open them with wine? and what is the point of the wine "applications" tab, all you can do is add exe files but it doesnt seem to do anything.

---

### Post by bishop9226 on 2007-05-29
> **hasimir44 said:**
> are you sure that wine was actually installed? 

if so, then this should give you the path to wine: 

```
which wine
```

the last time I used wine, I just double clicked on an exe (scite.exe) on my usb stick and wine popped up like a wrapper and ran it. I didn't need to install the exe from wine...

i was going to try and uninstall then reinstall, but it says its there.

art@art-desktop:~$ which wine
/usr/bin/wine
art@art-desktop:~$

---

### Post by bishop9226 on 2007-05-29
k i just uninstalled wine via automatix and downloaded it following winehq.com's instructions and synaptic, SAME THING.  :(

---

### Post by bodhi.zazen on 2007-05-29
LOL

Wine is a complex program.

utorrent is a simple program and works in wine out of the box. utorrent is distributed as an executable file and does not need to be installed in windows or wine.

utorrent != Photoshop

Photoshop is a complex program.

Start with : [http://blog.publicidadpixelada.com/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps/](http://blog.publicidadpixelada.com/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps/)

Here : [http://doc.gwos.org/index.php/HowToWine](http://doc.gwos.org/index.php/HowToWine)

And here : [http://appdb.winehq.org/appview.php?iAppId=17](http://appdb.winehq.org/appview.php?iAppId=17)

And for your menu :

Right click on the file and choose Properties from the menu that appears. The Properties dialog opens.

Click on the Open With tab. A list of applications appears.

Select the default application you want for the file type. If wine is not on the list, use the Add button to add wine to the list.

---

### Post by TravMan63 on 2007-06-12
In Xubuntu 7.04 - I've noticed I need to use wine file to install programs.
I've installed MS Office 2003 and win media player 6.x

Shortcuts/launchers were placed in my 'other' sub menu - they launch from there fine.
WMP placed a launcher/.lnk on my desktop

Otherwise "wine ...path to exe" works...

TM

---

