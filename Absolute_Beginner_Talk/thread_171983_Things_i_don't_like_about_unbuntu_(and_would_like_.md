---
title: "Things i don't like about unbuntu (and would like to fix)"
date: 2006-05-07
forum: Absolute Beginner Talk
---

### Post by raovq on 2006-05-07
i moved to unbuntu a couple of months ago, and i am finding that i am booting into windows less and less. But i do have a few annoyances in unbuntu i would like to get sorted, but i do not have the experience or knowledge. any assitance would be greatly appreciated-
1) when i right click on programs like xmms and various other applications, i get the horrible default grey menu, that are annoying to use and difficult to read quickly. is there a way i can enforce a default menu scheme across the board?

2) it seems like the majority of apps i use are made for KDE. i have not grown attached to my gnome desktop yet, and wouldn't i be better off running these apps in their default enviroment?

3) while i know i can see most of my installed programs through the debian menu, is there a better way? i like to know whats installed, and although i installed programs myself, i have found myself chopping and changing alot as i experiment with programs. as a result, i have no idea what remains on my machine. is there a list somewhere?

4) a small annoyance, but the window list bar on unbuntu (the equivilent to the start bar in windows) keeps resizing the tabs for open windows. they will stretch across the whole panel, and then, for seemingly no reason, will squash right down to under an inch. this is fairly annoying as i can't automatically swap windows, i need to keep reading the titles. (if any of that made sense)

5) running gnome, i constantly get errors for programs wanting kfmclient and the like. mostly when a program is wanting to open a url. is this a gnome v kde thing? is there a quick fix i can do to stop it?


thats about it. i have got this linux thing pretty well sorted, but these things i can't seem to fix on my own. once again, thanks for any replies.

---

### Post by nalmeth on 2006-05-07
[quote=raovq]i moved to unbuntu a couple of months ago, and i am finding that i am booting into windows less and less. But i do have a few annoyances in unbuntu i would like to get sorted, but i do not have the experience or knowledge. any assitance would be greatly appreciated-
1) when i right click on programs like xmms and various other applications, i get the horrible default grey menu, that are annoying to use and difficult to read quickly. is there a way i can enforce a default menu scheme across the board?

2) it seems like the majority of apps i use are made for KDE. i have not grown attached to my gnome desktop yet, and wouldn't i be better off running these apps in their default enviroment?

3) while i know i can see most of my installed programs through the debian menu, is there a better way? i like to know whats installed, and although i installed programs myself, i have found myself chopping and changing alot as i experiment with programs. as a result, i have no idea what remains on my machine. is there a list somewhere?

4) a small annoyance, but the window list bar on unbuntu (the equivilent to the start bar in windows) keeps resizing the tabs for open windows. they will stretch across the whole panel, and then, for seemingly no reason, will squash right down to under an inch. this is fairly annoying as i can't automatically swap windows, i need to keep reading the titles. (if any of that made sense)

5) running gnome, i constantly get errors for programs wanting kfmclient and the like. mostly when a program is wanting to open a url. is this a gnome v kde thing? is there a quick fix i can do to stop it?


thats about it. i have got this linux thing pretty well sorted, but these things i can't seem to fix on my own. once again, thanks for any replies.[/quote]
1. Don't know

2. Yes, typically better, but you can still run a lot of foreign DE app's. What you should do, (hard-disk space permitting) is install KDE. If you find yourself using that many KDE apps, you may as well try KDE.
In the command line type:
sudo apt-get install kubuntu-desktop
pick KDE when you log in with GDM

3. Try xfce-appfinder
sudo apt-get install xfce4-appfinder
I love this app

4. Don't really understand... well I think I might. This sound like a gnome "feature", which I kind of like. I don't get the tab squished unless I have a lot of apps running in the window list though.. KDE does not stretch the window tabs.
You should tell the window list not to display windows from all desktops, and use desktop switching, it's an efficient way of running a lot of apps.

5. Only KDE apps will request KDE libraries and dependencies, are you using konqueror to browse webpages???

Hopefully this answers some questions.

---

### Post by gondilon on 2006-05-07
1)you can enforce a menu scheme by going into system preferences.
2)Kde apps wil work on Gnome, but will probably run better in Kde.
3)

---

### Post by MetalMusicAddict on 2006-05-07
[QUOTE=raovq]
1) when i right click on programs like xmms and various other applications, i get the horrible default grey menu, that are annoying to use and difficult to read quickly. is there a way i can enforce a default menu scheme across the board?[/quote]
Its because they were compiled with the GTK1 library.
> 2) it seems like the majority of apps i use are made for KDE. i have not grown attached to my gnome desktop yet, and wouldn't i be better off running these apps in their default enviroment?
Use Kubuntu. Get it [HERE]("http://cdimage.ubuntu.com/kubuntu/releases/dapper/flight-6/"). *Note this is for the Dapper release.
> 3) while i know i can see most of my installed programs through the debian menu, is there a better way? i like to know whats installed, and although i installed programs myself, i have found myself chopping and changing alot as i experiment with programs. as a result, i have no idea what remains on my machine. is there a list somewhere?
Dont know about this. For me when I first started it was like this. Felt the install had become a mess. I just did a reinstall after I learned alot.
> 4) a small annoyance, but the window list bar on unbuntu (the equivilent to the start bar in windows) keeps resizing the tabs for open windows. they will stretch across the whole panel, and then, for seemingly no reason, will squash right down to under an inch. this is fairly annoying as i can't automatically swap windows, i need to keep reading the titles. (if any of that made sense)
Not sure I follow you on this one.
> 5) running gnome, i constantly get errors for programs wanting kfmclient and the like. mostly when a program is wanting to open a url. is this a gnome v kde thing? is there a quick fix i can do to stop it?
Not sure what this is. Ill look.

---

### Post by hito1 on 2006-05-07
[QUOTE=raovq]
4) a small annoyance, but the window list bar on unbuntu (the equivilent to the start bar in windows) keeps resizing the tabs for open windows. they will stretch across the whole panel, and then, for seemingly no reason, will squash right down to under an inch. this is fairly annoying as i can't automatically swap windows, i need to keep reading the titles. (if any of that made sense)
[/QUOTE]

I found an option to not resize the tabs somewhere (maybe in gconf or in that app with window preferences). I'm not in Ubuntu right now, but I'll try to find it tomorrow. 
Anyway, I'm very new in Ubuntu and found it already, If you're in a hurry, do a search and you'll probably find it too. 

(I don't know if we're talking about the same thing, though :) :p )

Ignore that, the option was only to expand the task bar. :-?

---

