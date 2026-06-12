---
title: "Frozen Package manager."
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by lordbyron on 2007-11-05
Hi guys, 
Firstly I am running ubuntu 7.10, updated from 7.04

I was attempting to install my Brother MFC 9180 through the Brother website for linux, I downloaded the driver, After I installed it, it didn't seem to bring up the driver in the printer option on the system > administration menu. so I attempted a reinstall driver through the package manager. the manager didn't like it and has now frozen and when I attempt to do anything, including add/remove in the applications drop down box, it comes up with the following errors.

E: The package mfc9180lpr needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

I reported it as a possible bug, but I am wondering if there is anyone else who has solved this.

---

### Post by hyper_ch on 2007-11-05
did you download this?

cupswrapperMFC9180-1.0.2-1.i386.deb

---

### Post by hyper_ch on 2007-11-05
Actually as I see it, you first have to install this:

mfc9180lpr-1.1.2-1.i386.deb
[http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/lpr_debian/mfc9180lpr-1.1.2-1.i386.deb&lang=English_lpr]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/lpr_debian/mfc9180lpr-1.1.2-1.i386.deb&lang=English_lpr")

And then this:
cupswrapperMFC9180-1.0.2-1.i386.deb
[http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/cups_wrapper/cupswrapperMFC9180-1.0.2-1.i386.deb&lang=English_gpl]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/cups_wrapper/cupswrapperMFC9180-1.0.2-1.i386.deb&lang=English_gpl")

---

### Post by lordbyron on 2007-11-05
I installed mfc9180lpr-1.1.2-1.i386.deb

---

### Post by lordbyron on 2007-11-05
i tried that, but now it's telling me that it can not open. "it says it may be corrupted or you are not allowed to open this file"

Thanks

---

### Post by hyper_ch on 2007-11-05
where and when is it telling you this?

---

### Post by lordbyron on 2007-11-05
The package installer is telling me that after I have downloaded the driver. but now I can't add or remover any other applications.

Cheers

---

### Post by hyper_ch on 2007-11-05
I still have no clue what and where and when you do it...

---

### Post by lordbyron on 2007-11-05
the package manager, install manager and the update manager, are all not allowing me any further. the update manager comes back with 

'E:The package mfc9180lpr needs to be reinstalled, but I can't find an archive for it.'

I hope this helps

---

### Post by hyper_ch on 2007-11-05
you still have the .deb file downloaded right?

Open a terminal, go to the place wherer the .deb file is
```

cd /path/to/dir/where/file/is

```

Then run:
```

sudo dpkg -P mfc9180lpr-1.1.2-1.i386.deb

```

And then reinstall:

```

sudo dpkg -i mfc9180lpr-1.1.2-1.i386.deb

```

and post the output here.

---

### Post by lordbyron on 2007-11-05
Hi. thanks for that. Just did the first option and I got this

dpkg: you must specify packages by their own names, not by quoting the names of the files they come in

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !


not sure what to do. cheers

---

### Post by hyper_ch on 2007-11-06
try:

dpkg-deb  then instead of dpkg

---

### Post by lordbyron on 2007-11-06
Thank you for your help, but I am just not getting any joy. it's telling me:
dpkg-deb: unknown option -p
sorry.

Byron

---

### Post by hyper_ch on 2007-11-06
then have a read at the man pages:

```

man dpkg

```

maybe you find something in there...

---

