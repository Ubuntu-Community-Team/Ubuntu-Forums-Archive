---
title: "Ubuntu 8.04 apt-get error"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by sunra350 on 2008-04-05
I ran the following command so that I could install acroreader. I'm using Ubuntu 8.04

sudo wget [http://medibuntu.sos-sts.com/sources.list.d/feisty.list](http://medibuntu.sos-sts.com/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/medibuntu.list

Now when I run apt-get update I get the following error:

Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list

How can I revert back to my original source.lst? 

Any and All Help Welcomed

THX

---

### Post by Oldsoldier2003 on 2008-04-05
> **sunra350 said:**
> I ran the following command so that I could install acroreader. I'm using Ubuntu 8.04

sudo wget [http://medibuntu.sos-sts.com/sources.list.d/feisty.list](http://medibuntu.sos-sts.com/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/medibuntu.list

Now when I run apt-get update I get the following error:

Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list

How can I revert back to my original source.lst? 

Any and All Help Welcomed

THX

```
sudo rm /etc/apt/sources.list.d/medibuntu.list
```

then go into System>Administration>Software Sources and check the repos you want. It appears you followed a bad tutorial on how install the repo.

---

### Post by The Titan on 2008-04-05
> **sunra350 said:**
> I ran the following command so that I could install acroreader. I'm using Ubuntu 8.04

sudo wget [http://medibuntu.sos-sts.com/sources.list.d/feisty.list](http://medibuntu.sos-sts.com/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/medibuntu.list

Now when I run apt-get update I get the following error:

Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list

How can I revert back to my original source.lst? 

Any and All Help Welcomed

THX
can you post the output of this command?  
```

cat /etc/apt/sources.list

```

---

### Post by Oldsoldier2003 on 2008-04-05
> **The Titan said:**
> can you post the output of this command?  
```

cat /etc/apt/sources.list

```

edit: There is no need to view the sources.list based on the content of the error message. The OP followed a tutorial that uses an out of date URL for the medibuntu repos. This problem is encountered several times a week. Clearing the malformed sources list for medibuntu will fix the issue.

Basically what happens is it wgets the html page that resides where the old  repo used to live. the problem is that it is in a format that confuses the package managers

---

### Post by The Titan on 2008-04-05
> **Oldsoldier2003 said:**
> what the cat will show is the html content of the page that resides at the url of the old medibuntu repo. There are several outdated tutorials that cause this issue... we see it several times a week...
it wont show the content of the sources.list file?

---

### Post by philinux on 2008-04-05
For 8.04 use this.

[http://www.adobe.com/products/acrobat/readstep2_allversions.html](http://www.adobe.com/products/acrobat/readstep2_allversions.html)

Medibuntu's version fails to install the firefox plugin. It's bugged at launchpad.

---

### Post by sunra350 on 2008-04-05
> **Oldsoldier2003 said:**
> ```
sudo rm /etc/apt/sources.list.d/medibuntu.list
```

then go into System>Administration>Software Sources and check the repos you want. It appears you followed a bad tutorial on how install the repo.

That worked! My system is functioning as it should. Thanks for the help. Ya gotta love Ubuntu and this forumn. I posted an issue and 2 minutes later I got a fix! That would never happen with Micro$haft :)

---

### Post by Oldsoldier2003 on 2008-04-05
> **The Titan said:**
> it wont show the content of the sources.list file?

actually it will I pressed reply too fast :) but there is no need to cat his sources list based on the error message

---

