---
title: "GnomeBaker"
date: 2006-06-10
forum: Absolute Beginner Talk
---

### Post by tartarian on 2006-06-10
Hey! I'm trying to compile GnomeBaker from source but I'm hitting a few problems:

When I run ./configure the terminal outputs the following error:

```

checking for GNOMEBAKER... configure: error: Package requirements (
        libgnomeui-2.0 >= 2.8.1
        gtk+-2.0 >= 2.4.0
        glib-2.0 >= 2.4.0
        libglade-2.0 >= 2.4.2
        gstreamer-0.8 >= 0.8.9
) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the GNOMEBAKER_CFLAGS and GNOMEBAKER_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.

```

I had a look in synaptic but all the packages listed above were installed.
I also ran sudo apt-get upgrade, sudo apt-get update and sudo apt-get install build-essential in the terminal but it still didnt work.

Any Ideas??

---

### Post by echo $USER on 2006-06-10
I just ran > sudo apt-get install gnomebaker, and it works for me.

---

### Post by tartarian on 2006-06-10
I did that also and the program installed no probs - but it didn't actually run - so  I'm trying to compile it from source to see whether that will work.

Any other ideas?

---

### Post by viciouslime on 2006-06-10
Do you have the -dev versions of these packages? They're the ones you want. Why is it you want to compile it anyway, why not just install its package?

---

### Post by tartarian on 2006-06-10
I'm not sure - how would I check if I do and how would I get them if I dont??

---

### Post by voitrix on 2006-06-10
Why don't you install K3b?

---

### Post by voitrix on 2006-06-10
[QUOTE=voitrix]Why don't you install K3b?[/QUOTE]
instaed of gnomebaker

---

### Post by tartarian on 2006-06-10
Because I'm running GNOME. 

When I try and install it through synaptic it says that I would have to uninstall Amarok before I could install k3b - which I dont want to do.

---

### Post by christopherdorrell on 2006-06-10
I installed k3b on my gnome desktop and it works.  I would suggest installing k3b via synaptic and see what happens.

---

### Post by tartarian on 2006-06-10
I tried to install the KDE desktop environment and it said i needed to uninstall Amarok.

When I try and install k3b from Synaptic it says:

```

k3b:
 Depends: k3blibs but it is not going to be installed
 Depends: kdelibs4c2 but it is not going to be installed
 Depends: libdbus-1-1 but it is not going to be installed
 Depends: libdbus-qt-1-1c2 but it is not going to be installed
 Depends: libmusicbrainz4c2 but it is not going to be installed
 Depends: kdebase-bin but it is not going to be installed
 Depends: kcontrol but it is not going to be installed

```

So I gave up. I'm not really bothered whether I use GnomeBaker or K3b - but neither of them seem to work!

---

### Post by voitrix on 2006-06-10
[QUOTE=tartarian]
When I try and install it through synaptic it says that I would have to uninstall Amarok before I could install k3b - which I dont want to do.[/QUOTE]

try installing k3b with apt-get, just type in a terminal 
       sudo apt-get install k3b
and good luck :)

---

### Post by tartarian on 2006-06-10
Output to that is:
```

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  k3b: Depends: k3blibs (>= 0.12.2) but it is not going to be installed
       Depends: kdelibs4c2 (>= 4:3.4.2) but it is not going to be installed
       Depends: libdbus-1-1 (>= 0.36.2) but it is not going to be installed
       Depends: libdbus-qt-1-1c2 (>= 0.36.2) but it is not going to be installed       Depends: libmusicbrainz4c2 (>= 2.1.1) but it is not going to be installed       Depends: kdebase-bin but it is not going to be installed
       Depends: kcontrol but it is not going to be installed
E: Broken packages

```

---

### Post by voitrix on 2006-06-10
Do you have Universe and Multiverse repositories added in synaptic package manager?

---

### Post by tartarian on 2006-06-10
I presume so - I have all the default ones. Can I check? How?! :p

---

### Post by voitrix on 2006-06-10
Go to System->Administration->Synaptic Package Manager after that on menu Settings->Repositories and click Add button, on Installation Media tab, and see if Community Maintained (Universe) and Non-free (Multiverse), options, are checked, if they aren't check them and then click Add.

---

### Post by tartarian on 2006-06-10
There are enteries on that list that have Non-Free (Multiverse) and Community Maintained (Universe) under them, but I dont actually have any enteries entitled that. 

???

---

### Post by voitrix on 2006-06-10
ok, then select all the enteries that have Universe and Multiverse under them.

---

### Post by echo $USER on 2006-06-10
This is the easiest way to add extra repo's.  > sudo cp /etc/apt/sources.list etc/apt/sources.list_backup> sudo gedit /etc/apt/sources.listDelete all the lines and replace with this:> ## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free

---

### Post by tartarian on 2006-06-10
OK, I seemingly have every repository checked but it still gives me that error - an ideas???

---

### Post by wickwire on 2006-06-10
"Seemingly" sugests that you eyed echo $USER's post instead of actually making a backup copy of your sources.list file and creating a new one, then doing sudo apt-get update or update synaptic.

After doing those steps, reinstall Gnomebaker and run it from the console - then post back the output error when it fails to run.

---

