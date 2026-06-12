---
title: "Trouble with package manager"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by oliverb on 2006-08-30
This all started with me looking for a java plugin. I read somewhere that it was in the multiverse repository.

Trouble is I can't find a multiverse. I can find backports multiverse but I understand that that's not the same.

Anyway I'm now finding that Synaptic or aptitude report an error 

W: Duplicate sources.list entry [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/universe Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-i386_Packages)

and if I run apt-get update I see

Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/main Packages

Where it looks as though the same repository is listed twice.



Or could I have just broken my sources.list somehow?

---

### Post by skymt on 2006-08-30
Yes, you broke your sources.list. Remove any duplicate entries, or just post it and one of us forum monkeys will fix it up for you.

---

### Post by PriceChild on 2006-08-30
Open up software properties from system>administration and delete everything there, then add them all from the self explanatory buttons there.

Alternatively, replace /etc/apt/sources.list with one generated from [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

---

### Post by oliverb on 2006-08-30
Thanks, after posting I found the checkbox for multiverse, tried installing the java plugin, pressed cancel during the download (please don't ask) and found I seem to have broken the package manager as I could no longer even select the java plugin in synaptic.

So I got fed up of it and reinstalled. I'd only installed on Monday after a drive-swap so it's no great loss.

So now I've just got the default list, I'm going to save a copy so I know what it should look like.

I saw the source-o-matic but I'm not sufficiently familiar with the rep names to know what to select and I suspect that checking everything just in case would be a bad idea.

---

### Post by dchglat on 2006-08-30
try going here:
[http://www.ubuntuforums.org/showpost.php?p=1090438&postcount=2]("http://www.ubuntuforums.org/showpost.php?p=1090438&postcount=2")

It's the original source list that came with your system. 
I would simply erase everything and paste the new one into it.


**oh well, too late. Well now you know where you can get the source list courtesy of ubuntu_demon if you ever lose it.

---

