---
title: "[SOLVED] get-apt update errors"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by cwrann on 2007-08-11
I get a few error messages when I try the sudo apt-get update and would like to know how to fix them. I have a gzip problem, as well as the occassional clvm is not configured problem wich leads to a red hat suite problem. for now I am concentrating on the gzip problem.

This comes up when I use apt-get-update in the terminal

Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/multiverse Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security/universe Translation-en_US
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security Release [50.9kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/multiverse Sources
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources [385kB]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages [69.3kB]
99% [6 Sources gzip 0]                                                           3840B/s 0s
gzip: stdin: not in gzip format
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources
  Sub-process gzip returned an error code (1)
99% [7 Packages gzip 0]                                                          3840B/s 0s
gzip: stdin: not in gzip format
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
  Sub-process gzip returned an error code (1)
Fetched 47.0kB in 18s (2592B/s)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-amd64/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by BobCFC on 2007-08-11
I found an old thread where someone else had the same error.

[http://ubuntuforums.org/showthread.php?t=9944](http://ubuntuforums.org/showthread.php?t=9944)


In it he said proxy content filtering was intercepting the bzip2 files and returning 404 

> "the simple fix was to switch to ftp:// URLs in the /etc/apt/sources.list file"

It seems to fix other people problems as well maybe you could try?

---

### Post by cwrann on 2007-08-11
thanks for the response but I am new to ubuntu and don't know how to start to switch to ftp:// URLs in the /etc/apt/sources.list file.

---

### Post by BobCFC on 2007-08-12
Well the sources list is a protected file so you have to open it using the root account .

The first thing I would do is make a backup copy so that you can restore it later if it goes wrong:

```
sudo cp /etc/apt/sources.list /etc/apt/myoldsources.list

```


Now you can open the file safely in you favourite editor such as:
```
gksudo gedit /etc/apt/sources.list
```



There will be lots of addresses in there such as **http**://us.archive.ubuntu.com..... the fix suggested in the other thread was to change the beginnings to **ftp**://us.archive.ubuntu.com 

If you click on the menu Seach->Replace you can enter **http:** in the Search for box and **ftp:** in the Replace with box.  Then click find and it will highlight all the http's in yellow.  Once you are satisfied with the changes it wants to make click Replace All.

Then save the file.

If you ever want to restore the backup you can just do the opposite to the first command to copy the old one back:

```
sudo cp /etc/apt/myoldsources.list /etc/apt/sources.list

```

---

### Post by cwrann on 2007-08-12
Thanks a lot for all the help. I'm new to ubuntu and when I read a lot of the instructions I feel like it is assumed that I should know the first step in the procedure, it feels like I am dropped in the middle of things. That last tip helps me clear up a whole bunch of problems. I'm running smoothly now.

---

### Post by BobCFC on 2007-08-12
Glad to hear that it worked.  Don't be afraid to ask for the basics that's what the beginner's section is for.

---

