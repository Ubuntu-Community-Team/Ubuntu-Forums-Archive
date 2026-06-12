---
title: "Real player wont start...."
date: 2005-12-18
forum: Absolute Beginner Talk
---

### Post by dannyngweekiat_85 on 2005-12-18
I just manage to get real player in the system... install all no problem... it even show up in application. but then th eprogram wont execute when i try to run it.. is the anything that i did wrong during the process? :confused:  i downloaded it from real.com...

---

### Post by djur on 2005-12-18
I had the same problem.  I ended up just using mplayer which is in the repositories.  For the most part this player has more codecs installed than windows players, I highly recommend it.

---

### Post by doitashimashite on 2005-12-18
It won't run? What happens when you do this:

ALT-F2
realplay

---

### Post by Perfect Storm on 2005-12-18
And you follow the installation instruction?

```

cd /where/the/file/is
chmod a+x RealPlayer10GOLD.bin
./RealPlayer10GOLD.bin

```

---

### Post by Perfect Storm on 2005-12-18
The easist thing is to add this to your repo:

```
 sudo gedit /etc/apt/sources.list
```

## Penguin Liberation Front
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

```
sudo apt-get update
sudo apt-get install realplay

```

---

### Post by dannyngweekiat_85 on 2005-12-19
[QUOTE=Artificial Intelligence]And you follow the installation instruction?

```

cd /where/the/file/is
chmod a+x RealPlayer10GOLD.bin
./RealPlayer10GOLD.bin

```[/QUOTE]

i follow this to install... but then dont know y the things still cannot start. manage to get it on the application already. but then the same thing happen ... it wont go... wierd....:confused: does mplayer got real support?

---

### Post by jetronic on 2005-12-19
I had the same exact problem.  I discovered that you have to completely remove the existing real player 8.0.11 that's in synaptic manager first.  Then install the real player that you got off the real site through apt-get command as outlined above.  Otherwise they will conflict with each other.  HTH

---

### Post by dannyngweekiat_85 on 2005-12-19
i havent install 8.0.11 b4 .... and in the synaptic manager i cant c any of things related to real player also... Is there any other reason that this thing will happen?

---

### Post by dannyngweekiat_85 on 2005-12-19
i havent install 8.0.11 b4 .... and in the synaptic manager i cant c any of things related to real player also... Is there any other reason that this thing will happen?

---

### Post by Perfect Storm on 2005-12-19
and you did add the lines I described in post #5 ?

---

### Post by dannyngweekiat_85 on 2005-12-19
[code]
Failed to fetch http://packages.freecontrib.org/ubuntu/plf/dists/breezy/free/binary-amd64/Packages.gz  404 Not Found
Failed to fetch http://packages.freecontrib.org/ubuntu/plf/dists/breezy/non-free/binary-amd64/Packages.gz  404 Not Found
Reading package lists... Done
W: Couldn't stat source package list http://packages.freecontrib.org breezy/free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://packages.freecontrib.org breezy/non-free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_non-free_binary-amd64_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
[\code]
i got this error when i am in the update, thats y i did not use it...

---

### Post by Perfect Storm on 2005-12-20
aaah you on amd64 arch, that's explain. PLF does only support i386 arch.

---

### Post by dannyngweekiat_85 on 2005-12-20
icic...no wonder cant... nvm i try to search for any other player c to make this work... thanks every 1 here!!!

---

### Post by Perfect Storm on 2005-12-20
But you could try following PLFs suggestion: [http://wiki.ubuntu-fr.org/doc/plf#archs_other_than_i386](http://wiki.ubuntu-fr.org/doc/plf#archs_other_than_i386)

just change libdvdcss2 with realplay

I don't know if it works

---

### Post by dannyngweekiat_85 on 2005-12-20
rahxephon@RahXephon:~$ sudo apt-get build-dep libdvdcss2
Reading package lists... Done
Building dependency tree... Done
E: Unable to find a source package for libdvdcss2

this come out for the second step...
should i add back the reprositry before?

---

