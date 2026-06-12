---
title: "login window fonts too big"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by Maxwell7 on 2007-01-23
Hi, I have just installed the Nvidia driver on my Edgy, following the procedure of this thread : [http://www.ubuntuforums.org/showthread.php?t=281823](http://www.ubuntuforums.org/showthread.php?t=281823)

Works great, except for one thing. At the login-window the fonts increased by 2 or 3 times the normal size. Is there a way to fix this ? 

I looked under Administration/Loginwindow but could not change the font settings. Now my characters are larger than the textbox, so it gets quite hard to read them. And then there's the aesthetic aspect of course. I want my linuxmachine to look as neat as possible ... Sort of an 'in your face' to my windows-friends :biggrin: 

ps : thanks for this great forum and all the help it gives

---

### Post by Maxwell7 on 2007-01-23
update :  for the record 

I use the happygnome theme with face browser

I have been able to change the font in the textbox, using this thread : [http://www.ubuntuforums.org/showthread.php?t=332101&highlight=login+window+font](http://www.ubuntuforums.org/showthread.php?t=332101&highlight=login+window+font)

But now the names next to the pictures are still 3 times too big .. And I don't seem to be able to change them in a similar way, as in the thread ...

( it is a purely aesthetic thing, but i would like to get it right ... i.e. the way it was ;-) )

---

### Post by Ben Sprinkle on 2007-01-23
Click System => Administration => Login Window
I believe you can set the fonts in there.

---

### Post by Maxwell7 on 2007-01-23
> **Ben Sprinkle said:**
> Click System => Administration => Login Window
I believe you can set the fonts in there.

I'm sorry, but I checked there. I can't see anything that has to do with fonts. I can select the theme, change the background, accessibility, etc.. but no fonts.  

I am looking in particular to change the font of the login names, next to the 'faces'.

---

### Post by Phosphoric on 2007-01-23
Maxwell, 
forgive me for joining your thread but I have the reverse problem.  My font is too small, in fact the resolution is out of range for my monitor.  Still works OK but as you say, dosen't look too good.

Thanks :)

---

### Post by Maxwell7 on 2007-01-23
> **Phosphoric said:**
> Maxwell, 
forgive me for joining your thread but I have the reverse problem.  My font is too small, in fact the resolution is out of range for my monitor.  Still works OK but as you say, dosen't look too good.

Thanks :)

No problem for joining ;-) 
Whilst searching these forums for my problem, i came up with a couple of threads regarding your problem. 

[http://www.ubuntuforums.org/showthread.php?t=106608&highlight=login+font+too+small](http://www.ubuntuforums.org/showthread.php?t=106608&highlight=login+font+too+small)
[http://www.ubuntuforums.org/showthread.php?t=22821&highlight=login+font+too+small](http://www.ubuntuforums.org/showthread.php?t=22821&highlight=login+font+too+small)
[http://www.ubuntuforums.org/showthread.php?t=260238&highlight=login+font+too+small](http://www.ubuntuforums.org/showthread.php?t=260238&highlight=login+font+too+small)

maybe they're not all useful :wink:  but hope it helps

---

### Post by Maxwell7 on 2007-01-23
Apparently someone had the same problem with a Dell laptop, way back in Breezy :-) Would this be applicable in Edgy too ? Can anyone confirm that ? 

Here's the thread : [http://www.ubuntuforums.org/showthread.php?t=68779](http://www.ubuntuforums.org/showthread.php?t=68779)

---

### Post by Ben Sprinkle on 2007-01-23
Look around in /usr/share/gdm or /etc/X11/gdm
I think there is a few config files.

---

### Post by Phosphoric on 2007-01-24
> **Maxwell7 said:**
> No problem for joining ;-) 
Whilst searching these forums for my problem, i came up with a couple of threads regarding your problem. 

[http://www.ubuntuforums.org/showthread.php?t=106608&highlight=login+font+too+small](http://www.ubuntuforums.org/showthread.php?t=106608&highlight=login+font+too+small)
[http://www.ubuntuforums.org/showthread.php?t=22821&highlight=login+font+too+small](http://www.ubuntuforums.org/showthread.php?t=22821&highlight=login+font+too+small)
[http://www.ubuntuforums.org/showthread.php?t=260238&highlight=login+font+too+small](http://www.ubuntuforums.org/showthread.php?t=260238&highlight=login+font+too+small)

maybe they're not all useful :wink:  but hope it helps

Hi Maxwell,

thanks for those links.  I didn't have time to look at them last night, spent all evening trying to get FAH running as a service, still no joy with that. :frown: 

Sorry you haven't had much help with your problem, at least this post will bump your thread up to the top briefly. ;)

---

### Post by ponnappan on 2007-02-10
I too faced the  same problem recently (when I was switching back and forth between kdm and gdm)

I restored by login window fonts by the following method.

- the login window themes for kubuntu was in /usr/share/apps/kdm/themes/kubuntu/
- the heart of the theme was kubuntu.xml
- sudo vi kubuntu.xml
- decrease the font size (in my case decreased it to 8)
- restart the display manager
- yo! it worked.

---

