---
title: "iTunes?"
date: 2006-04-08
forum: Absolute Beginner Talk
---

### Post by dylonium on 2006-04-08
Is there any way to get iTunes for Ubuntu?

---

### Post by raghav_p on 2006-04-08
There is no iTunes version for Linux. The windows version of the application works with [Crossover Office]("http://www.codeweavers.com/"). That however costs money.

There are various alternatives for iTunes however.

---

### Post by Jedeye on 2006-04-08
I have never looked into getting iTunes to work, as there are some nice Linux alternatives. Make sure you look at Rhythmbox, Listen and amaroK. Currently I have been using Listen and it has some nice features that are not in iTunes. 

I'm not sure of any player that has a integrated music store like iTunes.

But try those 3 out... and perhaps some others will be suggested.

---

### Post by dylonium on 2006-04-08
Are there any links to download Listen, Rythmbox or amaroK?

---

### Post by trent dillman on 2006-04-08
Rythmbox and amaroK are in the repos, so a search in Synaptic should show them. I'm not sure about Listen, but it might be as well...

---

### Post by moffa on 2006-04-08
[http://nanocrew.net/software/sharpmusique/](http://nanocrew.net/software/sharpmusique/)

Not sure how well it works

---

### Post by dylonium on 2006-04-09
That doesn't work. Anymore music players such as iTunes? How will I get my iPod to work though?

---

### Post by stinkypudding on 2006-04-09
I'm personally waiting for Songbird's release on linux.   Looks to have many of the same features as itunes.

---

### Post by Lhademmor on 2006-04-09
I also need to get my iPod working on Linux so I'm waiting...

---

### Post by xxFelixDCatxx on 2006-04-09
is there anything preventing you from running wine and installing itunes as a kind of windows app? I haven't actually done it yet, as I have a wireless problem that's taking priority, but that should work.... at least in theory.

---

### Post by aysiu on 2006-04-09
[QUOTE=xxFelixDCatxx]is there anything preventing you from running wine and installing itunes as a kind of windows app?[/QUOTE] iTunes doesn't work in Wine. You'd need Crossover Office.

---

### Post by dylonium on 2006-04-09
Anyone have a rip of CrossOver Office?

---

### Post by angkor on 2006-04-09
[QUOTE=Lhademmor]I also need to get my iPod working on Linux so I'm waiting...[/QUOTE]

No need to wait. ;)

[http://www.ubuntuforums.org/showthread.php?t=103071](http://www.ubuntuforums.org/showthread.php?t=103071)

[http://www.ubuntuforums.org/showthread.php?t=80492](http://www.ubuntuforums.org/showthread.php?t=80492)

I've used both Gtkpod and Amarok succesfully with my 4th gen iPod on Ubuntu 5.10.

---

### Post by x5452 on 2006-04-09
hi im looking at the howto for getting ipod to work, im setting this up for my friend, i dont know anything about ipods.  All he will need to do with it is transfer music and videos.  I have installed gtkpod, but it says for videos you need cvs version? what is that?

---

### Post by aysiu on 2006-04-09
[QUOTE=x5452]I have installed gtkpod, but it says for videos you need cvs version? what is that?[/QUOTE] That's [this](http://sourceforge.net/cvs/?group_id=67873), but I don't know how to install it.

---

### Post by nalmeth on 2006-04-10
I had a difficult time with an ipod, but thanks to some helpful people here I sorted it out.
For getting your ipod setup and operational with music/photos check here:
[http://www.ubuntuforums.org/showpost.php?p=870912&postcount=19](http://www.ubuntuforums.org/showpost.php?p=870912&postcount=19)
If you're not afraid of some copy/pasting and you have an able net connection you should get this working.
The guy that helped me is endersshadow, and he has made a howto for syncing video with video ipods. You'll find it here:
[http://www.ubuntuforums.org/showthread.php?t=114946](http://www.ubuntuforums.org/showthread.php?t=114946)
endersshadow has hooked us up with ipod howtos 8)
I have itunes running in crossover, but it's really not worth it. The actual sycning doesn't work, or at least it didn't for me. Audio/video is fine though.
itunes ain't that grand anyway in my opinion. Check out [listen]("http://listengnome.free.fr/") for gnome, or amarok for KDE. They can both be used independent of whether you are running gnome or kde.
They can both supposedly sync the ipod, but I prefer using separate apps specialized for their purpose.. Also things just work they way they are right now, and I'm happy.

---

### Post by x5452 on 2006-04-10
I dont know anything about ipods cause i dont even own one, lol, this entire fiasco of setting up the machine is for my friend, he has an ipod.  all i need it to be able to do is, encode videos to play in ipod, and be able to send videos and music to the ipod.  what is syncing really, is it neccesary?  if not, i dont need it, lol.

---

### Post by nalmeth on 2006-04-10
syncing is putting media on your ipod. I definately think you'd want that!
With GTKpod setup, you can go into SYSTEM --> PREFERENCES --> REMOVABLE DRIVES & MEDIA and have GTKpod pop open everytime you plug in the ipod.
I've never used a video ipod though.
EDIT:
I just remembered that two lines were left out of the original posted howto, here are the direction's again, with the missing steps included (just enter them into a terminal as you read them) :
```
sudo apt-get install checkinstall libexpat1-dev libglade2-0 libglade2-dev flex libid3tag0 libid3tag0-dev
wget http://search.cpan.org/CPAN/authors/id/M/MS/MSERGEANT/XML-Parser-2.34.tar.gz
tar xzf XML-Parser-2.34.tar.gz
cd XML-Parser-2.34
perl Makefile.PL
make
sudo checkinstall -D make install
wget http://umn.dl.sourceforge.net/sourceforge/gtkpod/libgpod-0.3.2.tar.gz
tar xzf libgpod-0.3.2.tar.gz
cd libgpod-0.3.2/
./configure
make
sudo checkinstall -D make install
sudo cp /usr/local/lib/libgpod* /usr/lib
wget http://easynews.dl.sourceforge.net/sourceforge/gtkpod/gtkpod-0.99.4.tar.gz
tar xzf gtkpod-0.99.4.tar.gz
cd gtkpod-0.99.4
./configure
make
sudo checkinstall -D make install 
```
and heres Endersshadow's original post again, with screenshots
Essentially, this is just installing the newest version of GTKpod not available in the repositories yet. 
[http://www.ubuntuforums.org/showpost.php?p=870912&postcount=19](http://www.ubuntuforums.org/showpost.php?p=870912&postcount=19)
ALSO a quick search found me this. Might help with the video encoding:
[https://wiki.ubuntu.com/iPodVideo](https://wiki.ubuntu.com/iPodVideo)

---

### Post by x5452 on 2006-04-13
ok i seem to have everything woring, except the only way i can get to gtkpod is through terminal.  How do i make it so when i plug in ipod gtkpod pops up?  i went to system>preferences>removeable drives but then what?

---

### Post by angkor on 2006-04-13
[QUOTE=x5452]ok i seem to have everything woring, except the only way i can get to gtkpod is through terminal.  How do i make it so when i plug in ipod gtkpod pops up?  i went to system>preferences>removeable drives but then what?[/QUOTE]

Try changing the command in the multimedia tab from rhythmbox to gtkpod and see if that does anything. Maybe it'll start playing your songs with gtkpod which could be quite annoying. :)

There's probably a better way but I dont' know of any.

---

