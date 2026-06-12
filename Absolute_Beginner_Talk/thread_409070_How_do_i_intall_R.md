---
title: "How do i intall R?"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by jonttix on 2007-04-14
Hello!

I wonder how I can intall R? I have tried with several different mirrors but I can´t get it to work. I have added this to my source list:

deb [http://CRAN.R-project.org/bin/linux/ubuntu](http://CRAN.R-project.org/bin/linux/ubuntu) dapper/

When I then starts the synapic and reloads the list an error comes up:

W: GPG error: [http://CRAN.R-project.org](http://CRAN.R-project.org) dapper/ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D67FC6EAE2A11821

The same text comes with every mirror I have tried can enybody help me please!!

---

### Post by BobbyBionic on 2007-04-14
Hello

A key is needed, I think there is a command line on the website in order to get it.

PS : Look at the README file ;-)

---

### Post by xopher on 2007-04-14
Well, actually the GPG-KEY shouldn't be required, but it's good to have, because it verifies the packages come from where they say they come.. Gives a little added security, at least a feeling of it, since these are still 3rd party repositories..

Anyway, if you'd have read the README, as BobbyBionic said, this is what you'd have found out: (relevant parts **bold**)
> 
* SECURE APT

The Ubuntu archives on CRAN are signed with the key of "Vincent Goulet
<vincent.goulet@act.ulaval.ca>" with key ID E2A11821. You can fetch
this with

  **gpg --keyserver subkeys.pgp.net --recv-key E2A11821**

and then you feed the key to apt-key with

  **gpg -a --export E2A11821 | sudo apt-key add -**

---

### Post by jonttix on 2007-04-14
Thanks!

Now next problem :)

when I tries to intall the files (r-base) from synapic I get an error message like this:

r-base:
 Depends: r-base-core but it is not going to be installed
 Depends: r-recommended but it is not going to be installed

Then I try to intall r-base-core an error like this shows:

r-base-core:
 Depends: zlib-bin  but it is not installable
 Depends: libgfortran0 (>=4.0.2) but it is not installable

and I cant find none of those packages in synapic.

When I try from the terminal window with:

sudo apt-get intall r-base r-recommended

this appears:

Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  r-base: Depends: r-base-core (>= 2.4.1-1dapper0) but it is not going to be installed
  r-recommended: Depends: r-base-core (>= 2.4.1-1dapper0) but it is not going to be installed
                 Depends: r-cran-boot (>= 1.2.19) but it is not going to be installed
                 Depends: r-cran-cluster (>= 1.9.6-2) but it is not going to be installed
                 Depends: r-cran-foreign (>= 0.7-2) but it is not going to be installed
                 Depends: r-cran-kernsmooth (>= 2.2.14) but it is not going to be installed
                 Depends: r-cran-lattice (>= 0.10.11) but it is not going to be installed
                 Depends: r-cran-mgcv (>= 1.1.5) but it is not going to be installed
                 Depends: r-cran-nlme (>= 3.1.52) but it is not going to be installed
                 Depends: r-cran-rpart (>= 3.1.20) but it is not going to be installed
                 Depends: r-cran-survival (>= 2.13.2-1) but it is not going to be installed
                 Depends: r-cran-vr (>= 7.2.8) but it is not going to be installed
E: Broken packages

How do I get it to work

---

### Post by igknighted on 2007-04-14
Oh boy, dependency hell... this is old days linux.  Unless someone here knows this app and knows where the dependencies are, I think google is your best bet on finding out how to get these.

---

### Post by BobbyBionic on 2007-04-14
Did you do apt-get update before ?

EDIT : Sorry, I understand wrong. Very strange, the repository should be include all of dependencies needed, what about your sources.list ? Perhaps the readme file can help you...

---

### Post by igknighted on 2007-04-14
> **BobbyBionic said:**
> Did you do apt-get update before ?

He's using synaptic, it should update automatically

---

