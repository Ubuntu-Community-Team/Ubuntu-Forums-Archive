---
title: "newbie needs help with vlc media player,please!!"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by leah1984 on 2008-03-20
**ihave downloaded vlc from the add/remove option i really like vlc have used it before on xp ,but cant play dvds on it or short videos that i have downloaded from azureus,when i try to play something it attemps to ,then nothing.totem on the other hand says i do not have the nesesary plug ins to play lets say"shrek the third".also i do not know if i have all the codecs i need and how do i find out what ones i have and need.i would like to get rid of totem and keep vlc can i remove it without it damaging anything else? im just trying to get all this stuff that i used to have on xp,on ubuntu,i got the computer for free and this is what came with it so i am trying to make the best of it,very different from windows!! tha](*,)nk you if you can help me out**:confused::(:(

---

### Post by wormser on 2008-03-20
**Stop putting your post in bold.**

It sounds like you need to install libdvdcss2 and win32codec.  Follow these [directions]("https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f").  Then from the terminal:

```
sudo apt-get update
```

```
sudo apt-get install libdvdcss2 w32codecs
```

---

### Post by kesman on 2008-03-20
you might also wnat to consider installing linux-restricted-extras -package with synaptic.

---

### Post by leah1984 on 2008-03-20
ok so i tryed typing that in the terminal and this is what it says;unmet dependancies,ubuntu14 is to be installed??????

---

### Post by mc4man on 2008-03-20
You'll probably need to add medibuntu to your sources or just get directly
[http://download.videolan.org/pub/libdvdcss/1.2.9/deb/](http://download.videolan.org/pub/libdvdcss/1.2.9/deb/) - 2nd one down
[http://debian-multimedia.org/pool/main/w/w32codecs/](http://debian-multimedia.org/pool/main/w/w32codecs/) -  third one down

will get you going on vlc

---

### Post by kesman on 2008-03-20
Before anything, run:
```

sudo apt-get update
sudo apt-get clean
sudo apt-get dist-upgrade

```

and let it update your packages. After this, try again installing the codecs.

---

### Post by leah1984 on 2008-03-20
ok am trying that now

---

### Post by eragon100 on 2008-03-20
Easier: search google for "automatix" and download the .deb from the project website.
To install it, double-click the package and click on the button "install package"
Type in your password and press enter. Done!

Now, go to applications -> System Tools -> automatix

accept the warningabout licenses or other junk info.

find the codecs tab on the menu on the left, and place a mark at he win32 dvd codecs.

click apply on the upper part of the automatix screen and wait till it's done. Now you can play dvd's :)

Then go to add/remove and install ubuntu-restricted extras (place a mark in fron of it and click apply).

Now you can play windows media, mp3, quicktime, divx, and lots of other things.

And for as far as i know you can't remove totem, it's like windows and internet explorer :(

---

### Post by leah1984 on 2008-03-20
ok a bunch of stuff came up after ientred sudo get update,then nothing after clen,then reading package list ,building dependancie tree,reading state info calculating upgrade 0 upgraded 0  newly installed 0 to remove and 0 not upgraded

---

### Post by kesman on 2008-03-20
make sure you have all the repositories enabled from system -> administration -> software sources

Also remove cdrom from the install sources. Then run the commands again.

---

### Post by leah1984 on 2008-03-20
which one do i download?

---

### Post by mc4man on 2008-03-20
> .i would like to get rid of totem and keep vlc can i remove it without it damaging anything else
You can remove totem movie player in synaptic no problem
just install 1st .deb I mentioned and 99.9% of the time you'll have dvd playback in vlc  - nothing else needed

---

### Post by leah1984 on 2008-03-20
what does .deb meen? im so frustrated with this ??? first install what?

---

### Post by kesman on 2008-03-20
Did you follow my post that suggested you to check your system -> administration -> software sources ?
Enable all of them, and remove cdrom from the sources. Then run the terminal commands I gave you. Also consider using ubuntuguide.org to look for help, there's plenty of stuff in there.

---

### Post by mc4man on 2008-03-20
double click on1st. link in my 1st post - it will take you to a page with 2 files, double click on 2nd file listed to download to desktop, then double click on the file you downloaded and say yes, ect to install

your downloading libdvdcss2_1.2.9_i386.deb

---

### Post by leah1984 on 2008-03-20
i downloaded the deb for gutsey 7.1 cause thats the only one that would work but the guy who reinstalled ubuntu on here said he put feisty 7.4  i tryed to download that distribution and it doesnt work,now i installed for gutsy 7.1 all went threough until i open it from applications then it gives me a warning that this version is for 7.1 only

---

### Post by kesman on 2008-03-20
Well maybe check what version are you using first? You can find it in system -> about ubuntu or something similar.

---

### Post by leah1984 on 2008-03-20
ok im using feisty fawn 7.04

---

### Post by leah1984 on 2008-03-20
managed to get the proper download working

---

### Post by leah1984 on 2008-03-20
ok did these

---

### Post by kesman on 2008-03-20
Did what? Did you get your vlc working?

---

### Post by leah1984 on 2008-03-20
hi i used your advice it seems to be working but the movie plays but there is no sound only constant beeping and the pitch seems to change as the movie plays

---

### Post by leah1984 on 2008-03-20
ok im so sorry for being a total idiot you guys thanks for your patience,i managed to get the libdvdcss2 and win32codecs installed.vlc now plays the movie but there is no sound only constant beeping.

---

### Post by kesman on 2008-03-20
Why cannot you tell what exactly have you done so far? Seems like you are completely unable to post specific info of your actions making it very difficult to give you any advice of what to do next.

---

### Post by leah1984 on 2008-03-20
well im sorry i dont know the computer lingo but i just told you i have the codecs  installed now it will play the movies but now the sound is cut in and out with a beeping noise,sometimes there is no sound at all only beeping,i downloaded the codecs from links

---

### Post by leah1984 on 2008-03-20
thank you  those links helped me now vlc plays my dvds but there is no sound only beeping

---

### Post by leah1984 on 2008-03-20
im sorry i have a few suggestions from different people and i am having trouble talking to specific people about there suggestions ,i dont know how to reply to only one person at a time?

---

### Post by kesman on 2008-03-20
Click the little "quote" button on the bottom of a message to reply to that one.
For the sound, I have no idea, maybe it's something that you can fix in vlc's options? Also, you could add medibuntu repository to your software sources to get more up-to-date versions of media players and codecs. The instructions can be found from ubuntuguide.org.

---

### Post by cmdowns on 2008-03-21
First I apologize if I'm improperly interrupting a thread. I don't write in forums much. However, I am a Ubuntu noob, and I do need help with the vlc player. Actually, I'm quite proud of myself, because I finally managed to successfully download and install it on my three day old, first ever Linux installation.

Can someone please tell me how to set vlc as the default media player?

Thanks

---

### Post by mc4man on 2008-03-21
From the upper panel choose system>preferencse>removable drives and media>multimedia tab and replace totem %m with ```
 vlc %m
```

---

