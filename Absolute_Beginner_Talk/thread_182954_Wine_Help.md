---
title: "Wine Help"
date: 2006-05-27
forum: Absolute Beginner Talk
---

### Post by KarmaKing on 2006-05-27
I am installing wine, but i want to make sure this:

>  wine-doc winesetuptk
0 packages upgraded, 1 newly installed, 2 to remove and 0 not upgraded.
Need to get 12.8MB of archives. After unpacking 43.7MB will be used.
Do you want to continue? [Y/n/?] y
WARNING: untrusted versions of the following packages will be installed!

Untrusted packages could compromise your system's security.
You should only proceed with the installation if you are certain that
this is what you want to do.

  wine
Should I go ahead and install the packages anyway?
To continue, enter "Yes"; to abort, enter "No":


is kosher.  When it says need to get 12MB of archives, is this idication it will make the archives or I have to?

second, Untrusted packages and compromise get me a little skittish, do others get this same thing when installing wine?

---

### Post by angkor on 2006-05-27
[QUOTE=KarmaKing]
Untrusted packages and compromise get me a little skittish, do others get this same thing when installing wine?[/QUOTE]

Please post your /etc/apt/sources.list and check what repository you are downloading Wine from. You will not get this message when you download Wine from the official Ubuntu repositories.

If you trust the repo you're downloading it from you don't have much to worry about.

---

### Post by KarmaKing on 2006-05-27
hello angkor,

this is what the repo said

[http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt)

I am not sure either way if it is trusted or not.

are there others??

thanks

KK

---

### Post by Koech on 2006-05-27
I think that repo is trustworthy enough. Just go ahead with it.

---

