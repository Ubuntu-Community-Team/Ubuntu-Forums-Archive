---
title: "Adding Wine repository to Synaptic"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by hedge153 on 2007-09-16
Hey guys, using the information found on [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb) I'm trying to get Synaptic to install newest version of Wine instead of the older version found in the main Ubuntu repositories, but running into an error when i try updating the synaptic listing.

[http://wine.budgetdedicated.com/apt/dists/feisty/main/binary-i386/Packages.gz:](http://wine.budgetdedicated.com/apt/dists/feisty/main/binary-i386/Packages.gz:) MD5Sum mismatch

I've tried also manually adding in the Key file and the entry into third party software, but it throws back the same error. Any ideas?

edit: heres the full error output from running sudo apt-get update
Failed to fetch [http://wine.budgetdedicated.com/apt/dists/feisty/main/binary-i386/Packages.gz](http://wine.budgetdedicated.com/apt/dists/feisty/main/binary-i386/Packages.gz)  MD5Sum mismatch
Failed to fetch [http://wine.budgetdedicated.com/apt/dists/feisty/main/binary-i386/Packages.gz](http://wine.budgetdedicated.com/apt/dists/feisty/main/binary-i386/Packages.gz)  MD5Sum mismatch

---

### Post by Kilz on 2007-09-16
You might want to attach the /etc/apt/sources.list  or copy it into a post to make it easier to help you. ```
gksudo gedit /etc/apt/sources.list
``` will bring it up so you can copy it.

---

### Post by Hossie on 2007-09-16
You can always install the .deb by hand:

```
wget 'http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.45~winehq0~ubuntu~7.04-1_i386.deb'
sudo dpkg -i 'wine_0.9.45~winehq0~ubuntu~7.04-1_i386.deb'
```

Maybe you also need the libwine from the server.

---

### Post by hedge153 on 2007-09-16
If I'm understanding the instructions correctly at [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb) the added repositories are not being added to the sources.list file but a file stored under sources.list.d/winehq.list, contents of said file is:
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) feisty main #WineHQ - Ubuntu 7.04 "Feisty Fawn"
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) feisty main #WineHQ - Ubuntu 7.04 "Feisty Fawn"

My actual sources.list file is attached as well.

---

### Post by hedge153 on 2007-09-16
Thanks Hossie, manually downloading and installing the package worked a treat. May I ask how you found the exact download path to the deb file?
Still wouldn't mind knowing how I screwed up the repository addition either for future reference :)
Thanks for any help.

---

### Post by Hossie on 2007-09-16
Just browse the repo with your browser? :D

[http://wine.budgetdedicated.com/apt/pool/](http://wine.budgetdedicated.com/apt/pool/)

---

### Post by Perfect Storm on 2007-09-16
> **Hossie said:**
> Just browse the repo with your browser? :D

[http://wine.budgetdedicated.com/apt/pool/](http://wine.budgetdedicated.com/apt/pool/)

Why's that? When you can get it delivered to the door without concerning if there's a new version out ;)

---

### Post by Perfect Storm on 2007-09-16
> **hedge153 said:**
> Hey guys, using the information found on [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb) I'm trying to get Synaptic to install newest version of Wine instead of the older version found in the main Ubuntu repositories, but running into an error when i try updating the synaptic listing.

[http://wine.budgetdedicated.com/apt/dists/feisty/main/binary-i386/Packages.gz:](http://wine.budgetdedicated.com/apt/dists/feisty/main/binary-i386/Packages.gz:) MD5Sum mismatch

I've tried also manually adding in the Key file and the entry into third party software, but it throws back the same error. Any ideas?

edit: heres the full error output from running sudo apt-get update
Failed to fetch [http://wine.budgetdedicated.com/apt/dists/feisty/main/binary-i386/Packages.gz](http://wine.budgetdedicated.com/apt/dists/feisty/main/binary-i386/Packages.gz)  MD5Sum mismatch
Failed to fetch [http://wine.budgetdedicated.com/apt/dists/feisty/main/binary-i386/Packages.gz](http://wine.budgetdedicated.com/apt/dists/feisty/main/binary-i386/Packages.gz)  MD5Sum mismatch

```

wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list -O /etc/apt/sources.list.d/winehq.list
sudo aptitude update && sudo aptitude upgrade

```

Note, it only works with 32 bit version.

If it fails,

```
sudo nano /etc/apt/sources.list
```

add

[b]### Upstream Wine
### GPG key: 387EE263
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) feisty main 
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) feisty main
[/b]

Save (ctrl)+(o) and exit (ctrl)+(x)

```
gpg --keyserver hkp://subkeys.pgp.net --recv-keys 387EE263
 gpg --export --armor 387EE263 | sudo apt-key add -
sudo aptitude update && sudo aptitude upgrade

```

---

### Post by hedge153 on 2007-09-17
Many thanks, the first method you describe worked a treat :) Can now see the winehq package in Synaptic.

---

