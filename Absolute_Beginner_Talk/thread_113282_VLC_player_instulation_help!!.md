---
title: "VLC player instulation? help!!"
date: 2006-01-06
forum: Absolute Beginner Talk
---

### Post by spikes2020 on 2006-01-06
hey i want to install VLC player but it dosent seem to find it when i use 



spikes@Nerv5:~$ sudo apt-get update

did some stuff

Fetched 39.6kB in 36s (1087B/s)
Reading package lists... Done
spikes@Nerv5:~$ sudo apt-get install vlc libdvdcss2
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package vlc



its not the only thing it cant find... i was wondering if i have somthing wrong. i tryed to get other files like weplab and aircrack, i had to download it and extract it manualy, this is realy getting anoying any advice would be helpfull.

also i had a problem with compiling and needed some basic files, i was wondering if there are anyother basic programs or files....

thanx 

spikes2020

---

### Post by buckley on 2006-01-06
have you added the extra repositories?  see here:  [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

and if that doesn't get you where you need to be, try this as well:  [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

---

### Post by diggs on 2006-01-06
Oh and while you're at it, add automatix. it is the best thing since sliced bread, it allows you to add all your programs and codecs and junk with just a couple clicks. it makes life A LOT easier with ubuntu!

wget [http://beerorkid.com/automatix/automatix-ubuntu_4.3-1_i386.deb](http://beerorkid.com/automatix/automatix-ubuntu_4.3-1_i386.deb)
sudo dpkg -i automatix-ubuntu_4.3-1_i386.deb

[http://www.ubuntuforums.org/showthread.php?t=66563&highlight=Automatix](http://www.ubuntuforums.org/showthread.php?t=66563&highlight=Automatix)

---

### Post by spikes2020 on 2006-01-06
thanx i think that solved many of my problems for lost programs... 
man i just installed ubuntu today as my first linux os and man i think im getting the hang of it, just soooo much reading.

thanx

spikes2020

---

### Post by spikes2020 on 2006-01-06
one more question could you  sudo gedit /etc/apt/sources.list be too long ever? Or could i just keep adding sites on to it.. also dose it cause problems if i put multples of the same site on there?

---

### Post by buckley on 2006-01-06
the longer the list the longer the update takes... thats about it.

what i did was when the source-o-matic generated the list, i just verified that what was in my original sources list was also present in the generated list, so i just copied the new list into the sources.list file, and did sudo apt-get update, and it all worked

for whatever odd reason the url for the backports giving in the guide does not want to work, but these did.

---

### Post by diggs on 2006-01-06
[QUOTE=spikes2020]thanx i think that solved many of my problems for lost programs... 
man i just installed ubuntu today as my first linux os and man i think im getting the hang of it, just soooo much reading.

thanx

spikes2020[/QUOTE]yeah, if I had known about automatix from the get go life would have been a lot easier! glad I could be of help, I'm on aboot a week of this ubuntu business over here.

---

