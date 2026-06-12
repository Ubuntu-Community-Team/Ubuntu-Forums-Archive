---
title: "apt-get update/upgrade problems"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by DrinkYourOvaltine on 2007-04-23
Hello.
I am getting this error msg when trying to upgrade:

```
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 143494 files and directories currently installed.)
Preparing to replace k3d 0.5.12.0-1ubuntu2 (using .../k3d_0.6.6.0.ds1-1_i386.deb) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1394, in <module>
    main()
  File "/usr/bin/pycentral", line 1388, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 955, in run
    pkg.read_version_info()
  File "/usr/bin/pycentral", line 542, in read_version_info
    raise PyCentralError, "package has no field Python-Version"
__main__.PyCentralError: package has no field Python-Version
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f]

update-python-modules: error: /usr/share/python-support/k3d.dirs does not exist
dpkg: error processing /var/cache/apt/archives/k3d_0.6.6.0.ds1-1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 2
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1394, in <module>
    main()
  File "/usr/bin/pycentral", line 1388, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 879, in run
    pkg.read_version_info()
  File "/usr/bin/pycentral", line 542, in read_version_info
    raise PyCentralError, "package has no field Python-Version"
__main__.PyCentralError: package has no field Python-Version
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Preparing to replace gzip 1.3.5-14ubuntu1 (using .../archives/gzip_1.3.9-2_i386.deb) ...
Unpacking replacement gzip ...
Errors were encountered while processing:
 /var/cache/apt/archives/k3d_0.6.6.0.ds1-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


I hesitate to say what is causing the problem but thinking that it had something to do with k3d, I attempted to remove it and got a whole slew of new and more annoying error msgs.

Thanks in advance.

---

### Post by jfinkels on 2007-04-23
What happens when you try to remove k3d, like this:
```

sudo aptitude remove k3d

```

---

### Post by DrinkYourOvaltine on 2007-04-23
I get:

```
The following packages will be REMOVED:
  k3d
