---
title: "Installing Kiba-Dock on Gutsy?"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by phoenix23 on 2007-10-21
How are people installing Kiba Dock on Gutsy? I went to the official site and read that you&#341;e supposed to use the Feisty repositories, but these will not load.

This error shows up

> Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

for these sources

> [http://download.tuxfamily.org/3v1deb/dists/feisty/*/binary-i386/Packages.gz:](http://download.tuxfamily.org/3v1deb/dists/feisty/*/binary-i386/Packages.gz:) 404 Not Found
[http://download.tuxfamily.org/3v1deb/dists/feisty/deb-src/binary-i386/Packages.gz:](http://download.tuxfamily.org/3v1deb/dists/feisty/deb-src/binary-i386/Packages.gz:) 404 Not Found
[http://download.tuxfamily.org/3v1deb/dists/feisty/http://download.tuxfamily.org/3v1deb/binary-i386/Packages.gz:](http://download.tuxfamily.org/3v1deb/dists/feisty/http://download.tuxfamily.org/3v1deb/binary-i386/Packages.gz:) 404 Not Found
[http://download.tuxfamily.org/3v1deb/dists/feisty/feisty/binary-i386/Packages.gz:](http://download.tuxfamily.org/3v1deb/dists/feisty/feisty/binary-i386/Packages.gz:) 404 Not Found


If I install it anyway, Kiba-Dock runs fine, but CompizConfig Settings Manager will no longer open, and my custom effects won´t work.

Any ideas?

---

### Post by kasulstyls on 2007-10-22
If your kiba-dock is running ok, go to your software sources and uncheck the added repo's of tuxfamily.

Then go to synaptic and search for compiz. When the list populates go to the settings manager and choose the previous version.

 so highlight compizconfig-settings-manager,  then go to package, force version, choose 20070912 or whatever is lower in your display. Also you can lock this version if you like.  

Keep in mind you will have to reset all your custom settings.

---

### Post by xfearxnxloathing on 2008-01-18
the same thing happened to me so i uninstalled kiba-dock and compiz fusion and reinstalled compiz fusion but when i went to search kiba-dock in the synaptic package manager it no longer appears, like it is unavailable or by some freak way did a total removal.  how could i get kiba-dock to show back up inside synaptic package manager?

---

### Post by xfearxnxloathing on 2008-01-19
bump

---

### Post by kasulstyls on 2008-01-24
You will have to reinstall it.    Go to this site and use his script.  It will install the latest version of kiba on your system with all the necessary files.  Please read his instructions but other than that it is really easy.

[http://www.kiba-dock.org/index.php?option=com_smf&Itemid=30&topic=540.msg2613#msg2613](http://www.kiba-dock.org/index.php?option=com_smf&Itemid=30&topic=540.msg2613#msg2613)

------
Past from instruction on the site from Joshsmith.

the bit of the left of the terminal tells you where you are, ie " josh@josh-computer: ~$ " means logged in as josh, on josh-computer at directory ~ (which is your home directory)

then type:
cd Desktop
which changes to your Desktop directory (capitals do matter)
then now you are in the right directory where the script is
now type
chmod +x intall_kiba-dock-en.sh
(which make it executable)
(due to a typo it is intall rather than install)
./intall_kiba-dock-en.sh i
(due to a typo it is intall rather than install)
then wait and follow the on screen instructions,
when its done, go into your main menu>accessories>kiba-dock

--------


let me know if you have any ?'s

Kas

---

