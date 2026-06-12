---
title: "Installing windows TTF fonts..."
date: 2005-12-10
forum: Absolute Beginner Talk
---

### Post by xelink on 2005-12-10
I have a ton of .TFF fonts on ym windows partition and seem unable to use them in linux ubuntu. How do I install them? I do work in photoshop(on either wine or using windows) and would like all my fonts...

---

### Post by BoyOfDestiny on 2005-12-10
[QUOTE=xelink]I have a ton of .TFF fonts on ym windows partition and seem unable to use them in linux ubuntu. How do I install them? I do work in photoshop(on either wine or using windows) and would like all my fonts...[/QUOTE]

Hi, I had a little difficulty myself. If you open up nautilus and press ctrl + l (that's a lowercase L), and enter fonts:///, hit enter... That's where the fonts are. To install a terranigma font I found on the net... Applications -> System Tools -> run as a different user, enter nautilus so you can use it as root. From there select all your fonts, then repeat the step above to get to fonts:///, paste it in, and for me I had to restart X to get the fonts to show up...

Good luck!

Also, they need to improve this big time...Might be worth posting about this in the Dapper Drake development forums.

---

### Post by xelink on 2005-12-10
thanks very much, I never knew about CTRL+l in file browser... I installed them and am checking to see how well it worked now... 

EDIT: it worked, thanks...

---

### Post by Rackerz on 2005-12-10
So am i getting this rite here, i can copy all my fonts from Windows to Linux?

---

### Post by cwaldbieser on 2005-12-10
[QUOTE=Rackerz]So am i getting this rite here, i can copy all my fonts from Windows to Linux?[/QUOTE]
At least all the True Type fonts.

---

### Post by xelink on 2005-12-10
[QUOTE=Rackerz]So am i getting this rite here, i can copy all my fonts from Windows to Linux?[/QUOTE]
yeah a fairly good fraction of them at the least. most windows fonts are TTF though so you should be fine.

one quick question for anyone who would know, I have heard you need tahoma installed to run steam through wine... would this qualify for that?

---

### Post by TeeAhr1 on 2005-12-10
Ooooh, nice.  Thanks, xelink, for asking my question for me!

---

### Post by d1337 on 2005-12-10
I'll try my best not to be a zeaolt of any nature, but I've used [Automatix]("http://ubuntuforums.org/showthread.php?t=66563p://") on my last three clean installs and have been thrilled...it just works :)  It allows you to do the MSTTF deal quite easily and you get to pick and choose what you do and what you don't.

---

### Post by Gray. on 2005-12-11
Yes you need tahoma to use Steam, and I'm guessing you can use the same method.

---

### Post by Rackerz on 2005-12-11
I just transferred all my fonts over from Windows. Konqueror didn't like it at first, had to reboot. But all my other browsers are using the correct fonts now :D. 

Thanks guys.

---

### Post by mztriz on 2005-12-11
[QUOTE=Rackerz]I just transferred all my fonts over from Windows. Konqueror didn't like it at first, had to reboot. But all my other browsers are using the correct fonts now :D. 

Thanks guys.[/QUOTE]
How do you copy the fonts into the folder? I tried to do it but it doesn't seem to have transfered into the folder. (all of the fonts I am trying to put there are .ttf)

---

### Post by Rackerz on 2005-12-11
Ok what i did is opened Konqueror and typed 'fonts:///' i then opened up the 'System' folder and copied all my Windows fonts into there.

---

### Post by mztriz on 2005-12-11
[QUOTE=Rackerz]Ok what i did is opened Konqueror and typed 'fonts:///' i then opened up the 'System' folder and copied all my Windows fonts into there.[/QUOTE]
ohhh, im not using KDE... [http://img498.imageshack.us/img498/1330/screenshotfontsfilebrowser7br.png](http://img498.imageshack.us/img498/1330/screenshotfontsfilebrowser7br.png)
see how everything is locked, well it doesn't let me add anything into that folder.

---

### Post by Rackerz on 2005-12-11
Hmmmm have you tried setting permissions for that folder? Sorry if i can't be of more help. I've locked myself out of my own OS, im in Windows at the moment.

---

### Post by Gray. on 2005-12-11
Try moving them as root or using sudo.

---

### Post by mztriz on 2005-12-11
[QUOTE=Rackerz]Hmmmm have you tried setting permissions for that folder? Sorry if i can't be of more help. I've locked myself out of my own OS, im in Windows at the moment.[/QUOTE]
How do I do that?

---

### Post by mztriz on 2005-12-11
[QUOTE=Gray.]Try moving them as root or using sudo.[/QUOTE]
I don't know how to do that... :???:

---

### Post by sigge on 2005-12-18
All this stuff with nautilus and stuff is really confusing, i think... Specially if you need to move _many_ fonts at one time... (I have 6 K + fonts) Nautilus tries to preview... and there u go...

Instead i suggest you all do this:

[COLOR="Black"]sudo cp /path/to/your/fonts/*.ttf /usr/share/fonts/truetype/[/COLOR]

This should make them accessible from all apps. :eek: 

Would be nice if someone corrected me if I am wrong, so I dont mess up peoples system... :p 

Oh well. good luck with u're fonts...

[INDENT]Correction: NB! Yo! Don't do what I wrote above... :§ It' is better if you do what i found at [http://ubuntuforums.org/showthread.php?t=85139&highlight=ttf+font]("http://ubuntuforums.org/showthread.php?t=85139&highlight=ttf+font") Still without nautilus, but including a few important pointers, I should think... I beg your pardon if I confused anyone with my rants.[/INDENT]

---

