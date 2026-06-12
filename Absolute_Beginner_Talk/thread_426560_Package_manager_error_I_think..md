---
title: "Package manager error I think."
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by rosswmcgee on 2007-04-28
E: Malformed line 2 in source list /etc/apt/sources.list.d/edgy-multiverse.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.


How do I correct this problem?:)

---

### Post by 67GTA on 2007-04-28
Sounds like one of your source list lines is screwed up. What version of Ubuntu are you using? Did you edit the list recently? Post the contents of your /etc/apt/sources.list.

---

### Post by rosswmcgee on 2007-04-28
Edgy 6.10 I do not think I edited any thing but I am not sure. This is what I get when I use the command apt-get
I do not know how to get to the sources list.

rosswmcgee@rosswmcgee-desktop:~$ apt-get
apt 0.6.45ubuntu14 for linux i386 compiled on Sep 27 2006 23:43:26
Usage: apt-get [options] command
       apt-get [options] install|remove pkg1 [pkg2 ...]
       apt-get [options] source pkg1 [pkg2 ...]

apt-get is a simple command line interface for downloading and
installing packages. The most frequently used commands are update
and install.

Commands:
   update - Retrieve new lists of packages
   upgrade - Perform an upgrade
   install - Install new packages (pkg is libc6 not libc6.deb)
   remove - Remove packages
   source - Download source archives
   build-dep - Configure build-dependencies for source packages
   dist-upgrade - Distribution upgrade, see apt-get(8)
   dselect-upgrade - Follow dselect selections
   clean - Erase downloaded archive files
   autoclean - Erase old downloaded archive files
   check - Verify that there are no broken dependencies

Options:
  -h  This help text.
  -q  Loggable output - no progress indicator
  -qq No output except for errors
  -d  Download only - do NOT install or unpack archives
  -s  No-act. Perform ordering simulation
  -y  Assume Yes to all queries and do not prompt
  -f  Attempt to continue if the integrity check fails
  -m  Attempt to continue if archives are unlocatable
  -u  Show a list of upgraded packages as well
  -b  Build the source package after fetching it
  -V  Show verbose version numbers
  -c=? Read this configuration file
  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp
See the apt-get(8), sources.list(5) and apt.conf(5) manual
pages for more information and options.
                       This APT has Super Cow Powers.
rosswmcgee@rosswmcgee-desktop:~$

---

### Post by taurus on 2007-04-28
You need to edit /etc/apt/sources.list.d/edgy-multiverse.list (not /etc/apt/sources.list) 

```
gksudo gedit /etc/apt/sources.list.d/edgy-multiverse.list
```
and place a # in front of the second line.  Save it and run

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by 67GTA on 2007-04-28
Go to PLACES>COMPUTER>FILESYSTEM>ETC>APT>SOURCES.LIST then copy the whole file and paste it here. apt-get needs an argument... apt-get install or apt-get update, etc. The /etc/apt/sources.list is a list of repository links that the package manager uses to find and download the software you specify from dedicated servers with the apt-get command. If you want to install hokypoky then you would have to have a repository link in the /etc/apt/sources.list file that led to a server that kept hokypoky on it. Then you would type sudo apt-get install hokypoky.

---

### Post by 67GTA on 2007-04-28
Yeah, ignore me for now. I didn't catch the .d in there.

---

### Post by rosswmcgee on 2007-04-28
rosswmcgee@rosswmcgee-desktop:~$ gksudo gedit /etc/apt/sources.list.d/edgy-multiverse.list

(gedit:6067): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

then in new window this:

# automatically added by gnome-app-install on 2007-04-04 08:03:48.911381
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates

---

### Post by taurus on 2007-04-28
Make it to look like this.

```
# automatically added by gnome-app-install on 2007-04-04 08:03:48.911381
deb http://archive.ubuntu.com/ubuntu/ edgy multiverse
deb http://security.ubuntu.com/ubuntu edgy-security multiverse
deb http://archive.ubuntu.com/ubuntu/ edgy-updates multiverse
```

---

### Post by rosswmcgee on 2007-04-28
Ok I did that now what? And thank you.

---

### Post by taurus on 2007-04-28
Save the changes.  Then, from a terminal, run

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by rosswmcgee on 2007-04-28
rosswmcgee@rosswmcgee-desktop:~$ sudo aptitude update
E: Malformed line 2 in source list /etc/apt/sources.list.d/edgy-universe.list (dist parse)
E: Malformed line 2 in source list /etc/apt/sources.list.d/edgy-universe.list (dist parse)
E: The list of sources could not be read.
rosswmcgee@rosswmcgee-desktop:~$ sudo aptitude upgrade

---

### Post by taurus on 2007-04-28
Post your /etc/apt/sources.list.d/edgy-universe.list then.

```
cat /etc/apt/sources.list.d/edgy-universe.list
```
I bet you it's the same deal with the /etc/apt/sources.list.d/edgy-multiverse.list thing.

---

### Post by rosswmcgee on 2007-04-28
I hope this is what you want.


rosswmcgee@rosswmcgee-desktop:~$ cat /etc/apt/sources.list.d/edgy-universe.list
# automatically added by gnome-app-install on 2007-04-04 07:51:38.131343
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates
rosswmcgee@rosswmcgee-desktop:~$

---

### Post by taurus on 2007-04-28
Make it look like this now.

