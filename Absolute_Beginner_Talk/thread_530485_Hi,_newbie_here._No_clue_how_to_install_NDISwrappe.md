---
title: "Hi, newbie here. No clue how to install NDISwrapper to get wireless card working"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by Lister2020 on 2007-08-20
Im using the WPNT511 card and I have seen guides to get it working,but I cannot get ndiswrapper to install. It keeps giving me error messages that it cannot access various stuff. I read the guide that came with it and I have absolutely no clue. This is literally my very first time using linux so I need spoonfed. Can anyone help?

---

### Post by mysticmatrix on 2007-08-20
Did you try this?

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

If this didn't work, can you be more specific about what errors did you get?

---

### Post by Lister2020 on 2007-08-20
Hi, ill try and get a list of the specific error messages but it says that it cannot access multiple files/resources/locations and that they must be in use by another program.

EDIT: And I did try that guide and I still don't understand a thing. It tells me to click this link to make sure I have multiverse and universe repositires enabled And I have no idea what these are and the page it links to doesn't mention them anywhere.

When I go to System and the administration, I dont see a software properties tab which is what it wants me to go to :/

---

### Post by Lister2020 on 2007-08-20
Heres a perfect example. I went to try and do it by command line.

It tells me to look at this /etc/apt/sources.list

When I type that in the  terminal it simply says "Access denied"

damien@damien-laptop:~$ /etc/apt/sources.list
bash: /etc/apt/sources.list: Permission denied
damien@damien-laptop:~$ 


What on earth :(

---

### Post by philinux on 2007-08-20
> **Lister2020 said:**
> Heres a perfect example. I went to try and do it by command line.

It tells me to look at this /etc/apt/sources.list

When I type that in the  terminal it simply says "Access denied"

damien@damien-laptop:~$ /etc/apt/sources.list
bash: /etc/apt/sources.list: Permission denied
damien@damien-laptop:~$ 


What on earth :(

To view this file you should either 
1. Browse to it from Places>Computer>etc ... or
2. Gedit /etc/apt/sources.list

---

### Post by mysticmatrix on 2007-08-20
> **Lister2020 said:**
> Hi, ill try and get a list of the specific error messages but it says that it cannot access multiple files/resources/locations and that they must be in use by another program.

EDIT: And I did try that guide and I still don't understand a thing.[COLOR="Red"] It tells me to click this link to make sure I have multiverse and universe repositires enabled And I have no idea what these are and the page it links to doesn't mention them anywhere.[/COLOR]

When I go to System and the administration, I dont see a software properties tab which is what it wants me to go to :/

Either you missed it or.....

See this page for what you need.(1st link on RepositaryHowTo)

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

