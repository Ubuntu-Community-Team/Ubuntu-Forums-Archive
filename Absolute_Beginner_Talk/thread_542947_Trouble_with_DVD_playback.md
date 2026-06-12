---
title: "Trouble with DVD playback"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by MstrTal on 2007-09-04
Hello. 

First off I am completly and utterly new to Linux. Second I tried following the steps listed in the Multimedia thread in the sticky section. My problem is when I type sudo gedit ect/apt/sources.list all that happens is a blank text editor opens. What amI doing wrong? 

Here are the steps I have followed 

Applicatons>Assesories>Terminal

The command string listed on the preveously mentioned thread . enter

a blank box opens that is it.

I tried following the steps listed on another how to articule on teh web with the only diffrrence being it asks for my password. 

I am loged into a Root account when I try this. 

Any advice would really be helpful as my wife is getting irritated with not being able to watch DVDs on the laptop in the bed room. 

Thank you for your time.

---

### Post by Ptero-4 on 2007-09-04
use gksudo gedit /etc/apt/sources.list instead.

---

### Post by wolfen69 on 2007-09-04
try:
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by mysticmatrix on 2007-09-04
> **MstrTal said:**
> Hello. 
First off I am completly and utterly new to Linux. Second I tried following the steps listed in the Multimedia thread in the sticky section. My problem is when I type sudo gedit[COLOR="Red"] ect[/COLOR]/apt/sources.list all that happens is a blank text editor opens. What amI doing wrong? 


Spelling mistake. Correct one is:

```
gksudo gedit /etc/apt/sources.list
```

This time, try copy-pasting :)

---

### Post by MstrTal on 2007-09-04
Thank you for the help thus far. I added the gk to the begining of the string and was able to go threw the process. 

However. when I try to "sudo apt-get update" I recieve this error message at the bottumW: GPG error: http/medibuntu.sos-sts.com feisty Release: The following signatures couldn't be verified becouse the public key is not avialable: NO_PUBKEY 2EBC26B60C5A2783

it tells me to run apt-get update agian to fix the problem yet I have run the apt-get update 6 times now.

Any help would be greatly appreaciated. 

Also when I try to use the Totum Player or GXine it tells me unable to read NAV packaage. What is this and how should I start going about fixing it?

---

### Post by sbassett on 2007-09-04
This means you don't have the Key for medibuntu. This is no "error" in the packages, it does however, mean the signatures of the packages cannot be verified.

Try this to fix:

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

As for the NAV packages, 

```
 sudo apt-get install libdvdnav4 libdvdnav-dev
```

---

### Post by MstrTal on 2007-09-04
Thank you.

DVDs are working now =)

---

### Post by rgb on 2007-09-26
I seem to be having similar issues in playing a dvd. 

First the background: I am running ubuntu edgy on a T42 laptop with a cd-dvd rom drive. I used to be able to play dvds on it using xine/vlc. However, trying to do so today is giving me trouble. 

1. dvds used to automount for me (gnome). Today it did not. 

2. I reinstalled w3codecs and libdvdread using apt-get. 

3. I also made the same modifications to the /etc/modules file suggested here. 

4.ls -l /dev/dvd
lrwxrwxrwx 1 root root 3 Sep 25 23:43 /dev/dvd -> hdc

On trying to run xine I get
```

libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdread: Could not open /dev/dvd with libdvdcss.
libdvdread: Can't open /dev/dvd for reading
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdread: Could not open /dev/dvd with libdvdcss.
libdvdread: Can't open /dev/dvd for reading

```

My fstab contains 
```

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /mnt/dvd   udf,iso9660 auto,user     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

```
5. ls -l gives 
```

ls -l /dev |grep dvd
lrwxrwxrwx 1 root root           3 Sep 25 23:43 dvd -> hdc

```

I think the problem is beginning with mounting rather than playback. Can you help?

Best Regards and Thanks in advance.

---

