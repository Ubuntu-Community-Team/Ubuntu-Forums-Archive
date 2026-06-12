---
title: "Phamerator"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by DutyDuty on 2008-02-24
I want to run a program named Phamerator. As far as I know, it is only available by this code: ```
 bzr branch http://bazaar.launchpad.net/~dabogsta/phamerator/phamerator
```

I did that code, it downloaded into a folder, and I don't know how to run the stupid thing. I have a very limited amount of time to get this working, so quick help would be much appreciated.

Related sites: 
[http://phage.cisat.jmu.edu/wiki/show/Start/]("http://phage.cisat.jmu.edu/wiki/show/Start/")
[http://hatfull12.bio.pitt.edu:8080/wiki/?title=Phamerator%20User%20Guide]("http://hatfull12.bio.pitt.edu:8080/wiki/?title=Phamerator%20User%20Guide")

---

### Post by seventhc on 2008-02-24
From the links provided, so far the documentation seems to be lacking quite a bit, for instance, they say it can be installed using *apt,* but when you click on that link it says
> The good news about apt is that if you are using [COLOR=Navy]create:VirtualBox[/COLOR] with the .vdi file that we provided, then your Linux system is already configured to use Apt.I don't really see anyplace I could even download it to see if i can figure out how to start it. :confused:

---

### Post by ByteJuggler on 2008-02-24
OK, I've pulled the code down with bazaar (as you've done.) Apparently, the system uses several python libraries which you must also install in order to run the system, as follows:

```
sudo apt-get install python-biopython python-pygoocanvas python-mysqldb pyro
```

(This by the way I figured out by reading the error messages when trying to start it (see below) and then using "apt-cache search" to find the relevant python library package to install to satisfy the missing dependency.)

Once you've done that, you can run the application by entering/running the programs, e.g:

Go into the folder...

```
cd phamerator
```

Then...

```
./phageManager.py
```

There are other runnable (marked as executable) python files which may be relevant/runnable, but it looks like you need a back end database to run against in many cases.  I presume you may know more about that than I do at this stage.

---

### Post by DutyDuty on 2008-02-24
I don't actually know what database or password to use, but thanks for your help.

---

### Post by ByteJuggler on 2008-02-24
OK, well I've not looked into this, but it may be that you need to install MySQL and configure a local database, which isn't actually that hard to do.  (It's not obvious how to set up this application to use a local server - I suppose there should be documentation for it... somewhere... :P )

---

### Post by DutyDuty on 2008-03-01
Could you run down the specifics of that process? I'm really, really running out of time.

---

