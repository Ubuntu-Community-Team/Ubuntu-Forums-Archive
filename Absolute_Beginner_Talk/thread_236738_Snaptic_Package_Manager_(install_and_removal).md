---
title: "Snaptic Package Manager (install and removal)"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by Lopsicle on 2006-08-15
Hiya I dont know what I done but I cannot check any packages to be installed or removed in Snaptic.The boxes are all filled in as if all packages have been installed (which of course there havnt) :confused: Anyone have any ideas? :D

---

### Post by goatflyer on 2006-08-15
Filled in, yes, but green or grey?  only green means installed.

See if it looks the same in the All section.

Are all your repositories selected? Settings>Repositories

Have you enabled universe and multiverse?

---

### Post by Lopsicle on 2006-08-15
Hi goatflyer yes the boxes are filled in green and yes to all the other questions?

---

### Post by siacs on 2006-08-15
For some reason You only have 1171 packages listed, the ones that were installed by default. You need to enable your repositories for more packages.

[http://www.psychocats.net/ubuntu/sources.php](http://www.psychocats.net/ubuntu/sources.php)

---

### Post by Klaidas on 2006-08-15
Ummm, ok.
Do you mean that ALL packages are installed? (The boxed are filled green)?

Also, how can you not mark them? Does it give some kind of an error?

---

### Post by siacs on 2006-08-15
Make sure you hit Reload after

---

### Post by Lopsicle on 2006-08-15
oops I forgot to enable repos when changing to Dapper :rolleyes: OMG !!! I cant enable repositories, Im going to settings/repos but its not coming up?

---

### Post by siacs on 2006-08-15
Use the manual method in the link I posted before.

---

### Post by Klaidas on 2006-08-15
Do
> sudo gedit /etc/apt/sources.list
Uncommnent the resposities.
Then do
> sudo apt-get update
> sudo apt-get upgrade

---

### Post by Malac on 2006-08-15
sudo gedit /etc/apt/sources.list
sudo apt-get update

---

### Post by Lopsicle on 2006-08-15
nope neither methods are working :sad:

---

### Post by Lopsicle on 2006-08-15
This is what Im getting.

---

### Post by siacs on 2006-08-15
That's correct, you haven't installed, upgraded or removed anything right? ;) Now check Synaptic to see how many packages you have listed.

---

### Post by Lopsicle on 2006-08-15
Yes 1170, but the problem now is enabling the repositories ;)

---

### Post by siacs on 2006-08-15
Ok no change then? Could you post your sources.list?

Or just take a screenshot so we can see what you have

---

### Post by siacs on 2006-08-15
Did you make sure to save your sources.list in gedit before updating?

---

### Post by siacs on 2006-08-15
Your sources should look like this at a minimum

# Automatically generated sources.list
# [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb [http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu) dapper main restricted
deb [http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src [http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb [http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb [http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src [http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb-src [http://uk.archive.ubuntu.com/ubuntu](http://uk.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

---

### Post by Lopsicle on 2006-08-15
No I dont think I saved it because nothing was listed.

---

### Post by siacs on 2006-08-15
Ok, then copy and paste the sources above into gedit and save them.

---

### Post by Lopsicle on 2006-08-15
Wohoooooooooo thank you Siacs your a Star and thanks to everyone else for helping :D

---

### Post by siacs on 2006-08-15
happy to have helped :)

---

