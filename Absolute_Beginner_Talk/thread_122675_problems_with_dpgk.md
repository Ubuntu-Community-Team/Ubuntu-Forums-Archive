---
title: "problems with dpgk"
date: 2006-01-28
forum: Absolute Beginner Talk
---

### Post by DeadEnd on 2006-01-28
Cannot update uninstall or install packages I get the error as displayed at the bootom of output'

 E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened


==========================================================
> apt-get --list-cleanup update
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg [189B]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release [19.6kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release [19.6kB]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release [19.6kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Sources
Fetched 59.6kB in 1s (31.2kB/s)
Reading package lists...
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

---

### Post by Lambert on 2006-01-29
There is a backup of the /var/lib/dpkg/status file in the same directory called status-old

You may want to copy that over to fix this.

```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```

The problem you might have is depending on how old and what's been done since status-old was created. If you have installed some programs then their status won't be shown accurately and you will need to reinstall that program to update.

If that file is corrupted and gives you the same errors you can look into /var/backups/dpkg.statusX These are more backups of that file zipped so you can unzip and copy over to status. Again though same problem with reported status of a package depending on how old the file you copy over is.

---

### Post by DeadEnd on 2006-01-29
Thank you for the information.
I did try your suggestion yesterday after scouring web along with others but no luck same error,so I took the easy way out and basically reinstalled.

---

### Post by Supertip on 2006-02-10
im not sure, but arn't you supposed to ```
sudo apt-get
```

---

