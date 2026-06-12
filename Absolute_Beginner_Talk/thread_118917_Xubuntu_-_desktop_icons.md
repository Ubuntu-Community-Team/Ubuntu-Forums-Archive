---
title: "Xubuntu - desktop icons?"
date: 2006-01-18
forum: Absolute Beginner Talk
---

### Post by johnraff on 2006-01-18
With my low-spec machine (128MB RAM, 450MHz CPU, 6GB HDD) Xubuntu seemed a better bet than the full Ubuntu with Gnome, but I really would like pretty icons (preferably lighting up when you hover on them :cool:  ) on my desktop  like Gnome- files, shortcuts, launchers...

I read you could do this by istalling Nautilus- it went in with some 60MB total which seemed a bit much for a file manager, I think a lot of libraries or whatever were needed. 
Is this slowing down my machine, or taking up a lot of RAM?
If so is there a more lightweight way of getting desktop icons with Xubuntu?
Failing that, would one of the other window managers on top of a server install of Ubuntu give me what I want?

Thanks for any suggestions.

---

### Post by aysiu on 2006-01-18
Running Nautilus on top of XFCE doesn't slow it down significantly, as far as I can tell.

---

### Post by johnraff on 2006-01-18
Aah so Xubuntu + Nautilus is a reasonable option...

Actually I'm wavering here:
* as a beginner I like the user-friendliness of Gnome, and would prefer to use it if it could be tweaked to run reasonably on my machine, but

*a lot of people seem to really like Xubuntu, so maybe with Nautilus (or Thunar?) to give me a desktop it might be the best way to go, or

*some of the other window managers are really fast and light, but harder to figure out. maybe one of them supports icons on the desktop? I found Enlightenment a bit too much, Windowmaker is simple but strange, and I've just put in Icewm too to check it out, but basically all I want is to be able to see the contents of my "Desktop" folder on my actual desktop, and add some shortcuts to files, websites and folders and launchers for applications. 

I suppose this is just thinking out loud, but any comments on all this would be appreciated.

(When I've figured out what to do I'll wipe off the whole hard disk and reinstall.)

---

### Post by T31 on 2006-01-19
You could try to use rox

*sudo aptitude install rox-filer*

and then run it like this

*rox --pinboard Default*

then you will be able to put links to programs and folders, just drag and drop :)
one more thing you cant save or create files there but you can make them anywhere else, i.e. /home, and then link it

with the option backdrop you can change the desktop wallpaper

and to start it everytime just create a simple script to call it, one of the ways to add programs to xfce starting is create in the folder /Desktop one more called Autostart

s[I]udo mkdir ~/Desktop/Autostart
cd ~/Desktop/Autostart
mousepad ~/Desktop/Autostart/roxeando.sh
[/I]
write [I]rox --pinboard Default
[/I]
save and in a terminal

 *chmod +x ~/Desktop/Autostart/roxeando.sh*


and that's it! :)

---

### Post by johnraff on 2006-01-20
[QUOTE=T31]You could try to use rox

*sudo aptitude install rox-filer*
[/QUOTE]
aptitude is another version of apt-get?
> 
and then run it like this

*rox --pinboard Default*

then you will be able to put links to programs and folders, just drag and drop 

I'm afraid I couldn't figure this out. You have to switch off the Xfce desktop or something. Where do you drag the icons from?
Still looks a bit hard for this Absolute Beginner... :(

Thanks for the suggestion anyway. :)

---

### Post by johnraff on 2006-01-21
T31, sorry I spoke too soon- now it's working perfectly! :)
I had no idea Rox could do a desktop like that...
Thanks again.

---

### Post by az on 2006-01-21
[QUOTE=aysiu]Running Nautilus on top of XFCE doesn't slow it down significantly, as far as I can tell.[/QUOTE]
Nautilus consumes a lot of ram and loads a lot of shared libaries.  Have you tried this with 128 megs of ram?

---

### Post by T31 on 2006-01-21
Rox really rocks :)

the only thing you have to remember with rox is to "set run action" clicking with the right button on a file and select that option is the way to tell rox what app to use, and in the options if you look a little you can have preview icons for the pics and you can change the icon set ;) enjoy rox is fast light and even can look nice :D


ops! one more thing I forget to tell you, aptitude is doing what apt-get does but it remembers better the files you install with the apps in this way when you remove an app you remove all the sh#$ ejem ejem the libraries you installed with ;) the use is the same just change apt-get for aptitude and you will see with the time the difference, a very much cleaner system

---

### Post by Vinze on 2006-01-26
I do like Thunar better, and you can see at [this thread]("http://ubuntuforums.org/showthread.php?t=95934") how to get it with a .deb . However, you still want something for the desktop, I believe there was a package called iDesk, you can try that. Of course you can also be satisfied with what you already have ;)

---

### Post by johnraff on 2006-01-26
You're right- recently I've come to think I can live without desktop icons, since you can put pretty much anything in the panel instead.
That Thunar thread is mighty long- 10 pages!
I read it through but it looks a bit iffy- maybe I'll try that a bit later.

---

