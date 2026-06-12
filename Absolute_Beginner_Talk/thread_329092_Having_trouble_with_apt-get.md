---
title: "Having trouble with apt-get"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by Torn on 2006-12-31
Really new, trying to get these dependencies to work out to where i can install stuff and feel more comfortable moving around in ubuntu. Read a few forums, caught a few posts talking about this install build-essential.  
ran the command myself and i ran into this 

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.0) but it is not going to be installed

Now iv have had troubles trying to get the dependencies myself off the site.
One dependency is missing to install this other dependency that i need to install something else, and everything i find has led me up to this and here i am.

i think the G++ is telling me i have a installed a recent version, but that's a guess
any help on the lib? 

comments feel free lemme know!

---

### Post by riven0 on 2006-12-31
Well, first try this:
> 
sudo apt-get -f remove

Now try:

> sudo apt-get install libc6-dev libc-dev build-essential 

what errors does it give after that?

---

### Post by Torn on 2006-12-31
Reading package lists... Done
Building dependency tree... Done
Note, selecting libc6-dev instead of libc-dev
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libc6-dev: Depends: libc6 (= 2.3.6-0ubuntu20) but 2.4-1ubuntu12 is to be installed
E: Broken packages

---

### Post by sabertooth_cat on 2006-12-31
I'm new also, but you might want to try aptitude instead of apt-get; it would help with the dependency problems.

[URL="http://www.psychocats.net/ubuntu/installingsoftware"][COLOR="Blue"]The quote below is from Psychocats excellent website: Installing software in Ubuntu[/COLOR]
[/URL]

> The advantages of aptitude over apt-get
aptitude has an important feature that its command-line cousin apt-get and the graphical frontends Synaptic and Adept do not have--it remembers dependencies. If you update with aptitude, install with aptitude, and then uninstall with aptitude, all the dependencies you installed with a particular package will be removed when that package is removed (unless other packages also depend on those dependencies). If you install with Synaptic, Adept, or apt-get, uninstalling will uninstall only the package you specify--not the dependencies that came with it.

For example, if you install kword, you will also install kspread, kword-data, and libwv2-1c2. If you install kword with aptitude and then uninstall with aptitude, kspread, kword-data, and libwv2-1c2 will also be removed along with kword. If, however, you install kword with apt-get and then uninstall kword, kspread, kword-data, and libwv2-1c2 will remain installed, and you will not be prompted to remove them. 

Hope this helps.

---

### Post by riven0 on 2006-12-31
> **Torn said:**
> The following packages have unmet dependencies:
  libc6-dev: Depends: libc6 (= 2.3.6-0ubuntu20) but 2.4-1ubuntu12 is to be installed
E: Broken packages

Alright, can you go into Synaptic Package Manager >> Custom Filters >> Broken

If there are any packages listed there, try removing them. Then close Synaptic, open the terminal and run this:
> 
sudo dpkg --configure -a

Then just do:

> sudo apt-get install build-essential

EDIT: sabertooth_cat is right. If it doesn't work with apt-get, try again with aptitude

---

### Post by Torn on 2006-12-31
Check on aptitude, I didnt see anything under the Custom > Broken filter. But searching for the libc6 "v2.4-lubuntu1u" files i found that only. libc6  was installed, and when i checked libc6-dbg,libc6-dev
it gave me this

libc6-dev:
  Depends: libc6 (=2.3.6-0ubuntu20) but 2.4-1ubuntu12 is to be installed

---

### Post by Torn on 2006-12-31
how do i access aptitude?

er. think i got it sudo aptitude xxxx

---

### Post by riven0 on 2006-12-31
> **Torn said:**
> how do i access aptitude?

You use aptitude in place of apt-get. For example *sudo apt-get install whatever* will be *sudo aptitude install whatever*.

Alright, try removing libc6-dev:
> 
sudo aptitude -f remove libc6-dev

---

### Post by Torn on 2006-12-31
sudo aptitude -f remove libc6-dev
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_CA:en",
        LC_ALL = (unset),
        LANG = "en_CA.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_ALL to default locale: No such file or directory
$ sudo aptitude install libc6-dev
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  libc6-dev


so i tried to install for shits'n giggles and i got this 
 sudo aptitude install libc6-dev
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  libc6-dev
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/2822kB of archives. After unpacking 11.2MB will be used.
The following packages have unmet dependencies:
  libc6-dev: Depends: libc6 (= 2.3.6-0ubuntu20) but 2.4-1ubuntu12 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Downgrade the following packages:
libc6 [2.4-1ubuntu12 (now) -> 2.3.6-0ubuntu20 (dapper)]

Score is -40

Accept this solution? [Y/n/q/?]

---

### Post by riven0 on 2006-12-31
> **Torn said:**
> 
The following actions will resolve these dependencies:

Downgrade the following packages:
libc6 [2.4-1ubuntu12 (now) -> 2.3.6-0ubuntu20 (dapper)]

Score is -40

Accept this solution? [Y/n/q/?]

So I guess it's best to try uninstalling libc6 instead. First try this:
> 
sudo apt-get -f remove --purge libc6 

If that doesn't work:
> 
sudo aptitude remove libc6 

---

### Post by Torn on 2006-12-31
sudo apt-get -f remove --purge libc6
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  console-data: Depends: debconf but it is not going to be installed or
                         debconf-2.0
                Depends: debconf (>= 0.5) but it is not going to be installed or
                         debconf-2.0
  libjline-java: Depends: java-gcj-compat but it is not going to be installed or
                          kaffe but it is not installable or
                          java2-runtime but it is not installable or
                          java1-runtime
  openoffice.org-l10n-en-gb: Depends: openoffice.org-common (>= 2.0.2) but it is  not going to be installed or
                                      language-support-en but it is not going to  be installed
                             Depends: openoffice.org-common (< 2.0.3) but it is not going to be installed or
                                      language-support-en but it is not going to  be installed
  openoffice.org-l10n-en-us: Depends: openoffice.org-common (>= 2.0.2) but it is  not going to be installed or
                                      language-support-en but it is not going to  be installed
                             Depends: openoffice.org-common (< 2.0.3) but it is not going to be installed or
                                      language-support-en but it is not going to  be installed
  openoffice.org-l10n-en-za: Depends: openoffice.org-common (>= 2.0.2) but it is  not going to be installed or
                                      language-support-en but it is not going to  be installed
                             Depends: openoffice.org-common (< 2.0.3) but it is not going to be installed or
                                      language-support-en but it is not going to  be installed
E: Broken packages

---

### Post by Torn on 2006-12-31
sudo aptitude remove libc6




.....Depends: libc6 (>= 2.3.4-1) but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Downgrade the following packages:
libc6 [2.4-1ubuntu12 (now) -> 2.3.6-0ubuntu20 (dapper)]

Score is -36

Accept this solution? [Y/n/q/?]

 aptitude had a much diffrent effect on the console

---

### Post by sabertooth_cat on 2007-01-01
Tom, it looks like there might be some kind of known bug causing your problem. Try dumping some of your output into Google (especially related to "libc6"), and see if that leads you anywhere. Sorry I don't know any more about your issue.

---

### Post by Torn on 2007-01-01
Il try downgrading to the 2.3 and see what happends next, thanks for the help

---

### Post by Torn on 2007-01-01
ahh tried the downgrade and 
some reason the aptitude doesent have super cow powers...
but apt-get install build-essential worked!
so yay

---

### Post by sabertooth_cat on 2007-01-01
:)  Good work and happy new year!

---

