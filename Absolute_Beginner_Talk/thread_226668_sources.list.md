---
title: "sources.list"
date: 2006-07-31
forum: Absolute Beginner Talk
---

### Post by greyash99 on 2006-07-31
I messed up my sources.list file. is there the default (or better one) somewhere?

---

### Post by Titus A Duxass on 2006-07-31
google with ubuntu repositories generator or source-o-matic.

---

### Post by moma on 2006-07-31
Step 6) here 
o---> [http://www.futuredesktop.org/]("http://www.futuredesktop.org/")

---

### Post by _simon_ on 2006-07-31
Here's mine if you want it, never given me any issues:

```

####################################
### Official Ubuntu Repositories ###
####################################

# Dapper Final Release Repository
deb http://archive.ubuntu.com/ubuntu dapper main
deb-src http://archive.ubuntu.com/ubuntu dapper main

deb http://archive.ubuntu.com/ubuntu dapper restricted
deb-src http://archive.ubuntu.com/ubuntu dapper restricted

deb http://archive.ubuntu.com/ubuntu dapper universe
deb-src http://archive.ubuntu.com/ubuntu dapper universe

deb http://archive.ubuntu.com/ubuntu dapper multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper multiverse

# Dapper Security Updates
deb http://archive.ubuntu.com/ubuntu dapper-security main
deb-src http://archive.ubuntu.com/ubuntu dapper-security main

deb http://archive.ubuntu.com/ubuntu dapper-security restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-security restricted

deb http://archive.ubuntu.com/ubuntu dapper-security universe
deb-src http://archive.ubuntu.com/ubuntu dapper-security universe

deb http://archive.ubuntu.com/ubuntu dapper-security multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-security multiverse

# Dapper Bugfix Updates
deb http://archive.ubuntu.com/ubuntu dapper-updates main
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main

deb http://archive.ubuntu.com/ubuntu dapper-updates restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates restricted

deb http://archive.ubuntu.com/ubuntu dapper-updates universe
deb-src http://archive.ubuntu.com/ubuntu dapper-updates universe

deb http://archive.ubuntu.com/ubuntu dapper-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates multiverse

# Dapper Backports (new software versions, provided by the Ubuntu Backports Project)
deb http://archive.ubuntu.com/ubuntu dapper-backports main
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main

deb http://archive.ubuntu.com/ubuntu dapper-backports restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-backports restricted

deb http://archive.ubuntu.com/ubuntu dapper-backports universe
deb-src http://archive.ubuntu.com/ubuntu dapper-backports universe

deb http://archive.ubuntu.com/ubuntu dapper-backports multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports multiverse


##############################
### Automatix Repositories ###
##############################

deb http://www.beerorkid.com/automatix/apt dapper main

## created by automatixrepo2

deb http://www.beerorkid.com/compiz/ dapper main
deb http://xgl.compiz.info/ dapper main

```

---

### Post by abowman on 2006-07-31
[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

---

