---
title: "rpm files?"
date: 2006-06-20
forum: Absolute Beginner Talk
---

### Post by maddbaron on 2006-06-20
I downloaded a rpm archive since kopete said its what is needed to view yahoo webcams but i dont know how to unzip it since double clicking says the archive isnt recognized. if i rename it to a zip file should that work? if not how to i get to the contents and install them?

---

### Post by wombat20 on 2006-06-20
ubuntu prefers .deb to .rpm (as it's based on Debian)

You can convert between the two with the alien command, I think... but I don't know the details.

---

### Post by taurus on 2006-06-20
You have to convert it to .deb first before you can do that.  First, install alien if you haven't done so and then convert and install it as
```

sudo apt-get install alien
alien <filename>.rpm
sudo dpkg -i <filename>.deb

```

---

### Post by maddbaron on 2006-06-20
thanks

---

### Post by acht on 2006-06-22
and where does it put the .deb package?

nvm i found it

---

### Post by jethro10 on 2006-06-22
[QUOTE=acht]and where does it put the .deb package?
[/QUOTE]
It uses the internal contents of the deb package to install suff in lots of places.

Your deb file remains where it was after installation.

If you want to know where it's installed stuff, open synaptic package manager and search for the program name and look at the properties. It shows a list of where all the files are installed.

I only just found out recently that a seperate deb once installed, is listed in Package manager! You can use this to de-install with as well.

---

### Post by penguintutor on 2006-06-22
Whilst you can use alien -i to install a rpm package, it's worth searching to see if there is a Debian equivelant first. Some documentation is biased towards rpm and don't give details of alternatives for those that don't use rpm.

My guess is that you may be looking for the Video4Linux drivers, which are available under Ubuntu.

e.g. searching for either Video4Linux or v4l gives the package
xserver-xorg-driver-v4l - which may be what you are looking for.

Search performed using
```

apt-cache search Video4Linux 
apt-cache search v4l

```

which you can then install with
```

apt-get install xserver-xorg-driver-v4l

```

Just a thought

---

### Post by nitricacid on 2006-06-22
You can download RPM from synaptic, that will unzip .RPM files and then you can manually install the app/program to your root file system (whick I prefer doing).
But, if you want the easy way you can just use the methods listed above.

---

