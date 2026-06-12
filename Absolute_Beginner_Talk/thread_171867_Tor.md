---
title: "Tor"
date: 2006-05-07
forum: Absolute Beginner Talk
---

### Post by sophtpaw on 2006-05-07
Stumbled upon Tor reading this months Linux Magazine or Format(dont remember which)

[http://tor.eff.org/index.html.en]("http://tor.eff.org/index.html.en")


It is in Ubuntu repositories and i installed it with synaptic but i can't run it successfully from command line. 

Is there a line in the /etc/apt/sources.list i need to add?

There was mention of lines to add in regard to the Debian/Sarge example which was used in the magazine article.

They were:

deb://mirror.noreply.org/pub/tor sarge main  (hit return/next line)
deb-src [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) sarge main (save)

Would i replace sarge with ubuntu or breezy? but its already in the repos so that doesn't make sense come to think of it. So, but why is it not working then? :confused: 

As usual much obliged for any help and comments

--
sophtpaw

---

### Post by sophtpaw on 2006-05-07
This is the read-out from running Tor in cli:

-bc:~$ tor
May 07 19:43:32.165 [notice] Tor v0.1.0.15. This is experimental software. Do no t rely on it for strong anonymity.
May 07 19:43:32.178 [warn] /var/lib/tor is not owned by this UID (1000). You mus t fix this to proceed.
May 07 19:43:32.178 [err] options_act(): Couldn't access/create private data dir ectory /var/lib/tor
May 07 19:43:32.178 [err] init_from_config(): Acting on config options left us i n a broken state. Dying.

Just occured to me this data could help. I can't translate it into anything meaningful unfortunately. :?: 

--
sophtpaw

---

### Post by Rinzwind on 2006-05-07
> May 07 19:43:32.178 [warn] /var/lib/tor is not owned by this UID (1000). You mus t fix this to proceed.

This says you need to change the owner of this file.
It's probably set as ROOT and not your username.

do an 
**ls -l /var/lib/tor**
and look at the username of the file.

Then a 
**chown {username} /var/lib/tor**
MIGHT do the trick.


OR 1st do a 
**sudo tor**
If that works you know it's cuz of wrong rights to the owner of that file for sure.


I read about it too in Tux Mag :)

---

### Post by helpme on 2006-05-07
Don't know if it helps, but there's a good howto in the howto section that worked for me:
[http://ubuntuforums.org/showthread.php?t=95527](http://ubuntuforums.org/showthread.php?t=95527)

---

### Post by sophtpaw on 2006-05-07
[QUOTE=Rinzwind]This says you need to change the owner of this file.
It's probably set as ROOT and not your username.

do an 
**ls -l /var/lib/tor**
and look at the username of the file.

Then a 
**chown {username} /var/lib/tor**
MIGHT do the trick.


OR 1st do a 
**sudo tor**
If that works you know it's cuz of wrong rights to the owner of that file for sure.


I read about it too in Tux Mag :)[/QUOTE]


Hi Rinzwind,

yea, you read it too-looks good, huh? just what i want.

Well, i cd'd, which is what i think you meant, into /var/lib/tor

then i typed chown [myusername] /var/lib/tor

Now when i type tor i get a different output. Look: 

-6a-bc:~$ tor
May 07 21:03:34.536 [notice] Tor v0.1.0.15. This is experimental software. Do not rely on it for strong anonymity.


This suggests that it works? Certainly, something has changed and it doesn't say 'dying' which is not what i wanted to hear. But the thing is, NOW what?!

Is it just running/working now in the background? How can i test it. I know there was something in the mag, but i don't have it in front of me.

thx again,

--
sophtpaw

P.S By the way sudo tor didn't do the trick to start with

---

### Post by Rinzwind on 2006-05-07
ps -ef | grep tor

shows you if a process named tor is running.

And yes from the documentation from synaptic I think it's a deamon/server you started. There must be a conf file somewhere.

And you probably can use your browser to do stuff.

edit1: you also need this: [http://www.privoxy.org/](http://www.privoxy.org/)
edit2: and you need this firefox plugin too [https://addons.mozilla.org/addon.php?id=125](https://addons.mozilla.org/addon.php?id=125)
It adds a new toolbar to FF

edit3: and to conclude all my edits:
here's a tutorial: [http://tor.eff.org/docs/tor-doc-unix.html.en#privoxy](http://tor.eff.org/docs/tor-doc-unix.html.en#privoxy)

---

### Post by sophtpaw on 2006-05-07
[QUOTE=Rinzwind]ps -ef | grep tor

shows you if a process named tor is running.

And yes from the documentation from synaptic I think it's a deamon/server you started. There must be a conf file somewhere.

And you probably can use your browser to do stuff.

edit1: you also need this: [http://www.privoxy.org/](http://www.privoxy.org/)
edit2: and you need this firefox plugin too [https://addons.mozilla.org/addon.php?id=125](https://addons.mozilla.org/addon.php?id=125)
It adds a new toolbar to FF

edit3: and to conclude all my edits:
here's a tutorial: [http://tor.eff.org/docs/tor-doc-unix.html.en#privoxy](http://tor.eff.org/docs/tor-doc-unix.html.en#privoxy)[/QUOTE]

Thx for that Rinzwind,

I already installed privoxy, when i installed tor, but thx for the link i will check out the documentation

did edit 2,

Will read your final tutorial - thx ;) 

--
sophtpaw

---

### Post by sophtpaw on 2006-05-07
[QUOTE=helpme]Don't know if it helps, but there's a good howto in the howto section that worked for me:
[http://ubuntuforums.org/showthread.php?t=95527](http://ubuntuforums.org/showthread.php?t=95527)[/QUOTE]

helpme, 

thx for the link! :D 

--
sophtpaw

---

### Post by sophtpaw on 2006-05-07
[QUOTE=Rinzwind]ps -ef | grep tor

shows you if a process named tor is running.

And yes from the documentation from synaptic I think it's a deamon/server you started. There must be a conf file somewhere.

And you probably can use your browser to do stuff.

edit1: you also need this: [http://www.privoxy.org/](http://www.privoxy.org/)
edit2: and you need this firefox plugin too [https://addons.mozilla.org/addon.php?id=125](https://addons.mozilla.org/addon.php?id=125)
It adds a new toolbar to FF

edit3: and to conclude all my edits:
here's a tutorial: [http://tor.eff.org/docs/tor-doc-unix.html.en#privoxy](http://tor.eff.org/docs/tor-doc-unix.html.en#privoxy)[/QUOTE]


Great Tutorial! 

I've got Tor running here now, but geez it's slow isn't? i expected it might be slower but not as considerably slower than it is. anyway, it has its use

--
sophtpaw

---

### Post by Rinzwind on 2006-05-08
[QUOTE=sophtpaw]Great Tutorial! 

I've got Tor running here now, but geez it's slow isn't? i expected it might be slower but not as considerably slower than it is. anyway, it has its use

--
sophtpaw[/QUOTE]

Yes. Enctrypted data or rerouting your connection is ALWAYS slow :) :)

Oh and I bought the Linux Magazine today (always comes a week later in Holland) and I read the article you mentioned. Tor/Pivoxy is very well explained in the article.

AntsP2P is also a very nifty tool! It'll replace bittorent.Wanna bet? :D

---

