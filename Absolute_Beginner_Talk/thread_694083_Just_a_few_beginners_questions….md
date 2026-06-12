---
title: "Just a few beginners questions…"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by Dissident85 on 2008-02-11
1) The bar at the top and bottom of the screen, when looking around on google image search I found that a lot of people have a transparent bar?? How is that done?

2) [http://www.troyandnaomi.com/images/Ubuntu_desktop_large.png](http://www.troyandnaomi.com/images/Ubuntu_desktop_large.png) i also noticed that people have this side bar sort of thing with all this info… like cpu usage and other teckie /geeky stuff… how do I get that? (oh and the pic I attached isn’t exactly the one I was looking for… but similar, I couldn’t find the other ones I found )

3) That little bar at the bottom of the screen… I did some research and found out that it is called avant or something? Well when I try to install it I get a whole lot of dependences. Do I just work my way down the list installing them all one by one to get it to work? Or is there an easier way? 

4)And finally, I have herd so much about this laptop HDD killer bug, how do I know if I am affected? 

By the way I am running ubunty 7.10 on a hp 530 laptop…

Thanks in advance:)

---

### Post by Tatty on 2008-02-11
1.  You need to right-click on the bar and there is something like "properties" which will let you do that (sorry, im not actually on a ubuntu machine at the moment to say for certain what it is called).

2.  That is called conky.  I have never used it myself but do a search on the forums for it.

3. How are you trying to install it?  synaptic is the easiest way and will take care of any dependancies.

---

### Post by Dissident85 on 2008-02-11
> **Tatty said:**
> 1.  You need to right-click on the bar and there is something like "properties" which will let you do that (sorry, im not actually on a ubuntu machine at the moment to say for certain what it is called).

2.  That is called conky.  I have never used it myself but do a search on the forums for it.

3. How are you trying to install it?  synaptic is the easiest way and will take care of any dependancies.

Cheers mate :) that for for (1) just about to research (2) on the forums now :):)

EDIT:

ummm i am using the synaptic package manager, but i just keeps coming up with all these dependancies it has and wont install?

---

### Post by jryprt on 2008-02-11
> **Dissident85 said:**
> 1) The bar at the top and bottom of the screen, when looking around on google image search I found that a lot of people have a transparent bar?? How is that done?

2) [http://www.troyandnaomi.com/images/Ubuntu_desktop_large.png](http://www.troyandnaomi.com/images/Ubuntu_desktop_large.png) i also noticed that people have this side bar sort of thing with all this info… like cpu usage and other teckie /geeky stuff… how do I get that? (oh and the pic I attached isn’t exactly the one I was looking for… but similar, I couldn’t find the other ones I found )

3) That little bar at the bottom of the screen… I did some research and found out that it is called avant or something? Well when I try to install it I get a whole lot of dependences. Do I just work my way down the list installing them all one by one to get it to work? Or is there an easier way? 

4)And finally, I have herd so much about this laptop HDD killer bug, how do I know if I am affected? 

By the way I am running ubunty 7.10 on a hp 530 laptop…

Thanks in advance:)

#1  Right click top or bottom panel go to Properties > Background choose solid color  then slide the Style bar to the left.

#2  Conky [This](http://ubuntuforums.org/showthread.php?t=205865) & [This](http://ubuntuforums.org/showthread.php?t=281865&highlight=conky)

#3  AWN

---

### Post by jan quark on 2008-02-11
1)>  The bar at the top and bottom of the screen, when looking around on google image search I found that a lot of people have a transparent bar?? How is that done?

right click, properties, solid background, set the transparency 
> 2) [http://www.troyandnaomi.com/images/U...ktop_large.png](http://www.troyandnaomi.com/images/U...ktop_large.png) i also noticed that people have this side bar sort of thing with all this info&#8230; like cpu usage and other teckie /geeky stuff&#8230; how do I get that? (oh and the pic I attached isn&#8217;t exactly the one I was looking for&#8230; but similar, I couldn&#8217;t find the other ones I found 

you mean probably the conky
see here
[http://conky.sourceforge.net/](http://conky.sourceforge.net/)


> 3) That little bar at the bottom of the screen&#8230; I did some research and found out that it is called avant or something? Well when I try to install it I get a whole lot of dependences. Do I just work my way down the list installing them all one by one to get it to work? Or is there an easier way?


there is a easier way try this

run in terminal

```
gksudo gedit /etc/apt/sources.list
```

add this line at the end of the file
```
##AWN
deb http://repo.freecreations.info/ubuntu gutsy freeverse
```

run 

```
sudo apt-get update
```

```
sudo apt-get install awn-core-applets awn-manager avant-window-navigator 
```

then start your bar by typing this into the terminal
```

avant-window-navigator 

```
> 4)And finally, I have herd so much about this laptop HDD killer bug, how do I know if I am affected?

never heard of that

---

### Post by Tatty on 2008-02-11
> **Dissident85 said:**
> ummm i am using the synaptic package manager, but i just keeps coming up with all these dependancies it has and wont install?

Interseting, it should normally take care of all the dependancies itself, what is it saying exactly?  

Also what repository are you using?

