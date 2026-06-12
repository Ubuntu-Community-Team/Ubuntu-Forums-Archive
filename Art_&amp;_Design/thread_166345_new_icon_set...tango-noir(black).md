---
title: "new icon set...tango-noir(black)"
date: 2006-04-26
forum: Art &amp; Design
---

### Post by wedderburn on 2006-04-26
UPDATE #4 ...14/05
added some more icons now if you're on ubuntu dapper and you log out the shut down restart and hibernate buttons are themed
settled on using the black+blue navigation buttons they look better on a dark background
**oh and you can grab the latest from ** [http://www.gnome-look.org/content/show.php?content=38964](http://www.gnome-look.org/content/show.php?content=38964)


**UPDATE #3**..07/05
ok heres a new version alot more icons fixed up that flag and some other icons added quite a few more as well
[ATTACH]9158[/ATTACH]
[ATTACH]9157[/ATTACH]



--------------------
**UPDATE #2**04/5
ok heres version .03
[ATTACH]9039[/ATTACH]


changes include:
the stop button(made it darker)
preferences-desktop-locale(changed the flages now its chinese and french)
drive-harddisk(used the oribinal tango one fir this just darkened it a bit and made it more simple)
media-cdrom(added more red it just looked better)

im still working on this if you have any suggestions please do let me know 

------------------------
UPDATE 29/4
i've just packaged version 0.02 its has more icons and now the set can be used 
[ATTACH]8850[/ATTACH]

hope you injoy
heres a screen shot as well
[http://www.ubuntuforums.org/gallery/showimage.php?i=2555&c=13](http://www.ubuntuforums.org/gallery/showimage.php?i=2555&c=13)
ps im still working on the navigation arrows and more


------------------
hey im moding/making a darker blue version of the tango-orange theme.

the reason is that i really like the orange version of many of the icons but because its orange it only really fitted in with ubuntu, so started to make this 
[ATTACH]8774[/ATTACH]

here a list of things i did differently
*shortened the white top half of the folder ( a few people didn't like having such a high one)

* added more black to the server box( i really liked the extra black on the box that orange tango introduced)

*added a recycling logo to the trash can ( some users thought it looked like a battery)

*removed some extra details from the computer screens(just to make it look more simple and uniform)

*added a shadow to network-offline 's X logo just like the network-error icon

hope some of you like it, if you don't please tell us what bugs you. i only started today so i open to suggestions comments or anyone that wants to add to it 
ps im thinking of changing the folder does anyone have a idea what should be done with that

---

### Post by Pekkalainen on 2006-04-27
Looks awesome from the screenshot you posted, but I cant install it: my theme manager says "file format invalid" :(

---

### Post by Rui Pais on 2006-04-27
Hi
i maked a copy of Tango icons folder, 
renamed Tango-noir, 
copied these icons over, 
edit file index.theme to say Name=Tango-Noir
and copied that folder to ~/.icons.

:)

---

### Post by wedderburn on 2006-04-29
[QUOTE=Pekkalainen]Looks awesome from the screenshot you posted, but I cant install it: my theme manager says "file format invalid" :([/QUOTE]
yes thanks its was just a preview i got a semi working version that i will post soonish (some of the icons haven't been added) and that is useable

---

### Post by wedderburn on 2006-04-29
[QUOTE=Rui Pais]Hi
i maked a copy of Tango icons folder, 
renamed Tango-noir, 
copied these icons over, 
edit file index.theme to say Name=Tango-Noir
and copied that folder to ~/.icons.

:)[/QUOTE]
very good i did that awile ago and im posting the version with a index file now

---

### Post by Pekkalainen on 2006-04-29
Thanks a bunch! It looks awesome indeed, finally an icon theme that matches my dark desktop :twisted: 

Keep up the good work and make it 100% complete now please :KS

---

### Post by wedderburn on 2006-04-29
[QUOTE=Pekkalainen]Thanks a bunch! It looks awesome indeed, finally an icon theme that matches my dark desktop :twisted: 

Keep up the good work and make it 100% complete now please :KS[/QUOTE]

do you have any suggestions?
like what icons do you think need a dark version

---

### Post by Rui Pais on 2006-04-29
[QUOTE=wedderburn]do you have any suggestions?
like what icons do you think need a dark version[/QUOTE]
Hi wedderburn,
on my post i was on a rush, i forgot to thanks.
Yes your icons are very cool.

In my case what i miss, mostly, is an open folder of 'noir' look. The one that appears when you drag an item over a folder before releasing the mouse button...
And an 'home' folder... the one that appears on file manager on the /home system.

Keep going, nice work. Thanks.

---

### Post by Pekkalainen on 2006-04-29
[QUOTE=wedderburn]do you have any suggestions?
like what icons do you think need a dark version[/QUOTE]


Hehe I think every icon needs this style :)
My desktop is dominated by gray and black and it looks very awesome with this set of icons so please convert as many as you can. As for suggestions I really dont have much to say so far, maybe the folder icon could go a bit darker but all in all in looks awesome!

---

### Post by wedderburn on 2006-04-29
[QUOTE=Rui Pais]Hi wedderburn,
on my post i was on a rush, i forgot to thanks.
Yes your icons are very cool.

In my case what i miss, mostly, is an open folder of 'noir' look. The one that appears when you drag an item over a folder before releasing the mouse button...
And an 'home' folder... the one that appears on file manager on the /home system.

Keep going, nice work. Thanks.[/QUOTE]

thanks for the comment yes i noticed this one to but didn't have enough time to create it 
i'll defently add this to hte next version hopefully soon

---

### Post by wedderburn on 2006-04-29
[QUOTE=Pekkalainen]Hehe I think every icon needs this style :)
My desktop is dominated by gray and black and it looks very awesome with this set of icons so please convert as many as you can. As for suggestions I really dont have much to say so far, maybe the folder icon could go a bit darker but all in all in looks awesome![/QUOTE]

well since you know what you want what do you think for the stop sigh in nautilus i need to convey that its a stop sign but it doesn't fit in with the general colours of my set
any ideas?

---

### Post by Pekkalainen on 2006-04-29
Well the tango icon looks good shapewise so maybe you can just try to change the color of it. The shiny black that the computer icon has might look nice or maybe some kinda of variation of the green in your folder icon even though that screws with the "color psycology" thing of a stop sign. Maybe you can try some sort of shiny dark red as well. 

I'm not entirely sure I'm just brainstorming a bit. :-k

---

### Post by Rui Pais on 2006-04-30
hi wedderburn,
thanks for the update. 

I see that it has now an home and an opened folder :)
But in order to the last of those to work is necessary
at scalable/status/:
```
cp folder-open.svg folder-drag-accept.svg
ln -s folder-open.svg gnome-fs-directory-accept.svg
ln -s folder-open.svg folder_open.svg
```

Keep on. Good work.

---

### Post by wedderburn on 2006-05-01
[QUOTE=Rui Pais]hi wedderburn,
thanks for the update. 

I see that it has now an home and an opened folder :)
But in order to the last of those to work is necessary
at scalable/status/:
```
cp folder-open.svg folder-drag-accept.svg
ln -s folder-open.svg gnome-fs-directory-accept.svg
ln -s folder-open.svg folder_open.svg
```

Keep on. Good work.[/QUOTE]

thanks i'll make sure that works in the next version :)

---

### Post by wedderburn on 2006-05-04
just updated it :) tell me if theres any kinks

---

### Post by Pekkalainen on 2006-05-04
Looks good, you solved that stop button thing nicely, keep up the good work :)

---

### Post by wedderburn on 2006-05-06
[QUOTE=Pekkalainen]Looks good, you solved that stop button thing nicely, keep up the good work :)[/QUOTE]
im glad you like it now i have to fix that refresh icon .. dunno doesn't fit in although i got a idea for all the navagation buttons see how that panns out :D

---

### Post by garba on 2006-05-12
very nice, congratulations

---

### Post by nealklomp on 2006-05-13
nice thank you.

---

