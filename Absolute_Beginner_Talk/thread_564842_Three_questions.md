---
title: "Three questions"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by Random Idiot on 2007-10-01
[LIST=1]
[*]Is it possible to connect to another computer on my network via FTP? I've tried but I can't figure out how it's done
[*]I don't get any bass through my speakers even when I turn it on full. If I use Windows it works fine, I have no idea what sound card I have if it matters
[*]How do I open .rar files? I've checked Online for help but none of it makes any sense.
[/LIST]Thanks to anyone who answers any of these questions, please help me not need to use Windows again by helping me with these 3 things.:KS

---

### Post by canadianwriterman on 2007-10-01
I can answer question #3. rar is a file compression format like tar or zip. To uncompress a rar file you need the program "unrar" which you can get by:

```
sudo apt-get install unrar
```

---

### Post by Linfreak on 2007-10-01
3. To open .rar.files.. if ur using debian or ubuntu... you could just use..

$ sudo apt-get install unrar or sudo apt-get install unrar-free..

Do state which Linux OS u r using.. so that i may help ya with the first 2 questions..

---

### Post by maryjanua on 2007-10-01
im not an xpert so i dunno about ftp's but to find your sound card try typing lspci into a teminal
that should tell you your soundcard:)

---

### Post by tenmillionmilesaway on 2007-10-01
1) you will need an ftp server running and set up on the computer that you want to ftp to.  if its windows i recommend filezilla.  if its ubuntu then search on these forums or look in the ubuntu guide, or google ([http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty))
2) sorry cant help
3) [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_handle_rar_files](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_handle_rar_files)

---

### Post by shad0w_walker on 2007-10-01
For problem 2 it might well be the bass channel is muted. Open up your volume control (System > Preferences > Volume control) and goto to Edit > Preferences. This should give you a list of all the different channels your audio card has available, tick them all to show them up and try unmuting them one by one, hopefully you should find the channel that does bass.

---

