---
title: "Sources.List"
date: 2006-06-30
forum: Absolute Beginner Talk
---

### Post by enyaw on 2006-06-30
Well I'm sure to show my ignorance here but here goes anyway:

When installing Automatix I allowed the Breezy sources.list to be changed.  Then I wanted to get the original sources.list back.  

I discovered there was a back up copy of a sources.list @ /etc/apt/

So, I used the cp command at terminal to replace the installed sources.list with the back up copy.  I don't know if the back up copy is of the original sources.list.  
 
So here is my question:  First what is the sources.list?  Is it simply the http// web locations shown when I look into /etc/apt/ directory and open the sources.list.

If this be the case, I should be able to print out the active sources.list and doing the same with the back up sources list and compare the two sources.list for a difference.  Does this make any sence?:roll:

---

### Post by pestilence4hr on 2006-06-30
Save the paper, run a "diff" on them:

diff /etc/apt/sources.list /etc/apt/sources.list.bak

You will have to replace the second file with the actual backup.

---

### Post by enyaw on 2006-06-30
[QUOTE=pestilence4hr]Save the paper, run a "diff" on them:

diff /etc/apt/sources.list /etc/apt/sources.list.bak

You will have to replace the second file with the actual backup.[/QUOTE]

Great help and I really appreciate it:D

---

### Post by enyaw on 2006-06-30
[QUOTE=pestilence4hr]Save the paper, run a "diff" on them:

diff /etc/apt/sources.list /etc/apt/sources.list.bak

You will have to replace the second file with the actual backup.[/QUOTE]

Hi!

I did this at Terminal: 

sudo diff -s /etc/apt/sources.list /etc/apt/sources.list_backup_200606031022

There are three sources.list_backup files in the /apt all have different dates and backup numbers.

Well I ran the three backup files and they were all Identical to the active file.  So, I still don't know if it's the Automatix or original sources.list that is being used.  

How would one go about getting a sources.list Breezy  was released with?

Thanks for your help:)

---

### Post by pestilence4hr on 2006-06-30
Here's what mine looks like, and the "default" one should be quite similar:

```
## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
#deb http://us.archive.ubuntu.com/ubuntu breezy universe multiverse
#deb-src http://us.archive.ubuntu.com/ubuntu breezy universe multiverse

```

---

