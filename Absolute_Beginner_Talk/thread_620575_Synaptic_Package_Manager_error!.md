---
title: "Synaptic Package Manager error!"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by Ubun2User on 2007-11-22
I am getting an error when I open the Synaptic Package Manager to add some Desklets but I keep getting this error...please help.

E: Type '--18:22:11--' is not known on line 1 in source list /etc/apt/sources.list.d/winehq.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

Thanks!

---

### Post by taurus on 2007-11-22
There is something wrong with the first line of your /etc/apt/sources.list.  Edit it

```
gksudo gedit /etc/apt/sources.list.d/winehq.list
```
and then run

```
sudo apt-get update
sudo apt-get upgrade
```
Otherwise, just post your /etc/apt/sources.list.d/winehq.list here.

---

### Post by Ubun2User on 2007-11-22
How do I run that stuff?  in the etc/apt/sources?

Here is the info you requested.

--18:22:11--  [http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list](http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list)
           => `gutsy.list'
Resolving wine.budgetdedicated.com... 81.171.111.184
Connecting to wine.budgetdedicated.com|81.171.111.184|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 181 [text/plain]

    0K                                                       100%    8.65 MB/s

18:22:11 (8.65 MB/s) - `gutsy.list' saved [181/181]

---

### Post by taurus on 2007-11-22
/etc/apt/sources.list.d/winehq.list is the one that gives you trouble, not /etc/apt/sources.list.

```
cat /etc/apt/sources.list.d/winehq.list
```

---

### Post by Ubun2User on 2007-11-22
Yeah, sorry, corrected that above.

---

### Post by taurus on 2007-11-22
Edit /etc/apt/sources.list.d/winehq.list

```
gksudo gedit /etc/apt/sources.list.d/winehq.list
```
and put a # in front of all the lines in there.  Then, save it and exit/close gedit editing window.  

Now, run these two commands from a terminal.

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Ubun2User on 2007-11-22
Thank You So Much!!!  Working Perfectly!

---

