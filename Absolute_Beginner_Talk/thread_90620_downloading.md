---
title: "downloading"
date: 2005-11-15
forum: Absolute Beginner Talk
---

### Post by catflea on 2005-11-15
Aside from gaming one of the only things that stop me from keeping ubuntu on all the time is downloading from a P2P type client.

I've got aMuke running,  but its always sooooo slow and can't seem to handle more than 1 download at once  (in limewire under XP i have been known to have download rates in excess of 100k - in aMule I am exceptionally lucky if I hit 5k)

any suggestions for a differenct client or how I might be able to change some settings to get quicker downloads?   Its mighy irritating!

\cheers

---

### Post by Chayak on 2005-11-15
I know some good P2P apps exist, but personally I've gotten 300k+ speeds with bittorrent so why use them?

---

### Post by Kvark on 2005-11-15
If you like Limewire then use that under Ubuntu. It's not in the repos so you'll have to go to their website to download it. It also needs Java, search the forums for a Java howto if you run into any problems.

---

### Post by yoshic on 2005-11-15
hi, i think you should try gtk-gnutella, works great, it's a p2p client based on gnutella network ;) 

Simply:
```

apt-get install gtk-gnutella

```

(make sure you have enabled the universe repository :p)

and then under the web aplications select gtk-gnutella ;) 

also you shoul look at the [Wondershaper How-To]("http://www.ubuntuforums.org/showthread.php?t=25911&highlight=wondershaper") to enhace your conection performance.:p ;)

---

### Post by catflea on 2005-11-15
[QUOTE=Chayak]I know some good P2P apps exist, but personally I've gotten 300k+ speeds with bittorrent so why use them?[/QUOTE]

Because my bittorrent client (bittornado) doesn't seem to be working too well.   Also, some things are easier to find in P2P

---

### Post by catflea on 2005-11-15
[QUOTE=yoshic]hi, i think you should try gtk-gnutella, works great, it's a p2p client based on gnutella network ;) 

Simply:
```

apt-get install gtk-gnutella

```
[/quote]


Got

```
dan@epic:~$ apt-get install gtk-gnutella
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
dan@epic:~$

```

????????

---

### Post by Kvark on 2005-11-15
You need root access to install programs, just add sudo in front of the command to get root access:
```
sudo apt-get install gtk-gnutella
```

---

### Post by catflea on 2005-11-15
Slaps self in face - I shoulda known to sudo it!   Guess its the newbisms showing through?

---

### Post by Chayak on 2005-11-15
[QUOTE=catflea]Because my bittorrent client (bittornado) doesn't seem to be working too well.   Also, some things are easier to find in P2P[/QUOTE]
 That's because you don't know the right places to look :cool:

---

