---
title: "[SOLVED] Websites are not openning in Firefox.."
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by chatterjee on 2007-07-21
Some websites are not openning in Firefox(Ubuntu).The strange thing is that...they all are working fine on Windows.Whenever I type ubuntuforums.org in firefox it open up a "server cannot be found" error message.Google.com,opera.org,Yahoo.com etc are easily openned in firefox while those particualr websites are blocked.But I surely know that they support firefox.What's happening?

   I downloaded a copy of Oper9.22 for Ubuntu.But it doesn't install.Instead it gives an error:"Dependency is not satisfiable:libqt3-mt".What's it?

thanks in advance...

---

### Post by wolfen69 on 2007-07-21
try downloading opera from synaptic.

---

### Post by ayenack on 2007-07-21
if you want to install libqt3-mt then type this in terminal.

sudo apt get install libqt3-mt

Look in synaptic>package>manager for more info on this do a search.

---

### Post by nitro_n2o on 2007-07-21
you need to check your internet connection.. r u using a dial up modem, router or DSL ?? 
for opera  just get it from snayptic 
```
sudo apt-get install opera
``` 
It'll take care of dependencies "libqt" is the QT library for the opera GUI you'll also need it for skype

---

### Post by chatterjee on 2007-07-22
When I used this in terminal,I got this error report.....

"Package libqt3-mt is not available,but is referred to by another package.This may mean that the package is missing,has been obsoletes,or is only available from another source"

How should I install it?

---

### Post by chatterjee on 2007-07-22
Please reply friends!

---

### Post by irish_flu on 2007-07-22
Open up the Terminal.

type:
ping [www.ubuntuforums.org](www.ubuntuforums.org)

(you can hit CTRL+C to stop it).

If that works, the problem is in Firefox.

If it doesn't work, try to get there by IP:
ping 82.211.81.186

(that's an ubuntuforums.org webserver IP)

If that works, the problem is DNS.

If that doesn't work, there are bigger issues afoot....

---

### Post by chatterjee on 2007-07-23
Thank you,the problem has been solved.The DNS was wrong.

Can please solve the problem of Opera about libqt3-mt?

---

