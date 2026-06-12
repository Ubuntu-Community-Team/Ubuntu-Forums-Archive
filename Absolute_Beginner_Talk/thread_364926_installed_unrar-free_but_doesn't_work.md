---
title: "installed unrar-free but doesn't work"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by rggavubt on 2007-02-18
I installed unrar-free using synaptic package manager but it doesn't show up anywere or when I try to extract says file not supported.  How do I use it???  HALP!

---

### Post by taurus on 2007-02-18
Applications -> Accessories -> Terminal
```
unrar x **filename.rar**
```

---

### Post by rggavubt on 2007-02-18
> **taurus said:**
> Applications -> Accessories -> Terminal
```
unrar x **filename.rar**
```



That doesn't work...I have unrar-free.  I entered unrar-free --usage and got the following :
Usage: unrar-free [-xtfp?V] [--extract] [--list] [--force] [--extract-newer]
            [--extract-no-paths] [--password] [--help] [--usage] [--version]
            ARCHIVE [FILE...] [DESTINATION]

How do I enter in terminal?  I tried "unrar-free --extract and then pasted file"...didn't work

---

### Post by Maestro23 on 2007-02-18
> **rggavubt said:**
> That doesn't work...I have unrar-free.  I entered unrar-free --usage and got the following :
Usage: unrar-free [-xtfp?V] [--extract] [--list] [--force] [--extract-newer]
            [--extract-no-paths] [--password] [--help] [--usage] [--version]
            ARCHIVE [FILE...] [DESTINATION]

How do I enter in terminal?  I tried "unrar-free --extract and then pasted file"...didn't work

The command that Taurus gave you is a terminal command.  How and where did you try to enter it?

---

### Post by taurus on 2007-02-18
Click Applications, then Accessories, then Terminal.  Now, change directory with the cd command to where the filename.rar is and see if you can unrar it.

```
unrar-free -x filename.rar
```

---

### Post by rggavubt on 2007-02-18
> **taurus said:**
> Click Applications, then Accessories, then Terminal.  Now, change directory with the cd command to where the filename.rar is and see if you can unrar it.

```
unrar-free -x filename.rar
```

I used 'unrar-free -x' and copied and pasted the file from my download folder.....didn't work.
Do I have to say were I want it to go or will it just extract it into the same folder.  I got the following reply : Bad address
Usage: unrar-free [OPTION...] ARCHIVE [FILE...] [DESTINATION]

---

### Post by taurus on 2007-02-18
What is the name of the file and where is it located?

---

### Post by rggavubt on 2007-02-18
> **taurus said:**
> What is the name of the file and where is it located?

Here is the file : /home/my name/Downloads/Elton John Greatest Hits 1970-2002.rar

I used cd in terminal to go to Downloads folder and pasted above....no go.  I got the following :   unrar-free: invalid archive '/home/my name/Downloads/Elton': Bad address
Usage: unrar-free [OPTION...] ARCHIVE [FILE...] [DESTINATION]

---

### Post by taurus on 2007-02-18
```
cd Downloads
unrar-free -x "Elton John Greatest Hits 1970-2002.rar"
```

---

### Post by Repent on 2007-02-18
I have the same thing happening  with  Cinelerra 2.1 CV. :confused:

---

### Post by rggavubt on 2007-02-18
> **taurus said:**
> ```
cd Downloads
unrar-free -x "Elton John Greatest Hits 1970-2002.rar"
```

For some reason they all failed...I go this :

Extracting  Cd1.zip                                                   Failed
Extracting  Cd2.zip                                                   Failed
Extracting  Cd3.zip                                                   Failed
Extracting  Elton_john_greatesthits70_02_1.jpg                        Failed
Extracting  Elton_john_greatesthits70_02_2.jpg                        Failed
5 Failed

---

### Post by taurus on 2007-02-18
It means that the file is probably corrupted.  Not sure exactly where you got that rar file from.

---

