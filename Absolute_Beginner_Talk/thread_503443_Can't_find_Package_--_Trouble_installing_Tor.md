---
title: "Can't find Package -- Trouble installing Tor"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by stormblue on 2007-07-17
When I try to install tor, I get the following:

user@machine:~$ sudo apt-get install tor
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  tor: Depends: libevent1 (>= 1.1a) but it is not installable
E: Broken packages


Any ideas?

Thanks!

---

### Post by DBStevens on 2007-07-17
It looks like tor isn't in the repositories you have setup.

Try visiting this page:

[http://tor.eff.org/download-unix.html.en](http://tor.eff.org/download-unix.html.en)

---

### Post by stormblue on 2007-07-17
Thanks, followed those directions and found that I was using edgy not feisty, so that's fixed.

But I'm still having the same problems.  Any other ideas?

---

### Post by stormblue on 2007-07-17
When I try to compile from source I get this:

checking for libevent directory... configure: error: Could not find a linkable libevent. You can specify an explicit path using --with-libevent-dir

---

### Post by DBStevens on 2007-07-17
Do a search for libevent using Synaptic.

I would install the two entries with the Ubuntu logo ;-).

---

### Post by Celegorm on 2007-07-17
Sounds like you're missing a dependency, libevent. Try > sudo apt-get install libevent1 and then try configuring and compiling again.

---

### Post by stormblue on 2007-07-17
Thanks for the advice so far, but I've already tried those.

I don't know if we are talking about the same synaptic, but I don't see any ubuntu logos.  All I see are libevents-someprogramminglanguage

and as far as the apt-get install routine, it says:

Package libevent1 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libevent1 has no installation candidate


Keep the ideas coming!

---

### Post by stormblue on 2007-07-17
FIXED!!!

Somehow feisty main got # out.  No idea how that happened, but thanks for the help so far!

---

### Post by RomeReactor on 2007-07-18
Hi. You're using Edgy, right? I think you may not have Universe and Multiverse repositories enabled; for that, look [here]("https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096"). After adding the extra repositories, you need to bring your package manager's repository information up to date: you can do that from the terminal (Applications->Accessories->Terminal) by entering:
```
sudo apt-get update
```
or you can do that from Synaptic (by pressing the **Reload** button)

You can then search for **libevent1** and install it (it *shoud* appear then).

If it still doesn't show up, you can grab the **.deb** package from [here]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Flibe%2Flibevent%2Flibevent1_1.1a-1_i386.deb&md5sum=86dd60b8a47e7f0be8e2a2fbd91b368e&arch=i386&type=main"). 
After downloading the file, double-click on it to bring up Gdebi to assist you through the installation.

**EDIT**: Glad you sorted it out!

---

