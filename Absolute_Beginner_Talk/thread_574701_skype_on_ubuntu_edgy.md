---
title: "skype on ubuntu edgy"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by shadowboxer_k on 2007-10-13
hi everyone,

i have to install skype on my mom's laptop which uses edgy and i can't find relevant advise anywhere. there is some advise around the forums recommending to add skype to the repos, but it seems the link is broken. i add it to the repos and then i can't install anything.

can anyone please help me install skype in ubuntu edgy?
any help greatly appreciated.

thanks!

---

### Post by mendingo84 on 2007-10-13
go to the skype home page and download the ".deb" package. after that, right click on it-> package manager->install . and voila :)

---

### Post by merike on 2007-10-13
I'm trying to do the same thing here. Do you mean Debian Etch or Feisty Fawn as .deb?

---

### Post by merike on 2007-10-14
I tried with a .deb package from Skype's webpage and I got the same issues with dependancies as before when I tried adding Skype to repositories list. Apparently Skype needs newer versions of some packages, but those seem to be unavailable to Edgy because when I try intalling them apt-get says I already have the latest version. Any suggestions?

---

### Post by shadowboxer_k on 2007-10-14
hi. :)

try this in terminal:

```
sudo wget http://www.medibuntu.org/sources.list.d/edgy.list -O /etc/apt/sources.list.d/medibuntu.list

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

then:

```
sudo apt-get install skype
```

it should work. it did for me. :)

---

### Post by haldean on 2007-10-14
Go to [http://www.skype.com/go/getskype-linux-ubuntu](http://www.skype.com/go/getskype-linux-ubuntu) and when the window comes up asking you to save or open, click open and then click download.

After a while the GDebi window will come up. Click "Install Package" and then put in your password when it asks for it- the tool should download all of the dependencies for you.

---

### Post by merike on 2007-10-14
Medibuntu didn't do it for me, still getting:
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  skype: Depends: libasound2 (> 1.0.12) but 1.0.11-7ubuntu3 is to be installed
         Depends: libqt4-core (>= 4.2.1) but 4.2.0-1ubuntu6 is to be installed
         Depends: libqt4-gui (>= 4.2.1) but 4.2.0-1ubuntu6 is to be installed
E: Broken packages

And I already tried .deb from webpage with no luck.

---

