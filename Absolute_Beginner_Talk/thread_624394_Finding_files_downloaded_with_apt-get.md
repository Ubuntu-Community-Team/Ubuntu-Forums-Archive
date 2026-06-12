---
title: "Finding files downloaded with apt-get"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by kukuku on 2007-11-26
I heard about this remake of my old favorite game, Maze of Galious, and then saw that it supports Linux from its homepage. The only problem is that their download servers are offline and it's been a couple years since any real activity there.

Google brought up the tidbit that the Debian repos have the datafiles, so on a whim I executed apt-get mazeofgalious-data. It downloaded some stuff required to compiling the sources, but I have no idea where they were put after that. 

Examples of commands I tried:

```

find -name 'maze*'
whereis mazeofgalious-data

```

And some others with no success. I ran sudo updatedb at some point too, but it didn't help any. Testing find -name on stuff I know exists on the hard drives brings up the files, so I can't quite imagine what the problem is. I've interest in two matters: firstly how to correctly locate a file downloaded by apt-get, and failing that figuring out where apt-get puts its downloaded files. Or should I delete the package and use apt-get -d to retrieve it again?

Could someone help with these mysteries, please?

---

### Post by FuturePilot on 2007-11-26
Apt puts all downloaded packages in /var/cache/apt/archives

---

### Post by kukuku on 2007-11-27
Thanks, I found them.

---

