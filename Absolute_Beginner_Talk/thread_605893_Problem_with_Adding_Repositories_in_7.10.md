---
title: "Problem with Adding Repositories in 7.10"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by AgCrew08 on 2007-11-07
Forgive me if this is a stupid question as I'm very very new to Ubuntu and Linux in general. I'm trying to add repositories. 

I've been attempting to add a repository following directions from the documentation section of the help site.

The instructions say...



   1.

      Open System &#8594; Administration &#8594; Software Sources and press Third-Party Software.
   2.

      Press Add to add a new repository.
   3.

      Enter the APT line for the extra repository. This should be available from the website of the repository or similar, and should look similar to the following:

      deb [http://ftp.debian.org](http://ftp.debian.org) sarge main

   4.

      Press Add Source and then click Close to save your changes.
   5.

      Click Reload in the package manager to update the list of available packages.



I get to step 4, but the "Add Source" button never lights up for me to click on it. Is there something I'm completely missing or is there something deeper wrong with the system?

---

### Post by NeoLithium on 2007-11-07
No, there's nothing that should be deeply wrong.  Check out the guide for adding repositories here: [http://www.ubuntuguide.org](http://www.ubuntuguide.org)  simple walkthroughs, and even copy and paste if you want to try some command line stuff :)

---

### Post by Inxsible on 2007-11-07
you can also do it the terminal way (which I prefer) :)

```
gksudo gedit /etc/apt/sources.list
```

Add the deb line to the end of the file and save. Then```
sudo aptitude update && sudo aptitude upgrade
```

Of course, if you use KDE, then change the first command to ```
kdesu kate /etc/apt/sources.list
```

---

### Post by AgCrew08 on 2007-11-07
Thanks for the quick responses guys.

I have also tried the command line method going into the source list. 

I'm attempting to add the Medibuntu repository.

I added the following to the source list...

> sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list

I saved and closed the source list and then reopened the synaptic manager which then gave me an error message. I feel like I'm probably missing something basic I just can't seem to figure out what.

---

### Post by taurus on 2007-11-07
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Inxsible on 2007-11-07
> **AgCrew08 said:**
> Thanks for the quick responses guys.

I have also tried the command line method going into the source list. 

I'm attempting to add the Medibuntu repository.

I added the following to the source list...



I saved and closed the source list and then reopened the synaptic manager which then gave me an error message. I feel like I'm probably missing something basic I just can't seem to figure out what.the sudo wget is a command that you need to run in the terminal NOT add it to sources.list

---

