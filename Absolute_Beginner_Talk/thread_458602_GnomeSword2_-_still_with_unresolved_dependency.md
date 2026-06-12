---
title: "GnomeSword2 - still with unresolved dependency"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by ken_38 on 2007-05-29
Having got everything up and running really well - so I thought - on Edgy, I landed myself with this puzzler - at least it is for me.
Tried to install GnomeSword2 ["works well with Ubuntu"] through Add/Remove and received "conflict with other installed software" message.
Went to SPM as instructed and tried install there. Received the following message:
[CENTER]The following packages have unresolved dependencies. Make sure that 
all required repositories are added and enabled in the preferences.
GnomeSword depends:  libsword5c2ca (>=1.5.8-7) but it is not
installable.[/CENTER]
I could only find libsword6 in SPM, already installed.
Questions:
1] how can I get the "not installable" item and how can I find it in the first place? Third party is enabled.
2] if I can't get it, is there anything I can use instead?
3] how is GnomeSword2 on the A/R list if it cannot be installed because of an unresolved dependency which can't seem to be resolved. This is not meant to be a moan - I'm just thinking I may have missed something blindingly obvious.
If **Chaplanger** who posted an original thread on this in Dec.06 is still out there can he give me more detail on his solution, or if **ComplexNumber** reads this can he take a new user through to a successful conclusion?  Or if anyone else can help me find the way through, I'll be indebted.:confused::confused:

---

### Post by zvacet on 2007-05-30
Do you have universe repository open? Is this what are you looking for?

[http://packages.ubuntu.com/edgy/gnome/gnomesword]("http://packages.ubuntu.com/edgy/gnome/gnomesword")


Install all dependencies first.

---

### Post by ken_38 on 2007-05-30
Thanks - but did that when setting up wanted packages at beginning.

If you refer to thread Resolving Software Conflict [Dec 29 06] by Chaplanger, you'll see the problem is in a needed but unresolved - and unobtainable - dependency. Chaplanger found a solution, bujt got lost trying to follow his steps - not enough detail.

---

### Post by ken_38 on 2007-05-30
Please - can anyone give me an up-to-date way of installing this - especially accessing the libsword5c2a package - the one GnomeSword will recognise.

I tried the links suggested in two previous threads [Dec06 and Jan07] only to find that they were broken or no longer applied.

Does this mean it's now impossible for a new user to install this package? I did see a suggestion about installing eSword using Wine, but I'm not ready to think about going down the Wine path yet.

---

### Post by kittyhawk63 on 2007-05-30
> **ken_38 said:**
> Please - can anyone give me an up-to-date way of installing this - especially accessing the libsword5c2a package - the one GnomeSword will recognise.
I tried the links suggested in two previous threads [Dec06 and Jan07] only to find that they were broken or no longer applied.
Does this mean it's now impossible for a new user to install this package? I did see a suggestion about installing eSword using Wine, but I'm not ready to think about going down the Wine path yet.

I found "libsword5c2a" ready for installing from Synaptic. Did you look there? I am using Dapper 6.06. When I found "GnomeSword" in Synaptic and checked it, it automatically selected "libsword5c2a" to be installed. I just installed GnomeSword and everything worked fine. I prefer eSword. It has much more selections as you are probably aware.

---

### Post by david_kt on 2007-05-30
I have tried gnomesword, it is much inferior compared to Esword. Why don't you try Esword? Below is how to install Esword,

[http://ubuntuforums.org/showthread.php?t=404042](http://ubuntuforums.org/showthread.php?t=404042)

But you must install wine before you could use that how to

```
sudo apt-get install wine
```

Make sure universe reps is enabled.

DK

---

### Post by ken_38 on 2007-05-30
Thanks **kittyhawk63** and **davidkt** for replies. Sorry to be so long getting back. "...a friend of mine on a journey has come to me..."

1] Kittyhawk63. I haven't got Dapper - I'm on Edgy and support of the libsword file for that seems to have been suspended even on Debian.
2] To both of you - I know what you mean about e-sword.....but it does mean installing wine. I'm hoping I don't mess it up. I'll give it a go anyway. Watch this space for a*** h--e--l--p*** or a ***yippee!!***

---

### Post by ken_38 on 2007-06-01
Having thought about yesterday's advice, I've decided to go with e-sword through Wine. Because of this, can
you answer one [I hope] more thing.
Do I have to install the e-sword package into /.wine? 
OR
Can I use my e-sword installation on Windows and make a link to it?  I suppose it's the first, but I thought that the second might be handier and space-saving.
Do I use the Wine package in Synaptic?  I see the Ubuntu doc. says the WineHQ newer Edgy version is  "not recommended". Does this mean that it will cause problems, or that it hasn't yet been taken into Ubuntu itself?
***HAVE MOVED THIS ON TO A SEPARATE THREAD IN CASE PEOPLE THINK IT'S ENDED - EASIER TO SPOT***

---

