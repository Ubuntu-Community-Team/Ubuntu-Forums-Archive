---
title: "burning CD"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by mendingo84 on 2006-10-24
why doesn't windows recognize a data CD burned with k3b? what should i do?

---

### Post by taurus on 2006-10-24
Are you able to read that CD in Ubuntu?  Have you tried to see if you can read it on another PC running Windows?

---

### Post by mendingo84 on 2006-10-24
i am able to read it in ubuntu and it works. but on windows it just wont work.

---

### Post by peteguhl on 2006-10-24
What format did you use? UDF?

---

### Post by mendingo84 on 2006-10-24
no. i used both Joliet and RockRidge

---

### Post by tatimmer on 2006-10-24
#!/bin/sh

# burn data-cd disk-at-once

# the first time i tried to use k3b it crashed  
# this script will burn a directory to a cd
# qtytrack = single, type = data-cd
# see mkisofs and cdrecord for more info
# Tom Timmermann 4/9/06
# [www.ticon.net/~tatimmer](www.ticon.net/~tatimmer)

echo "*********************************"
echo Welcome to BURNDIR
echo This script is a front end for 
echo mkisofs and cdrecord
echo useful for making a data-cd
echo all contents of dir entered
echo will be burned to cd
echo from a directory on your hard drive
echo author: Tom Timmermann
echo [www.ticon.net/~tatimmer](www.ticon.net/~tatimmer)
echo "*********************************"
echo

#get name of directory to burn
echo
echo Enter name of directory to burn to cd
read burndirectory



# test for something entered
if [ -z $burndirectory ]
then
	echo you must enter a burn directory
	exit 1
fi


#test for valid directory
if [ -d $burndirectory ]
then 
	echo directory to burn is $burndirectory
else 
	echo $burndirectory is not valid 
	exit 1
fi



# get estimated filesize needed for disk-at-once
cdblocks=` mkisofs -v -print-size $burndirectory `

echo
echo mkisofs returns cdblocks = $cdblocks
echo


# use -dummy after -v for a trial run without burning
# i ran <cdrecord -scanbus> to get the "dev=ATA:1,1,0" string for my drive
# my drive is a khypermedia 52x24x52 but burning at 8x worked well on windows

mkisofs -v -r $burndirectory | cdrecord -v -dao speed=8  dev=ATA:1,1,0  -data tsize=${cdblocks}s -

---

