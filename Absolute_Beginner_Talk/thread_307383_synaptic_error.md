---
title: "synaptic error"
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by Carolyn62 on 2006-11-26
Hi again,


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

when I run dpkg --configure -a

I get this:

Setting up flashplugin-nonfree (7.0.68~ubuntu2~dapper1) ...
Downloading... +

and that's it, everything freezes (that is as far as it goes). I did attempt to download the flash plugin yesterday and of course it froze at the last line in synaptic.

I have spent over 38 hours hours trying to fix the package managers and an almost printer and have gotten nowhere. I have tried here but no one seems to have the answers that I need and I am too new at this to figure it out myself, I have read books and gone to web sites that others here have sent me and either it does not work or it's just too deep for me at this time, I am just plain tired. Between this and an almost printer I think that maybe I should uninstall Ubuntu and just give up any hope of getting away from windows. It certainly won't be for a lack of trying.

Carolyn

---

### Post by taurus on 2006-11-26
Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
```

---

### Post by Carolyn62 on 2006-11-26
ok, I put this in:
[COLOR="Red"]blank@tux:~$ sudo dpkg --configure -a[/COLOR]

and got this--and that's where it has been for the last 7 minutes](*,) 
blank@tux:~$ sudo dpkg --configure -a
Password:
[COLOR="Red"]Setting up flashplugin-nonfree (7.0.68~ubuntu2~dapper1) ...
Downloading...[/COLOR]

---

### Post by taurus on 2006-11-26
```
sudo aptitude remove flashplugin-nonfree --force
```
p.s.  If you want to install flash, use automatix2...

[http://www.getautomatix.com](http://www.getautomatix.com)

---

### Post by Carolyn62 on 2006-11-26
and I got:

blank@tux:~$ sudo aptitude remove flashplugin-nonfree --force
Password:
aptitude: unrecognized option `--force'
aptitude 0.4.0
Usage: aptitude [-S fname] [-u|-i]
       aptitude [options] <action> ...
  Actions (if none is specified, aptitude will enter interactive mode):

 install      - Install/upgrade packages
 remove       - Remove packages
 purge        - Remove packages and their configuration files
 hold         - Place packages on hold
 unhold       - Cancel a hold command for a package
 markauto     - Mark packages as having been automatically installed
 unmarkauto   - Mark packages as having been manually installed
 forbid-version - Forbid aptitude from upgrading to a specific package version.
 update       - Download lists of new/upgradable packages
 upgrade      - Perform a safe upgrade
 dist-upgrade - Perform an upgrade, possibly installing and removing packages
 forget-new   - Forget what packages are "new"
 search       - Search for a package by name and/or expression
 show         - Display detailed information about a package
 clean        - Erase downloaded package files
 autoclean    - Erase old downloaded package files
 changelog    - View a package's changelog
 download     - Download the .deb file for a package
 reinstall    - Download and (possibly) reinstall a currently installed package

  Options:
 -h             This help text
 -s             Simulate actions, but do not actually perform them.
 -d             Only download packages, do not install or remove anything.
 -P             Always prompt for confirmation or actions
 -y             Assume that the answer to simple yes/no questions is 'yes'
 -F format      Specify a format for displaying search results; see the manual
 -O order       Specify how search results should be sorted; see the manual
 -w width       Specify the display width for formatting search results
 -f             Aggressively try to fix broken packages.
 -V             Show which versions of packages are to be installed.
 -D             Show the dependencies of automatically changed packages.
 -Z                 Show the change in installed size of each package.
 -v             Display extra information. (may be supplied multiple times)
 -t [release]   Set the release from which packages should be installed
 -q             In command-line mode, suppress the incremental progress indicators.
 -o key=val     Directly set the configuration option named 'key'
 --with(out)-recommends Specify whether or not to treat recommends as
                strong dependencies
 -S fname: Read the aptitude extended status info from fname.
 -u      : Download new package lists on startup.
 -i      : Perform an install run on startup.

                  This aptitude does not have Super Cow Powers.
blank@tux:~$

---

### Post by LLRNR on 2006-11-26
What does ```
sudo aptitude purge flashplugin-nonfree
```give you?

LLRNR

---

### Post by Carolyn62 on 2006-11-26
It gives me:

blank@tux:~$ sudo aptitude purge flashplugin-nonfree
Password:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
blank@tux:~$

---

### Post by LLRNR on 2006-11-26
Ok, and after
```
sudo dpkg --configure -a
```...? Then try purge again, it's most likely that it's a broken package.

Another thing to do would be to go in Synaptic and see in the lower bar ("status" bar), where it tells you how many packages you have installed etc., to check and see if there's something like "1 package(s) broken". If so, there is an option in the menu regarding fixing broken packages (I can't quite remember though, I'm running Kubuntu).

