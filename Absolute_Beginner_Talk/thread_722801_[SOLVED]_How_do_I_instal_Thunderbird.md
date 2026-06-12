---
title: "[SOLVED] How do I instal Thunderbird?"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by Billy d on 2008-03-12
I'm new to Linux, how do I instal Thunderbird?
I have downloaded thunderbird 2.0.0.9.tar.gz but it's not like windoze (!) and there doesn't seem to be any instal proceedure when I unzip it to a subdirectory in Ubuntu.
TIA
Bill

---

### Post by dedmonds on 2008-03-12
I believe Thunderbird is in the Ubuntu repositories. You can install the 'thunderbird' package using the Synaptic Package Manager or at the terminal with the following:

```

sudo apt-get install thunderbird

```

---

### Post by dedmonds on 2008-03-12
FYI - The one in the Ubuntu repositories (2.0.0.12) also appears to be a newer version than the one you downloaded.

---

### Post by ODF on 2008-03-12
If you're not familiar with the terminal you can also go through Synaptic package manager by system / administration

It's the GUI version of apt-get

* GUI = graphical user interface

---

### Post by Billy d on 2008-03-12
Thanks for the replies but the pc I want to instal on is offline so I believe I cannot use these repositories things you refer to because they are on the web.
The pc has the thunderbird .tar.gz file sitting on the Ubuntu desktop - but I can't even seem to get it unzipped, I keep getting errors.
There's plenty of room on the harddrive, I even created a subdirectory for it. When I try to unzip it I get a ton of "Cannot utime: ...." errors.
I know how to instal apps in windoze but this Linux is a really strange beast. :-)

---

### Post by ODF on 2008-03-12
> **Billy d said:**
> Thanks for the replies but the pc I want to instal on is offline so I believe I cannot use these repositories things you refer to because they are on the web.
The pc has the thunderbird .tar.gz file sitting on the Ubuntu desktop - but I can't even seem to get it unzipped, I keep getting errors.
There's plenty of room on the harddrive, I even created a subdirectory for it. When I try to unzip it I get a ton of "Cannot utime: ...." errors.
I know how to instal apps in windoze but this Linux is a really strange beast. :-)

Look if CD ROM is checked in your source. You can find your source list at the buttom of your add/remove window.

Dont forget to put your cd in :)

Its always better to use repo to install =)

---

### Post by jcwmoore on 2008-03-12
mozilla products are different than most, as far as installing.  extract the file you downloaded and in the new folder you will see many files.  there should be a file called thunderbird, just double click on that and it should run (select on run in terminal if "Run" doesn't work for you).  Basically mozilla products that you download don't "install" but they come pre-built and ready to run.

---

### Post by Billy d on 2008-03-12
OK, well I tried unzipping to a subdirectory (getting some errors), then I double clicked thunderbird and got a pop-up that let me "run" "run in terminal" "cancel".
Tried both run and run in terminal but nothing happened.

---

### Post by jcwmoore on 2008-03-12
what errors are you getting (when you extract) exactly?

---

### Post by Irihapeti on 2008-03-13
Instructions for installing the official Mozilla version of Thunderbird are available here (about half way down the page):

[https://help.ubuntu.com/community/ThunderbirdNewVersion?highlight=%28CategoryDocumentation%29](https://help.ubuntu.com/community/ThunderbirdNewVersion?highlight=%28CategoryDocumentation%29)

---

### Post by jken146 on 2008-03-13
Visit [http://packages.ubuntu.com/gutsy/thunderbird](http://packages.ubuntu.com/gutsy/thunderbird) and download the package.  It's the exact same one that's in the repositories.  You can then transfer it to your PC and double click on it to install.

---

### Post by Billy d on 2008-03-14
Lovely, thankyou jken146.
Got that installed just fine.
Things are so much harder to do in Linux, bit like back in the old DOS 2.1 days when alls I had was a floppy drive. Couldn't afford the 10 Meg hard drive!

---

