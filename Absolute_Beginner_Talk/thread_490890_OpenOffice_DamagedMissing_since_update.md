---
title: "OpenOffice Damaged/Missing since update"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by RBird on 2007-07-03
I am currently using Ubuntu 6.06 LTS - the Dapper Drake on my laptop.

I'm not sure what happened. I just updated Ubuntu using Update Manager. During the process I noticed there were some errors. Sorry I didn't write them down. I simply clicked "Install Updates" and assumed that whatever the errors were, they would be fixed during the update.

After the update, OpenOffice disappeared from my machine. Apparently it was deleted during the update process. I tried re-installing OpenOffice using Synaptic. I marked OpenOffice.org for installation and I got the following message: 
-------------------------------
Could not mark all packages for installation or upgrade.
The following packages have unresolvable dependencies. Make sure that all required repositories are added and enabled in the preferences.

openoffice.org:
 Depends: openoffice.org-core but it is not going to be installed
 Depends: openoffice.org-java-common but it is not going to be installed
--------------------------------


This makes no sense. I marked and installed both of these. Then I went back to try to install OpenOffice again and I still got the same message. OpenOffice simply refuses to re-install.

What am I missing? And does anyone know why Update Manager erased OpenOffice from my computer in the first place?

:confused:   I am one confused newbie. Any advice at all would be appreciated.

-R Curtis

---

### Post by Maxtorm on 2007-07-03
From a terminal session, what does the following command return?
```
sudo apt-get install openoffice.org
```
(This should be doing the same thing as the Synaptic GUI.)

---

### Post by RBird on 2007-07-03
I tried running the command:  sudo apt-get install openoffice.org

Here is the resulting error message:

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  openoffice.org: Depends: openoffice.org-core (> 2.0.2) but it is not going to be installed
                  Depends: openoffice.org-java-common but it is not going to be installed
E: Broken packages

-----------------------------------------------------

Does this give any information that might help me install OpenOffice?


R Curtis

---

### Post by Maxtorm on 2007-07-05
In Synaptic, there is a menu option for "Fix Broken Packages" (sorry, can't recall exactly where it is; don't have my Ubuntu box in front of me right now).  Have you tried that?

---

