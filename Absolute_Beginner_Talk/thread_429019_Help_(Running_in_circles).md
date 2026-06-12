---
title: "Help (Running in circles)"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by Bearcharlemagne on 2007-04-30
Hello everyone

So here is the situation, I hope that I can word this all properly so it can be properly understood, but here goes:

I had recently done a reinstallation of windows, with the intent of installing ubuntu to it later. I have a 160 gig drive, so I split it, and allowed the ubuntu portion 30 gigs. I was running windows and everything was fine, then I decided to install ubuntu last night. So I did, but for some reason it decided to always boot into ubuntu rather than toggle me the option of what operating system I want. I'm unfamiliar with ubuntu, so I needed to get into windows, not only because I can use it, but because everything I own is geared towards it. After numerous reinstallations of both operating systems, I have decided that a disk formatting is what needs to happen to take care of this mess, the problem is that I have amassed a very decent sized music and video library that I do not want to redownload. 

I have an external hard-drive that I can hook up, but ubuntu won't allow me the priveledges to copy to it because it is NTFS, so I then tried installing "ntfs-3g", but that won't install because "C Compiler cannot create executables". So I did some research and found out that it was a problem associated with not having the build essentials. I typed in the command to get those and I get the message "Can't find a package whose name or description matched "build essential". I decided that I would download the build essentials, put them on my ipod, and transfer them to the computer for installation. I did that and tried to install them, I then got the error message "The Dpkh development files (dpkg-dev) must be installed to build this package". So I downloaded them, put them on my ipod, and tried to install them. I was optimistic, but then I got slammed with the ol' familiar "C Compiler cannot create executables" message.

So in order to fix that error message, I need to install the builld essentials, but the only way to do that is to install the Dpkg-dev package, but the only way to install that is to install the build essentials, etc....

Please help

Thanks, Ben

EDIT: By the way, I am running Feisty

---

### Post by taurus on 2007-04-30
What happens when you run these two commands from a terminal?

```
sudo aptitude update
sudo aptitude install build-essential
```
If you still get the same error message about not finding the build-essential package, post your /etc/apt/sources.list here then.

```
cat /etc/apt/sources.list
```

---

### Post by Clay_Banger on 2007-04-30
i think the command you are after for the build essential is:
```
sudo aptitude install build-essential
```a "-" between the words instead of a space

---

### Post by Seisen on 2007-04-30
Try putting it in the terminal like this

```
sudo apt-get install build-essentials
```

---

### Post by Bearcharlemagne on 2007-04-30
Thank you for the quick replies,

the "sudo apt-get install build-essentials" command only gives me the "Can't find a package whose name or description matched "build essential"" error. and the "sudo aptitude update" doesn't do anything because I am also having a hard time getting my wifi to work

---

### Post by taurus on 2007-04-30
First of, it's build-essential, NOT build-essentials.

And if you don't have a network connection, then you need to use the installer CD since it is on the CD.  Insert the CD into a drive, open a terminal (Applications -> Accessories -> Terminal), and run

```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
gcc -v
```

---

### Post by Bearcharlemagne on 2007-04-30
YAY! It worked.

Thanks a bunch Taurus, you are my hero

---

