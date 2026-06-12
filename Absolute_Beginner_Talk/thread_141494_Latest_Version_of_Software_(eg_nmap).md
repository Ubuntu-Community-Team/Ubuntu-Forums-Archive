---
title: "Latest Version of Software (eg nmap)"
date: 2006-03-08
forum: Absolute Beginner Talk
---

### Post by grim1234 on 2006-03-08
How is the version of an app in the repository decided? If I want the latest version of a package, is that dependant upon someone building and submitting the package?

Take nmap for example - 

breezy - nmap version 3.81
dapper - nmap version 3.95

I know that version 4 has been out for a couple of months now, yet to get this for ubuntu, would I have to compile from source?

If I do this, how would that affect apt? What happens if apt wants to install an app, due to a dependancy for example, after I've compiled from source and installed?

---

### Post by meborc on 2006-03-08
well i can't answer all your questions, but i know few things... for one, there are different kinds of repositories... 

in the default/original repositories there are only STABLE versions of software, from the time the distro came out... that way if a person installs breezy even NOW, there will be no problem with the software... it's kind of backup :)

then there are backports, which basically take the progz from dapper and make then run under breezy... so that you have newer versions of programs, but still quite safe as backports are stricktly under control

to get the ultimate new version of a prog, you have to download the source and compile it yourself... it is because usually there are a lot of dependency problems and each system is different... you might also find .deb or other packs ready for use, but then again, they are not as safe as STABLE versions...

hope i made some sence :neutral:

EDIT: to get the newer nmap (3.95) to breezy, ask the backport team to backport it... if it hasn't been done already

---

