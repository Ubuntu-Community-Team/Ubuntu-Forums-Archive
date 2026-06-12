---
title: "[SOLVED] Gnome and AmaroK"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by Inxsible on 2007-05-02
I liked all the features in Amarok. Also, on comparing Amarok with RhythmBox, Amarok trounced RB.

So i went ahead and installed Amarok and removed RB. Since then I have had a lot of trouble even starting the app. It starts the first time, then tells me that the MP3 support is not installed, do you wanna install it. I say yes and after the install it tells me to restart Amarok.

Amarok never comes up at all after that. I have tried installing and uninstalling Amarok atleast 6 times now. Finally, I am giving up now and going back to RB.

Moral of the story : If you use Gnome, stick to Gnome apps as much as you can or be prepared for issues. Same for KDE (probably, I haven't used it).

Although, AmaroK has now become Amarok (note the smaller K), it is still a Kubuntu specific app which "may" work in Gnome for some. I am just not that some :(

---

### Post by igknighted on 2007-05-02
To be specific, its a KDE app, not a kubuntu app.  But the difference here is unimportant.  I don't think the codec installer can handle Amarok because it uses a different back-end (xine) then the gnome players (gstreamer).  It needs different packages to enable playback.  If you read the restricted formats page in the wiki it should show you how to install the proper xine packages to enable mp3's.

---

### Post by WanderingKnight on 2007-05-02
I had the same problem with Amarok. The answer is: get exile. It's Amarok's GNOME version. You can get it with automatix2.

---

### Post by igknighted on 2007-05-02
> **WanderingKnight said:**
> I had the same problem with Amarok. The answer is: get exile. It's Amarok's GNOME version. You can get it with automatix2.

Exile is OK but has many flaws too.  The internet radio features are very poor for example.  There really is no GREAT app for gnome, I have found that for updating my ipod and playing songs on my computer and internet radio that rhythmbox works very very well, despite its bland looks.  Also check out listen, xmms, exaile and songbird (VERY beta).

---

### Post by Inxsible on 2007-05-03
Does Exaile and/or Exile or listen have support for iPods. I dont want to install one player for listening and another for transferring music to and from iPods. I know Amarok has iPod compatibility and so does RhythmBox ...so I guess I will stick to RB

---

### Post by igknighted on 2007-05-03
> **Inxsible said:**
> Does Exaile and/or Exile or listen have support for iPods. I dont want to install one player for listening and another for transferring music to and from iPods. I know Amarok has iPod compatibility and so does RhythmBox ...so I guess I will stick to RB

Yes, exaile has support for ipods

---

### Post by InuyashaDuelist on 2007-05-03
Exaile isn't exactly up to Amarok's standards yet, but if you're looking for something that is for GNOME and not KDE, Exaile would still be the best choice.

---

### Post by BLTicklemonster on 2007-05-03
There's a new player out, called [Dissent](http://ubuntuforums.org/showthread.php?t=423825) you can try. Still in development, but it's really good once you get it going.

---

### Post by sumitsen on 2007-05-03
Hi All,

Try this before giving up....

Go to /usr/lib/amarok. There you will find install mp3. Click it , mp3 support will be installed. Then start amarok, it will work fine.

Cheers
Sumit

---

### Post by ronocdh on 2007-05-05
> **sumitsen said:**
> Hi All,

Try this before giving up....

Go to /usr/lib/amarok. There you will find install mp3. Click it , mp3 support will be installed. Then start amarok, it will work fine.

Cheers
Sumit
This is a nice method, but I just went to Synaptic and grabbed the xine "extra codecs" pack when Amarok failed to grab it itself (in Gnome).

Thanks for mentioning Dissent, Ticklemonster!

---

### Post by Happy_Man on 2007-05-05
Well, there is an Amarok clone for GNOME available in the repos, it's called Exaile. You could use that, I'm using it and have had no problems, ever.

---

### Post by orb9220 on 2007-05-05
> Well, there is an Amarok clone for GNOME available in the repos, it's called Exaile.

I'm sorry but it is no way a clone of Amarok. It Lacks about 50-70% of the features of Amarok.
How is that a clone.

Clone = EXACT duplicate.

Exaile looks promising but it is no Amarok.

---

### Post by angkor on 2007-05-05
I've been using amarok on gnome for a long time now. It used to be a pain in the a^^, until I installed it from SVN using a script.
[http://amarok.kde.org/wiki/Amarok-svn](http://amarok.kde.org/wiki/Amarok-svn)

Since then it has been nothing but easy sailing for me. Ipod support was a bit flaky at first but has  much improved and amarok never crashes on me anymore.

---

### Post by Pistolla on 2007-05-05
i use Amarok almost exclusively in Gnome. The thing is, i have Kubuntu as a secondary Desktop (of which i cannot b/c of a keyboad prob) and i see no problem whatsoever. Is it b/c i have Kubuntu, i know not but i LOVE it

---

### Post by bean77 on 2007-05-15
Can I get other applications like Gnutella to sync up with Singbird so I can get music onto my iPod?  Is there another method to get music on my iPod?  I have Songbird, Rhythmbox, Amarok, and I'm still very confused.

---

### Post by wataboutbob on 2007-05-15
> **bean77 said:**
> Can I get other applications like Gnutella to sync up with Singbird so I can get music onto my iPod?  Is there another method to get music on my iPod?  I have Songbird, Rhythmbox, Amarok, and I'm still very confused.

Never could get Exaile and Songbird to sync with my 5G iPod... while Rythmbox syncs with my iPod, I use Amarok as its feature list is so much better than RB and it sync perfectly too.

---

### Post by TNBY963 on 2007-05-15
I'm using Amarok for a long time on Gnome and it works very well. The only thing that only works sometimes are the scripts, but I think it's because the scripts look for KDE specific stuff wich I haven't installed. Whetever it is, it doesn't bother me much.

I'm running Ubuntu studio and was feeling lazy, so I installed via the apps menu > install. Very easy.

Greetz

Gert

---

### Post by Iokua on 2007-05-15
I also use Amarok in GNOME without any problems. Once all of the codecs were installed, Amarok hasn't given me so much as a hiccup in months.

---

### Post by Miroku on 2007-11-02
am i the only one where using amarok in gnome gives me random stutters? its not constant or anything, it just happens once in a while. it will be playing an mp3 and then 'skip' like how a cd skips and then continue to play fine. i tried playing around with the OSS and stuff but no luck. rhythmbox and movies and other media works fine in other programs.

---

