---
title: "Copying synaptic packages"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by Belliinator on 2008-01-21
How do I copy downloaded .deb packages in synaptic from another machine and install them on my own cleanly, so I don't have to download them again?

---

### Post by capink on 2008-01-21
The deb packages should be located in /var/cache/apt/archives.

copy them from there and place them in the same direcotry on your machine (i.e /var/cache/apt/archives).

whenever you install a package that is present in /var/cache/apt/archives you will not need to download it again, it will install directly from there.

---

### Post by banewman on 2008-01-21
If you are using the synaptic package manager there is an option to only download the package after you select it then click apply - check that.
then you can copy the file to cd, usb etc and give synaptic on the other machine the option to use that cd etc as a source.
:

---

### Post by Belliinator on 2008-01-21
Cool, thanks

---

### Post by sailor2001 on 2008-01-21
or burn a cd...  in synaptics:  aptoncd

---

### Post by Belliinator on 2008-03-16
Another question. How do I get official packages that were already installed  when ubuntu itself was installed, so I can transfer them to linux mint?

---

### Post by capink on 2008-03-17
Ubuntu is made up by handful of [metapackages]("https://help.ubuntu.com/community/MetaPackages") that depends on all the packages needed to build the system.

If you want to know all the packages installed by the live cd not just the names of the metapackages you need to install apt-rdepends:

```
sudo apt-get install apt-rdepends
```

Now run the following command to get the names of the packages:

```
apt-rdepends ubuntu-minimal ubuntu-standard ubuntu-desktop linux-generic linux-headers-generic | sed 's/^  Depends: //' | awk '{print $1}' | sort -u 
```


Note:
====
- If you are using Kubuntu or Xubuntu replace ubuntu-desktop with kubuntu-desktop or xubuntu-desktop.

- The kernel packages (e.g linux-image-version) contain the version in the filename. I am not sure the same kernel versions will be available in Mint (I never used it). It is better to exclude these packages and rely on the linux-generic packages to pull the appropriate kernel version for you. To exclude the ubuntu-specific kernels append: | grep -v '^linux-.*-2.6' to the last command to be as follows:

```
apt-rdepends ubuntu-minimal ubuntu-standard ubuntu-desktop linux-generic linux-headers-generic | sed 's/^  Depends: //' | awk '{print $1}' | sort -u | grep -v '^linux-.*-2.6'
```

---

### Post by Belliinator on 2008-03-26
How do I copy them over once I found out what the are?

---

