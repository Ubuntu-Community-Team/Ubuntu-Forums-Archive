---
title: "Installing latex without internet"
date: 2006-03-01
forum: Absolute Beginner Talk
---

### Post by Nazgulled on 2006-03-01
Hi,
I'm installing ubuntu on my friend's laptops cause we need it for school... However, I could't find anything related to it on the synpatic package manager...

I don't have any internet connection available on their laptops, so... how can I download all the required stuff to and how do I install it on their laptops?

---

### Post by daredevil on 2006-03-01
I think u should look out for .deb package of latex software then write it onto a cd and then copy it onto laptop then type the command

```
sudo dpkg -i <packagename>
```

if u find only an RPM package use alien to convert rpm to .deb pakkage

```
sudo alien <packagename.rpm>
```

---

### Post by Nazgulled on 2006-03-01
but I have no idea where to get those .deb packages... or even rpm :S

---

### Post by daredevil on 2006-03-01
Google is our friend

---

### Post by daredevil on 2006-03-01
I have seen latex editors in sourceforge.net

---

### Post by Brunellus on 2006-03-01
[QUOTE=Nazgulled]Hi,
I'm installing ubuntu on my friend's laptops cause we need it for school... However, I could't find anything related to it on the synpatic package manager...

I don't have any internet connection available on their laptops, so... how can I download all the required stuff to and how do I install it on their laptops?[/QUOTE]
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

that's a web-searchable and browsable way of getting individual .deb packages from ubuntu.  Download each package and all its dependencies, and then install them in order using

sudo dpkg -i $packagename

where $packagename is the name of the package you are installing.

As far as editors, you won't really need anything more than a garden-variety text editor to edit LaTeX files--they're really just plaintext with markup.  You *will* need some sort of LaTeX compiler to output them, though, which is what you will be installing. 

If you need a semi-gui way of doing things with LaTeX, I recommend LyX, which I'm learning, and have been reasonably impressed with.

All of these packages are in the universe and multiverse repositories.  enable them in Synaptic, or by editing /etc/apt/sources.list

---

### Post by Nazgulled on 2006-03-01
thanks, but there's too many dependencies and I think I will not install them that way... if I had an internet connection, how would I install latex?

---

### Post by Brunellus on 2006-03-01
enable the universe and multiverse repositories in synaptic

search for latex and/or lyx

mark them for installation

apply the changes.

---

### Post by Nazgulled on 2006-03-01
[QUOTE=Brunellus]enable the universe and multiverse repositories in synaptic

search for latex and/or lyx

mark them for installation

apply the changes.[/QUOTE]

that's only if I had ana internet connection right?

---

### Post by Brunellus on 2006-03-01
yes.  otherwise, install the debs.

---

