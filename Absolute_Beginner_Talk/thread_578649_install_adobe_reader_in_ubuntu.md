---
title: "install adobe reader in ubuntu"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by fooligan on 2007-10-17
ive just bought a second hand laptop with feisty fawn 7.04 on it

im total beginner computer phobe

can anyone tell me in laymans terms how to install adobe reader please

thanks

---

### Post by santiagoward2000 on 2007-10-17
Hi,
If you are still using Feisty (7.04), you can just add the Medibuntu repository and the look for acroread in Synaptic.
Here's the link:
[http://www.medibuntu.org/]("http://www.medibuntu.org/")

---

### Post by stchman on 2007-10-17
> **fooligan said:**
> ive just bought a second hand laptop with feisty fawn 7.04 on it

im total beginner computer phobe

can anyone tell me in laymans terms how to install adobe reader please

thanks

[http://www.stchman.com/install_adobe.html](http://www.stchman.com/install_adobe.html)

---

### Post by Perfect Storm on 2007-10-17
Hiya, welcome to Ubuntu :)

Go to System tab ---> Administration ---> Synaptic Package Manager

type you password when asked.

Go to settings tab ---> repositories

Enable universe and multiverse (and restricted if you want non-GPL stuff).

When done close it.

Click the reload button in synaptic, afterwards click the search button and search for adobe.

Right click on **acroread**, **acroread-escript**, **acroread-plugins** and mark them for installation. After that click the apply button.

---

### Post by funrider on 2007-10-17
KPDF is a good alternative! I like its handtool and it is fast!

---

### Post by timcredible on 2007-10-17
look at [www.ubuntuguide.org](www.ubuntuguide.org).

---

### Post by FredB on 2007-10-17
You can also use Evince. It is great to display pdf files.

---

### Post by jayaramk on 2007-10-17
the best pdf reader other than acrobat is the evince.... try using it first and then look at acrobat!!!!

---

### Post by dward526 on 2007-10-17
My recomendation is to try looking at native applications first.  If none of these please you, I belive that the 'multiverse' repository (added in synaptic manager) has Acrobat reader.  I know for a fact that there is a linux Acrobat, as SUSE EVAL 10 had it.

Welcome to Ubuntu!

---

### Post by fooligan on 2007-10-17
> **Artificial Intelligence said:**
> Hiya, welcome to Ubuntu :)

Go to System tab ---> Administration ---> Synaptic Package Manager

type you password when asked.

Go to settings tab ---> repositories

Enable universe and multiverse (and restricted if you want non-GPL stuff).

When done close it.

Click the reload button in synaptic, afterwards click the search button and search for adobe.

Right click on **acroread**, **acroread-escript**, **acroread-plugins** and mark them for installation. After that click the apply button.


got as far as searching for adobe but ]acroread[/b], **acroread-escript**, [b]acroread-plugins[ arent there to right click on

---

### Post by fooligan on 2007-10-17
> **timcredible said:**
> look at [www.ubuntuguide.org](www.ubuntuguide.org).


this looks good but i dont understand a word of it












n Ubuntu Feisty Fawn Acrobat Reder is not in Main Repositories because of licensing issues so you need to install using one of the following methods

Using medibuntu Repository

Medibuntu (Multimedia, Entertainment & Distractions In Ubuntu) is a repository of packages that cannot be included into the Ubuntu distribution for legal reasons (copyright, license, patent, etc).

Add gpg key using the following command

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add -

Edit sources.list with new repo data

sudo wget [http://medibuntu.sos-sts.com/sources.list.d/feisty.list](http://medibuntu.sos-sts.com/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/medibuntu.list

Update the source list using the following command

sudo apt-get update

Install acrobat reader with firefox plugin in Ubuntu

sudo apt-get install acroread mozilla-acroread acroread-plugins

This will complete the installation

If you want top open acrobat reader go to Applications -> Office -> Adobe Reader

Using Edgy Repository

Edit the sources.list file

sudo vi /etc/apt/sources.list

Add this line at the end of sources.list

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security restricted main multiverse universe

Update the source list using the following command

sudo apt-get update

---

