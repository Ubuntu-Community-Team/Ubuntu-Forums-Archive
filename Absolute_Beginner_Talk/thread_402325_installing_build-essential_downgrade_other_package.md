---
title: "installing build-essential downgrade other packages? Safe?"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by NicoleM on 2007-04-05
I've been reading the wiki regarding ati drivers and I was going to give the proprietary drivers a try.  I'm trying to get everything installed that I might need while in the process.

synaptic kept giving me errors when I tried to install build-essential so I turned to the terminal in hopes of getting some more information. (yes i *should* have all teh correct repositories enables)

it seems as though to install build essential it wants to downgrade some other packages I have, but that's about all I can make of it.  I was hoping someone here could take a look at this output and let me know if it's alright to proceed or if I could be breaking something in the process:

```

nicole@Zaphod:~$ sudo aptitude install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  libc6-dev 
The following NEW packages will be automatically installed:
  g++ g++-4.1 libstdc++6-4.1-dev linux-libc-dev 
The following NEW packages will be installed:
  build-essential g++ g++-4.1 libstdc++6-4.1-dev linux-libc-dev 
0 packages upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 7821kB of archives. After unpacking 29.9MB will be used.
The following packages have unmet dependencies:
  libc6-dev: Depends: libc6 (= 2.4-1ubuntu12) but 2.4-1ubuntu12.3 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Downgrade the following packages:
libc6 [2.4-1ubuntu12.3 (now) -> 2.4-1ubuntu12 (edgy)]
libc6-i686 [2.4-1ubuntu12.3 (now) -> 2.4-1ubuntu12 (edgy)]

Score is -124

Accept this solution? [Y/n/q/?] 

```

system is p4 2 ghz, 1gb ram, ati radeon 9200 pro dual booting edgy and xp pro sp2

---

### Post by Bachstelze on 2007-04-05
The libc6 you are currently running doesn't appear to be in the official Ubuntu repos. Where did you get it from ?

TO answer your question, it will install official Ubuntu packages instead of the ones you currently have so yeah, it is safe.

But could you please pastebin your sources.list ?

---

### Post by NicoleM on 2007-04-05
to be honest i'm nto entirely sure.  when i first installed ubuntu I followed a couple different guides for getting all my stuff set up so it could have come from something I was reading at the time...it's my own fault for not documenting exactly what i did.

thanks for having me look into my sources.list file though because I think there's something slightly wrong...my list doesn't look like a lot that I've seen posted on the forums.

I used the gui in the settings of synaptic to enable the repository options there so I don't know if that's why this file isn't longer, but this is all I've got in /etc/apt/sources.list:

```
deb http://flomertens.free.fr/ubuntu/ edgy main main-all
deb http://squentin.free.fr/gmusicbrowser ./
```

I've seen sort of a "default" sources.list file posted...should I find that and replace this file with the standard ones i've seen?

i wish i could be more helpful in describing how i got to this point, but any insight is appreciated.  thanks.


edit: i also have files in /etc/apt/sources.list.d/ called things like edgy-multiverse.list, edgy-main.list, edgy-universe.list as below
```
nicole@Zaphod:~$ ls /etc/apt/sources.list.d
edgy-main.list       edgy-multiverse.list       edgy-universe.list       winehq.list
edgy-main.list.save  edgy-multiverse.list.save  edgy-universe.list.save  winehq.list.save
``` did you want me to go into those files as well?

---

### Post by Maestro23 on 2007-04-05
Your /etc/apt/sources.list for Edgy, should look something like this: [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by Bachstelze on 2007-04-05
Hmm, I guess you should get a better sources.list indeed, do this :

```
cd
wget http://fkraiem.no-ip.org/ftp/pub/sources.list_edgy
sudo mv sources.list_edgy /etc/apt/sources.list
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install build-essential
```

---

### Post by NicoleM on 2007-04-05
thank you very much.

looks like i got some needed updates to open office among a host of other things and build-essential installed without any kind of errors.

I appreciate you guys taking the time to take a look and help me out even if it was something simple :)

new sources.list looks normal now :)

```
nicole@Zaphod:~$ cat /etc/apt/sources.list
deb http://fr.archive.ubuntu.com/ubuntu/ edgy main restricted
#deb-src http://fr.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://fr.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
#deb-src http://fr.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Security updates
deb http://fr.archive.ubuntu.com/ubuntu edgy-security main restricted
#deb-src http://fr.archive.ubuntu.com/ubuntu edgy-security main restricted


## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://fr.archive.ubuntu.com/ubuntu/ edgy universe multiverse
#deb-src http://fr.archive.ubuntu.com/ubuntu/ edgy universe multiverse

deb http://fr.archive.ubuntu.com/ubuntu/ edgy-updates universe multiverse
#deb-src http://fr.archive.ubuntu.com/ubuntu/ edgy-updates universe multiverse

deb http://fr.archive.ubuntu.com/ubuntu edgy-security universe multiverse
#deb-src http://fr.archive.ubuntu.com/ubuntu edgy-security universe multiverse


## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://fr.archive.ubuntu.com/ubuntu/ edgy-backports main restricted
#deb-src http://fr.archive.ubuntu.com/ubuntu/ edgy-backports main restricted

deb http://fr.archive.ubuntu.com/ubuntu/ edgy-backports universe multiverse
#deb-src http://fr.archive.ubuntu.com/ubuntu/ edgy-backports universe multiverse


deb http://fr.archive.ubuntu.com/ubuntu/ edgy-proposed main restricted
#deb-src http://fr.archive.ubuntu.com/ubuntu/ edgy-proposed main restricted

deb http://fr.archive.ubuntu.com/ubuntu/ edgy-proposed universe multiverse
#deb-src http://fr.archive.ubuntu.com/ubuntu/ edgy-proposed universe multiverse

```

---

### Post by ado on 2007-04-07
hi, excuse for my english, I'm an italian user.

I can't install build-essential.
my ubuntu don't have internet connection.

I use the CD to install build-essential & co.

but errors crash my mission.

Ca you help me??

---

### Post by sailor2001 on 2007-04-07
I believe you should remove the hashes on all the deb-src xxxxxxx  at least all of mine are removed

---

