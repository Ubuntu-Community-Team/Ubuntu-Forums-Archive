---
title: "gdesklets help"
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by Lethal84 on 2006-10-20
I have installed gdesklets and I am trying to figure out the basic commands you use to open apps. I want to add firefox for an example..what is the command to open this? Any help is appreciated...

---

### Post by meng on 2006-10-20
The command is:
firefox
(or more completely, /usr/bin/firefox)

Perhaps you could explain in a little more detail what you are trying to do? Add an application/icon to a launcher bar? Or what?

---

### Post by podunk on 2006-10-20
If you installed Ubuntu, Firefox is installed by default – it should have a launcher icon (a globe) at the top of the screen on the task panel (task bar for windows users).

Finding a program can sometimes be a pain. Many programs come without an icon and menu item so it won't get put on a menu.

Most programs are installed in the directory /usr/bin you can use the file browser (Under the “Places” menu or type in nautilus in the terminal) to go there and double click.

Many programs are installed in your home folder 
/home/your_name

as .dot_files or folders. These are hidden from view, you can view them in the file bowser by clicking Edit>View>Show hidden files

---

### Post by Lethal84 on 2006-10-20
reply to meng. Yes, I am trying to add an app to the launcher bar. I want to add firefox and some other apps to the bar but I dont know what the command line should say in the launcher properties. Thanks.

---

### Post by podunk on 2006-10-21
Desktop launchers are easy.
Open Nautilus
Find the file you want to launch.
Right click the desktop and chose Create Desktop Launcher.
Use your mouse to click and drag the program to the "command" line, the path will be filled in for you.
Give it an easy to remember name and click close and your done.

To put launchers on the top bar (System Bar in Linux) you can drag a launcher to the area next to the clock. You can do the same with stuff from the Applications menu, just click and drag to the system area.

The way I find files is
```
sudo updatedb
```
then
```
locate file_name | less
```

---

### Post by Lethal84 on 2006-10-21
Thanks alot Podunk.

---

### Post by crossedout on 2006-10-21
> I have installed gdesklets and I am trying to figure out the basic commands you use to open apps. I want to add firefox for an example..what is the command to open this? Any help is appreciated...

For gdesklets launchers, follow Meng's advice by using the complete path in the 'Command' section.  In certain instances for gdesklets you may need to specify which program to call in order to set the launcher properly.
--For example, if you want to add a launcher for a specific document, you would use ooffice /path/filename.
Keep in mind gdesklets are slightly different than desktop icons so their behavior is mildly different.
--For example, changing the icon theme will not change the gdesklet launcher bar icons.  They will need to be changed manually if you want them to be different when you change icon themes.
Hope that helps.


-Xout

---

