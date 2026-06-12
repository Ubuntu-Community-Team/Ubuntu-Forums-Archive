---
title: "Upgrade to Fiesty problems"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by HareBall on 2007-09-04
I did a search and can't find any reference to my problem.
Whenever I try to upgrade to Fiesty using the button at the top of the upgrade(?) screen, I get a message that it can't download the files after about 119. It then only gives me a choice of closing. I have tried to do this off and on for about the last 3 months.
Any ideas?:confused:

---

### Post by afonic on 2007-09-04
Make sure you have the latest version of update-manager package from the repos and a full updated Edgy system. You may need to use the edgy-proposed update-manager, right click on it in and see the available versions.

Other than that general advice, post the error message exactly so we can provide some kind of help.

---

### Post by HareBall on 2007-09-04
Here are the errors I get. I get all of these in one message window.
I told you wrong earlier, it makes it to file 123 and then keeps trying to get the rest over and over untill it pops up this message.

"A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry."

Then this is in a box below the message above.

Failed to fetch [http://wine.lowvoice.nl/apt/dists/dapper/Release.gpg](http://wine.lowvoice.nl/apt/dists/dapper/Release.gpg) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/dapper/main/i18n/Translation-en_US.bz2](http://wine.lowvoice.nl/apt/dists/dapper/main/i18n/Translation-en_US.bz2) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://www.beerorkid.com/compiz/dists/dapper/Release.gpg](http://www.beerorkid.com/compiz/dists/dapper/Release.gpg) The HTTP server sent an invalid reply header
Failed to fetch [http://www.beerorkid.com/compiz/dists/dapper/main/i18n/Translation-en_US.bz2](http://www.beerorkid.com/compiz/dists/dapper/main/i18n/Translation-en_US.bz2) Bad header line
Failed to fetch [http://ubuntu.compiz.net/dists/dapper/main/binary-i386/Packages.gz](http://ubuntu.compiz.net/dists/dapper/main/binary-i386/Packages.gz) 302 Found [IP: 63.251.133.40 80]
Failed to fetch [http://wine.lowvoice.nl/apt/dists/dapper/main/binary-i386/Packages.gz](http://wine.lowvoice.nl/apt/dists/dapper/main/binary-i386/Packages.gz) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://www.beerorkid.com/compiz/dists/dapper/main/binary-i386/Packages.gz](http://www.beerorkid.com/compiz/dists/dapper/main/binary-i386/Packages.gz) Bad header line

---

### Post by rsambuca on 2007-09-04
Those are all non-standard ubuntu repositories.  For now I would suggest commenting them out by placing a number sign in front of them in your /etc/apt/sources.list.

Also, because you have been using them, there is a distinct possibility that the upgrade will not go smoothly, so make sure you have every piece of critical data backed up.

---

### Post by HareBall on 2007-09-04
How do I know which sources.list to modify? I have 7 different files, not counting backups.

---

### Post by rsambuca on 2007-09-04
Use ```
gksudo gedit /etc/apt/sources.list
```

---

### Post by HareBall on 2007-09-05
Just got finished. So far, so good.

---

### Post by HareBall on 2007-09-05
> **HareBall said:**
> Just got finished. So far, so good.
Well I lost my access to newsgroups with Pan and when I set it back up to use again I can't seem to get it to work right. It didn't want to go online at first and now that it is, I can't figure out how to get it to download the list of groups.
Any help will be appreciated.

---

