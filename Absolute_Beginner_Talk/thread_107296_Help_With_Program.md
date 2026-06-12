---
title: "Help With Program"
date: 2005-12-22
forum: Absolute Beginner Talk
---

### Post by Dr Von Bon Bon on 2005-12-22
A little while ago I tried to install Lilypond but now all i want to do is get rid of it as whenever I try and install anything else (such as badly needed updates) is comes up trying to install Lilypond data and then comes up with the error message:

/var/cache/apt/archives/lilypond-data_2.6.3-9~breezy1_all.deb: subprocess new post-removal script returned error exit status 1

I have tried deleteing this file; it didnt work
I have tried reinstalling Lillypond; it didnt work
I have tried deleting all Lillypond files and reinstalling Lillypond; it didnt work
I have tried uninstalling all Lilypond files, guess what? It didnt work.


Please can someone help me out?

---

### Post by Kyral on 2005-12-22
could you scroll up and find the error itself? It should display

---

### Post by xtacocorex on 2005-12-22
Did you uninstall with the following?

```

sudo apt-get remove lilypond

```

---

### Post by Kyral on 2005-12-22
Might help to purge

```
sudo aptitude purge lilypond
```

Other than that only thing I can think of is that something depends on it

---

### Post by Dr Von Bon Bon on 2005-12-24
When i tried to purge this came up in the terminal:



Preconfiguring packages ...
(Reading database ... 77919 files and directories currently installed.)
Preparing to replace lilypond-data 2.6.3-9~breezy1 (using .../lilypond-data_2.6. 3-9~breezy1_all.deb) ...
Unpacking replacement lilypond-data ...
/var/lib/dpkg/info/lilypond-data.postrm: line 23: /usr/bin/kpsewhich: No such fi le or directory
dpkg: warning - old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: line 23: /usr/bin/kpsewhich: No such file or direct ory
dpkg: error processing /var/cache/apt/archives/lilypond-data_2.6.3-9~breezy1_all .deb (--unpack):
 subprocess new post-removal script returned error exit status 1
/var/lib/dpkg/tmp.ci/postrm: line 23: /usr/bin/kpsewhich: No such file or direct ory
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/lilypond-data_2.6.3-9~breezy1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
Ack!  Something bad happened while installing packages.  Trying to recover:
Setting up lilypond-doc (2.6.3-9~breezy1) ...

Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done


I hope that helps



EDIT:
Those were the results I got from the sudo aptitude one and the apt-get one i have tried lots and doesn't seem to work.
Thanks

---

### Post by Greg2 on 2006-01-07
[QUOTE=Dr Von Bon Bon]A little while ago I tried to install Lilypond but now all i want to do is get rid of it as whenever I try and install anything else (such as badly needed updates) is comes up trying to install Lilypond data and then comes up with the error message:

/var/cache/apt/archives/lilypond-data_2.6.3-9~breezy1_all.deb: subprocess new post-removal script returned error exit status 1

I have tried deleteing this file; it didnt work
I have tried reinstalling Lillypond; it didnt work
I have tried deleting all Lillypond files and reinstalling Lillypond; it didnt work
I have tried uninstalling all Lilypond files, guess what? It didnt work.


Please can someone help me out?[/QUOTE]
This is a known bug in the Synaptic package manager. It requires a clean environment with no half installed packages to perform any additional changes.

In a terminal do:```
sudo apt-get install -f
```
Then remove Lilypond-data with the Synaptic package manager.

---

