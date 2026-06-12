---
title: "Breezy - No w32 codecs available ?"
date: 2005-09-20
forum: Absolute Beginner Talk
---

### Post by flebber on 2005-09-20
Hi

I have a simple question ? is the w32codecs available in breezy yet? I cannot find them in synaptic, and I tried to sudo apt-get install w32codecs but still joy this is result of apt > Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate 

On a totally different note, installed Ubuntu 2 days ago an was well surprised, had tried a few distro's lastly vectorlinux which I still feel is a great distro. I had Mepis as well but this is better, lighter, faster more configurable the Mepis 3.3 release was like a brick compared to 2004.6. Anyway I am enjoying Ubuntu Nvidia done if I can play a few videos all will be sweet.

 :-#

---

### Post by Gustav on 2005-09-20
[QUOTE=flebber]Hi

I have a simple question ? is the w32codecs available in breezy yet? I cannot find them in synaptic, and I tried to sudo apt-get install w32codecs but still joy this is result of apt  

On a totally different note, installed Ubuntu 2 days ago an was well surprised, had tried a few distro's lastly vectorlinux which I still feel is a great distro. I had Mepis as well but this is better, lighter, faster more configurable the Mepis 3.3 release was like a brick compared to 2004.6. Anyway I am enjoying Ubuntu Nvidia done if I can play a few videos all will be sweet.

 :-#[/QUOTE]
 No there's no w32codecs in Breezy.

But it can be installed from the backport repository. Even if the breezy backports isn't started yet you can use the hoary extras repository.

---

### Post by flebber on 2005-09-20
Since I would only want to use hoary bacports for this download, can you tempoaraily eanble it thru apt?

like apt-get install ws32codecs --http://hoary for example

---

### Post by Kapre on 2005-09-20
[QUOTE=flebber]Since I would only want to use hoary bacports for this download, can you tempoaraily eanble it thru apt?

like apt-get install ws32codecs --http://hoary for example[/QUOTE]

flebber - I dont think you can get it from apt-get because the hoary backports is down (which I think is together with the Ubuntu guide).

If they are on-line, I would suggest just to edit your list and add the backports of hoary in your breezy source list and after getting what you want, just comment them again so that when you look for other apps that are on hoary you can go back and uncomment them.

K

---

### Post by dngpng on 2005-09-20
there is another way when there is no w32codec available: download this codec package: 
[http://www1.mplayerhq.hu/MPlayer/releases/codecs/all-20050412.tar.bz2](http://www1.mplayerhq.hu/MPlayer/releases/codecs/all-20050412.tar.bz2) , 
then untar/decompress it
```
tar xjvf all-20050412.tar.bz2
```
and change the name of the folder to "codecs", move it to /usr/lib/.
```
sudo mv all-20050412 /usr/lib/codecs
```
 After that, make a "win32" folder link to it with
```
sudo ln -s /usr/lib/codecs /usr/lib/win32
```
Then Mplayer and totem-xine could play almost all kinds of auidos / videos.

---

### Post by flebber on 2005-09-26
Thanks for the replies :)  dngpng it worked perfect thank you.

---

### Post by NZ-Wanderer on 2005-09-26
Ohh been looking for something like this, cause I can't play my WMV files...

Alas dngpng following your guide to the letter didn't make any difference, I still can't play my wmv files in totem.. :(

---

### Post by manicka on 2005-09-26
[QUOTE=NZ-Wanderer]Ohh been looking for something like this, cause I can't play my WMV files...

Alas dngpng following your guide to the letter didn't make any difference, I still can't play my wmv files in totem.. :([/QUOTE]
are you using totem-xine?

---

### Post by TristanMike on 2005-09-26
For Breezy w32codecs, you can torrent the file here.. [http://tinyurl.com/87ofx](http://tinyurl.com/87ofx). And a simple ```
sudo dpkg -i <packagename>
``` is all you need.

Don't forget to seed please.

---

### Post by NZ-Wanderer on 2005-09-26
[QUOTE=manicka]are you using totem-xine?[/QUOTE]

Well I wasn't according to the Synaptic Package Manager..
So I installed it and now I got Video.. 

Thank you very much, muchly appreciated the help I get around here :) :)

---

### Post by 23meg on 2005-09-26
here's a direct link:

[ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb](ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb)

---

