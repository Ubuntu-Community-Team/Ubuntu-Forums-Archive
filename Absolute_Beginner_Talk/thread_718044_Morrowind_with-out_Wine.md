---
title: "Morrowind with-out Wine?"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by Astura on 2008-03-07
Hi my system is incompatable to  wine which I hear is the best way to accomplish this, but

I'v got Morrowind iso mounted with Gmount, and Im looking inside the Iso at the .exe and what not... 

but how to run the .exe for linux?

---

### Post by AvengingAngel718 on 2008-03-07
i dont think morrowind works on wine anyway, and theres not much you can do with an exe on linux. your best bet would be dual booting, if its at all possible.

---

### Post by namegame on 2008-03-07
> **AvengingAngel718 said:**
> i dont think morrowind works on wine anyway, and theres not much you can do with an exe on linux. your best bet would be dual booting, if its at all possible.

I have successfully installed and played Morrowind, without tweaking, with Wine. So right now the best option seems to be to use Wine, but that doesn't seem to be an option for the OP. .exe files are Windows files. I wouldn't know how to run them in Linux without some emulator such as wine. You might want to give Cedega a try, it could work.

---

### Post by tekguy on 2008-03-07
You can not run an .exe in Linux without using something like wine, CrossOver, or Cedega.

Some alternatives:
[http://www.winehq.org/site/docs/wineusr-guide/alternatives](http://www.winehq.org/site/docs/wineusr-guide/alternatives)

What do you mean your machine is not compatible with Wine?

From Winehq:
What are the system requirements for Wine?

The rule of thumb is that if your application runs fine in Windows, it should run fine on the same system using Wine. Wine, along with the operating system you use to run it, generally requires less disk space and memory than Windows itself. If you're not currently running a Windows application, Wine won't consume any resources at all other than about 20 megabytes of disk space.

---

### Post by Daveth on 2008-03-07
why do you think your system is incompatible with wine???

---

### Post by Astura on 2008-03-07
Right off the Add/Remove Programs:

Wine Windows Emulator
This application is provided by the Ubuntu community.
Wine Windows Emulator cannot be installed on your computer type (amd64). Either the application requires special hardware features or the vendor decided to not support your computer type.

...I got no reason why though, my laptop is brand new.


I looked at Cedega and it would probaly do the trick, but I am not so sure about a fee.

Whats my next best bet?

---

### Post by JoshuaRL on 2008-03-07
Install directly from the Wine website.  I run that same version and have no problems.  Three steps:

1).  Get the Wine repo key:
```

wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -

```

2).  Add the Wine repo to your list of sources:
```

sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/winehq.list

```

3).  Install Wine:
```

sudo apt-get update
sudo apt-get install wine

```

Now, don't forget to go into Applications->Wine->Configure Wine.

That will allow you to finish the setup for what you are wanting to run.

---

### Post by Astura on 2008-03-07
following your steps josh i get to this

astral@Velio:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate
astral@Velio:~$

---

### Post by JoshuaRL on 2008-03-07
You did the apt-get update right?

If so, can you go to System->Administration->Synaptic Package Manager.  Then search for "wine"  And look for either version 0.9.56 or 0.9.57.

---

### Post by Astura on 2008-03-07
Yes I did the apt-get

I did not see the version you mention but I see libwine and libwine-dev

so I click and this shows

libwine:
 Depends: wine  but it is not installable

or

libwine-dev:
 Depends:wine but it is not installable

---

### Post by JoshuaRL on 2008-03-07
Okay, can you go into the Filters in Synaptic and see if there's anything in the Broken one?

---

### Post by Astura on 2008-03-07
I went through your commands again and got a different result, here:

astral@Velio:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: ia32-libs (>= 1.6) but it is not going to be installed
        Depends: lib32asound2 (> 1.0.14) but it is not going to be installed
        Depends: libc6-i386 (>= 2.6-1) but 2.5-0ubuntu14 is to be installed
E: Broken packages
astral@Velio:~$ 


Seems wine is blocked from install this way, too?

---

### Post by JoshuaRL on 2008-03-07
Okay, try this:
```

sudo apt-get -f install
sudo dpkg --configure -a

```

---

### Post by Astura on 2008-03-07
this happend:

astral@Velio:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libsamplerate0 liboggflac3
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
astral@Velio:~$ sudo dpkg --configure -a
astral@Velio:~$ 

then I went to synaptic and scrolled down and see 0.9.56 wine and wine-dev

and get this:

wine:
 Depends: ia32-libs but it is not going to be installed
 Depends: lib32asound2 but it is not going to be installed
  Depends: libc6-i386 (>=2.6-1) but 2.5-0ubuntu14 is to be installed

wine-dev:
 Depends: wine but it is not going to be installed

---

### Post by JoshuaRL on 2008-03-07
Alright, could you try:
```

sudo apt-get -f install ia32-libs lib32asound2 libc6-1386

```

---

### Post by Astura on 2008-03-07
astral@Velio:~$ sudo apt-get -f install ia32-libs lib32asound2 libc6-1386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libc6-1386
astral@Velio:~$ 


I wish I knew what more to say other than just feed back data, I apprechiate the specific help your giving me

---

### Post by JoshuaRL on 2008-03-07
No problem, we all start somewhere.

Try:
```

sudo apt-get install libc6

```

---

### Post by Astura on 2008-03-07
astral@Velio:~$ sudo apt-get install libc6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libc6 is already the newest version.
The following packages were automatically installed and are no longer required:
  libsamplerate0 liboggflac3
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
astral@Velio:~$

---

### Post by JoshuaRL on 2008-03-07
Alright, can you try installing Wine again?

---

### Post by happyhamster on 2008-03-07
Err, aren't you trying to use a gutsy repository on a feisty machine now?

---

### Post by JoshuaRL on 2008-03-07
> **happyhamster said:**
> Err, aren't you trying to use a gutsy repository on a feisty machine now?

Dude, you're right.  I forgot to check that.  Thanks.

Okay, here is the revised 3 Steps:

1).  Get the Wine repo key:
```

wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -

```

2).  Add the Wine repo to your list of sources:
```

sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list -O /etc/apt/sources.list.d/winehq.list

```

3).  Install Wine:
```

sudo apt-get update
sudo apt-get install wine

```

Now, don't forget to go into Applications->Wine->Configure Wine.

That will allow you to finish the setup for what you are wanting to run.

---

### Post by Astura on 2008-03-07
Okay I think it installed, on synaptic next to wine and wine-dev it says under installed version it shows:

0.9.56~winehq0~ubuntu~7.04-1

But it doesnt show up under applications tab?

even add/remove programs shows that it is installed on my system

---

### Post by JoshuaRL on 2008-03-07
Not really sure.  Could you try a restart?

---

### Post by Astura on 2008-03-07
back from restart, no wine :(

---

### Post by JoshuaRL on 2008-03-07
Alright, I'm not sure why it isn't in the Applications menu.  If you can tell me the path of the .exe you want I should be able to tell you the way to run Wine from the terminal.  Wine is easy to run from the Applications menu, but it also runs from the terminal.

---

### Post by Astura on 2008-03-08
Desktop -> Morrowind -> Setup.exe

---

### Post by Astura on 2008-03-08
WOOT

I figured out the terminal control for wine from another forum, thanks sooo much for your help man I know I'd never had gotten wine set up with out it!

---

