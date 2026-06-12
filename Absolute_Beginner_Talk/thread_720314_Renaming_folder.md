---
title: "Renaming folder"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by mmarif4u on 2008-03-10
Hi.
i installed a theme in Ubuntu.After that i create folder but it cant let me rename it,and kinda hang for the folder.i change the theme but no luck.
Any ideas???
thanks in advance.

---

### Post by NightwishFan on 2008-03-10
Can you rename if you right click? What type of theme by the way.

---

### Post by mmarif4u on 2008-03-10
When i right click it give me menu for rename,but when i try to rename, it cant.
Theme is hardy slim.But i tried to change theme,but it also not work.

---

### Post by NightwishFan on 2008-03-10
:(

Click rename and type anyway to see if it will change even if you cannot see it. Although I assume you already tried that. I really meant what theme as in metacity, emerald etc. I really am not sure about this problem.

---

### Post by mali2297 on 2008-03-10
Have you checked the permissions for the folder?

---

### Post by mmarif4u on 2008-03-10
Yes,i check the permissions,it was working before with no problem.
But from yesterday i don't know what happened it.

---

### Post by mmarif4u on 2008-03-10
Plz any help.i am really stuck with this,i cant rename any folder and file.

---

### Post by forrestcupp on 2008-03-10
If you're sure your permissions are set right, you could try renaming it from the terminal.  First change to the directory that has that folder, then rename it:
```
cd /path/to/folder
mv old_folder_name new_folder_name
```
Replacing the proper places with the path to your folder and the correct folder names.

---

### Post by mmarif4u on 2008-03-10
This is what i tried:
> arif@ANL-Laptop:/media/disk-1$ mv untitled foler uni
mv: target `uni' is not a directory

The folder default name is untitled folder with space in between.i want to rename it to uni.
By the way i will use terminal for renaming.what is the problem in Ubuntu.why it cant let me rename it from menu or F2.

---

### Post by alphaniner on 2008-03-10
```
mv untitled**\** folder uni
```

you need the slash whenever you have a space(s) in a filename or folder name.

edit: you also seemed to have misspelled 'folder' in your command, gotta keep an eye out for that ;)

---

### Post by mmarif4u on 2008-03-10
> **alphaniner said:**
> ```
mv untitled**\** folder uni
```

you need the slash whenever you have a space(s) in a filename or folder name.

This works,thanks man.
Can tel me why Ubuntu not let me rename from menu.what is the possible problem in Ubuntu.

---

### Post by forrestcupp on 2008-03-10
> **mmarif4u said:**
> This works,thanks man.
Can tel me why Ubuntu not let me rename from menu.what is the possible problem in Ubuntu.

It's just one of those freak things that happens sometimes.  I once had an icon on my desktop that I couldn't delete by right clicking on it, but when I tried from the terminal, it worked.

On second thought, maybe it's because the folder is being used by Gnome.  In the terminal sometimes you can do things that Gnome can't.

---

### Post by alphaniner on 2008-03-10
> **mmarif4u said:**
> This works,thanks man.
Can tel me why Ubuntu not let me rename from menu.what is the possible problem in Ubuntu.

Unfortunately I can't help you with that.  If it happens again write down precisely what you did and what happened and maybe file a bug report.  There may also be some errors in one or more of the logs but I'm not too familiar with that kind of stuff yet.

---

### Post by mmarif4u on 2008-03-10
Thanks Forrestcupp and alphaniner for the valuable info.

---

### Post by alphaniner on 2008-03-10
I was browsing the [ Known gutsy bugs and workarounds]("http://ubuntuforums.org/showthread.php?t=595825") thread and noticed this entry:

**Can't rename file in Gutsy's Desktop and Nautilus? See here.**
- Workaround : [http://ubuntuforums.org/showthread.php?t=586819]("http://ubuntuforums.org/showthread.php?t=586819")
- Bug report : [https://bugs.launchpad.net/ubuntu/+bug/153233]("https://bugs.launchpad.net/ubuntu/+bug/153233")

---

