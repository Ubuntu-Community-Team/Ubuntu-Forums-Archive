---
title: "Update manager..."
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by road_rage on 2008-04-08
I ran update manager, it finishes and then says "Your system is up-to-date", but then lists an update package for Miro under "other updates" but it is grayed out and can't seem to resolve this. 

I did some searching around both here and google and can't find a resolution. I tried to remove the repository and then re-add it as I saw some similar posts, but this did not help. 

I would really like to resolve this as I am having issues with Miro and think they have been corrected on newer code but for some reason that update seems stuck ?

Here is an image of the error.

[[IMG]http://img392.imageshack.us/img392/8514/screenshotupdatemanagerqi6.th.png[/IMG]](http://img392.imageshack.us/my.php?image=screenshotupdatemanagerqi6.png)

When I do an "sudo apt-get update" here are the results to that repository.
```
Ign http://ftp.osuosl.org gutsy/ Release.gpg
Ign http://ftp.osuosl.org gutsy/ Translation-en_US                                    
Ign http://ftp.osuosl.org gutsy/ Release                                              
Ign http://ftp.osuosl.org gutsy/ Packages 
```

The only thing I have not tried is to remove and re-install the package, but would rather not unless I find no other way to correct. 

TYIA,

--RR

---

### Post by warbread on 2008-04-08
Open up Synaptic and look under the "Broken" filter.  If there's nothing there, try pressing the "Mark All Upgrades" button in the upper lefthand side of the screen and then "Apply".

---

### Post by zvacet on 2008-04-08
```
sudo apt-get updadte && sudo apt-get upgrade
```

---

### Post by road_rage on 2008-04-08
I tried both. I first tried the gui and then the cmd. The gui did not see any broken, the command line returned the following and then returned back to the cmd prompt. 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  miro
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```

--RR

---

### Post by warbread on 2008-04-08
Ok, then.  Sudo apt-get dist-upgrade.

---

### Post by road_rage on 2008-04-08
That also did not seem to resolve the issue.

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  miro
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```

--RR

---

### Post by zvacet on 2008-04-09
```
sudo apt-get -f install
```

---

