---
title: "Kubuntu Effects?"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by LostArt on 2007-05-06
So I just changed from ubuntu to Kubuntu, and am wondering first of all how to make windows transparent, as well as how to apply other effects??:confused:

---

### Post by teddybairs1 on 2007-05-07
The best way to work with window effects in KDE is to use Beryl and Aquamarine (you can use Emerald too under Feisty, but Aquamarine is the KDE window decorator). Superkaramba is a good eyecandy program too. Basically just right click on things, check in the Systems Settings and just poke around. One thing about transparency though is that it may cause X to crash if you try enabling it in the system settings. Better to use Beryl for all your effects.

---

### Post by jargoman on 2007-05-07
do a search for beryl or compiz. I believe there both in the repositories but there's way more to it than just installing them. I'd give you a link but I had to use many how 2's and combine them. It really depends on what type of video card you have and what drivers you use for them. 

as an example I had to search ATI xgl compiz but if you have nvidia it may be different. A good place to start would be beryl's home page.

[http://www.beryl-project.org/](http://www.beryl-project.org/)

I had no luck with this so I went with compiz.

---

### Post by Nythain on 2007-05-07
if the "desktop effects" of ubuntu are what you are refering to, check out beryl... kde can do a bit of transparency itself (mostly menus and panels, not actual windows) and as mentioned, superkaramba is AWESOME desklet goodness

---

### Post by LostArt on 2007-05-07
That Superkaramba thing seems cool, but I still don't get how to use Tars, The file is currently sitting on my desktop as SuperKaramb a-0.39.tar.gz, how do I install it??

---

### Post by GSF1200S on 2007-05-07
> **jargoman said:**
> do a search for beryl or compiz. I believe there both in the repositories but there's way more to it than just installing them. I'd give you a link but I had to use many how 2's and combine them. It really depends on what type of video card you have and what drivers you use for them. 

as an example I had to search ATI xgl compiz but if you have nvidia it may be different. A good place to start would be beryl's home page.

[http://www.beryl-project.org/](http://www.beryl-project.org/)

I had no luck with this so I went with compiz.

I dont know about that.. I went to the Adept installer and installed Beryl. Then, I searched for the Emerald Theme Manager and installed that. Ive had no problems...

Granted, my video drivers (Nvidia) were already installed, but still. I dont think Beryl is that hard to install.

---

### Post by GSF1200S on 2007-05-07
> **LostArt said:**
> That Superkaramba thing seems cool, but I still don't get how to use Tars, The file is currently sitting on my desktop as SuperKaramb a-0.39.tar.gz, how do I install it??

If you arent so concerned with "pretty," I would consider doing a forum search for Conky, which is sorta like Karambas lightweight alternative. You can do things with Conky that karamba cant do...

---

### Post by GSF1200S on 2007-05-07
> **LostArt said:**
> That Superkaramba thing seems cool, but I still don't get how to use Tars, The file is currently sitting on my desktop as SuperKaramb a-0.39.tar.gz, how do I install it??

Place the tar in your /home folder. Now, extract the folder there.

Open a terminal and change directory to the Superkaramba folder. EX:

cd superkaramba-0.9.1

Then, type:

./configure

then

sudo make

sudo make install

sudo make clean


Post back if you have any issues...

---

### Post by akudewan on 2007-05-07
Or you can get superkaramba from apt-get.
```

sudo apt-get install superkaramba

```

---

### Post by teddybairs1 on 2007-05-07
Agreed with above. you shouldn't have to use a tar file for almost any piece of software you want. Superkaramba is already available and properly configured in the repos. Use Adept to locate and install it.

I see a lot of newbies trying to handle source packages or tar balls. Don't. I'm not a newbie anymore and I still have trouble with them. The package type Ubuntu uses is .deb and you can usually find anything you want in a .deb package if you look hard enough.

Also, the easiest way of installing Superkaramba is to look for it in Add/Remove programs and check the box and hit apply.

---

### Post by GSF1200S on 2007-05-07
> **teddybairs1 said:**
> Agreed with above. you shouldn't have to use a tar file for almost any piece of software you want. Superkaramba is already available and properly configured in the repos. Use Adept to locate and install it.

I see a lot of newbies trying to handle source packages or tar balls. Don't. I'm not a newbie anymore and I still have trouble with them. The package type Ubuntu uses is .deb and you can usually find anything you want in a .deb package if you look hard enough.

Also, the easiest way of installing Superkaramba is to look for it in Add/Remove programs and check the box and hit apply.

Well, im not trying to argue with you, but the poster said he had a tarball and didnt know what to do with it.

Some programs are not made specifically for debian based distros, and are not included in the package manager. Many programs written generically come as tarballs because all Linux distros can use them. We all have to learn sometime...

That being said, tarballs can be tricky. I still scratch my head from time to time...

---

### Post by teddybairs1 on 2007-05-07
But why make him go through the trouble of fighting with compilation when he can just get it from the repos through a package manager? That's what they're there for. Not everyone wants to fight with compilation, and not everyone should have to unless they want to. Why make someone work with a tarball for hours when they can use Synaptic and get their program in five minutes?

---

### Post by Nythain on 2007-05-07
> **teddybairs1 said:**
> Agreed with above. you shouldn't have to use a tar file for almost any piece of software you want. Superkaramba is already available and properly configured in the repos. Use Adept to locate and install it.

I see a lot of newbies trying to handle source packages or tar balls. Don't. I'm not a newbie anymore and I still have trouble with them. The package type Ubuntu uses is .deb and you can usually find anything you want in a .deb package if you look hard enough.

Also, the easiest way of installing Superkaramba is to look for it in Add/Remove programs and check the box and hit apply.
i would have to disagree somewhat...
while i do agree you should use apt to get things from the repos...
A. the repo versions are often times outdated and...
B. i suggest almost every linux newbie to attempt as many source installs as possible... its more than likely something they are going to have to learn to do someday anyways... and its also the most feared thing by all newcomers to linux.

the worst they can do is find out they dont meet dependencies and get frustrated, but after a few (or many) attempts they will eventually get the hang of it, be more familiar with how thier system works to begin with, and be less frightend of trying other things feeling confident in thier victory of one of the more difficult and feared projects inside of linux.

And as for why helping someone to struggle through potential hours of source compilation to accomplish what can be done in a matter of minutes with apt... the same reason i will recomend people do something with apt instead of using faster easier methods like automatix and envy... its just good form to know as much as you can/want to know about your system

---

### Post by LostArt on 2007-05-07
Ok I got it through Synaptic, but how do you move around the things you add, and how do you get amarok to play mp3's???? Lastly Beryl and Compiz don't work on my ubuntu distro, but will it work in Kubuntu, Sorry for all the quesstions, and the gap between posts. :-)

---

### Post by GSF1200S on 2007-05-07
> **Nythain said:**
> i would have to disagree somewhat...
while i do agree you should use apt to get things from the repos...
A. the repo versions are often times outdated and...
B. i suggest almost every linux newbie to attempt as many source installs as possible... its more than likely something they are going to have to learn to do someday anyways... and its also the most feared thing by all newcomers to linux.

the worst they can do is find out they dont meet dependencies and get frustrated, but after a few (or many) attempts they will eventually get the hang of it, be more familiar with how thier system works to begin with, and be less frightend of trying other things feeling confident in thier victory of one of the more difficult and feared projects inside of linux.

And as for why helping someone to struggle through potential hours of source compilation to accomplish what can be done in a matter of minutes with apt... the same reason i will recomend people do something with apt instead of using faster easier methods like automatix and envy... its just good form to know as much as you can/want to know about your system

I agree here.. also, I dont really feel a source install is all that hard. Believe me, Ive used the repos many times and they are nothing short of awesome. But, when 4 commands taking less than a minute can compile a program, its really not that hard at all. Its just the mental obstacle of knowing the form to get it done.

If it werent for me knowing how to do source installs, my wireless/video still wouldnt work. Using the repos I could get the wireless to work, but Id have to use NV drivers. The GLX driver would have an API mismatch with the common kernel, and if I uninstalled the common kernel, it uninstalled my video/wireless drivers. Installing both my Nvidia drivers and my madwifi drivers from source made all of it work perfectly...

Im not fighting with you on this though.. the repos are great, but source installs are made quite easy on Ubuntu. It would be a bit harder (but more effecient) on Gentoo for example..

---

### Post by teddybairs1 on 2007-05-08
LostArt -- On most Superkaramba widgets you can right click on them and there is a part in the menu which says "unlock" or something to that effect. Click this and you should be able to drag the widget around the screen, there should also be an option in the right-click menu to configure it.

Where MP3s are concerned, Amarok runs on the Xine engine. What that means is that you need to enable all of the xine librairies. Go to Synaptic again and mark just about everything labeled "libxine" for install. You can disregard the one's marked "-dev" as these are used for development and compilation. There's a transitional package marked "libxine-extracodecs" which you should mark; while it's a dummy package itself, it should install it's own dependencies which are the packages you need.

I also recommend adding the medibuntu repositories to your Synaptic sources list. These repositories generally have all of the media codecs and third party sometimes proprietary software which makes life a little easier. Go to medibuntu.org and there should be instructions on how to add them: 

[http://www.medibuntu.org/repository.php](http://www.medibuntu.org/repository.php)

Medibuntu's downloads are typically a little slower than the standard repos so be patient. You can also find w32codecs and libdvdcss2 which make life with a dvd player under linux livable and .wmv and .wma playable.

GSF1200S and Nythain -- you guys are brilliant at what you do, and I know I have benefited many times from your expertise and experience, and i know other people have as well; let me use another analogy however:

I began to study Ancient Greek in order to really understand what the New Testament (in which it was written) has to say. It really opens things up to me. I really think everyone who professes Christianity should learn Greek in order to really "get it", and when I was younger I let this opinion be known and "encouraged" as many people as possible to do so. As I got older, one of the things I began to understand is that while the best of all possible worlds would be for everyone to learn Greek, when it comes down to practical matters, not every needs to learn it for their day to day practical lives, and most don't or won't. They leave it to the translators and exegetes and trust them to provide for them an accurate and meaningful translation. Now, I still don't think this is the best thing, but I understand that for most people it is the best way to manage their religious lives in a way that is feasible for them, and where possible I try to give them the benefit of my experience and what I have acquired through it. But I have stopped trying to hand them a Greek Lexicon and Grammar unless they really want to slog through it.

Yes, maybe the packages in the repos are older (although in many cases this means stability). Yes, maybe it might be the best of all possible worlds for everyone to learn how to compile source. But unless someone really wants to slog through it, and has the time to do so, they're going to rely on a "translator" such as the Synaptic package manager and apt-get for their day to day lives; and in truth you really need to show them how to use the simpler tools before you show them the advanced ones. Someone should really know how to use an English (or whatever vernacular) Bible before they start going into Greek. You need to learn how to add 1 and 1 to get 2 before you try to tackle advanced calculus.

Like it or not, there will also be a kind of tier or hierarchical system with the more informed people at the top giving the less informed at the bottom the benefit of their expertise and while inviting them to move up, giving the the choice to either remain where they are or helping them step up.

i really do appreciate everything you guys know and impart, and I am thankful you guys do give your time on the forums to impart the things you have learned. Just go easy on the newbies until they're comfortable enough to move on to the next step.

---

