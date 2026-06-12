---
title: "Problems updating Wine"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by Jorge32 on 2006-12-29
Hi, I am havin a problem updating wine. On the synaptic package manager I select the upgrade of wine and wine-dev  and It doesn't starts the update. This message is appearing:

W: Failed to fetch [http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine-dev_0.9.28~winehq0~ubuntu~6.10-1_i386.deb](http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine-dev_0.9.28~winehq0~ubuntu~6.10-1_i386.deb)
  Could not connect to wine.budgetdedicated.com:80 (81.171.111.184). - connect (111 Connection refused)


W: Failed to fetch [http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.28~winehq0~ubuntu~6.10-1_i386.deb](http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.28~winehq0~ubuntu~6.10-1_i386.deb)
  Could not connect to wine.budgetdedicated.com:80 (81.171.111.184). - connect (111 Connection refused)

Where is my problem? it is because I just changed to Xubuntu? I can read that there it says ~ubuntu~6.10-1_i386.deb, or is it for another reason?

This message also appears when I click on the reload button on the synaptic:
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://wine.budgetdedicated.com/apt/dists/edgy/Release.gpg:](http://wine.budgetdedicated.com/apt/dists/edgy/Release.gpg:) Could not connect to wine.budgetdedicated.com:80 (81.171.111.184). - connect (111 Connection refused)
[http://wine.budgetdedicated.com/apt/dists/edgy/main/i18n/Translation-en_US.bz2:](http://wine.budgetdedicated.com/apt/dists/edgy/main/i18n/Translation-en_US.bz2:) Could not connect to wine.budgetdedicated.com:80 (81.171.111.184). - connect (111 Connection refused)

---

### Post by OffHand on 2006-12-29
> **Jorge32 said:**
> Hi, I am havin a problem updating wine. On the synaptic package manager I select the upgrade of wine and wine-dev  and It doesn't starts the update. This message is appearing:

W: Failed to fetch [http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine-dev_0.9.28~winehq0~ubuntu~6.10-1_i386.deb](http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine-dev_0.9.28~winehq0~ubuntu~6.10-1_i386.deb)
  Could not connect to wine.budgetdedicated.com:80 (81.171.111.184). - connect (111 Connection refused)


W: Failed to fetch [http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.28~winehq0~ubuntu~6.10-1_i386.deb](http://wine.budgetdedicated.com/apt/pool/main/w/wine/wine_0.9.28~winehq0~ubuntu~6.10-1_i386.deb)
  Could not connect to wine.budgetdedicated.com:80 (81.171.111.184). - connect (111 Connection refused)

Where is my problem? it is because I just changed to Xubuntu? I can read that there it says ~ubuntu~6.10-1_i386.deb, or is it for another reason?

This message also appears when I click on the reload button on the synaptic:
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://wine.budgetdedicated.com/apt/dists/edgy/Release.gpg:](http://wine.budgetdedicated.com/apt/dists/edgy/Release.gpg:) Could not connect to wine.budgetdedicated.com:80 (81.171.111.184). - connect (111 Connection refused)
[http://wine.budgetdedicated.com/apt/dists/edgy/main/i18n/Translation-en_US.bz2:](http://wine.budgetdedicated.com/apt/dists/edgy/main/i18n/Translation-en_US.bz2:) Could not connect to wine.budgetdedicated.com:80 (81.171.111.184). - connect (111 Connection refused)

Just means the mirror is down. Try again later. Drink some beer.

---

