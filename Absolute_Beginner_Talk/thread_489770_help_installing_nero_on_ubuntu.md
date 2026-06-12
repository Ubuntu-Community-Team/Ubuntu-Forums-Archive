---
title: "help installing nero on ubuntu"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by ndrew2505 on 2007-07-01
i want to get nero for my new ubuntu os but i dont know what to get since im new to linux. 32 or 64 bit? rpm or deb package? im using 7.04 ubuntu i386 with wine. any help would be great and sorry if this post is in the wrong place but i didnt see anything pertaining to this topic anywhere so i put it in community.

---

### Post by Buendia on 2007-07-01
Why don't you use gnomebaker?

---

### Post by vexorian on 2007-07-01
afaik there is no nero for Linux and you SERIOUSLY shouldn't consider it on WINE.

Brasero (look for it on synaptic) or k3b (if you got KDE) are very good alternatives to nero.

IMO they are actually better than nero. I wish I could run K3b on windows...

---

### Post by Mapkoz on 2007-07-01
no prob man.
so firstly you should get the .deb file of nero linux 3. (you can find them in the official NERO site...but remember you have to pay for it since it's not a free software).
once you downloaded the .deb file you should just put yourself in the folder where you downloaded it, open a console in that folder and write this code
```
dpkg -i nameofthenerofile.deb
```
it will automatically install the program.

Anyway...why don't u try K3B...it's a free software and it's better than Nero acording to me.
You can find it in the repositories...just check on Synaptic or Adept...

TEll me if it worked.

---

### Post by hsweet on 2007-07-01
Try sticking a blank cd into your drive and see what happens.  You should get a dialog box asking you if you want to burn a cd.  

As nero is windows you could install wine, figure out how that works and nero may or may not work.  The point is, if you just want to burn cd's/dvd's you probably already have what you need.

---

### Post by thisllub on 2007-07-01
K3b is the best burning app period.

NERO makes drink coasters.
I have never lost one with K3B

---

### Post by LookTJ on 2007-07-01
k3b is the best burning app for Linux imho.

*Brasero is second on my list.

---

### Post by Footissimo on 2007-07-01
Shame that there's no such thing as a 'search machine' (engine?) where you can just [put the words 'nero' and 'linux'](http://www.google.co.uk/search?q=nero+linux&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a) and find out that there is a [native linux version](http://www.nero.com/eng/NeroLINUX.html) of nero and has been for a couple of years.

To the OP - you need the deb...and probably (unless you're using the 64bit version of Fiesty) the 32bit.  Just click on the deb and it should open it for you.

edit:  Oh and K3B is better anyway..and free / open source!

---

### Post by ndrew2505 on 2007-07-01
> **Footissimo said:**
> Shame that there's no such thing as a 'search machine' (engine?) where you can just [put the words 'nero' and 'linux'](http://www.google.co.uk/search?q=nero+linux&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a) and find out that there is a [native linux version](http://www.nero.com/eng/NeroLINUX.html) of nero and has been for a couple of years.

To the OP - you need the deb...and probably (unless you're using the 64bit version of Fiesty) the 32bit.  Just click on the deb and it should open it for you.

edit:  Oh and K3B is better anyway..and free / open source!


yeah nero linux 3 so theres been at least a few. i found that out by searchin google...any every1's saying i should go with the k3b so ill try that its just that im so used to windoze crap and am just now tryin linux. thanks for the input to all.


also what type of files will k3b burn to disc? i usually burn iso, bin &cue, and mdf & mds using alcohol on windows but how will i be able to do this with linux ubuntu?

---

### Post by Raineer on 2007-07-01
To be honest, Nero makes the most reliable discs on my system, I really do like this version.

---

### Post by vexorian on 2007-07-02
somehow I don't see how the cdburner software and reliaty are related, thus I am asking, I need to learn.

Either way, to me Nero brings bad memories since it is one of the many apps that can't burn a CD in windows for my comp, and then I can't even uninstall it and the attempt to use a new nero cd to update it tells me that it can't update that old version  of Nero and I should uninstall it...

---

### Post by evolving_monkey on 2007-07-02
I liked Nero also....until I tried the above mentioned software alternatives. After that i realized that nero, in fact, blows. I thought most burning software made many coasters. It turns out that some software is actually dependable.....who knew? Even Nero 7 blows with hurricane force. It is just a little bit prettier while doing it.

---

### Post by forestpixie on 2007-07-02
> **Footissimo said:**
> Shame that there's no such thing as a 'search machine' (engine?) where you can just [put the words 'nero' and 'linux'](http://www.google.co.uk/search?q=nero+linux&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a) and find out that there is a [native linux version](http://www.nero.com/eng/NeroLINUX.html) of nero and has been for a couple of years.

To the OP - you need the deb...and probably (unless you're using the 64bit version of Fiesty) the 32bit.  Just click on the deb and it should open it for you.

edit:  Oh and K3B is better anyway..and free / open source!


Of course someone who's new would probably appreciate this page - and K3B!

[http://linuxappfinder.com/](http://linuxappfinder.com/)

---

### Post by orb9220 on 2007-07-02
> I liked Nero also....until I tried the above mentioned software alternatives. After that i realized that nero, in fact, blows. I thought most burning software made many coasters. It turns out that some software is actually dependable.....who knew? Even Nero 7 blows with hurricane force. It is just a little bit prettier while doing it.

I would have to disagree. I have Nero 6.6.0.13 thru .16 installed on a couple of dozen machines with clueless to average user's and not a single problem among them on burning cd's or DVD's.

I do hate 7 tho and refuse to use it.

But people here saying k3b is the greatest is also untrue. I have used them all and find them lacking in features and usability. 

1) K3b - Have tried on two different machines with two different burner's one P4 with a nec 3550a 16x and a Amd 3500+ with a Liteon 20a1h 20x drive. And on either one I can not get above **actual** 4x even tho main window says 16x and it takes 15 mins to burn. Yes I do have DMA on.

2) k9copy cannot rip as fast or as many encrypted movie disc's as window programs period.
or has the customizing features that dvdshrink and dvdecrypter has in windows.

3) Nautilus builtin burner does indead burn iso's at 16x and I have a finished disc in 8mins. So what is k3b's problem.

I constantly see people complaining of speed burning issue's and lack of features. So don't let the zealots fool you into believing that k3b or gnomebaker or k9copy,etc... are the greatest since slice bread because that is untrue.

I hope that this changes and they do become as or more powerful than the windows conterparts. But with all the treads related to cdrom drives and burning issue's this is still a ways off.

This issue and lack of Video,Graphics editing equal to windows counterparts is why I still have a dual boot system. I still dream of the day when Linux can fill all my needs but it is still not there yet unfortunately.

---

### Post by Raineer on 2007-07-02
I've had Nautilius' built-in burner make quite a few coasters when I've tried to run at those speeds (but yes, at least it will attempt it).  I have certainly noticed the slowdown you mention in the other programs as well.

Nero to me is a good balance of the 2, it tends to run at a good clip and keep a high buffer without making trash.

Trust me, I hate Nero 7 as much as anyone (actually don't like any release above about 4), just got too bloated and I don't like the interface. I don't like K3B's interface either, guess it's just what you are used to.

---

### Post by evolving_monkey on 2007-07-02
Just for the record, I am not one of the zealots you speak of. In fact I am actually fairly new to Linux/Ubuntu. I haven't had time to become jaded enough to become a zealot yet. I have just found some of the Linux alternatives to be better. That is just my personal experience. 

Not that I don't respect the opinions of those more experienced than I, but I still think Nero 7 blows with hurricane force.

---

### Post by orb9220 on 2007-07-02
> but I still think Nero 7 blows with hurricane force.

I concur !

And sorry wasn't trying to single you out. It just alot of these thread boast the greatness of CD/DVD burning apps in Linux and I find it to be inaccurate and misleading since they do not stack up to the windows equivalents** yet **. I will be glad when they do.

Have not tried Nero 3 yet but will give it a whirl and see if it is getting there.

---

### Post by evolving_monkey on 2007-07-02
I agree. Sometimes folks get a bit passionate and forget about the lost art of objective and rational thought (guilty of it myself at times). Which is why, even with all of the great advice that I have seen in this forum, it still sometimes comes down to just trying things out yourself.

---

### Post by wink on 2007-07-02
This isn't going to help ndrew2505 with installing Nero for Linux but ever since I found an easy way to copy an .iso image from a DVD to my hard drive using 

```
dd if=/dev/cdrom of=filename.iso
```
(where cdrom = your DVD drive and filename = any name you chose) 

I quit using anything but this method.

After completion I simply navigate to the newly created file in the home folder and select write/copy to disk. Burning  may be a little on the slow side, but so far it has never produced a coaster.  Besides, even when using Nero I always opted for less than maximum write speeds.

Just my 2 cents worth.

---

### Post by evolving_monkey on 2007-07-02
Nero puts a size cap on how big of ISO it will let you create or burn. I think it is somewhere around 2 gigs. This becomes a problem when you are trying to make a 4 gig Linux OS DVD or back up your DVD movie collection.. It would just fail any time I tried to burn or create anything larger. I started using Magic ISO and I haven't had a problem since. It burns or creates an ISO up to 10 gigs as per the manual. (The largest I have tried is around 4 gigs and I have yet to make a coaster.)

If the size limit isn't enough it also has copyright problems. I like to make a copy and carry that with me on the road so I don't scratch the original. I leave an ISO of the data on my server in case I want to replace the copy. Sometimes Nero would prevent me from doing that.  Once I buy the music I will back it up as I see fit. I do not need software to hold my hand and control what I do with my computer. 

Neither of the above concerns may be important to many but they where 2 of the larger reasons I stopped using it. Nero just isn't worth the price paid in my opinion.

---

### Post by evolving_monkey on 2007-07-03
I thought Magic ISO offered a version for Linux. I checked the website and it looks like I was wrong. Sorry about that.

Here is there website if anyone is curious.

[http://www.magiciso.com/](http://www.magiciso.com/)

---

### Post by stinger30au on 2007-07-28
would be nice if nero 3 for linux had all the options of nero 6 on windows

---

### Post by RaZoR1394 on 2007-07-29
> **Raineer said:**
> To be honest, Nero makes the most reliable discs on my system, I really do like this version.

Same here. I have had a lot of problems with K3B and other similar apps but Nerolinux works great. K3B can't even handle 4GB+ files on UDF. Nerolinux 3.0 is even better.

Sometimes you have to realise that propriatery apps are better. I love opensource but but sometimes it just doesn't cut it.

---

### Post by rburks on 2007-08-08
Well I have a different problem with Nero 3 for Linux.  It installs fine but can't find my burners.  I've got two DVD-RW drives and they both work just fine for everything else.  I currently use GnomeBaker and it's ok but I wanted to play around with Nero just because it's there.  But every time I start it up it says:

"Please check that you have the correct permissions on the corresponding device files. Nero Linux cannot get access to the following devices:

     /dev/sg0/ (SCSI Generic Device)
                 |
                 |
                 |
                 V
   /dev/sg4/ (SCSI Generic Device)"

I'm using a stock version of Feisty and I'm kinda new at Linux (been dabbling with it for a year off and on but started using Ubuntu since Dapper Drake.)

Any ideas?

---

### Post by Tiggzz on 2007-08-10
Wow, I get to help someone already, this is great!!!

Nero doesn't ask the question if you start it from terminal with "sudo nero"

My problem is the fact that it won't read any quicker than 4x. Not acceptible. I'm just trying K3b now. It's looking like its taking just on 10mins to do a copy of a 4.3gb dvd on the fly with 8x disc. not perfect and not Nero in windows speed, but it will do the job I guess.

Tiggzz :)

---

### Post by TeaSwigger on 2007-08-10
The original poster (and maybe others) may like to know that there is a very simple command-line utility to convert NERO's .nrg images to a regular .iso, so that you can burn it with any burning app you choose, for example k3b.

Simply open a terminal and type:

```
sudo apt-get install nrg2iso
```

:)

---