```
# automatically added by gnome-app-install on 2007-04-04 07:51:38.131343
deb http://archive.ubuntu.com/ubuntu/ edgy universe
deb http://security.ubuntu.com/ubuntu edgy-security universe
deb http://archive.ubuntu.com/ubuntu/ edgy-updates universe
```
Save the changes.  Then, run this command again from a terminal and post the output here.

```
sudo aptitude update
```

---

### Post by rosswmcgee on 2007-04-28
rosswmcgee@rosswmcgee-desktop:~$ sudo aptitude update
E: Malformed line 2 in source list /etc/apt/sources.list.d/edgy-universe.list (dist parse)
E: Malformed line 2 in source list /etc/apt/sources.list.d/edgy-universe.list (dist parse)
E: The list of sources could not be read.
rosswmcgee@rosswmcgee-desktop:~$

---

### Post by taurus on 2007-04-28
Can you post your /etc/apt/sources.list.d/edgy-universe.list again?

```
cat /etc/apt/sources.list.d/edgy-universe.list
```

---

### Post by rosswmcgee on 2007-04-28
rosswmcgee@rosswmcgee-desktop:~$ cat /etc/apt/sources.list.d/edgy-universe.list
# automatically added by gnome-app-install on 2007-04-04 07:51:38.131343
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates
rosswmcgee@rosswmcgee-desktop:~$

---

### Post by taurus on 2007-04-28
Well, you never modified it like in my Post #14!

```
gksudo gedit /etc/apt/sources.list.d/edgy-universe.list
```
and make it look like this now.

```
# automatically added by gnome-app-install on 2007-04-04 07:51:38.131343
deb http://archive.ubuntu.com/ubuntu/ edgy universe
deb http://security.ubuntu.com/ubuntu edgy-security universe
deb http://archive.ubuntu.com/ubuntu/ edgy-updates universe
```
Save it and run

```
sudo aptitude update
```

---

### Post by rosswmcgee on 2007-04-28
rosswmcgee@rosswmcgee-desktop:~$ sudo aptitude update
Password:
E: Malformed line 2 in source list /etc/apt/sources.list.d/edgy-multiverse.list (dist parse)
E: Malformed line 2 in source list /etc/apt/sources.list.d/edgy-multiverse.list (dist parse)
E: The list of sources could not be read.
rosswmcgee@rosswmcgee-desktop:~$ 


when I get to the window I make it look like you show it to be exactly, then save the file, then close the file the run the sudo aptitude update and get what is shown above. Perhaps I am doing some thing wrong?

---

### Post by taurus on 2007-04-28
Can you post /etc/apt/sources.list.d/edgy-multiverse.list again?

```
cat /etc/apt/sources.list.d/edgy-multiverse.list
```

---

### Post by rosswmcgee on 2007-04-28
rosswmcgee@rosswmcgee-desktop:~$ cat /etc/apt/sources.list.d/edgy-multiverse.list
# automatically added by gnome-app-install on 2007-04-04 07:51:38.131343
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates

---

### Post by taurus on 2007-04-28
> **rosswmcgee said:**
> rosswmcgee@rosswmcgee-desktop:~$ cat /etc/apt/sources.list.d/edgy-multiverse.list
# automatically added by gnome-app-install on 2007-04-04 07:51:38.131343
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates

Hmm...  Instead of modifying it like in Post #14, you went and removed multiverse from the third line!  Well, you have two options.

Edit /etc/apt/sources.list.d/edgy-multiverse.list

```
gksudo gedit /etc/apt/sources.list.d/edgy-multiverse.list
```

1. and make it look like this.
```
# automatically added by gnome-app-install on 2007-04-04 07:51:38.131343
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates
```

or

2.  make it look like this.
```
# automatically added by gnome-app-install on 2007-04-04 07:51:38.131343
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates multiverse
```

Whichever option you pick, save the changes and run this command again.

```
sudo aptitude update
```

---

### Post by rosswmcgee on 2007-04-28
Thank you for your patience. It worked in option # 1. I have no idea how I fouled up before. Now I will see if this is the reason why I could not update to 7.04. Probably not I keep getting failed to fetch error 2, we shall see and thanks a gain. Viva Ubuntu!

---

### Post by rosswmcgee on 2007-04-28
Failed to fetch [http://archive.canonical.com/ubuntu/dists/edgy-commercial/main/binary-i386/Packages.bz2](http://archive.canonical.com/ubuntu/dists/edgy-commercial/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://archive.canonical.com/ubuntu/dists/edgy-commercial/main/binary-i386/Packages.bz2](http://archive.canonical.com/ubuntu/dists/edgy-commercial/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
 No  it did not update so if you have the fix for this it would be great. And thanks again. Edgy is working just fine now.

---

### Post by taurus on 2007-04-28
You probably need to comment out that repo by placing a # in front of it in /etc/apt/sources.list.

```
gksudo gedit /etc/apt/sources.list
```
Then, run

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by rosswmcgee on 2007-04-28
You are right again and made my day. The thing is there have at least a 100 or so others with the 
problem. I wish they all knew this.

---

### Post by maa on 2007-05-06
i wany to update my ubuntu and it shows this

W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5



some budy help me!!!!!!!!!!!!!!!

---

### Post by jiminycricket on 2007-05-06
That means that the packages can't be verified as trusted, but they should still install.  The wine repository might have its own key, I don't know.

If you wait a while to reload, the Ubuntu repository key should be fine as well.

---

