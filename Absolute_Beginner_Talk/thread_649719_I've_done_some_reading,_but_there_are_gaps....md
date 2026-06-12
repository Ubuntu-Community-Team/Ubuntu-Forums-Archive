---
title: "I've done some reading, but there are gaps..."
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by Legomaniac25 on 2007-12-25
First off I would like to say that I am a veteran forums user, and I am very impressed with the attitude around here, in many places there is much frustration over someone not reading the huge "READ FIRST" threads, but here it seems as though everyone is trying their hardest to live in the spirit of ubuntu and giving people polite direction instead of scornful posts.

Furthermore, before I get started I would like to try to establish my experience with open source and linux. I breathe open source in many portions of my everyday life, I have participated in small unit specific Rockbox communities and use the most popular open source applications (openoffice, firefox, etc.) ranging to some that are a little under the radar (misterhouse). I am very attune to the open source ideal and my decision to move to ubuntu is set. 

As far as linux goes I have dabbled in Fedora Core 6, and I am not the type to go making a post reminiscent of "wht's teh terminal OmGs!!!111!" I am simply a newb to gnu who needs some direction on things he wasn't able to find in his reading. So without further adue I give you my undying gratitude for your assistance and the questions that I was probably just too much of a dumbass to find answers to.

1) Gutsy, Edgy, Feisty? I am pretty sure that these are all just version names for ubuntu but I want to be sure, and is there some page that will keep my noob brain straight on all of these names and what version they associate to?

2) I plan on having a dual boot system, as I had with Fedora, but should I use my PartedMagic live CD to resize the partitions beforehand or is there a way I can do this in ubuntu installation?

3) I plan on installing Beryl, and I have been getting a lot of fuzzy information on the difference between Beryl and the new Compiz fusion. I understand that the projects merged but nowhere have I been able to find key differences between them. The compiz fusion site just reiterates that beryl is not compiz fusion and compiz fusion is not compiz. Any helpful opinions would be great.

4) I am aware that nvidia provides linux drivers, however I am not sure how such a venture will work on my machine. I have an nvidia GeForce Go 6600 and unfortunately because it is an MXM module nvidia does not supply drivers on it's website for it, linux or not. They must be distributed through the manufacturer due to case functions like my external VGA switch and lid closing features etc. etc... My manufacturer (ibuypower) unfortunately does not provide ANY up to date drivers, I had some issues with this and found out that my laptop comes from a big conglomerate (uniwell) that also made my model for alienware (area 51 m5550) and I was able to get the appropriate drivers from their website. I am willing to go through quite a bit of effort to get it to work, however I thought I better ask to see if it was even possible and if anyone here has had experience with an issue similar to this.

Once again thanks to whoever comes to my need. I am taking this time off my schoolwork to put some effort into a complete transformation, as I have been wanting to move all along, and I feel that these are the most pressing matters at hand. And even though I don't tout myself as being particularly religious, Merry Christmas! I hope you all have a holiday in the spirit of ubuntu!

---

### Post by skyjacker on 2007-12-25
Welcome!!
1) These are just the names given to the different versions. It eould benefit you to get the "current version (Gutsy Gibbon - version 7.10).
2) You can use the partition editor that comes on the install disk, and it will do an excillant job.
3) Can't help ypu. Don't use either one.
4) you can try "Envy". I does a good job of loading nVidia drivers.
Good luck:)

---

### Post by rune0077 on 2007-12-25
1. [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
2. If you're already familiar with PartedMagic, I would suggest just using that first, since it's a pretty frustrating thing to accidentally wipe your Windows partition (speaking from experience here).
3. Compiz Fuzion comes preinstalled with the newest version of Ubuntu (Gutsy), so there's little reason *not* to use it. As for the difference between the two, I'm as clueless as you are.
4. Can't help you here, since I'm using ATI.

---

### Post by bumanie on 2007-12-25
Answers to your questions as best I can.

1) The names are just that names, the important thing is the numbers attatched to the names. the first number denotes the year of release and the second number the month within that year that that version was released. Therefore 7.10 means the release was October, 2007.

2) There is an in-built partiton editor on the live cd. Otherwise the best tool touse would be the gparted live cd, which provides more options than the partition editor.

3) Beryl is no longer supported since its fusion with compiz, the same goes for compiz. Therefore if your system is able to handle the full desktop effects, it would be best use compiz fusion which has support and is still undergoing further development (I think development is continuing)

4) I have no idea how to install a graphics card that has no linux driver. You could try envy as suggested in the previous post. Alternatively search for a similar nvidia card, often the drivers are also similar and will run another card OK. Can't remember the url but I think there is a Japanese site that codes linux drivers. If you can find the site, you may come across something there.

---

### Post by dpar on 2007-12-25
You should be able to get the drivers for your card through the resrticted drivers manager in Gutsy. If not, then you can try Envy, as skyjacker says.

---

### Post by The Cog on 2007-12-25
1) 
Ubunti releases every 6 months. Each release has a project name and a release number (year.month). The project names are now going in alphabetical order - Dapper Drake, Edgy Eft, Feisty Fawn, Gutsy Gibbon and coming in April, Hardy Heron (v8.04). 

2)
Better to use PM if you are familiar with it. Just reduce the size of the Windows partition and leave un-partitioned space for the Ubuntu installer, then tell it to use the free space - it will make its own partitions how it likes them.

3)
I think that since Beryl and Compiz have buried the hatchet and re-merged, the separate projects are probably just landmarks in history. I'm happy with the effects that come with Gutsy in the repositories.

