---
title: "Problem with Gutsy upgrade"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by Xezal on 2008-01-15
I tried to upgrade Feisty to Gutsy because, as the Adept Manager keeps reminding me, it's available.

However, after the manager attempts to fetch files, I get this message:

Error during update
A problem occured during the update.  This is usually some sort of network problem, please check your network connection and retry.

Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg](http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2](http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz](http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz) Could not resolve 'wine.lowvoice.nl'


Does anyone have any suggestions of where to start looking for a correction to this problem?  

Thanks.

---

### Post by linuxwizard on 2008-01-15
Remove or disable the extra repos you added to your source list

---

### Post by Xezal on 2008-01-15
Thanks for the reply.

I uninstalled wine and tried to upgrade again.  Is there something else I should be looking at instead?

---

### Post by carverj on 2008-01-15
I had some problems when I tried also. So ended up just installing Gutsy from scratch.
This is the preferred method, particularly when you want to install the 64-bit OS!

---

### Post by kostkon on 2008-01-15
As *linuxwizard* says, you need to remove this repository because it does not exist anymore. Since you are using K*ubuntu*, the thing you have to do is to open *Adept* and go to *View > Manage Repositories*, find the repository in question and delete it.

After this, your upgrade should continue fine.

You have the option, after the upgrade to put the official *Wine* repository if you want to get fresh versions of this application. Just visit [this page and follow the how-to]("http://www.winehq.org/site/download-deb"). It does not matter that it says *Ubuntu* and not *Kubuntu*, you need to do the same things.

Since you have already uninstalled *Wine*, after adding the repository, reinstall it and you'll have the latest version and get updates every time there is a new version (usually every 2-3 weeks).

---

