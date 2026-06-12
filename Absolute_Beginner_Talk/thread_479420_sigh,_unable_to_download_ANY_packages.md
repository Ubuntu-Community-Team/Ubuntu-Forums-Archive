---
title: "sigh, unable to download ANY packages?"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by mark. on 2007-06-20
being pretty noob at linux (but im getting the hang of it :D), i need some help...again.

so i was using add/remove program, but when i pressed apply, this error came up 
"E: The package virtualbox needs to be reinstalled, but I can't find an archive for it."

-and i tried going into terminal and trying a 
sudo apt-get install virtualbox, but it gives me that same error as well in the terminal.
-if i put sudo apt-get install wine (just to try), i also get that error.
-also, when i try and open synaptic package manager i get this error before the program even launches :/


how can i fix this? i really need someone to ask lol

---

### Post by tcrroadie on 2007-06-20
Could you please post your apt sources list. 
```

less /etc/apt/sources.list
```

And the output you recieve when you run 

```
sudo apt-get update
```

The server just may be down or experiencing other problems.

---

### Post by mark. on 2007-06-20
less /ect/apt/sources.list

```
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) feisty main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) feisty main
```


and sudo apt-get update (i think i tried this before and got this...the error is ironic :/)

```
mark@l--desktop:~$ sudo apt-get update
Password:
Get:1 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty Release.gpg [191B]
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Translation-en_US    
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US              
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US       
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Err [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty Release
  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release                         
Get:5 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty Release [1007B]         
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty Release                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages                   
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources    
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources    
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
Fetched 1201B in 1s (915B/s)
Reading package lists... Done
W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: You may want to run apt-get update to correct these problems
mark@l--desktop:~$ 
```


well thanks in advance if you can fix my problem :D

---

### Post by tcrroadie on 2007-06-20
```
W: GPG error: http://wine.budgetdedicated.com feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY
```

The output here that you received from apt, indicates that there is a gpg key that is used to verify the package signatures.  This is not really a big deal in your case.  You can either visit the web site for the wine repository listed and get the gpg key, or you can just force the install. 

Try just installing wine using apt-get
```

sudo apt-get install wine
```

When apt ask you if you would like to install the package, given it needs the gpg key, just select yes.  It should install for you.

---

### Post by mark. on 2007-06-20
well what in trying to fix is that i cannot install any programs at all :/

i always get this error 
"E: The package virtualbox needs to be reinstalled, but I can't find an archive for it."

for example
```
mark@l--desktop:~$ sudo apt-get install wine
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
mark@l--desktop:~$ 
```

so eyah, i need help :/

---

### Post by Cypher on 2007-06-20
How about trying
```

sudo apt-get install -f

```

---

### Post by mark. on 2007-06-20
tried it --

```
mark@l--desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.

```

ahh #@$#$@#$. is there a way to fix the virtualbox problem

---

### Post by HereInOz on 2007-06-20
Are you actually using VirtualBox?  If not, try going in to Synaptic Package Manager and search for it, and if you find it in there, mark it for complete removal.

Then you could visit the VirtualBox site and download the program - I think they have a deb there for Feisty.   Install it that way.

---

### Post by Cypher on 2007-06-20
While at the terminal just type
```

suto apt-get autoremove virtualbox

```

---

### Post by mark. on 2007-06-20
guessing virtualbox is a OS emulator, im just using plain ubuntu.

when i go into synaptic package manager it says there was an error while starting up.
details are-
"E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report."
*sob*



also, when i put apt-get revmove virtualbox, i get this-
```
mark@l--desktop:~$ sudo apt-get autoremove virtualbox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
mark@l--desktop:~$ 

```
.....

---

### Post by forestpixie on 2007-06-20
I had exactly the same issue with virtualbox, was given this.
```

sudo dpkg --remove --force-remove-reinstreq virtualbox
```

That might work for you.

---

### Post by mark. on 2007-06-20
i got this-

```
mark@l--desktop:~$ sudo dpkg --remove --force-remove-reinstreq virtualbox
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 
dpkg: serious warning: files list file for package `virtualbox' missing, assuming package has no files currently installed.
116479 files and directories currently installed.)
Removing virtualbox ...

```

but it worked THANK YOU :D

now i only have lik 2 more issues to fix before completely going linux ;x

---

### Post by forestpixie on 2007-06-20
Glad bout that - hope it hasn't broken anything!

:)

---

