---
title: "[SOLVED] gedit highlight mode grayed out"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by LRT on 2008-01-28
For some strange reason when I open Gedit, click on 'View', the 'Highlight Mode' option is grayed out. 

If I go to 'Edit'->'Preferences'->'Fonts&Colors', I can choose a color scheme but it does not display proper syntax highlighting.

How can I get this to work???

---

### Post by seventhc on 2008-01-28
The syntax should show if you have saved a file with a file extension that would enable it. Not the best explanation but lets say I am writing a python script, I would save the file as name.py the py extension will then have gedit highlight the syntax. If you open the source code of an html document, that too would be highlighted.

---

### Post by LRT on 2008-01-28
it doesn't matter what kind of file i have open (.html, .rthml, .py, .pl, .rb), highlight mode is always grayed out.

---

### Post by seventhc on 2008-01-28
That is strange, I tried unchecking all of my options, I still have highlight mode. What version are you using? I have gedit 2.20.3, have you installed any plugins??
AFAIK gedit has highlight mode out of the box.

---

### Post by LRT on 2008-01-28
i agree it is strange. i have gedit 2.20.3 also. the only thing i have installed when looking at synaptic manager is gedit and gedit-common. i've tried uninstalling and then reinstalling but still same problem. ... just curious though... do you have /usr/share/gtksourceview1.0/ or /usr/share/gtksourceview2.0/ or both ... i have both. 2.0 has the language specs and styles folder, but 1.0 only has the language-specs folder... could this be a problem??? (thanks for you quick replies)

---

### Post by seventhc on 2008-01-28
I took a look and I too have both, I honestly don't know what would stop syntax highlighting from working. I tried to make mine not work and it still works. :confused:
I literally unchecked everything in preference, including every plugin and i still have it. try this
open gedit then type paste this in
```
print 'this is a test'
```
then click on file, save as and save it as test.py
once you save it, it should show with highlighted syntax.

---

### Post by LRT on 2008-01-28
strange... i found this file.. /home/leandro/.gconf/apps/gedit-2/preferences/syntax_highlighting/%gconf.xml

```
<?xml version="1.0"?>
<gconf>
        <entry name="enable" mtime="1190647606" type="bool" value="false">
        </entry>
</gconf>

```

what does yours say?

---

### Post by LRT on 2008-01-28
ok found out something real strange... 

if i fire up gedit from the gnome panel... i don't get the syntax highlighting...

if i fire up gedit from /usr/bin/gedit... i DO get the syntax highlighting!! (so when i tried your test it did work!).

so the gnome panel must be pointing to a different gedit???? any ideas??

---

### Post by seventhc on 2008-01-28
I don't even have a syntax_highlighting folder there

/home/j0hn/.gconf/apps/gedit-2/preferences in that folder I have 2 folders, one called editor and one called ui I looked in both, nothing. I do have different gconf.xml files in the different folders but all are blank. 0bytes
Maybe create a folder and place your syntax_highlighting folder in it to break the path (or just rename it) and see if that fixes the highlighting issue. at most you can always put it back,

---

### Post by emarkd on 2008-01-28
I've got no syntax_highlighting directory either, but my syntax highlighting works fine.

I don't know how to solve this, but having that file doesn't make it work.

---

### Post by seventhc on 2008-01-28
There is a way to make a symbolic link to make it point to the working one, here is a link
[http://ubuntuforums.org/showthread.php?t=255573](http://ubuntuforums.org/showthread.php?t=255573)

---

### Post by seventhc on 2008-01-28
oh wait, you can right click on gedit from the panel, choose properties and enter this into the command line
/usr/bin/gedit

---

### Post by LRT on 2008-01-28
none of your solutions worked and i think i know why... i don't think gedit was installed properly (perhaps installed as root)... and so i believe there is a permissions problem... when i run gedit as a normal user (/usr/bin/gedit ) i don't get the syntax highlighting.. when i run gedit as root i DO get the syntax highlighting... which leads me to think that syntax highlighting has only superuser permissions somewhere in the gedit program files...

---

### Post by seventhc on 2008-01-28
That's a new one to me, gedit is installed by default when you install the system...did you change permissions on it?

---

### Post by LRT on 2008-01-28
it was installed by default but if my memory serves me correct i believe i was trying to manually upgrade because the ubuntu repo was outdated. this was a while ago so i don't remember to well.. i'm going to manually remove all gedit files and reinstall ... i'll let you know what happens...

---

### Post by LRT on 2008-01-28
success!!!

manually uninstalled everything and installed the package again from synaptic... everything looks good.. thanks for everyone's help.

---

### Post by seventhc on 2008-01-28
Glad you got it working, :)  I am curious what caused that, but I guess it doesn't matter now that it works. :)

---