### Post by rggavubt on 2007-02-18
> **taurus said:**
> ```
cd Downloads
unrar-free -x "Elton John Greatest Hits 1970-2002.rar"
```

That worked but failed.  How did you know to use quotations?  Here is reply I got :

Extracting  Cd1.zip                                                   Failed
Extracting  Cd2.zip                                                   Failed
Extracting  Cd3.zip                                                   Failed
Extracting  Elton_john_greatesthits70_02_1.jpg                        Failed
Extracting  Elton_john_greatesthits70_02_2.jpg                        Failed
5 Failed

---

### Post by taurus on 2007-02-18
> **rggavubt said:**
> That worked but failed.  How did you know to use quotations?  Here is reply I got :

Extracting  Cd1.zip                                                   Failed
Extracting  Cd2.zip                                                   Failed
Extracting  Cd3.zip                                                   Failed
Extracting  Elton_john_greatesthits70_02_1.jpg                        Failed
Extracting  Elton_john_greatesthits70_02_2.jpg                        Failed
5 Failed

Double post!

---

### Post by rggavubt on 2007-02-18
> **taurus said:**
> It means that the file is probably corrupted.  Not sure exactly where you got that rar file from.

Thanks, I moved it to the trash.  Do you use parenthesis when there are spaces in file name?

---

### Post by rggavubt on 2007-02-18
> **taurus said:**
> It means that the file is probably corrupted.  Not sure exactly where you got that rar file from.

Thanks, I moved it to the trash.  Do you use quotations when there are spaces in file name?

---

### Post by taurus on 2007-02-18
You can either use the quotes or \ before the space.

```
"Just something here"
-or-
Just\ something\ here
```

p.s.  And why do you start double-posting?

---

### Post by rggavubt on 2007-02-18
> **taurus said:**
> You can either use the quotes or \ before the space.

```
"Just something here"
-or-
Just\ something\ here
```

p.s.  And why do you start double-posting?

It was on the 2nd page and I didn't think it had posted......sorry

---

### Post by Jucato on 2007-02-19
You might have to install the other **unrar** utility, the one in multiverse. The free version seems to be limited it what it can handle.

The unrar-free package description says:
> Unrar can extract files from .rar archives. Can't handle archives in the RAR 3.0 format, only the non-free "unrar" package can do that.

Homepage: [https://gna.org/projects/unrar/](https://gna.org/projects/unrar/)

Take note that the (non-free) unrar in multiverse is only non-free in the license sense. You don't have to pay for anything to use it.

---

### Post by badbreeze on 2007-02-19
7-ZipPortable also works great under wine, right-click your first rar file, select open with other application, select use a custom command, leave use as default for this type of file checked, enter
> wine "whatever your path to 7-ZipPortable.exe"
and in future you can just click on rar files to extract. weird but works great.

---

### Post by badbreeze on 2007-02-19
wine of course is the thing that lets you run windows programs on linux:
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)
and 7-zip is an extracter for windows:
[http://portableapps.com/apps/utilities/7-zip_portable](http://portableapps.com/apps/utilities/7-zip_portable)

---

### Post by zvacet on 2007-02-19
Uninstall that unrar and go with Automatix.You will have unrar,p7zip and one more wich name I can not remember right now.After installing  them only thing you hawe to do to extract some file is to right click on it and in dropdown menu you will see unpack here.Good luck.

---

### Post by mcduck on 2007-02-19
After installing rar & unrar-nonfree Gnome's own archive manager handles rar packages. So you can just right-click one and select 'extract here'. For multi-archives extract the first one and the rest will be extracted automatically.

---

### Post by rggavubt on 2007-02-19
I want to thank everyone for all of the advice.  I will go ahead and install unrar(not free but free??) and automatix.  Keep on sharing knowledge with us noobies.  I like this OS a lot so far!  I'm like a dog with a bone trying to get everything to work.

---

### Post by mcduck on 2007-02-19
> **rggavubt said:**
> I will go ahead and install unrar(not free but free??)
It's free as in no cost, but not free as in freedom.. That should explain the name ;)

---

