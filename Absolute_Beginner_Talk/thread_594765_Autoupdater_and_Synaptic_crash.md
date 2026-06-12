---
title: "Autoupdater and Synaptic crash"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by Justgeek on 2007-10-28
When I used the automated updater the last time there was new package it totally crash. After a reboot I keep getting this:

Could not initialize the package information
```

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Malformed 2nd word in the Status line, E:Der skete en fejl under behandlingen af mount (UsePackage2), E:Problem with MergeList /var/lib/dpkg/status, E:Pakkelisterne eller statusfilen kunne ikke tolkes eller åbnes.'

And Add/Remove:
Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.
```

When running the synaptic application i get this:
```
E: Malformed 2nd word in the Status line
E: Der skete en fejl under behandlingen af mount (UsePackage2)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

```

---

### Post by Crafty Kisses on 2007-10-28
> **Justgeek said:**
> When I used the automated updater the last time there was new package it totally crash. After a reboot I keep getting this:

Could not initialize the package information
```

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Malformed 2nd word in the Status line, E:Der skete en fejl under behandlingen af mount (UsePackage2), E:Problem with MergeList /var/lib/dpkg/status, E:Pakkelisterne eller statusfilen kunne ikke tolkes eller åbnes.'

And Add/Remove:
Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.
```

When running the synaptic application i get this:
```
E: Malformed 2nd word in the Status line
E: Der skete en fejl under behandlingen af mount (UsePackage2)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

```
Sounds like the Synaptic package is broken, Try reinstalling it.
```
sudo apt-get install synaptic
```

---

### Post by Justgeek on 2007-10-28
Hmm. Its not possible to install any thing without that same message comming alive

> jens@jens-laptop:~$ sudo apt-get install synaptic
Password:
Indlæser pakkelisterne... Fejl!
E: Malformed 2nd word in the Status line
E: Der skete en fejl under behandlingen af mount (UsePackage2)
E: Problem with MergeList /var/lib/dpkg/status
E: Pakkelisterne eller statusfilen kunne ikke tolkes eller åbnes.
jens@jens-laptop:~$ 


---

### Post by Andrew123 on 2007-10-28
I have the same problem

---

### Post by Pumalite on 2007-10-28
I imagine you already:
sudo apt-get update
sudo apt-get install -f

---

### Post by Crafty Kisses on 2007-10-28
> **Andrew123 said:**
> I have the same problem

Are you using Gutsy or Feisty?

---

### Post by Andrew123 on 2007-10-28
this is the error i get E: Type '“deb' is not known on line 56 in source list /etc/apt/sources.list when i type  sudo apt-get update

---

### Post by Andrew123 on 2007-10-28
gusty

---

### Post by Pumalite on 2007-10-28
> **Andrew123 said:**
> this is the error i get E: Type '“deb' is not known on line 56 in source list /etc/apt/sources.list when i type  sudo apt-get update

Edit your sources.list and comment out (#) line 56
gksudo gedit /etc/apt/sources.list
Backup first:
sudo cp /etc/apt/sources.list /etc/apt/sources.list.back

---

### Post by Justgeek on 2007-10-28
Hmm my source list only has 43 lines ;)

But Im also on Feisty any suggestions?

> I imagine you already:
sudo apt-get update
sudo apt-get install -f
Tried does and it sends the same error. It loads the packages but end up with the same error

---

### Post by Pumalite on 2007-10-28
> **Justgeek said:**
> When I used the automated updater the last time there was new package it totally crash. After a reboot I keep getting this:

Could not initialize the package information
```

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Malformed 2nd word in the Status line, E:Der skete en fejl under behandlingen af mount (UsePackage2), E:Problem with MergeList /var/lib/dpkg/status, E:Pakkelisterne eller statusfilen kunne ikke tolkes eller åbnes.'

And Add/Remove:
Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.
```

When running the synaptic application i get this:
```
E: Malformed 2nd word in the Status line
E: Der skete en fejl under behandlingen af mount (UsePackage2)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

```

These are my first 2 lines in dpkg/status; compare them with yours:

Package: python-bittorrent
Status: install ok installed

---

### Post by Justgeek on 2007-10-29
My status:
> Package: python-bittorrent
Status: install ok installed

---