4)
It may be worth trying the nvidia driver, but if that doesn't work, you may be stuck with the open source 2D only driver. If so, there is no point worrying about Beryl/Fusion.

---

### Post by scorp123 on 2007-12-25
> **Legomaniac25 said:**
>  1) Gutsy, Edgy, Feisty?  These are the names of the various Ubuntu releases. As the others here have already pointed out you will find the list of releases and their version numbers here: 
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Or on Wikipedia:
[http://en.wikipedia.org/wiki/Ubuntu_%28Linux_distribution%29#Releases](http://en.wikipedia.org/wiki/Ubuntu_%28Linux_distribution%29#Releases)

> **Legomaniac25 said:**
>  should I use my PartedMagic live CD to resize the partitions beforehand or is there a way I can do this in ubuntu installation?  You can choose the "Manual Partitioning" option during the installation and then increase + shrink existing partitions, create new ones, and so on.

> **Legomaniac25 said:**
>  3) I plan on installing Beryl, and I have been getting a lot of fuzzy information on the difference between Beryl and the new Compiz fusion. I understand that the projects merged but nowhere have I been able to find key differences between them.  Beryl is obsolete now. And Compiz-Fusion comes pre-installed with the new Ubuntu release, so all you need to do is to get your NVidia card going.

"Compiz" is the original project that started back in 2005. Unhappy with the slow progress some people left that team and created their own framework and plugins: "Compiz-Quinn". Later they changed their name again to "Beryl". Now free to do what they wanted the "Beryl" team created lots of fancy eye-candy effects (e.g. transparent cube) that were completely absent in the original "Compiz".

So during 2006 people had this choice: Enjoy fancier plugins thanks to "Beryl" at the risk of system instability ... or rather go for "Compiz" and enjoy its better stability and be happy with the few effects that are there ...

Whatever the dispute between the two teams was about, they merged again, and as consequence the project is now called "Compiz Fusion", apparently merging the best of Beryl with Compiz. Looking at "Fusion" I can recognise some of the "Beryl" plugins in there; other plugins though are missing (apparently some of the Beryl plugins were too unstable for most people?).

Do you need "Beryl"? Nope. When you install the current Ubuntu release you'll already have "Compiz Fusion" out of the box.

> **Legomaniac25 said:**
>  The compiz fusion site just reiterates that beryl is not compiz fusion and compiz fusion is not compiz.  Exactly. Those three are different projects. Only "Compiz Fusion" is alive now, the others (Beryl, Compiz) are obsolete now.

> **Legomaniac25 said:**
>  4) I am aware that nvidia provides linux drivers, however I am not sure how such a venture will work on my machine.  If it says "Nvidia" on your card then the Nvidia Linux driver should work.

> **Legomaniac25 said:**
>  I have an nvidia GeForce Go 6600 and unfortunately because it is an MXM module nvidia does not supply drivers on it's website for it, linux or not. They must be distributed through the manufacturer due to case functions like my external VGA switch and lid closing features etc. etc  Sounds like Windowsish blah blah blah to me. Just forget about this. If your system has a Nvidia card then you need the Linux driver provided by Nvidia. It's the same few binaries for all the Nvidia cards anyway, as far as I know. e.g. my system here uses the  "nvidia-glx-new" package which is the same everybody with any newer Nvidia card would have to use. This is not like Windows where e.g. graphics cards with just minor differences have to use a completely different driver ... Here such stuff doesn't matter. If it says "Nvidia" on your card, you install the "nvidia" package, and voila, you're done.

---

### Post by Legomaniac25 on 2007-12-25
Hardcore, thank you guys so much, this forum truly holds itself to the ideals of the ubuntu way, from everything I have read and know this is exactly how an open source community should operate.

Only with the time waiting for replys, which wasn't long at all thanks to you guys, I have come up with only more questions...

1) I remember an application I used in the terminal in Fedora core 6 that would download applications from a simple command line, I have a feeling I am going to need to use this through my exploration into ubuntu but I can't find the name anywhere. I know it's pretty basic and once I see it I will remember but it's one of those brain drain situations...

2) Does Gutsy include all the nescessary proprietary codecs to play standard media? I use VLC now and I know there is a linux version but I have heard some discussion around here about divx not working, and I just wanted to make sure.

And Scorp123 thank you so much for your incredibaly in depth post, it helped a ton, it's good to know that regardless of key differences I don't even have to worry about installing any window effects or anything.

And thanks to everyone again, this community rocks!

---

### Post by rune0077 on 2007-12-25
1) The command is called "apt-get" Type it into the terminal followed by the name of the package you want to download and install (usually you want to do "sudo apt-get" instead). There's also the Synaptic GUI found in System > Administration > Synaptic Package Manager, which is basically the same thing (it downloads the package and installs it for you). If you're a "command-line only" type of guy, then use apt-get, otherwise Synaptic is a lot easier to use, since it shows you a list of all available packages and has a search function. 

2) You need to install the ubuntu-restricted-extras package. This is in the Multiverse repo, and allows you to play most music and video formats, if it isn't enough, more is available through the medibuntu repo. Read this: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by Tteddo on 2007-12-25
4. You should definitely go with the restricted drivers route. If you use the one that you can download from nVidia it will work for your card, but any time there is an update to the linux kernel or the headers you will need to re-run the setup again to get it to work. With the restricted drivers that is taken care of automatically.
This actually happened last week because I am using a beta driver while I wait for a new driver for my card (7300GS- random freezes)) and the headers were updated or something.

---

### Post by The Cog on 2007-12-25
1)
That was probably wget. It is installed by default in Ubuntu.

---

