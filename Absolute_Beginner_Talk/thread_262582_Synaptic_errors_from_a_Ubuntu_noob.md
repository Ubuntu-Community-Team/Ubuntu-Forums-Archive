---
title: "Synaptic errors from a Ubuntu noob"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by lckeeper1 on 2006-09-21
Hey all,

I tried to update my flash player and I'm not quite sure what happened to synaptic. I get the following error messages when I try to open it, either view the System menu, or the update icon on the try:

E: Problem parsing dependency Depends
E: Error occurred while processing hplip (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.


I really have no clue how to fix this. I've tried getting all repositories and all that I know how to do, but it's no go for me.

---

### Post by Metacarpal on 2006-09-21
Open a terminal (Applications menu > Accessories > Terminal) and type this in:
```
sudo aptitude update
```
Then (don't close terminal yet), try to open Synaptic again.  If it doesn't open, go back to terminal and copy the output from your command, and paste it here.

---

### Post by lckeeper1 on 2006-09-21
Here's my output from the command:

```
ubuntu@ubuntu-desktop:~$ sudo aptitude update
Reading package lists... Error!
E: Problem parsing dependency Depends
E: Error occurred while processing hplip (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
Reading package lists... Error!
E: Problem parsing dependency Depends
E: Error occurred while processing hplip (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
```


Not sure what any of it really means. I would like to get it working ASAP, as I've really been enjoyed Ubuntu thus far.

---

### Post by james_san on 2006-09-21
Have you tried pressing "refresh" in Synaptic to reload the package information from the internet? That might fix it.
Also you might have some weird repositories installed. You won't need any other than the ones available by pressing Add in the Repositories dialog. I usually delete all the listed ones, then add all four repositories, and tick all four sub-categories for each one. Then close the dialog and press Refresh.

---

### Post by Metacarpal on 2006-09-21
> **james_san said:**
> Have you tried pressing "refresh" in Synaptic to reload the package information from the internet? That might fix it.
Also you might have some weird repositories installed. You won't need any other than the ones available by pressing Add in the Repositories dialog. I usually delete all the listed ones, then add all four repositories, and tick all four sub-categories for each one. Then close the dialog and press Refresh.

He can't open synaptic, so that's not going to do him a lot of good.

Ice, the file it's talking about is a list of all the software packages currently installed on your system.  The system keeps a backup copy, fortunately, called status-old in the same folder.  So here's what we're going to try - in terminal:
```
cd /var/lib/dpkg
cp status status-bkp
cp status-old status
```

Then try opening Synaptic.

---

### Post by lckeeper1 on 2006-09-22
Metacarpal,

Thanks so much! Worked like a charm!

Back to learning the art which is Ubuntu!

---

### Post by linuxican on 2006-09-23
I posted this once ago but got no answer,
Hi,
I'm having a problem with my synaptic in dapper. the problem appeared after i tried to install a wrong package to make my internal modem work. it was a conexant package. it didn't get installed though because of dependencies.
After whenever i try to open synaptic, at first it tells me about a broken package:

> Warning:
You have 1 broken package on your system!
Use the "Broken" filter to locate it.
and then it shows this error message:

> E: The package conexant needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

after that synaptic has no packages listed, nothing.
when i try to fix the broken package ( Edit -> Fix broken packages) it says:
> E: I wasn't able to locate file for the conexant package. This might mean you need to manually fix this package.

how should i fix it manually? i even tried to remove it but apt-get remove doesn't work.
Thanks,
UPDATE: i  trien replacing the status-old but that didn't work.

---

