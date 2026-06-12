---
title: "Koffice help!"
date: 2006-03-28
forum: Absolute Beginner Talk
---

### Post by wpp42000 on 2006-03-28
I have been playing with Breezy for a few weeks thinking I was learning something, so I decided to remove openoffice2 (the menus did not all work and it seemed slow) and install Koffice (the recent announcement on version 1.5beta made me do it).

Anyway, Using Adept, I removed openoffice2 and all its baggage.  Then I added the package 

deb [http://kubuntu.org/packages/koffice-15beta2](http://kubuntu.org/packages/koffice-15beta2) breezy main 
 
in Adept/manage repositories.

Then did a fetch updates and nothing happened.  When I do a quick filter on "koffice", all I get is

koffice-data
koffice-libs

What did I do wrong?  How do I get Koffice installed?

---

### Post by gazj on 2006-03-28
did you remember to update your adept, i don't use kubuntu, so i dont know how to do it in adept, but if you open a command line terminal and type this command then try adept again

```
sudo apt-get update
```

Hope this works for you

---

### Post by wpp42000 on 2006-03-28
gazj-

I did as you suggested and it updated!  I thought the fetch-updates button on Adept did the same thing, but maybe not.  Anyway, I am moving forward.  Thanks.

---

### Post by gazj on 2006-03-28
just do you know

the fetch updates in adept fetches updated versions of programs that are available.

this can be done in the command prompt with sudo apt-get upgrade

the command i gave you updates to the latest list of programs available, if that makes sense i think it does

there should be somewhere in adept to do the first command i gave you (sudo apt-get update), but i couldn't tell you exactly where as i use ubuntu not kubuntu

---

### Post by MartinJ on 2006-03-28
[QUOTE=gazj]
the fetch updates in adept fetches updated versions of programs that are available.[/QUOTE]

Are you sure about that?
I've been using KDE for a while but I tested Adept anyway:

'Fetch Updates' is equivalent to apt-get update
'Full Upgrade' is equivalent to apt-get upgrade

So, Fetch Updates will refresh the package list, while Full Upgrade should pick out any upgradable packages.

:D

---

### Post by gazj on 2006-03-29
[QUOTE=MartinJ]Are you sure about that?
I've been using KDE for a while but I tested Adept anyway:

'Fetch Updates' is equivalent to apt-get update
'Full Upgrade' is equivalent to apt-get upgrade

So, Fetch Updates will refresh the package list, while Full Upgrade should pick out any upgradable packages.

:D[/QUOTE]

your a lot more likely right than me, im only try to remember from when i used kde, lol

---

