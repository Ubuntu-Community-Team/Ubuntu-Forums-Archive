---
title: "update error ?"
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by Blade1357 on 2006-08-17
have an update error 404 sight not found anny ansers?

---

### Post by kb3hkg on 2006-08-17
can you give detail as to what you are doing at the time and maybe what site if known?

---

### Post by Blade1357 on 2006-08-17
the updat managet pop up an i go to download the updates an it give me an error 404 not found  [http://www.beerorkid.com/compiz/pool/main/f/fontconfig/fontconfig_2.3.2-7ubuntu1_i386.deb](http://www.beerorkid.com/compiz/pool/main/f/fontconfig/fontconfig_2.3.2-7ubuntu1_i386.deb)
an all of the others

---

### Post by kb3hkg on 2006-08-17
sounds like that file doesn't exist anymore or isn't accessible, you may want to edit /etc/apt/aources.list so that the line with that repository on it starts with a #

---

### Post by Blade1357 on 2006-08-17
well it an update from the auto manager an i ck the list it ther anny more sugestions

---

### Post by Blade1357 on 2006-08-17
an i also get this in the ternal 
 
 `fontconfig-config_2.3.2-7ubuntu1_all.deb'
Resolving [www.beerorkid.com](www.beerorkid.com)... 208.113.152.130
Connecting to www.beerorkid.com|208.113.152.130|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
20:20:51 ERROR 404: Not Found.

---

### Post by taurus on 2006-08-17
What does your /etc/apt/sources.list look like then?

```
more /etc/apt/sources.list
```

---

### Post by Blade1357 on 2006-08-17
####################################
### Official Ubuntu Repositories ###
####################################

# Dapper Final Release Repository
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

# Dapper Security Updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security multiverse

# Dapper Bugfix Updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates multiverse

# Dapper Backports (new software versions, provided by the Ubuntu Backports Project)
#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main

#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports restricted
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports universe
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports universe

#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports multiverse
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main


##############################
### Automatix Repositories ###
##############################

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

## created by automatixrepo3
deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main

that is wht it look like as of now

---

### Post by taurus on 2006-08-17
Look at the error message from apt-get and look at the last line of your /etc/apt/sources.list!  Detect something interesting there...  Try to comment it out by placing a # sign in front of "deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main" and run

```

sudo apt-get update
sudo apt-get upgrade

```

---

### Post by Blade1357 on 2006-08-17
tried that an it didnt work eather

---

### Post by taurus on 2006-08-17
Same error message!!!

---

### Post by Blade1357 on 2006-08-17
now i get this 
Do you want to continue [Y/n]? y
Err [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main libcairo2 1.2.2-0ubuntu2
  404 Not Found
Err [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main libvte4 1:0.12.2-0ubuntu2
  404 Not Found
Err [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main libvte-common 1:0.12.2-0ubuntu2
  404 Not Found
Err [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main python-vte 1:0.12.2-0ubuntu2
  404 Not Found
Failed to fetch [http://www.beerorkid.com/compiz/pool/main/libc/libcairo/libcairo2_1.2.2-0ubuntu2_i386.deb](http://www.beerorkid.com/compiz/pool/main/libc/libcairo/libcairo2_1.2.2-0ubuntu2_i386.deb)  404 Not Found
Failed to fetch [http://www.beerorkid.com/compiz/pool/main/v/vte/libvte4_0.12.2-0ubuntu2_i386.deb](http://www.beerorkid.com/compiz/pool/main/v/vte/libvte4_0.12.2-0ubuntu2_i386.deb)  404 Not Found
Failed to fetch [http://www.beerorkid.com/compiz/pool/main/v/vte/libvte-common_0.12.2-0ubuntu2_all.deb](http://www.beerorkid.com/compiz/pool/main/v/vte/libvte-common_0.12.2-0ubuntu2_all.deb)  404 Not Found
Failed to fetch [http://www.beerorkid.com/compiz/pool/main/v/vte/python-vte_0.12.2-0ubuntu2_i386.deb](http://www.beerorkid.com/compiz/pool/main/v/vte/python-vte_0.12.2-0ubuntu2_i386.deb)  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

### Post by taurus on 2006-08-17
Okay, I need to see your /etc/apt/sources.list again because you still have that bloody thing, "deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main", in!!!

---

### Post by Blade1357 on 2006-08-17
####################################
### Official Ubuntu Repositories ###
####################################

# Dapper Final Release Repository
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

# Dapper Security Updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security multiverse

# Dapper Bugfix Updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates multiverse

# Dapper Backports (new software versions, provided by the Ubuntu Backports Project)
#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main

#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports restricted
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports universe
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports universe

#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports multiverse
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main


##############################
### Automatix Repositories ###
##############################

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

## created by automatixrepo3
deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main
 ther it is an the putting the # in front of the deb well it wont run that way i have tried

---

### Post by taurus on 2006-08-17
you NEED to put a # in front of this line "deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main" in your /etc/apt/sources.list so it would look something like this now!!!  ](*,) 

```

## created by automatixrepo3
#deb http://www.beerorkid.com/compiz/ dapper main

```

---

### Post by Blade1357 on 2006-08-17
ok i did that but then i get noting the update incon is still ther

---

### Post by taurus on 2006-08-17
Try this from a terminal and what do you get?

```

sudo aptitude update
sudo aptitude upgrade

```

---

### Post by Blade1357 on 2006-08-17
noting just this 
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mike@mike-desktop:~$

---

### Post by taurus on 2006-08-17
Well, maybe you want to remove the # sign in front of the universe & multiverse in /etc/apt/sources.list and run those two commands again then...

---

### Post by Blade1357 on 2006-08-17
thanks for all of your help i think that did it it finly went away thanks for all of your help ther my friend

---

### Post by taurus on 2006-08-17
So everything is working fine now, upgrading!

---

### Post by kb3hkg on 2006-08-17
comment out that line then on command line type apt-get update. after that try seeing if it works.

edit: nevermind, resolved while typing

---

