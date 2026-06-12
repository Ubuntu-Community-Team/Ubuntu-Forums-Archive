---
title: "Installing Thunderbird 3.0 alpha"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by gupta_sumesh63 on 2007-09-22
Hi,
I have downloaded Thunderbird 3.0 alpha. I have Thunderbird 2.0 already installed.
How do I install 3.0 alpha? Do I have to remove 2.0 before installing 3.0 alpha. If so, how do I remove TB 2.0 which was downloaded as tar.bz2 and installed using ./install.?
Thanks

---

### Post by alienexplorers on 2007-09-22
You can use the two versions together.  Just have to make a new profile file for 3.0 so you don't have conflicts with 2.0.0.7...   
Just untar it using tar -xvjf NAME.tar.bz2  into your home directory.

---

### Post by ramjet_1953 on 2007-09-22
Unless you are familiar with compiling your own binaries from source, I would not attempt it at this stage.

It is not just a matter of compiling and all is rosy, unfortunately.

You have to satisfy dependencies yourself and this usually also entails installing both the required packages and the .dev package, as well.

However, if you still want to go ahead, you need to install this package first:

In a terminal copy and paste this command:

[COLOR="Red"]sudo apt-get install build-essential[/COLOR]

Of course, if you can get a .deb package, the above doesn't apply.

Regards,
Roger 8)

---

### Post by alienexplorers on 2007-09-22
Ramjet,
I am currently running Thunderbird 3.0 and it extracts from the bz2 file ready to go.  I just made a seperate profile using thunderbird -profilemanager.

---

