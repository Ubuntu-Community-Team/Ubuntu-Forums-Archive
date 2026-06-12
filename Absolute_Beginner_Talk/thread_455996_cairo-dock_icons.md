---
title: "cairo-dock icons"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by ferronica on 2007-05-27
when i move cursor over cairo dock it shows me only floating icon name without ICONS, only DC++ ICON seen, what i need to do now. please i am new in linux explain

---

### Post by Kobalt on 2007-05-27
How did you install it ? Which version did you install ? There's a newer version that supports PNG icons (the ones shipped in Ubuntu) and there's an older one that only supports SGV. 
The cairo-dock isn't very usable in my opinion, and as I understood the project is no longer running as is... You should maybe look after Avant Window Navigator if you really want a dock.

---

### Post by olavjunior on 2007-08-17
Nah, Cairo-dock's the best!

---

### Post by fabounet on 2007-08-24
I agree, especially since a team resurected it !

you can take a look at :

[french wiki]("http://doc.ubuntu-fr.org/gnome_dock")
[The Berlios devellopment site]("http://developer.berlios.de/project/showfiles.php?group_id=8724")
[the french Ubuntu forum about this dock]("http://forum.ubuntu-fr.org/viewtopic.php?pid=1126637#p1126637")

---

### Post by picpak on 2007-08-24
I know since most people don't speak French (I can read some of it, so it's okay for me) here's a quick guide in English for getting cairo-dock:

1) Go to [http://fabounet03.free.fr/](http://fabounet03.free.fr/) and download the cairo-dock and cairo-dock-plug-ins .deb files.

2) Open up a terminal and type:
```
sudo dpkg -i cairo-dock*.deb
```

3) Hit Alt+F2, type *cairo-dock*, and click Ok. It will ask you to choose a theme (I chose Fabounet). 

4)Once that's set up, right-click the dock and go to Cairo-Dock > Configure Cairo-Dock. Click the "Cairo-Dock" tab, and change the language from "fr" to "en" (it will be the first setting in the tab). Click Ok. You may need to restart cairo-dock (*pkill cairo-dock && cairo-dock &*).

5) After that, the rest should be self-explanatory. Have fun tweaking!

---

### Post by fabounet on 2007-08-25
thanks for the summary, it was certainly useful ! :)
just a thing, you don't need to restart it after changing language, just validate the config panel, and the next time you open it ti will be in english.

I've made a little video to show different possible themes :

[youtube video]("http://www.youtube.com/watch?v=G4bNdznE0qc")
or [http://fabounet03.free.fr/cairo-dock-demo2.avi](http://fabounet03.free.fr/cairo-dock-demo2.avi) for those who can't read youtube or prefer to download it.

---

### Post by picpak on 2007-08-25
> **fabounet said:**
> just a thing, you don't need to restart it after changing language, just validate the config panel, and the next time you open it ti will be in english.

Are you sure? I had to restart several times.

---

### Post by Kpax1 on 2007-08-25
This dock looks really nice. One issue I am having: The active area of the cairo dock is solid black. When it is in call back mode, with an area of x by y pixels, then this area is solid black. Also, when the dock is called up, the area surrounding it is solid black. So if there is information below the dock it will be covered. I am pretty sure I set the transparencies in the setup, so I cannot figure out what is causing it. Any thoughts?

---

### Post by fabounet on 2007-08-25
@picpak : yes you don't need to restart it to change language, nor any other options.
of course there may be some bugs inside, but normally it should work fine. ^_^
@Kpax1 : you need to have a composite window manager, like Beryl, Compiz, Metacity+xcompmgr, or the last Kwin.

---

### Post by Kpax1 on 2007-08-25
great, thanks! It was a matter of enabling desktop effects in System>Preferences.

---

### Post by moore.bryan on 2007-08-26
[I]can't seem to get it to go to english and my french is tres mal.  any ideas?
[/I]

---

### Post by fabounet on 2007-08-27
select "en" in the language list, and then validate.once you reopen the config window, it will be in english ;-)

---

### Post by moore.bryan on 2007-08-27
*that didn't do it until i tried a different theme.  for whatever reason, on my system, the "default" theme won't let me change languages.  all fixed; merci.*

---

### Post by ppmt on 2007-10-07
Hi,

A english version of the french Wiki now exist. Go to:

[http://help.ubuntu.com/community/CairoDock](http://help.ubuntu.com/community/CairoDock)

You can fix the english (or anything else) if you want.

---

### Post by RiceKrispies on 2007-10-11
i'm having trouble when i boot this from startup with the command cairo-dock. specifically that my regular panels won't start up; its fine otherwise. is anybody else having this problem?

---

### Post by az_s_za on 2007-11-23
By the way, if you want to read the French pages easily, just go to [http://babelfish.altavista.com/]("http://babelfish.altavista.com/") and paste the french pages address into the "Translate a  Webpage" box, select the from and to languages and now you can read it in english (or whatever language you chose).  

Any links that you use will also be translated.  It works great!

---

