---
title: "question about nautilus"
date: 2006-06-10
forum: Absolute Beginner Talk
---

### Post by hikitsu4 on 2006-06-10
Hello i got a question about "nautilus".
How do you change what program you want a file to start with manually. I cannot get it to work anymore with this new installation, when i right click on the file and try to change it, it just freezes it didnt do this with my last install so i dont know what the problem is.

NOTE: the problem accurs when i try to change mkv files.

---

### Post by frenkel on 2006-06-10
Right click on the file->Properties
Then click on the the Open with tab.
Place a bullet before the program you want to open the files in by default.

---

### Post by hikitsu4 on 2006-06-10
[QUOTE=frenkel]Right click on the file->Properties
Then click on the the Open with tab.
Place a bullet before the program you want to open the files in by default.[/QUOTE]
If you read the post you would see that i wrote that it crashes then ;)

---

### Post by frenkel on 2006-06-10
[QUOTE=hikitsu4]If you read the post you would see that i wrote that it crashes then ;)[/QUOTE]
You said "when i right click on the file and try to change it" I didn't understand what you meant with it.
Open up a terminal or nautilus and go to ~/.local/share/applications. There you'll find all custom file association files.
Remove the file called something like <name of app you used to open .mkv>-usercustom.desktop
You can also edit the file defaults.list in the same directory.

Or to be sure, completely remove the .local/share/applications directory, but in that way you'll lose all the file associations.

---

### Post by hikitsu4 on 2006-06-10
[QUOTE=frenkel]You said "when i right click on the file and try to change it" I didn't understand what you meant with it.
Open up a terminal or nautilus and go to ~/.local/share/applications. There you'll find all custom file association files.
Remove the file called something like <name of app you used to open .mkv>-usercustom.desktop
You can also edit the file defaults.list in the same directory.

Or to be sure, completely remove the .local/share/applications directory, but in that way you'll lose all the file associations.[/QUOTE]
Im sorry for the misunderstanding i guess i can put the blame that English isnt my first language :)

---

### Post by frenkel on 2006-06-10
[QUOTE=hikitsu4]Im sorry for the misunderstanding i guess i can put the blame that English isnt my first language :)[/QUOTE]
Did you solve it now? :)

---

### Post by hikitsu4 on 2006-06-10
[QUOTE=frenkel]Did you solve it now? :)[/QUOTE]
Not exactly becourse i dont know what file to edit and what program is causing the problem, but no matter i can still change avi files and that is what's important. And i can still right click and choose "open with".

---

### Post by frenkel on 2006-06-10
[QUOTE=hikitsu4]Not exactly becourse i dont know what file to edit and what program is causing the problem, but no matter i can still change avi files and that is what's important. And i can still right click and choose "open with".[/QUOTE]
What happens when you double click an mkv file?
And can you paste the contents of the file ~/.local/share/applications/defaults.list

---

### Post by hikitsu4 on 2006-06-10
The default program seems to be the totem player, when i removed the 1280x1024 from "metamodes" for tvout and SubSection "Display" in xorg.conf and x11 just worked again and i could start totem-xine again. But it still crashes it most be becorse xine is so shitty with handling h264 it takes to much cpu.

---

