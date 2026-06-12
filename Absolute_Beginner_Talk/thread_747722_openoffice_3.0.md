---
title: "openoffice 3.0"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by miesnerd on 2008-04-06
How do I install OOo 3.0 (developer build)-
There are a ton of .deb's from the package I downloaded, after extracting, which is here:
[ftp://ftp.ussg.iu.edu/pub/openoffice/developer/DEV300_m3](ftp://ftp.ussg.iu.edu/pub/openoffice/developer/DEV300_m3)
(i chose the second one)

Now, there are a few problems I have:
1. I need to be able to work around the architecture problem, ie- when i run dpkg it says wrong arch (its built for 386, im on 64 bit linux)
2. Aside from the problem in #1, can I just double click each .deb. Surely, there's a way from the command line to do this faster, right?

Thanks guys.

BTW, I have 2.4, but im anxious to see 3.0 because of some of the bibliography type support I hear it has. Plus, im just anxious in general.

Oh, and a 3rd question-- is there a repo I could have just added that would have listed this through synaptic for me, instead of me doing this the "hard" way through firefox?

---

### Post by dizee on 2008-04-06
To install 32-bit programs you use the "--force-architecture" option. So navigate to the folder where you have all the .deb files for OpenOffice, open a terminal and type ```
sudo dpkg -i --force-architecture *.deb
``` and that will install all the deb files in one go.

Regarding question 3, as OO3 is in development I don't think there'd be a specific repository for it yet.

---

### Post by miesnerd on 2008-04-06
ok, so now the install from the terminal looked successful, but I dont know the package name and since I didnt use add/remove or synaptic, it didnt add it to the office tab. I dont know if it shows up in the debian menu because I havent installed that on this system, and I forgot how to do it.
I'll play, but if anyone knows how to start the program from the term, I'd love to know.

---

### Post by miesnerd on 2008-04-06
nevermind. You can launch it manually from /opt/ooo-dev3.0/program/soffice
now, to make a launcher for it.

---

### Post by benste on 2008-05-07
I did have the same prblem:
only your directory is wrong, it mus be 
```

/opt/openoffice.org3/program/sbase
/opt/openoffice.org3/program/scalc
/opt/openoffice.org3/program/sdraw
/opt/openoffice.org3/program/simpress
/opt/openoffice.org3/program/smath
/opt/openoffice.org3/program/soffice
/opt/openoffice.org3/program/swriter
```

---

### Post by benste on 2008-05-07
One additional question: nautilus doesn't recognize soffice for all odf files anymore - where can I change it? - i want to double click on an odp and this shoul open in IMpress and not evince

---

### Post by benste on 2008-05-07
And: is it right that there is no mpg and avi video support? - which files are supported?

---

### Post by pavolzetor on 2008-05-08
hello i wrote own script to the install
copy it to the directory, where are packages
change permission to "acces run program"

---

