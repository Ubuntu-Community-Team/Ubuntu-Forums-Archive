---
title: "[SOLVED] Make Dolphin default file manager [GNOME]"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by plr4ever on 2008-01-11
I just used dolphin and was amazed a file manager could look so pretty. I don't want to totally drop GNOME, but i do want to use dolphin as my default file manager. Does anyone know how to do this?

If not, does compiz work with KDE 4?

---

### Post by nikoPSK on 2008-01-11
compiz yes. Yes you can. (I agree dolphin is very beautiful).  Just right click a folder, goto properties, open with. and it will say open with open folder. Add dolphin to there and set as default! I think that's it as I am not quite sure.

Best,
nikoPSK

---

### Post by subru77 on 2008-01-13
I tried it  but does not work . 

Is there any script which can do it ? 

Subbu

---

### Post by nikoPSK on 2008-01-13
OK, know how to set file associations:

```
gedit ~/.local/share/applications/defaults.list
```But that should be blank, copy everything from here over to there and then modify.

```
sudo gedit /usr/share/applications/defaults.list

```I might be wrong, if I am, just try the second file.

---

### Post by plr4ever on 2008-01-13
That still didn't work. I tried replaced nautilus-file-browser with dolphin-file-browser, but nautilus still opened. And it would not create

> gedit ~/.local/share/applications/defaults.list

---

### Post by oldos2er on 2008-01-13
You can try [http://psychocats.net/ubuntu/nonautilusplease](http://psychocats.net/ubuntu/nonautilusplease) .

---

### Post by plr4ever on 2008-01-13
Thanks oldoser, but it doesnt give scripts for using Dolphin, just thunar and konqueror.

---

### Post by VenomousGecko on 2008-01-15
You can edit the following file:

/usr/share/applications/gnome-nautilus-folder-handler.desktop 

and change nautilus --no-desktop %U to d3lphin and it should cause all file handling to be done by d3lphin.  This worked for me.

---

### Post by plr4ever on 2008-01-15
I dont have that file in that directory. is there anywhere else it might be located?

---

### Post by zeltak on 2008-01-20
Hi

Can you guys create a new folder in dolphin. ive installed it through synaptics for ubuntu (gnome) and it seems to work but i cant seem to be able to use the create new folder (or create anything actually)...

thx 

Zeltak

---

### Post by ubun_two on 2008-01-27
> **VenomousGecko said:**
> You can edit the following file:

/usr/share/applications/gnome-nautilus-folder-handler.desktop 

and change nautilus --no-desktop %U to d3lphin and it should cause all file handling to be done by d3lphin.  This worked for me.

Actually it was 

/usr/share/applications/nautilus-folder-handler.desktop

...on my environment.

---

### Post by plr4ever on 2008-01-27
Thanks ubun_two, that did it. 

You guys are GREAT:guitar:

---

### Post by alazou on 2008-06-07
hi ! please, I want to do the same thing but I can't find the file on my hardy

---

### Post by xgermx on 2008-07-04
I don't think this thread should be labeled as "Solved", as this did not work on a clean install of Hardy. Is there anything else I can try?

---

### Post by iansyngin on 2008-07-04
I found another workaround for this if anyone wants to test further.

Instructions

1. right click Menu Bar and choose edit menu
2. highlight Other
3. right click "open folder" item and go to properties
4. just replace nautilus + arguments with dolphin.

Thats it. 

Hope it helps someone.

Ian

---

### Post by xgermx on 2008-07-04
Thanks for the prompt reply, but unfortunalty, that did not work for me.
I did not have the "Open Folder is selected" option under "other".
I did have "File Manager", which I selected and replace gnome with dolphin, but that didn't work either.

---

### Post by iansyngin on 2008-07-04
xgermx,
When you go to edit menues.
do you have the "open folder" item in the "Other" section?
This is where you need to change the properties

---

### Post by xgermx on 2008-07-04
I have the "Others" section, but there is no option for "Open Folders".
It goes from 'Menu Editor' to 'OpenJDK'.

---

