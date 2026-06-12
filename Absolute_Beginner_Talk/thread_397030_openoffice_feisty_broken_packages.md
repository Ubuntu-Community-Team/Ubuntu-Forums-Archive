---
title: "openoffice feisty broken packages"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by benner on 2007-03-30
i installed feisty 64 on the weekend and was never able to get openoffice 2.2 working.  the splash screen would come up, the bar that shows it's loading would get halfway and then it would all vanish.  i kept marking for reinstall etc... in synaptic and was geting nowhere.  i posted elsewhere about this and a couple of guys left a few posts to help me out but i got nowhere.  finally i did a complete removal of everything associated with openoffice.org in synaptic.  dumb.  not i can't reinstall it at all.  it keeps telling me that there are unmet dependencies but the dependencies are all part of openoffice--i try to install the base and it tells me i need the core, i try to install the core and it tells me i need writer, i try to install writer and it tells me i need the base and so on.  finally i downloaded it from the site.  it is a weird bunch of rpm's that can't be installed one at a time because they all depend on one another,  it finally occurred to me that the reason it may not have worked was because i didn't have java installe yet.  i took care of that and it still won't work.  here's my feeble attempts (including dumb typos...

ben@ramen:~$ sudo apt-get install openoffice.org-core
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
  openoffice.org-core: Depends: openoffice.org-common (> 2.2.0) but it is not going to be installed
E: Broken packages
ben@ramen:~$ sudo apt-get install openoffice
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package openoffice
ben@ramen:~$ sudo apt-get install openoffice.org
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
  openoffice.org: Depends: openoffice.org-core (= 2.2.0-0ubuntu2) but it is not going to be installed
                  Depends: openoffice.org-writer but it is not going to be installed
                  Depends: openoffice.org-calc but it is not going to be installed
                  Depends: openoffice.org-impress but it is not going to be installed
                  Depends: openoffice.org-draw but it is not going to be installed
                  Depends: openoffice.org-math but it is not going to be installed
                  Depends: openoffice.org-base but it is not going to be installed
                  Depends: openoffice.org-filter-binfilter but it is not going to be installed
                  Depends: openoffice.org-filter-mobiledev but it is not going to be installed
                  Depends: openoffice.org-java-common but it is not going to be installed
E: Broken packages
ben@ramen:~$ sudo apt-get install openoffice.org-base
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
  openoffice.org-base: Depends: openoffice.org-core (= 2.2.0-0ubuntu2) but it is not going to be installed
                       Depends: openoffice.org-java-common but it is not going to be installed
E: Broken packages
ben@ramen:~$ sudo apt-get install openoffice.org-java-common
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
  openoffice.org-java-common: Depends: openoffice.org-common but it is not going to be installed
E: Broken packages
ben@ramen:~$ sudo apt-get install openoffice.org-common
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
  openoffice.org-common: Depends: openoffice.org-core (> 2.2.0~rc3~oof680m10) but it is not going to be installed or
                                  openoffice.org-core-experimental (> 2.2.0~rc3~oof680m10) but it is not installable
E: Broken packages
ben@ramen:~$ sudo apt-get install openoffice.org-core-experiments
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package openoffice.org-core-experiments
ben@ramen:~$ sudo apt-get install openoffice.org-core-experimental
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package openoffice.org-core-experimental is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package openoffice.org-core-experimental has no installation candidate
ben@ramen:~$ 


any suggestions would be appreciated.

---

### Post by TonKi on 2007-03-30
Updated and working packages are available - and there is the [developement 'forum']("http://www.ubuntuforums.org/forumdisplay.php?f=179")

---

### Post by benner on 2007-04-09
i managed to get it installed again but it still crashes from the splash screen.  i have found a lot of other posts by people with the same problem and have moved my discussion over there.  thanks.

---

