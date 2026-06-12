---
title: "Question about debs"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by Atreus12 on 2007-10-28
This is actually a question about debian etch, but it should all be the same.

I want to install openoffice 2.3. I downloaded the deb from openoffice.org, and had a few questions.

First, do I need to apt-get remove (or purge) openoffice 2.0 that was installed from the repos?

Do I need to run dpkg with any options to insure that I can completely remove openoffice 2.3 in the future (this one is important, I don't have much hard drive space left)

Do I need to keep the .deb package to be able to remove openoffice 2.3 in the future? It's over 100mb.

Finally, should I be using dpkg to install the deb, or should I try to use apt to "upgrade" my current package from the .deb?

-Andrew

---

### Post by Seisen on 2007-10-28
You will want to remove the old openoffice packages before you run the .deb file. You don't need to run any special commands with dpkg, when you want to remove openoffice just do this ```
sudo dpkg -r openoffice
```. Once you install Openoffice you can delete the .deb file.

---

