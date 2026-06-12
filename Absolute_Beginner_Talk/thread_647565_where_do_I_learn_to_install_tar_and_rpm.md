---
title: "where do I learn to install tar and rpm"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by jerbear590 on 2007-12-22
Hi,, I am completely lost,,,I thought rpm downloads would install by clicking on them...I have no idea how to instal java or lime wire or frost wire or anything..RPM or tar,,whats the difference and where do I go to learn..Complete newbie

---

### Post by jerbear590 on 2007-12-22
I forgot to say,,that I have a new install of Ubuntu and have not installed anything on it yet,,cause I don't know how.

---

### Post by aysiu on 2007-12-22
You don't install Java with an RPM.

Try this:
[http://www.psychocats.net/ubuntu/java](http://www.psychocats.net/ubuntu/java)

Nor do you install FrostWire with an RPM, not when it already supplies a DEB for Ubuntu:
[http://dl.frostclick.com/frostwire/4.13.4/frostwire-4.13.4.i586.deb](http://dl.frostclick.com/frostwire/4.13.4/frostwire-4.13.4.i586.deb)

---

### Post by bumanie on 2007-12-22
This is not an officail guide, but seems to have relevant things covered.
[www.ubuntuguide.org/](www.ubuntuguide.org/)
There are guides for all the ubuntu releases.
Also you can get most things you need from synaptic package manager. System --> Administration --> (Choose) Synaptic package manager from drop box

---

### Post by mellowd on 2007-12-22
tar comes installed by default

---

### Post by StGeorge on 2007-12-22
never knew that and I have been using Ubuntu on and off for a year or so.
I just gave up.
didn't realise that the prograns were installed with tar because they don't appear in my apps list.

---

### Post by kestrel1 on 2007-12-22
For Ubuntu you require DEB packages. RPM's do not install directly, I think you can use Alien to install RPM's though.
To install Java try the following from a terminal:
sudo apt-get install ubuntu-restricted-extras
or just follow the link above.

---

### Post by bumanie on 2007-12-22
> **kestrel1 said:**
> For Ubuntu you require DEB packages. RPM's do not install directly, I think you can use Alien to install RPM's though.
To install Java try the following from a terminal:
sudo apt-get install ubuntu-restricted-extras
or just follow the link above.

Yes. You're corerct. Alien does convert rpm files into deb files, but there usually is no need to go to such lengths, although it is handy when needed!

---

### Post by aysiu on 2007-12-22
> **StGeorge said:**
> never knew that and I have been using Ubuntu on and off for a year or so.
I just gave up.
didn't realise that the prograns were installed with tar because they don't appear in my apps list.
Programs are not installed *with* tar.

The tar program *itself* is installed by default in Ubuntu.

---

### Post by kestrel1 on 2007-12-22
Thanks for confirming about Alien, I am new to Ubuntu myself, but I have used other distro's. Found Ubuntu to be the best yet.

---

### Post by jerbear590 on 2007-12-23
Thanks for your help ,,,I will try all your great advice and let you know if I am just too thick to understand it or not.hahahaha

---

### Post by LinuxGuy1234 on 2007-12-23
> **jerbear590 said:**
> Hi,, I am completely lost,,,I thought rpm downloads would install by clicking on them...I have no idea how to instal java or lime wire or frost wire or anything..RPM or tar,,whats the difference and where do I go to learn..Complete newbie

Tar is installed with Ubuntu. RPM isn't. Install it using:
```
sudo apt-get install rpm
```

---

### Post by SOULRiDER on 2007-12-23
> **LinuxGuy1234 said:**
> Tar is installed with Ubuntu. RPM isn't. Install it using:
```
sudo apt-get install rpm
```

IMHO, theres not a worse idea than doing that.

Debian and therefore Ubuntu use deb packages. RPM is another format used by Red Hat and other distros like suse or Mandriva. You can find deb packages almost for everything.
Tar files contain sources which you have to compile in order to use.

I suggest you check out this links:
[https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement)

---

### Post by jfank on 2007-12-23
I had a question myself about installing .tar files, because there is a few programs that I've found that sadly aren't .deb format just yet or not that I have found that is.  The website that SOULRiDER gave is a big help to learn different things about installing programs.  However, yes most programs are in the .deb format already.  You will find very very very few programs that don't have the .deb setup.

---

### Post by jerbear590 on 2007-12-23
Thanks for all your great advice,,I will give it a try and let you know if I am unteachable or not.

---

### Post by jerbear590 on 2007-12-25
I am teachable,,,I had a whole day of flawless installs yesterday...thanks for everything.

---

### Post by Sef on 2007-12-25
Read [How to Install Anything in Ubuntu]("http://monkeyblog.org/ubuntu/installing/").

---

