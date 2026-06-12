---
title: "Pidgin 2.0.2 Released."
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by Kosimo on 2007-06-15
Hi guys, new pidgin version available.  2.0.2  

[Pidgin]("http://pidgin.im/pidgin/home/")

I'm using PIdgin 2.0.1 witch was downloaded from getdeb.net as a normal and super easy .deb (I love debs guys... All programs should have a .deb release :P ) 
Anyway, now I want the last one, and is not on getdeb so,  somebody can tell me how can I upgrade to the last version?  

Thank you! 

From Barcelona

---

### Post by nylecoj813 on 2007-06-15
When I compiled 2.0.1, I followed the instructions in this post: [http://ubuntuforums.org/showpost.php?p=2646809&postcount=121](http://ubuntuforums.org/showpost.php?p=2646809&postcount=121)

I removed 2.0.0 before I did this though. I will probably follow this same procedure for 2.0.2 (unless I'm too lazy and just wait for the .deb...which didn't work for me for 2.0.1 >_<)

I'm not sure if that's the route you want to go, maybe someone else will have a better answer :)

---

### Post by Kosimo on 2007-06-15
Hmm... It looks really easy.
So, first uninstall pidgin, then install ALL libraries and just compile it..
Thanks man! :)

---

### Post by Malibu Illusion on 2007-06-15
Thanks for the heads up, just gone ahead and compiled the new version from source and installed it myself. =^^=

As is standard:

```
./configure
make
sudo make install
```

---

### Post by maddbaron on 2007-06-15
anyone have a deb for edgy please?

---

### Post by Kosimo on 2007-06-15
> **Malibu Illusion said:**
> Thanks for the heads up, just gone ahead and compiled the new version from source and installed it myself. =^^=

As is standard:

```
./configure
make
sudo make install
```

Done!!!  That's much more easy than I though....

Thanks :)

---

### Post by Kosimo on 2007-06-15
My system try icon is now doubled size!!  very big..... Someone else have this problem?

---

### Post by Kosimo on 2007-06-15
> **Kosimo said:**
> My system try icon is now doubled size!!  very big..... Someone else have this problem?

Fixed :)

---

### Post by tvor on 2007-06-15
Hi, 
I would love to find .deb file of new pidgin 2.0.2 as it has important updated for me....
I'm trying to compile from source and getting message > configure: error:

You must have libxml2 >= 2.6.0 development headers installed to build.

I can see libxml2 version 2.6.27 installed..... any ideas?

Thanks.

---

### Post by cactaur on 2007-06-16
tvor: You have to install libxml2-dev along with libxml2

---

### Post by MagnetiK on 2007-06-16
Here it is : [http://www.getdeb.net/app.php?name=Pidgin](http://www.getdeb.net/app.php?name=Pidgin)

---

### Post by steveneddy on 2007-06-16
What is so hard about compiling?

---

### Post by xdarkxanarchyx on 2007-06-17
I don't know. I prefer to compile things actually.

---

### Post by tvor on 2007-06-17
cactaur: thanks for the tip - it worked perfectly! Unfortunately this installation did not supported SSL :-( also problems with big icons and QQ data error. So I used[ this thread]("http://ubuntuforums.org/showthread.php?t=475977&highlight=how+to+uninstall") to uninstall. Worked perfectly!

MagnetiK: awesome, this is what i was waiting for - missed it by few hours :-)!I have used this to install Pidgin

steveneddy: not hard at all, when it all works! ;-)

---

### Post by steveneddy on 2007-06-17
> **xdarkxanarchyx said:**
> I don't know. I prefer to compile things actually.

Myself - I fell as if I have more control and things run better after being compiled on MY machine.

---

### Post by kknd on 2007-06-17
How to compile pidgin 2.0.2:

sudo apt-get build-dep gaim

cd pidgin-source

./configure --prefix=/usr/yourchoosendir
make
sudo make install

---

### Post by Luk0r on 2007-06-17
The new 2.0.2 version is now on getdeb.

[http://www.getdeb.net/app.php?name=Pidgin](http://www.getdeb.net/app.php?name=Pidgin)

---

### Post by Kosimo on 2007-06-18
The thing is...
When I compiled by myself, pidgin was working. But, it didn't install the (misspelled words) and I couldn't uninstall it without having the source.
Then I tried the .deb 2.0.2 from getdeb.net and it installed it perfectly and I got the misspelled words corrector installed by defoult and I can remove it easily from terminal or synaptic.
Maybe pidgin has lots of extras included in the compilation in getdeb.  
How can I compile it with all this stuff enabled?

By the way I dream with a world where all software have a .deb release perfectly functional :)  That's the right way to take in my opinion guys. People wants things that works with one click. Then, if somebody wants the source code, there it is.

---

### Post by bbrewerg on 2007-06-18
i still don't understand why i can't get extendedprefs to show up in the plugins.... i hate these bloaty giant fonts and icons.

---

### Post by Corbelius on 2007-06-20
> **Kosimo said:**
> Fixed :)

How? tnx :)

---

### Post by Virtual DarKness on 2007-06-20
@Kosimo: how did you fixed the big icon problem? I'm facing it too.. 
are you still using the getdeb.net package?
thanks.

bye,
Giovanni.

---

### Post by Kosimo on 2007-06-20
> **Virtual DarKness said:**
> @Kosimo: how did you fixed the big icon problem? I'm facing it too.. 
are you still using the getdeb.net package?
thanks.

bye,
Giovanni.

Nope.. I couldn't fix the icon size.
When in vertical bar is still double size. There is a small trip to fix it (temporally). Take the bar, move it into horizontal position, then vertical again, the icon will have the normal size.
This is a bug from Pidgin 2.0.2 that wasn't present in 2.0.1. If is really annoying to someone I recommend to move to 2.0.1 'till the next version comes fixed. We have to notify to developers. Someone can do it?

Thanks.

---

### Post by Kosimo on 2007-06-20
By the way.
Can someone from KDE test it?

Have a vertical bar and open pidgin. The notification area icon should be in a wrong size (too big)

---

### Post by Kosimo on 2007-06-20
up ;)

---

### Post by Virtual DarKness on 2007-06-20
eheh cool.. so I'm not the only man on earth having the notification area on a vertical panel :D
thanks for the information and the tip.

bye,
Giovanni.

---

### Post by lostthetrail on 2007-06-24
> **kknd said:**
> How to compile pidgin 2.0.2:

sudo apt-get build-dep gaim

cd pidgin-source

./configure --prefix=/usr/yourchoosendir
make
sudo make install

So after these commands have been ran, what is the next step? I am a bit new to compiling. I thought I might benefit from giving it a try before downloading the deb.

As a side note, it appears everything worked correctly. I just don't know what to do now.

---