Try and see if these things work.

LLRNR

---

### Post by Carolyn62 on 2006-11-26
[COLOR="Red"]Tried this and get this:[/COLOR]

blank@tux:~$ sudo aptitude purge flashplugin-nonfree
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
blank@tux:~$


[COLOR="Red"]loaded synaptic and got this:[/COLOR]

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

on the bottom of the screen it says:

0 packages listed, 0 installed, 0 broken, 0 to install/upgrade, 0 to remove.

Yesterday there was a bazillon of them.

---

### Post by LLRNR on 2006-11-26
> **Carolyn62 said:**
> [COLOR="Red"]Tried this and get this:[/COLOR]

blank@tux:~$ sudo aptitude purge flashplugin-nonfree
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
blank@tux:~$

Ok,... I was wondering what's happening when you ACTUALLY DO what it tells you, like "manually run 'dpkg --configure -a'"... But never mind that, because...


> **Carolyn62 said:**
> [COLOR="Red"]loaded synaptic and got this:[/COLOR]

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

on the bottom of the screen it says:

0 packages listed, 0 installed, 0 broken, 0 to install/upgrade, 0 to remove.

Yesterday there was a bazillon of them.

:shock: Yeah, I bet there was a whole bunch... 0 packages listed ?? 0 installed ???? :shock: This doesn't look good. Post in the output of ```
cat /etc/apt/sources.list
```

---

### Post by Carolyn62 on 2006-11-26
blank@tux:~$ cat /etc/apt/sources.list
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper multiverse universe main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security multiverse universe main restricted
blank@tux:~$

---

### Post by LLRNR on 2006-11-26
I don't know, at first glance it looks ok... But let's see what happens if:

1. you make a copy of your existing sources.list:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
```

2. open the sources.list file:
```
sudo nano /etc/apt/sources.list
```
And delete EVERYTHING from there !

3. paste in this: (just highlight, right-click -> copy and in the terminal press the middle mouse button... AFTER you deleted everything that you see there - step no.2 - ok?)
```
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu dapper universe
deb-src http://archive.ubuntu.com/ubuntu dapper universe

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://archive.ubuntu.com/ubuntu dapper multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper multiverse

deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu dapper-commercial main

deb http://packages.freecontrib.org/plf/ dapper free non-free
deb-src http://packages.freecontrib.org/plf/ dapper free non-free 
```

Then save the file by hitting Ctrl+O -> Enter -> close the file by pressing Ctrl+X

4. ```
sudo aptitude update
```

Good luck

LLRNR

---

