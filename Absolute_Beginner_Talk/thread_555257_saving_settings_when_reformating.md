---
title: "saving settings when reformating"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by pdlethbridge on 2007-09-19
I've created an extra partition for home along with the OS's partition and swap. There is about 3 gigs in the home partition. I would like to save things like firefox's settings and bookmarks. How is the best way to gather files like this for the home folder?

---

### Post by pdlethbridge on 2007-09-19
bump

---

### Post by bobplano on 2007-09-19
if you are just adding the partiton on look [here]("http://psychocats.net/ubuntu/separatehome"). for the firefox things there aren't on your /home folder, or at least there is no .firefox folder.  you might want to look at /us/lib/firefox, there's plugins there so i assume there are your prefrences

---

### Post by pdlethbridge on 2007-09-19
The home partition is all ready installed and the files are going there, but not the bookmarks and firefox. I'd like to be able to save settings for firefox but I haven't found a way yet. All this plus a couple of other items are in the home folder and are available if I hose the OS again.
/home/pdleth/downloads
/home/pdleth/Examples
/home/pdleth/mail
/home/pdleth/Music
/home/pdleth/pauls files
/home/pdleth/Pictures
/home/pdleth/Public
/home/pdleth/Templates
 XP had a file and setting transfer wizard to do this.

---

### Post by bobplano on 2007-09-19
well it seems all your firefox prefrences are in the /usr/lib/firefox folder. you also might want to backup /usr/share/firefox just in case. an easy way to backup any files is to use rsync

rsync -av /home/pdleth /path/to/backup
rsync -av /usr/lib/firefox /path/to/backup
rsync -av /usr/share/firefox /path/to/backup

again more info at [psychocats]("http://psychocats.net/ubuntu/backup"). sorry if you already know this stuff and i'm just telling you the wring answer, but i think this is right

---

### Post by willskills on 2007-09-19
Great little addon for firefox - saves all your stuff :)

[https://addons.mozilla.org/en-US/firefox/addon/2109](https://addons.mozilla.org/en-US/firefox/addon/2109)

I am sure someone more experienced can give you a *nix orientated answer - but this'll let you do it easily too :)

---

### Post by pdlethbridge on 2007-09-20
bobplano, I copied those share and lib files to the home folder.Thanks
willskills I downloaded that add on and it will be backing up firefox shortly, Thanks

---

