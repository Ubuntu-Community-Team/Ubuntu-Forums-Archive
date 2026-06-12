---
title: "msttcorefonts installation"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by falk3r on 2007-03-26
I'm trying to install msttcorefonts to no avail:

I uncommented a few lines in a file to enable the universe and multiverse repositories and ran the code:

```
sudo apt-get install msttcorefonts
```

But I get the following error:

```
falk3r@falk3r-desktop:~$ sudo apt-get install msttcorefonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package msttcorefonts is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package msttcorefonts has no installation candidate
```

Suggestions?
 - falk3r

---

### Post by Michaelt74 on 2007-03-26
They're available in the repositories,  ensure multiverse repositories are enable. When they are, search for the msttcorefonts and they should be there.

---

### Post by lamalex on 2007-03-26
maybe try going through synaptic, i know it's the exact same thing but, ya never know right?

---

### Post by falk3r on 2007-03-26
Call me a newb, but what exactly am I selecting to install via Synaptic?

Searches produce nil for "multiverse"... 

What *Section* (left pane) and *Selection* (top pane) should I be looking for?

Thanks,
 - falk3r

---

### Post by Michaelt74 on 2007-03-26
If you're using Ubuntu 6.10: From your desktop, select 'System>Administration>Synaptic package manager>Settings>Repositories. Ensure on 'Internet' all repositories are checked.

Then click on search and search for msttcorefonts, check then and install.

If you're not sure keep asking; that's why the forums are here.

---

### Post by falk3r on 2007-03-26
Ubunto 6.10, yes.

Got it, thanks!

---

