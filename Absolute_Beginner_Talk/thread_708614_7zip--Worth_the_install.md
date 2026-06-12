---
title: "7zip--Worth the install?"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by sports fan Matt on 2008-02-26
I have seen items that have needed a zip archive to install them ex: some tar.gz files for themes..etc..

Is it worth the trouble of installing 7zip or do ya'll recomend another archive program?

---

### Post by BassKozz on 2008-02-26
I didn't think 7zip had a linux version available, I could be wrong thou?
You can however get the 7z package that will allow you to compress and decompress 7z file types, it is called [p7zip](https://wiki.ubuntu.com/7-zip)

As for software that manages these compression formats, Ubuntu comes with it's own archive manager ([File-Roller](http://packages.ubuntu.com/dapper/gnome/file-roller)), but I prefer [PeaZip](http://peazip.sourceforge.net/)

---

### Post by julian67 on 2008-02-26
7-zip is open source software and is available for Linux from the repositories. Peazip uses it (amongst other formats) and installing peazip should pull down 7-z as a dependency. 7-z is quite common in the Windows world so you should at least be able to unzip a 7-z archive. It's useful for making password protected encrypted archives very easily using the terminal, or with the Peazip gui.

---

### Post by BassKozz on 2008-02-26
> **julian67 said:**
> 7-zip is open source software and is available for Linux from the repositories. Peazip uses it (amongst other formats) and installing peazip should pull down 7-z as a dependency. 7-z is quite common in the Windows world so you should at least be able to unzip a 7-z archive. It's useful for making password protected encrypted archives very easily using the terminal, or with the Peazip gui.

This has always confused me thou...
7-zip is the actual archive manager (GUI Program) while 7z is the archive format, correct :confused:

---

### Post by misfitpierce on 2008-02-26
Its in the repos... hit add/remove programs and its at top

---

### Post by SNuxoll on 2008-02-26
not really worth the install when file-roller or whatever KDE uses does the job, just my 2 cents.

---

### Post by Bruce M. on 2008-02-26
> **julian67 said:**
> 7-zip is open source software and is available for Linux from the repositories.

Really?  I don't see it, and search shows nothing. What am I missing?
Sorry to bump in on the thread.

---

### Post by julian67 on 2008-02-26
it's in the Gutsy universe repo, where it's called p7zip

---

### Post by julian67 on 2008-02-26
> **SNuxoll said:**
> not really worth the install when file-roller or whatever KDE uses does the job, just my 2 cents.

it's mostly useful when needing to unpack or make a password protected encrypted 7-z archive. Fileroller can't do this for 7-z, don't know about the KDE tool (ark?).

---

### Post by stchman on 2008-02-26
You can install 7zip and rar plugins for Archive Manager

```
sudo apt-get -y install rar unrar p7zip p7zip-full
```

You will now be able to use Archive Manager to create and deflate .7z and .rar archives.

---

### Post by julian67 on 2008-02-26
> **stchman said:**
> You can install 7zip and rar plugins for Archive Manager

```
sudo apt-get -y install rar unrar p7zip p7zip-full
```

You will now be able to use Archive Manager to create and deflate .7z and .rar archives.

encrypted ones??? This something that file-roller and xarchiver can't handle with 7z. What is Archive Manager? KDE app?

---

### Post by stchman on 2008-02-26
> **julian67 said:**
> encrypted ones??? This something that file-roller and xarchiver can't handle with 7z. What is Archive Manager? KDE app?

I have never tried and encrypted archive in .7z or .rar so I cannot comment.

Archive Manager or as it is called File Roller is installed by default in Ubuntu.  The KDE version is called Ark.

---

### Post by Chris555 on 2008-02-26
Archive manager works with Nautilus, gives you the context menu to open an archive when you right click on an archive in Nautilus. Right click on the opened archive gives you menu where you can chose to extract that archive, amongst other options. Mine was part of standard Gutsy 7.10 install.

---

### Post by julian67 on 2008-02-26
> **stchman said:**
> I have never tried and encrypted archive in .7z or .rar so I cannot comment.

Archive Manager or as it is called File Roller is installed by default in Ubuntu.  The KDE version is called Ark.

Well if Archive manager = File Roller then it can't really use 7z fully, basically is only good for packing/unpacking unencrypted and unpassworded 7z archives. You'd  need the terminal (or peazip) to use all 7z's features.

---

### Post by bred on 2008-02-26
> **stchman said:**
> You can install 7zip and rar plugins for Archive Manager

```
sudo apt-get -y install rar unrar p7zip p7zip-full
```

You will now be able to use Archive Manager to create and deflate .7z and .rar archives.

Thx for the tip,
 works great with Archive Manager, no need to dwload and install 7zip for me :)

---

### Post by PinkFloyd102489 on 2008-02-26
7z has a higher compression ratio than bzip2, which is higher than gzip.


bzip2 has a 1:6 ratio, dunno exactly what 7z is.

---

### Post by divindavid on 2008-02-26
i reccomend winrar under wine it is great even for .7z files

---

### Post by AndyCooll on 2008-02-26
> **sox fan Matt said:**
> I have seen items that have needed a zip archive to install them ex: some tar.gz files for themes..etc..

Is it worth the trouble of installing 7zip or do ya'll recomend another archive program?

For basic unzipping, (as has already been mentioned) Archive Manager which is part of the default Ubuntu install will do the job. You can also install unrar as an extension if you need to unzip such files with the same app. In which case 7-zip is hardly worth installing (I've certainly never felt the need).

7-zip comes into its own if you have more advanced zip archive needs, and if that's you then go ahead.

:cool:

---

### Post by Bruce M. on 2008-02-27
> **julian67 said:**
> it's in the Gutsy universe repo, where it's called p7zip

Ah, OK, I thought I was missing something because I recall it was there (7zip) in Feisty.

---

### Post by Chame_Wizard on 2008-02-27
how the heck can i extract a rar file with password?:(

---

### Post by Giorgio tani on 2008-02-27
> **Chame_Wizard said:**
> how the heck can i extract a rar file with password?:(
p7zip can extract password protected RAR archives in Linux; it uses the same unrar code rewritten by Igor Pavlov for 7-Zip.
You can also use p7zip through PeaZip (it contains last stable p7zip binaries) to have a GUI, and you can save the command line composed through PeaZip's GUI if you would like to use it in console or scripts.

---

### Post by Chame_Wizard on 2008-03-04
great but how to use it ?

---

### Post by julian67 on 2008-03-04
> **Chame_Wizard said:**
> great but how to use it ?```
man 7z
```

or navigate to /usr/share/doc/p7zip-full/DOCS and read the manual there.

If you simply want to unpack a password protected 7z archive: ```
7z e yourarchive.7z
``` and it will prompt you for the password.

---

### Post by Chame_Wizard on 2008-03-05
and within Ark?

---

### Post by julian67 on 2008-03-05
> **Chame_Wizard said:**
> and within Ark?

don't know, don't use KDE. Try reading the manual ;-)

---