0 upgraded, 0 newly installed, 1 to remove and 773 not upgraded.
3 not fully installed or removed.
Need to get 0B of archives.
After unpacking 44.5MB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: error processing k3d (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 k3d
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I have also tried -f and --force, all unsuccessful.

---

### Post by jfinkels on 2007-04-23
> **DrinkYourOvaltine said:**
> I get:

```
The following packages will be REMOVED:
  k3d
0 upgraded, 0 newly installed, 1 to remove and 773 not upgraded.
3 not fully installed or removed.
Need to get 0B of archives.
After unpacking 44.5MB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: error processing k3d (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 k3d
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I have also tried -f and --force, all unsuccessful.

well then, do what dpkg says, try to reinstall it:
```

sudo aptitude reinstall k3d

```
Does that work?

---

### Post by DrinkYourOvaltine on 2007-04-23
Yes, tried and failed:

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be upgraded:
  k3d
1 upgraded, 0 newly installed, 0 to remove and 773 not upgraded.
3 not fully installed or removed.
Need to get 0B/10.9MB of archives.
After unpacking 840kB of additional disk space will be used.
(Reading database ... 143651 files and directories currently installed.)
Preparing to replace k3d 0.5.12.0-1ubuntu2 (using .../k3d_0.6.6.0.ds1-1_i386.deb) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1394, in <module>
    main()
  File "/usr/bin/pycentral", line 1388, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 955, in run
    pkg.read_version_info()
  File "/usr/bin/pycentral", line 542, in read_version_info
    raise PyCentralError, "package has no field Python-Version"
__main__.PyCentralError: package has no field Python-Version
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f]

update-python-modules: error: /usr/share/python-support/k3d.dirs does not exist
dpkg: error processing /var/cache/apt/archives/k3d_0.6.6.0.ds1-1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 2
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1394, in <module>
    main()
  File "/usr/bin/pycentral", line 1388, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 879, in run
    pkg.read_version_info()
  File "/usr/bin/pycentral", line 542, in read_version_info
    raise PyCentralError, "package has no field Python-Version"
__main__.PyCentralError: package has no field Python-Version
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/k3d_0.6.6.0.ds1-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by jfinkels on 2007-04-23
Sad :P

Umm try to install it from the cached package maybe? I'm no expert in this area, just throwin out ideas :)
```

sudo dpkg -i /var/cache/apt/archives/k3d_0.6.6.0.ds1-1_i386.deb

```

---

### Post by tcrroadie on 2007-04-23
Try just pining k3d so apt will just ignore it when upgrading.
```

sudo aptitude hold k3d 0.5.12.0-1ubuntu2
```

The try upgrading

```
sudo aptitude update
```

```
sudo aptitude upgrade
```

---

### Post by DrinkYourOvaltine on 2007-04-23
Nope, no luck. 

Funny, I don't even want this damn program anymore - just want my updates to run smoothly. Thanks for the advice - any ideas are better than mine as I am out of them.

---

### Post by DrinkYourOvaltine on 2007-04-23
For clarity -

```
sudo dpkg --remove k3d
``` returns:

```
dpkg: error processing k3d (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 k3d
```

```
sudo dpkg -i /var/cache/apt/archives/k3d_0.6.6.0.ds1-1_i386.deb
``` returns:

```
sudo dpkg -i /var/cache/apt/archives/k3d_0.6.6.0.ds1-1_i386.deb
(Reading database ... 143651 files and directories currently installed.)
Preparing to replace k3d 0.5.12.0-1ubuntu2 (using .../k3d_0.6.6.0.ds1-1_i386.deb) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1394, in <module>
    main()
  File "/usr/bin/pycentral", line 1388, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 955, in run
    pkg.read_version_info()
  File "/usr/bin/pycentral", line 542, in read_version_info
    raise PyCentralError, "package has no field Python-Version"
__main__.PyCentralError: package has no field Python-Version
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f]

update-python-modules: error: /usr/share/python-support/k3d.dirs does not exist
dpkg: error processing /var/cache/apt/archives/k3d_0.6.6.0.ds1-1_i386.deb (--install):
 subprocess new pre-removal script returned error exit status 2
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1394, in <module>
    main()
  File "/usr/bin/pycentral", line 1388, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 879, in run
    pkg.read_version_info()
  File "/usr/bin/pycentral", line 542, in read_version_info
    raise PyCentralError, "package has no field Python-Version"
__main__.PyCentralError: package has no field Python-Version
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/k3d_0.6.6.0.ds1-1_i386.deb
```

---

### Post by tcrroadie on 2007-04-23
Try pinning k3d
```

sudo aptitude hold k3d 
```
```

sudo aptitude upgrade
```

---

### Post by eyelessfade on 2007-04-23
sometimes the magic "sudo apt-get -f install" works. Note that its nothing after install

---

### Post by DrinkYourOvaltine on 2007-04-23
Well, its an error I haven't seen yet. It's a *kind* of progress, right? 

```
Writing extended state information... Error!
E: I wasn't able to locate file for the k3d package. This might mean you need to manually fix this package.
E: Couldn't lock list directory..are you root?

```

---

### Post by dannyboy79 on 2007-04-23
do you have synaptic open while your using aptitude from the terminal? you can't do that. also, you have 773 upgrades to do before you should be installing any software!! that way Ubuntu has all what it needs updated and then you shouldn't have anymore problems. didn't you see that you had 773 upgrades? whenever you install any os, you should always do an online update and upgrade before anything.

---

### Post by DrinkYourOvaltine on 2007-04-23
Nope, -f  has not worked for this. It seems the first thing the updater looks for is this cripple package that may or may not be on my computer somewhere. 

*shakes fist*

---

### Post by DrinkYourOvaltine on 2007-04-23
Those 774 updates won't go through until I can... you know, update. 

No, I do not have synaptic or aptitude running.

---

### Post by tcrroadie on 2007-04-23
Have you tried holding k3d?
```

sudo aptitude hold k3d
```

Then upgrading
```

sudo aptitude upgrade
```

---

### Post by DrinkYourOvaltine on 2007-04-23
hold produces a similar error:

```
....(long list of packages)....Writing extended state information... Error!
E: I wasn't able to locate file for the k3d package. This might mean you need to manually fix this package.
E: Couldn't lock list directory..are you root?

```

---yes, I am root.

---

### Post by DrinkYourOvaltine on 2007-04-23
Ohhhh -[ [COLOR="Red"]I found a bug report.[/COLOR] ]("https://bugs.launchpad.net/ubuntu/+source/k3d/+bug/64848")

*reading*

---

### Post by DrinkYourOvaltine on 2007-04-23
Bug report seems to indicate that this issue has been fixed.  I did the following:

```
sudo mv /usr/bin/pycentral /tmp
```

and then tried to install with:   sudo apt-get install k3b   :and got this:

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be upgraded:
  k3d
1 upgraded, 0 newly installed, 0 to remove and 765 not upgraded.
1 not fully installed or removed.
Need to get 0B/10.9MB of archives.
After unpacking 840kB of additional disk space will be used.
Selecting previously deselected package k3d.
(Reading database ... 143651 files and directories currently installed.)
Preparing to replace k3d 0.5.12.0-1ubuntu2 (using .../k3d_0.6.6.0.ds1-1_i386.deb) ...
Unpacking replacement k3d ...
Setting up k3d (0.6.6.0.ds1-1) ...
WARNING: compile error while trying to byte-compile /usr/share/k3d/tutorials/gts_boolean.py: Sorry: TypeError: ('compile() expected string without null bytes',)
```

--- Please remember, I don't care if this program needs removed or installed (right now it seems like it needs to be reinstalled) - in the end, I just want to be able to update/upgrade.

And thanks again for the feedback and suggestions.

---

### Post by dannyboy79 on 2007-04-23
when you say you tried the -f option, you tried it with what? also, are you logged in as root or are you using sudo?

---

### Post by DrinkYourOvaltine on 2007-04-23
I tried the -f option when doing standard update/upgrade, after my non -f'ed updates/upgrades didn't work. Also while trying to get k3d on or off my computer.

Typically like this:

```
sudo apt-get -f install k3d

-or-

sudo apt-get -f remove k3d
```

Likewise for the Update/Upgrade.

I am doing all of this in a shell session (konsole) and I usually use apt-get. I have also, when suggested here, tried aptitude in place of apt-get.

---

### Post by dannyboy79 on 2007-04-24
this solution looks the most promising: 

[https://bugs.launchpad.net/ubuntu/+source/python-central/+bug/93518](https://bugs.launchpad.net/ubuntu/+source/python-central/+bug/93518)


**OR/AND**


try this, open the pycentral file within /usr/bin/ and comment out the last 2 lines.

I found the fix here 
[http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg327034.html](http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg327034.html)

and it states, ""Fixed" by commenting out last two lines of pycentral"

**OR/AND**

And then this also possibly here [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/64604](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/64604)
it's posted by BaRzO

i hade the same problem and i have checked the error the error was on this file /var/lib/dpkg/available on line 13477 there was a Y whit 2dot top it i have changed the line like this

before was line
Depends: xutils ( Y= 4.0.2), defoma, debconf | debconf-2.0
i have change it like this
Depends: xutils (>= 4.0.2), defoma, debconf | debconf-2.0

and upgrade fixed i thing i am not profesional at linux
i dont know is it right what i did...

---

### Post by DrinkYourOvaltine on 2007-04-24
Awesome, it's working now. 

I think that this is what did it:

```
sudo mv /usr/bin/pycentral /tmp

sudo apt-get -f update

sudo apt-get -f upgrade
```

I did this after booting to a command line so that there was no chance of any other package managers running. And that damn pycentral can just hang out in /tmp as punishment for all I care.

Thanks dannyboy and others for the quick replies and help.

---

### Post by dannyboy79 on 2007-04-25
I am so happy to have helped. I enjoy helping others.

---

