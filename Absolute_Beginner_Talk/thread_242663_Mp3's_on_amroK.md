---
title: "Mp3's on amroK??"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by Linux4HumanBeings on 2006-08-24
I cant seem to find a way to play mp3's? Any Help? Heres what it shows when I try to add a mp3 to my playlist. [http://i19.photobucket.com/albums/b169/jlavi0/Screenshot-amaroK.png](http://i19.photobucket.com/albums/b169/jlavi0/Screenshot-amaroK.png)

---

### Post by hollaburoo on 2006-08-24
[Try Automatix.]("http://www.ubuntuforums.org/showthread.php?t=80295")

---

### Post by nalmeth on 2006-08-24
To explain why ubuntu can't play formats like mp3 and wmv out-of -the-box:
[http://wiki.ubuntu.com/RestrictedFormats](http://wiki.ubuntu.com/RestrictedFormats)

---

### Post by gunksta on 2006-08-24
Do you have the w32codecs installed?

--andy

---

### Post by koshari on 2006-08-24
you will need to install xine extra codecs from the multiverse/universe repos, and then amarok will hapily play mp3 :-)

you dont need w32codecs for mp3,

---

### Post by koshari on 2006-08-24
and by looking at your error, you dont have the xine engine configured at all, the void engine from memory is a null device that is activated if the sound hardware isnt seen as configured properly, 

so i would additionally be checking your mixer settings, alsa settings, and the xine configuration in amaroks engines tab.

---

### Post by lambengolmor on 2006-08-24
Sorry, I'm new, and I have Kubuntu 6.06. When I try installing Xine extra plugins with "Add/Remove Programs" the package is gray and I can't select it, when I try with "package manager" I can't find the package... Can anyone explain me exacly where those packages are? I had before an ubuntu installation and I managed to have mp3 support, but I needed kde, and now I can't find the way... Haven't they the same repositorys?

---