### Post by Carolyn62 on 2006-11-26
blank@tux:~$ sudo nano /etc/apt/sources.list
blank@tux:~$ sudo aptitude update
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [191B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release [30.9kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources [255kB]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources [1478B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources [975kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources [46.6kB]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages [128kB]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages [14B]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources [47.7kB]
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources [14B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
[COLOR="Red"]Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release.gpg
  Could not connect to packages.freecontrib.org:80 (1.0.0.0), connection timed out
Err [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg
  Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out
Fetched 1486kB in 2m4s (11.9kB/s)
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: Couldn't rebuild package cache[/COLOR]
blank@tux:~$
blank@tux:~$

This thing seems to have a one track mind with this dpkg thing

Wait, I don't know if this has anything to do with it but I turned off IPv6 support because I had a very slow connection after I installed Ubuntu.

I was told to go here ([https://help.ubuntu.com/community/We...ngSlowIPv6IPv4](https://help.ubuntu.com/community/We...ngSlowIPv6IPv4)) and I followed directions and it fixed it right up. Is it possible that there are 2 problems? the first with Ipv6 to Ipv4 and the flash software that would (does not) download?

Carolyn

---

### Post by LLRNR on 2006-11-26
Yes, it wants you to run that "dpkg --configure -a" thing - just... try to please him, who knows ? :) 

Anyway, I never had to go through that IPv6 to IPv4 thing, really, since I don't have problems with the connectivity, but since you did this recently and now you can't install and can't get your updates, it seems that the problem is somehow connected to this.

I don't know if there's a workaround, but maybe someone here has an idea. It would be dull to rollback what you did in order to disable the IPv6, as I see it, right?

The sources.list I gave you are taken from Aysiu's [tutorial](http://www.psychocats.net/ubuntu/sources), in case you were wondering. They're the same that I use, too (with some minor add-ons).

So... I don't know about that IPv6 thing but at any case you could try to run, as it asks you to:
```
sudo dpkg --configure -a
sudo aptitude update
```
again, to see what happens.

LLRNR

---

### Post by Carolyn62 on 2006-11-26
This is as far as it goes:

blank@tux:~$ sudo dpkg --configure -a
Password:
Setting up flashplugin-nonfree (7.0.68~ubuntu2~dapper1) ...
Downloading...

for the last 15 minutes or so.
(edit) After I sent this I went back to take a look and it now shows:

Downloading... +

I do not know what the + means.

---

### Post by Carolyn62 on 2006-11-26
I just tried to download Automatix2 thinking that I could download flash with that to get rid of the error and this is what I get:


blank@tux:~$ gpg --import key.gpg.asc
gpg: directory `/home/swrcar/.gnupg' created
gpg: new configuration file `/home/swrcar/.gnupg/gpg.conf' created
gpg: WARNING: options in `/home/swrcar/.gnupg/gpg.conf' are not yet active during this run
gpg: keyring `/home/swrcar/.gnupg/secring.gpg' created
gpg: keyring `/home/swrcar/.gnupg/pubring.gpg' created
gpg: /home/swrcar/.gnupg/trustdb.gpg: trustdb created
gpg: key 521A9C7C: public key "Justin Hayes (Automatix Repository Master) <wildtangent@w1ldt4ng3nt.net>" imported
gpg: Total number processed: 1
gpg:               imported: 1
blank@tux:~$ gpg --export --armor 521A9C7C | sudo apt-key add -
OK
blank@tux:~$ sudo apt-get update
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release.gpg [189B]
Get:2 [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release.gpg [189B]
Get:3 [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release [4147B]
Get:4 [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release [5161B]
Get:5 [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages [572B]
Get:6 [http://www.getautomatix.com](http://www.getautomatix.com) dapper/main Packages [435B]
Ign [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Ign [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Ign [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Err [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
  404 Not Found
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
[COLOR="Red"]Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
  404 Not Found
Err [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
  404 Not Found[/COLOR]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
[COLOR="Red"]Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
  404 Not Found[/COLOR]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
[COLOR="Red"]Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
  404 Not Found
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
  404 Not Found
99% [Connecting to packages.freecontrib.org (1.0.0.0)] [Connecting to us.archive.ubuntu.com (1.0.0.0)][/COLOR]
[COLOR="Red"]Failed to fetch [http://packages.freecontrib.org/plf/dists/dapper/Release.gpg](http://packages.freecontrib.org/plf/dists/dapper/Release.gpg)  Could not connect to packages.freecontrib.org:80 (1.0.0.0), connection timed out
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg)  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0), connection timed out
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.[/COLOR]

I'm done in. Going to get some dinner, have a good cry, then try to decide what to do. I don't have much time tonight as I have to go to work next week. Spent most of my vacation week on Ubuntu with nothing to show for it.

Carolyn

---

### Post by dg88 on 2006-11-28
i got a similar problem. but i think mine is trying to configure "locale en..." something. ill get back to it this weekend. that computer is at my parents

---

### Post by lennartack on 2006-12-01
I also had a similiar problem. The solution for me was downloading a .deb file of the broken package and installing it with dpkg -i.

---

### Post by sander marechal on 2006-12-04
The problem is with the deb packaging for flash.

The .deb is just a wrapper around a postinstall script. It doesn't contain the flash plugin itself. When the .deb postinstall runs it tries to wget the flash binaries from the official flash site.

The problem starts with people behind a proxy server. Synapyic and the shell both need to have a proxy defined. If you only set the proxy in synaptic (or in /etc/apt/apt.conf) but not a proxy for all shell programs (such as wget) then the flash download will hang.

Solution: Define you proxy in the shell.

I'm reporting a bug about this in Launchpad. Postinstall scri[pts should use the proxy settings from APT when they differ from the general proxies because people may want to allow updates through a proxy but nothing else.

---

### Post by sander marechal on 2006-12-04
See bug #45722.

Here's what you can do yourself: Edit /etc/wgetrc to include your proxy settings:

http_proxy = [http://username:password@proxy:port](http://username:password@proxy:port)
use_proxy = on

the open synaptic, find the flashplugin, remove it completely, then reinstall it.

---

### Post by rajeev1204 on 2006-12-04
hi

this may seem like a silly solution but worked for me.i have the 64 bit version 6.06dapper. sun java 5 jre always breaks . and it gives me that dpkg warning . i just unmark the package in synaptic , then say fix broken packages . it works for me everytime . 

so unmark flash plugin and try it . maybe it will be ok? 


regards

rajeev . (total noob)

---

### Post by peggyjo on 2006-12-24
Rajeev, thanks.

In Synaptic, I didn't have the same option available for unmarking and then "fix broken packages". (Apparently it wasn't broken, but some other problem that was getting my download stuck.)

But following your reported success, I did mark Flash for *removal*, and that did the trick. I'm not getting the dreaded "you must manually run dpkg --configure -a" message any longer, and Synaptic will let me proceed now.

---

