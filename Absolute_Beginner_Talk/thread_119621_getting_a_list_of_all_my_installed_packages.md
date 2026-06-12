---
title: "getting a list of all my installed packages"
date: 2006-01-19
forum: Absolute Beginner Talk
---

### Post by grandline on 2006-01-19
Hi everyone :) 

How do i get a list of all my installed packages into a text file?

The reason i need it is because i dont have internet at home, so i'll have to download packages at internet cafes. often when i download a package, i missed some of its dependencies, so i'll have to go back to the cafe.
I figure if i have a list of all my instaled packages, i could check if i have the dependencies right away

Thank you for your help

---

### Post by az on 2006-01-19
Use the --print-uris switch to make a list of downloads.


emma@Dapper:~$ sudo apt-get install --print-uris build-essential gcc-3.4
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  binutils cpp-3.4 dpkg-dev g++ g++-4.0 gcc gcc-3.4-base gcc-4.0 libc6-dev
  libstdc++6-4.0-dev linux-kernel-headers make
Suggested packages:
  binutils-doc debian-keyring gcc-4.0-doc lib64stdc++6 manpages-dev autoconf
  automake1.9 libtool flex bison gcc-doc gcc-3.4-doc libc6-dev-amd64 lib64gcc1
  gcc-4.0-locales glibc-doc libstdc++6-4.0-doc stl-manual
Recommended packages:
  libmudflap0-dev
The following NEW packages will be installed
  binutils build-essential cpp-3.4 dpkg-dev g++ g++-4.0 gcc gcc-3.4
  gcc-3.4-base gcc-4.0 libc6-dev libstdc++6-4.0-dev linux-kernel-headers make
0 upgraded, 14 newly installed, 0 to remove and 0 not upgraded.
Need to get 3752kB/12.3MB of archives.
After unpacking 51.2MB of additional disk space will be used.
Do you want to continue [Y/n]? y
'http://ca.archive.ubuntu.com/ubuntu/pool/main/b/binutils/binutils_2.16.1cvs20060117-1ubuntu1_i386.deb' binutils_2.16.1cvs20060117-1ubuntu1_i386.deb 1406252 a52d49199b53d810aca4f0725bb98887
'http://ca.archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4-base_3.4.5-1ubuntu5_i386.deb' gcc-3.4-base_3.4.5-1ubuntu5_i386.deb 164132 28e2d85198094246321d95dfaf48a8d2
'http://ca.archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/cpp-3.4_3.4.5-1ubuntu5_i386.deb' cpp-3.4_3.4.5-1ubuntu5_i386.deb 1687844 ab8a514cac61ffa0b34868e86126ab02
'http://ca.archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4_3.4.5-1ubuntu5_i386.deb' gcc-3.4_3.4.5-1ubuntu5_i386.deb 493634 4abd4a629701dff9c2275dbe1c0f4c5e
emma@Dapper:~$

---

### Post by grandline on 2006-01-19
wow that was fast :D 

Thank you, i'll try that as soon as i get home

---

### Post by mental_noise on 2006-01-19
i would also like to ask the same question and i think that it is not possible for me to do the suggested solution

[quote=azz]emma@Dapper:~$ sudo apt-get install --print-uris build-essential gcc-3.4
...[/quote]

since it shows that i need internet connection (see quoted text below)

[quote=azz]...
Do you want to continue [Y/n]? y
'http://ca.archive.ubuntu.com/ubuntu/pool/main/b/binutils/binutils_2.16.1cvs20060117-1ubuntu1_i386.deb' binutils_2.16.1cvs20060117-1ubuntu1_i386.deb 1406252 a52d49199b53d810aca4f0725bb98887
'http://ca.archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4-base_3.4.5-1ubuntu5_i386.deb' gcc-3.4-base_3.4.5-1ubuntu5_i386.deb 164132 28e2d85198094246321d95dfaf48a8d2
'http://ca.archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/cpp-3.4_3.4.5-1ubuntu5_i386.deb' cpp-3.4_3.4.5-1ubuntu5_i386.deb 1687844 ab8a514cac61ffa0b34868e86126ab02
'http://ca.archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/gcc-3.4_3.4.5-1ubuntu5_i386.deb' gcc-3.4_3.4.5-1ubuntu5_i386.deb 493634 4abd4a629701dff9c2275dbe1c0f4c5e[/quote]

and my computer at home is not connected to the internet. are there any alternatives to this solution?

i have installed ubuntu 5.10 on [FONT="Courier New"]**server**[/FONT] mode only since i have a very old pc and i want to download some packages for it but since it doesn't have any internet connection, the [FONT="Courier New"]**sudo apt-get**[/FONT] from the repositories is out of the question. i want to generate a list on which packages are installed so that i will only download packages (and dependencies) which are not.

---

### Post by cwaldbieser on 2006-01-19
[QUOTE=mental_noise]i would also like to ask the same question and i think that it is not possible for me to do the suggested solution



since it shows that i need internet connection (see quoted text below)



and my computer at home is not connected to the internet. are there any alternatives to this solution?

i have installed ubuntu 5.10 on [FONT="Courier New"]**server**[/FONT] mode only since i have a very old pc and i want to download some packages for it but since it doesn't have any internet connection, the [FONT="Courier New"]**sudo apt-get**[/FONT] from the repositories is out of the question. i want to generate a list on which packages are installed so that i will only download packages (and dependencies) which are not.[/QUOTE]

Try:
```

$ dpkg -l > packagelist.txt

```

---

