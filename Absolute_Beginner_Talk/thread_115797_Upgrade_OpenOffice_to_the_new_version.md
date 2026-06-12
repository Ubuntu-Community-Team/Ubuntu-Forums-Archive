---
title: "Upgrade OpenOffice to the new version"
date: 2006-01-11
forum: Absolute Beginner Talk
---

### Post by shaynaynay on 2006-01-11
I'm using Ubuntu 5.10, and I have there OpenOffice that came with it.
I downloaded the latest OpenOffice (Hebrew interface) from the official site (the file's name is:OOo_2.0_linux_install_he_deb.sh; they also have *_he_rmp.sh there) and I would like to install it on my machine, and replace the old OpenOffice that is installed.

Have no clue about compiling etc..

Thanks,
Guy.

---

### Post by s6dalane on 2006-01-11
First start the terminal.

Then:
> sudo gedit /etc/apt/sources.list

Add the following line:
> deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

And last but not least:
> sudo apt-get update
sudo apt-get upgrade

If everything worked well, you now have OO.o 2.0.1 installed on your system.
I hope this works.

---

### Post by shaynaynay on 2006-01-11
Thanks! I'll try that... but I can see that the version in that site is the English version- not the Hebrew version (Hebrew Interface)...

So, the site has deb files, I have a deb file (which is what I need)- What's next?

---

### Post by SSTwinrova on 2006-01-11
2 things:

1) It appears you downloaded a shell script, not an actual deb file (hence the deb.sh). To run this, open a terminal, go to the directory where that file is, and try running "sh ./OOo_2.0_linux_install_he_deb.sh" (you might need a sudo before that, not sure).

2) Deb files have already been compiled, so depending on what that shell scrip does, you might need to install it. Barring and dependency issues, a "sudo dpkg -i (insert deb file here)" should work.

---

### Post by joelito on 2006-01-11
I think the Hebrew Files are among those with the l10 in the file name

---

### Post by shaynaynay on 2006-01-12
No, the Hebrew is not there. The name of the file should include "he" instead of "es" or "fr" etc.

hmmm.. wondering... What if I add myself as a source? like, adding my IP (of course, putting it in /var/www)? Should this work?

---

### Post by lodp on 2006-03-13
the hebrew version in the repository is somewhate misleadingly called "hebrew language package for openoffice". when you install that you get the hebrew interface version (but in fact it's only OO 1.15).

i downloaded the same file as you did (OOo_2.0_linux_install_he_deb.sh). i did the following (i don't know a thing about shell scripts so there might be some redundant stuff, please correct me):
```
chmod a+x OOo_2.0_linux_install_he_deb.sh
./OOo_2.0_linux_install_he_deb.sh

```

that unpacked the deb files to /var/unpack_openoffice (or something like that). then i just went into that folder and installed the deb files: ```
dpkg -i *.deb
```

that was mainly it

---

### Post by be4truth on 2007-01-21
try this one for dapper.
[http://bodmas.org/blog/?p=523](http://bodmas.org/blog/?p=523)
works fine with me!

---

