---
title: "How to change an aplication's icon?"
date: 2006-03-29
forum: Absolute Beginner Talk
---

### Post by Akli on 2006-03-29
I can only do so for a single file or a folder, but I can't change the icon associated with a program.

for example, I want to change the icon for the folders, I can do it to a single folder but I can't change all of them.

---

### Post by mostwanted on 2006-03-29
I guess you'd have to modify a theme to do that.

---

### Post by Ubuntuud on 2006-03-29
The look of all of your folders is made by your icon theme. If you install an other one and activate it, the icons will change. 
You can also edit your current theme by going to ~/.icons/[name of your theme]. Inside that directory there probably will be a lot of files an folders. Look through those directorys and their sub-directorys until you find the icon you wish to change, delete it but make sure you remember the name. Then copy your desired icon into that directory and rename it after the one you deleted. Log out, log in and it should work...

---

### Post by Akli on 2006-03-29
Ubuntuud,

~/.icons/ exists but there is nothing inside (I have enabled hidden files), using the command "ls -a" shows nothing.

~/.themes/ exists but there is only one file : theme.index

---

### Post by Ubuntuud on 2006-03-30
Oh, I forgot. If you use a pre-installed theme, it doesn't show inside that directory (.themes is for the looks of your apps and has nothing to do with the icons)...
I found the directory they are in. First do: System > Preferences > Theme. Click on theme details. There will be a list of themes here and three tabs. You can try these out without any risk (maybe you allready know this...). Once you have found your prefered theme (you need to select a diferent Controls, Icons and Borders theme you must remember the name of the icons theme.
Then go to a terminal and enter (without the "") "sudo nautilus /usr/share/icons --no-desktop". You will enter a weird, old looking version of nautilus. Double click on the name of your theme (the icon will look like a piece of paper, it is an directory. Inside that directory there will be a lot (or not so many) directorys with the name of an resolution (16x16, 24x24, 48x48, scalable etc.).
Go and seach for the icon you want to change. Once you found it change it in the same way I said above. Log out and log in. And, voila (it's french), you will have a new icon. (If not, post it and I will see what I can do).

---

### Post by TrendyDark on 2006-03-30
You can change an application's icon by adding the icon you'd like to the /user/share/icons/ folder. Then right click on the icon of the application you'd like to change, select properties. There you will see the current icon, just click on it to reveal a list of icons, choose the one you've added to the folder (or browse to the folder in question) then you're all done.

---

### Post by mustang on 2006-03-30
[QUOTE=TrendyDark]You can change an application's icon by adding the icon you'd like to the /user/share/icons/ folder. Then right click on the icon of the application you'd like to change, select properties. There you will see the current icon, just click on it to reveal a list of icons, choose the one you've added to the folder (or browse to the folder in question) then you're all done.[/QUOTE]

That only changes the icon for that single file or folder, not for every file associated with that extension which is what the original poster wants.

---

### Post by TrendyDark on 2006-03-30
[QUOTE=mustang]That only changes the icon for that single file or folder, not for every file associated with that extension which is what the original poster wants.[/QUOTE]

OH, sorry, i'm half asleep. lol](*,)

---

### Post by Akli on 2006-03-30
[QUOTE=Ubuntuud]Oh, I forgot. If you use a pre-installed theme, it doesn't show inside that directory (.themes is for the looks of your apps and has nothing to do with the icons)...
I found the directory they are in. First do: System > Preferences > Theme. Click on theme details. There will be a list of themes here and three tabs. You can try these out without any risk (maybe you allready know this...). Once you have found your prefered theme (you need to select a diferent Controls, Icons and Borders theme you must remember the name of the icons theme.
Then go to a terminal and enter (without the "") "sudo nautilus /usr/share/icons --no-desktop". You will enter a weird, old looking version of nautilus. Double click on the name of your theme (the icon will look like a piece of paper, it is an directory. Inside that directory there will be a lot (or not so many) directorys with the name of an resolution (16x16, 24x24, 48x48, scalable etc.).
Go and seach for the icon you want to change. Once you found it change it in the same way I said above. Log out and log in. And, voila (it's french), you will have a new icon. (If not, post it and I will see what I can do).[/QUOTE]


Thanks for the long reply, I can now understand how it works, but I don't want to convert a png icon into an xpm or svg with quality loss.

What I want to do, is to change the file that links to these icons, that would be perfect.

BTW, i did not know that deutsch people speak french ;)

---

### Post by Akli on 2006-03-30
Ok, I converted the apx into png (with gimp) it seems to work fine, but i had to make several copies in order to get several sizes (44*44, 36*36...etc.).

Takes lot of time.

Thank you.

---

### Post by Ubuntuud on 2006-03-31
I'm Dutch. Deutsch looks like the German word for German... Voila comes from France but is fairly commonly used in the Netherlands. And most Dutch children (like me, 13 years) learn at least 4 languages (in the "VWO" (it stands for something like continued scientific education, don't know how it is called in the States)), I even learn 6. 
Not that is matters, but I'm quite proud on my languages since in most other countries you only learn 2 or 3 (that's what I heard).

And good luck, don't forget _not_ to change the user rights on the /usr directory. It would have a very negative effect on your administration activities and the security of your PC.

---