[http://wiki.awn-project.org/index.php?title=DistributionGuides#Reacocard.27s_Ubuntu_Gutsy_Repository]("http://wiki.awn-project.org/index.php?title=DistributionGuides#Reacocard.27s_Ubuntu_Gutsy_Repository")

There is a guide here on how to install, But I do not have AWN installed myself so i cant really guide you much more, might be best to follow jan quirk's advice above

---

### Post by Dissident85 on 2008-02-11
Cheers :) that should keep me busy for a while :)

---

### Post by Tatty on 2008-02-11
> **Dissident85 said:**
> Cheers :) that should keep me busy for a while :)

good luck! :)

---

### Post by jw5801 on 2008-02-11
By the way (4) was an issue with the older kernel in feisty. It wasn't likely to actually kill your hard drive in a hurry, just was improperly shut down, causing an emergency head park on shutdown. Given your average hard drive can deal with the emergency head park hundreds to thousands of times, it wasn't as dangerous as some of the hype might have lead people to believe.

Regardless, the kernel in Dapper didn't have this bug and the kernel in Gutsy doesn't have this bug, so if you're using either of the currently supported versions of Ubuntu, then you don't have this bug!

---

### Post by Dissident85 on 2008-02-11
> **jryprt said:**
> #1  Right click top or bottom panel go to Properties > Background choose solid color  then slide the Style bar to the left.

#2  Conky [This](http://ubuntuforums.org/showthread.php?t=205865) & [This](http://ubuntuforums.org/showthread.php?t=281865&highlight=conky)

#3  AWN

i am having a little trouble with installing conky... i get this error 
> checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
when i run this command?
> ./configure --prefix=/usr --mandir=/usr/share/man --infodir=/usr/share/info --datadir=/usr/share --sysconfdir=/etc --localstatedir=/var/lib --enable-xft --enable-seti --enable-double-buffer --enable-own-window --enable-proc-uptime --enable-mpd --enable-mldonkey --enable-x11 --enable-portmon --enable-infopipe
anyone :S 
[

---

### Post by jw5801 on 2008-02-11
You'll need to install the build-essential package to compile source code:
```
sudo apt-get install build-essential
```

---

### Post by Dissident85 on 2008-02-11
Cheers mate :) 

Sorry, but i am having another problem. i get this error when trying to install openssh-server
> openssh-server:
  Depends: openssh-client (=1:4.2p1-7ubuntu3) but 1:4.6p1-5build1 is to be installed

how do i get past that?

---

### Post by Joeb454 on 2008-02-11
Hmm...that is odd...it wants you to have an older version of openssh-client installed...

I'll have a look around google ;)

---

### Post by Dissident85 on 2008-02-11
> **Joeb454 said:**
> Hmm...that is odd...it wants you to have an older version of openssh-client installed...

I'll have a look around google ;)

i know... and i am getting it all the time, its driving me nuts!

---

### Post by Dissident85 on 2008-02-11
> **jw5801 said:**
> You'll need to install the build-essential package to compile source code:
```
sudo apt-get install build-essential
```

is there a way to install build-essential with out the cd?

---

### Post by jw5801 on 2008-02-11
Where are you installing openssh-server from? You have the version of openssh-client that is available in the repositories, are you trying to compile a newer version of openssh-server?

---

### Post by jw5801 on 2008-02-11
> **Dissident85 said:**
> is there a way to install build-essential with out the cd?

If you have an internet connection, make sure you have the repositories enabled. You may have to update your packages list as well if this is a vanilla install, run: ```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install build-essential
```
To tell your computer about the packages it has available, upgrade old packages to the newest version and to install the build-essential package.

---

### Post by Dissident85 on 2008-02-11
> **jw5801 said:**
> Where are you installing openssh-server from? You have the version of openssh-client that is available in the repositories, are you trying to compile a newer version of openssh-server?
no what i am typing is: 
```
sudo apt-get install openssh-server
```
then get
> The following packages have unmet dependencies:
  openssh-server: Depends: openssh-client (= 1:4.2p1-7ubuntu3) but 1:4.6p1-5build1 is to be installed

---

### Post by Dissident85 on 2008-02-11
> **jw5801 said:**
> If you have an internet connection, make sure you have the repositories enabled. You may have to update your packages list as well if this is a vanilla install, run: ```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install build-essential
```
To tell your computer about the packages it has available, upgrade old packages to the newest version and to install the build-essential package.

i got the same thing, how do i enable repositories?

---

### Post by JoshuaRL on 2008-02-11
Go into Settings->Preferences->Software Sources and make sure everything except the source code one is checkmarked.  Then run Update Manager.  Then try the build-essential package.

---

### Post by jw5801 on 2008-02-11
Also try running ```
sudo apt-get -f install
```That should hopefully fix the dependancy issue.

---

### Post by Dissident85 on 2008-02-11
> **JoshuaRL said:**
> Go into Settings->Preferences->Software Sources and make sure everything except the source code one is checkmarked.  Then run Update Manager.  Then try the build-essential package.

thats still not working, its still asking me to put the cd in? :S

---

### Post by jw5801 on 2008-02-11
Do you have an active internet connection on the Linux box you're trying to install the package?

---

### Post by Dissident85 on 2008-02-11
> **jw5801 said:**
> Also try running ```
sudo apt-get -f install
```That should hopefully fix the dependancy issue.

cheers mate, that worked.

---

### Post by Dissident85 on 2008-02-11
> **jw5801 said:**
> Do you have an active internet connection on the Linux box you're trying to install the package?

yeah, it just downloaded 190mb of updates when i ran the update manager

---

