---
title: "Cant's find Firestarter"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by Grouper on 2006-10-29
Hello everyone!

    A complete Linux newbie here. I just loaded Edgy Eft a few hours ago! I would like to install Firestarter, but I am unable to find it. I did a search of Synaptic Package Manager and come up with zip. Any help would be appreciated.

Thanks!

---

### Post by spectrum42 on 2006-10-29
Maybe this will help? I'm using dapper, so I can test it myself.
[http://ubuntuguide.org/wiki/Ubuntu_Edgy]("http://ubuntuguide.org/wiki/Ubuntu_Edgy")

Type in a terminal:
```

sudo apt-get install firestarter

```

---

### Post by mahy on 2006-10-29
> **Grouper said:**
> Hello everyone!

    A complete Linux newbie here. I just loaded Edgy Eft a few hours ago! I would like to install Firestarter, but I am unable to find it. I did a search of Synaptic Package Manager and come up with zip. Any help would be appreciated.

Thanks!

Zip in Synaptic? Just open Terminal and type:

sudo apt-get install firestarter :mrgreen:

---

### Post by Grouper on 2006-10-29
I went to applications> system tools> root terminal, wrote the password, then copied and pasted:

sudo apt-get install firestarter

Terminal came back with:

E: Couldn't find package firestarter

Now what is my next move?

Thanks for the help!

---

### Post by PriceChild on 2006-10-29
I advise you don't use the root terminal, just use "sudo" before commands when you want them to run with root.

This has been disabled in ubuntu for a reason: [http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo)

Please post the output of```
cat /etc/apt/sources.list
```

---

### Post by Grouper on 2006-10-29
Okay. I went Applications> accessories> terminal> cut-n-pasted>: cat /etc/apt/sources.list

I got in return:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

I can see I have alot to learn! For instance; when I installed Ubuntu (6.10) I filled out Name, Login Name, Password and Computer name. As far as I recall I filled out only one password. Is it that the root password or the users password?

---

### Post by randomi on 2006-10-30
Root password is randomly generated in Ubuntu. If you really want to change the password for root you can
```
sudo passwd root
```
and enter in a password for root to use.

As for the firestarter problem you need to enable the universe repositories. Enter
```
sudo nano /etc/apt/sources.list
```
and take out the # in front of deb. Once that's done press ctrl-x then y then enter
```
sudo aptitude update
```
then
```
sudo aptitude install firestarter
```

Once that's done you can find firestarter under system -> administration -> firestarter

---

### Post by chaktar on 2007-06-11
For starters I'm new here and am hoping that dragging up old threads is better ettiquette here than starting new ones. I have the exact same problem as the OP. I've tried all the suggestions so far in this thread and gotten nowhere. To be specific, I did as randomi suggested, removing the # in front of deb and got:
sudo aptitude update
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates Release
Get:4 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty Release.gpg [191B]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty Release
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Sources
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Packages
Fetched 4B in 1s (3B/s)
Reading package lists... Done

From there: 
sudo aptitude install firestarter
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "firestarter"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

How the heck do i get "firestarter" in the first place as that seems to be the first problem?! I tried to download it from the site and I never got to an actual download link.

O yes finally don't know if this will help but here's the output code of 
cat /etc/apt/sources.list that pricechild asked for.

cat /etc/apt/sources.list

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

The first time i looked at that code the two first lines about deb weren't there, it was only after following randomi's post that they appeared.
Hopefully thats enough info for someone to help me out.

---

### Post by RomeReactor on 2007-06-11
Hi. You need to enable the Universe repositories; for that enter the following on the terminal:
```
gksduo gedit /etc/apt/sources.list
```
then remove the **#** from this line:
> # deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper universe
save and close the text editor, and still from the terminal:
```
sudo apt-get update
```
and when that finishes Firestarter will be available from Synaptic. Or:
```
sudo apt-get install firestarter
```

And Welcome!

---

### Post by ramjet_1953 on 2007-06-11
Let's go back to the start here.

Is there a reson why you need to edit iptables?

Firestarter IS NOT a firewall, it is a graphical GUI for editing the iptables firewall.

Certainly, if you have to change iptables for port forwarding go ahead, but if not, leave the iptables firewall well alone, as your system by default has all ports closed and is VERY SECURE.

By the way, to run the Firestarter GUI requires it to be run in root mode and by doing this, it is a security risk in itself.

To cut to the chase, unless you have good reason to edit iptables, leave well alone.

Regards,
Roger :cool:

---

