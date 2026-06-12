---
title: "Problem with GDebi Package Install"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by n_murthy on 2008-01-13
I'm trying install the repositories for the Medibuntu package. I attempted to install the package with GDebi, but I get the following error (see thumbnail below). Does anyone have any solutions?

---

### Post by kostkon on 2008-01-13
Instructions on how to add the *Medibuntu* repository to your software sources are given [here]("https://help.ubuntu.com/community/Medibuntu") (don't forget to add the G*PG* key and do a *sudo apt-get update*). After you add the repository, open *Synaptic*, search for *Mplayer* and install it. Alternatively, you can install it from the terminal, like this
```
sudo apt-get install mplayer
```

---

### Post by n_murthy on 2008-01-13
I get the following terminal response after 'sudo apt-get udpate':

murthy@murthy-desktop:~$ sudo apt-get install mplayer
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
  mplayer: Depends: libartsc0 (>= 1.5.0-1) but it is not installable
           Depends: libaudio2 but it is not installable
           Depends: libdvdread3 (>= 0.9.6) but it is not installable
           Depends: libfaac0 (>= 1.24clean) but it is not installable
           Depends: libggi2 (>= 1:2.2.1) but it is not installable
           Depends: liblame0 (>= 3.97) but it is not installable
           Depends: liblzo1 but it is not installable
           Depends: libmad0 (>= 0.15.1b) but it is not installable
           Depends: libmp4v2-0 (>= 2.0.0+cvs20040908+mp4v2+bmp) but it is not installable
           Depends: libmpcdec3 but it is not installable
           Depends: libpulse0 but it is not installable
           Depends: libungif4g (>= 4.1.4) but it is not installable
           Depends: libx264-54 but it is not installable
           Depends: libxvidcore4 (>= 1:1.0.0-0.0) but it is not installable
           Depends: libxvmc1 but it is not installable
           Depends: mplayer-skins but it is not installable
E: Broken packages

---

### Post by oldos2er on 2008-01-13
You likely don't have all the repositories enabled. Can you post the output of  cat /etc/apt/sources.lst ?

---

### Post by kostkon on 2008-01-13
> **n_murthy said:**
> I get the following terminal response after 'sudo apt-get udpate':

murthy@murthy-desktop:~$ sudo apt-get install mplayer
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
  mplayer: Depends: libartsc0 (>= 1.5.0-1) but it is not installable
           Depends: libaudio2 but it is not installable
           Depends: libdvdread3 (>= 0.9.6) but it is not installable
           Depends: libfaac0 (>= 1.24clean) but it is not installable
           Depends: libggi2 (>= 1:2.2.1) but it is not installable
           Depends: liblame0 (>= 3.97) but it is not installable
           Depends: liblzo1 but it is not installable
           Depends: libmad0 (>= 0.15.1b) but it is not installable
           Depends: libmp4v2-0 (>= 2.0.0+cvs20040908+mp4v2+bmp) but it is not installable
           Depends: libmpcdec3 but it is not installable
           Depends: libpulse0 but it is not installable
           Depends: libungif4g (>= 4.1.4) but it is not installable
           Depends: libx264-54 but it is not installable
           Depends: libxvidcore4 (>= 1:1.0.0-0.0) but it is not installable
           Depends: libxvmc1 but it is not installable
           Depends: mplayer-skins but it is not installable
E: Broken packages

What version of Ubuntu are you using? Are you sure you added the corresponding *Medibuntu* repository for your version?

Another possibility is that you don't have all the official repositories enabled. In order to activate them (assuming that you use Ubuntu 6.10 or newer), go to *Sytem -> Administration -> Software Sources*, click on the first tab and select all the repositories, i.e universe, multiverse, main, restricted. Press *Close* and then try again to install *Mplayer*.

---

### Post by ugm6hr on 2008-01-13
> **n_murthy said:**
> I'm trying install the repositories for the Medibuntu package. I attempted to install the package with GDebi, but I get the following error (see thumbnail below). Does anyone have any solutions?

Have you got internet access on your Ubuntu computer?
Did an installation stop half-way?

These are potential causes for problems with apt-get.

---

