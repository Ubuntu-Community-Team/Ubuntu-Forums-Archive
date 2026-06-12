---
title: "default icons"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by manutdfan2850 on 2007-01-03
hi,

in ubuntu dapper, the icons for multimedia files and pdf files, etc all show a preview for that document and are quite large. I want to either turn that feature off and/or shrink default the icon size. How can I do that? 

i can post a screenshot if necessary

---

### Post by meng on 2007-01-03
When in the file browser, go to Edit > Preferences > Preview and turn off previews.

---

### Post by bluefrog on 2007-01-03
the previous post is to disable preview in the file explorer which is not what you want.


use the configuration editor (applications/system tools or in console  gconf-editor)

then go to desktop/gnome and click on thumbnailer and check the box disable all.

this will not disable your existing thumbnail but will prevent new thumbnails to be created when you save a file on your desktop.

James

---

### Post by manutdfan2850 on 2007-01-03
> **meng said:**
> When in the file browser, go to Edit > Preferences > Preview and turn off previews.

ok that temporarily solves it... its there a more advanced menu where I can chose which files I want a preview for? Like I want images and videos to be previewed but not PDF files

and also, can I reduce the size of all Icons and desktop fonts, etc somehow?  I just feel like my desktop is so cramped compared to when I was at Windows running at the same screen resolution.

---

### Post by Efwis on 2007-01-03
> **manutdfan2850 said:**
> 
and also, can I reduce the size of all Icons and desktop fonts, etc somehow?  I just feel like my desktop is so cramped compared to when I was at Windows running at the same screen resolution.

read this thread, [http://www.ubuntuforums.org/showthread.php?t=330549](http://www.ubuntuforums.org/showthread.php?t=330549) for you Icon, fonts issue.

---

### Post by manutdfan2850 on 2007-01-03
ok i also found that in the File Browser preferences, I lowered the default zoom to 75% so that helped a lot.

Open up any folder---Edit--Preferences--Views--Default Zoom Level

Thanks for the quick replies.

---

### Post by manutdfan2850 on 2007-01-03
> **manutdfan2850 said:**
>  its there a more advanced menu where I can chose which files I want a preview for? Like I want images and videos to be previewed but not PDF files


anyone? 

thanks in advance

---

### Post by Efwis on 2007-01-03
go to alacarte menu editor and then click on system tools, in the right hand window put a check next to configuration Editor and close.

now go to Applications>System Tools>Configuration Editor
goto Desktop>Gnome>Thumbnailers>Application@PDF and uncheck the box next to enable.

This will stop the PDF files from thumbnailing.

---

### Post by manutdfan2850 on 2007-01-03
> **Efwis said:**
> go to alacarte menu editor and then click on system tools, in the right hand window put a check next to configuration Editor and close.

now go to Applications>System Tools>Configuration Editor
goto Desktop>Gnome>Thumbnailers>Application@PDF and uncheck the box next to enable.

This will stop the PDF files from thumbnailing.

yes i did that, however it seems to only affect NEW pdf files, meaning ones i just create or download. 

I even tried rebooting. but my previous pdf files remain thumbnailed. 

hmm.. minor annoyance i know but an annoyance nonetheless.](*,) 

anyone know what else i can do? 

thanks again in advance

---

### Post by Efwis on 2007-01-03
change the icons manually on the existing ones. that is the only way to fix that. Right click on the PDF file, then click on the Icon and choose a custom Icon for it. You will have to do this for all the PDF files you already have on your system.

Another suggestion is to copy all the PDF files to a blank CD/DVD, erase them from your system, then copy them back over from the cd/dvd.

AFAIK, Gnome isn't set up like windows where you can change the icons system wide with one command from one icon. of course I could be wrong but I haven't foudn it yet. of course i keep all my PDF files in a separate folder from everything else.

---

