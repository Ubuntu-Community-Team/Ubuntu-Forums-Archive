---
title: "Could someone make a bash script sh in order toSet upThe NFS sharing?(toHelpNewbies)"
date: 2005-10-20
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2005-10-20
Hi, 

I did : apt-get smb 
apt-get smb-common


----
I was thinking to make 2 bash scripts for helpign me:
  
newnfsshare.sh         (for setting up everthing)

and 

addnfsshare.sh         (for adding nfs shared folders)
 
  
 
     (These scripts would then been checked on the localhost by changing the /etc/fstab tooo with umask=000 and for users)
Let's say up to 10 shared folders .... 

The script would be as follows:  
____________ SCRIPT __ newnfsshare.sh _______________________  


#!/bin/bash
echo "/etc/hosts.deny" >> "$1" 
"$1" (rw) "$2" (rw)

$3


hosts.allow .... 


fstab .... 

____________ END SCRIPT _________________________



Thank you for helping Newbies !!!!
This script will save soul and problems for a lot of new Linux Users  !!

Patrick

---

