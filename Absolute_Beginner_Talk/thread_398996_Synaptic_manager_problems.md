---
title: "Synaptic manager problems"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by PreachanStoirm on 2007-04-01
Hello, wee problem here. 
Have been using Ubuntu for about a month now, getting an error message when i go into "add/remove.." or "Synaptic package manager"

add/remove error message is = 

[COLOR="DarkOrange"]Failed to check for installed and available applications

This is a major failure of your software management system. Check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information: 'sudo apt-get update'.[/COLOR]

Synaptic is 
[COLOR="DarkOrange"]
An error occured

The following details are provided:

E: Malformed line 3 in source list /etc/apt/sources.list.d/edgy-universe.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.[/COLOR]


If anyone could tell me how to fix this it would be much appreciated thanks



-from the emerald isle where the rain never ceases-

---

### Post by qamelian on 2007-04-01
SOunds like something is wrong with your sources.list. Post the contents of /etc/apt/sources.list so we can se what might be wrong.

---

### Post by Maestro23 on 2007-04-01
>  cat /etc/apt/sources.list

Copy/Paste output here.

---

### Post by bruenig on 2007-04-01
The problem is not with sources.list is it with, /etc/apt/sources.list.d/edgy-universe.list.
I would just do
```
sudo rm /etc/apt/sources.list.d/edgy-universe.list
```

And then enable all the repos in the real sources.list with
```
sudo sed -e 's/# deb/deb/g' -e 's/universe$/universe multiverse/g' -i.backup /etc/apt/sources.list && sudo apt-get update
```

---

### Post by PreachanStoirm on 2007-04-01
ok, this is the info in etc/apt/sources.list


[PHP]## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ edgy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu/ edgy-updates restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://archive.ubuntu.com/ubuntu/ edgy universe

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted

deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe

deb http://archive.ubuntu.com/ubuntu/ edgy multiverse
deb-src http://archive.ubuntu.com/ubuntu/ edgy multiverse


deb http://archive.canonical.com/ubuntu edgy-commercial main
deb http://security.ubuntu.com/ubuntu/ edgy-security restricted main multiverse universe
deb http://archive.ubuntu.com/ubuntu/ edgy-backports restricted main multiverse universe
[/PHP]

---

### Post by PreachanStoirm on 2007-04-01
bruenig  i could kiss you


Thanks.That sorted it all out.

---

