---
title: "Unable to Extract .rar files"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by zhinker on 2007-05-04
I'm trying to extract a .rar file using Xarchiver 0.4.0 (it's the first time I'm using it) but I keep getting this error message:
[INDENT]Sorry, this archive format is not supported:
the proper archiver is not installed![/INDENT]
Does anyone know how I can get the right archiver, or know of  some other file extracter I can use instead?

---

### Post by taurus on 2007-05-04
Can you try to extract it from a terminal,

Applications -> Accessories -> Terminal
```
unrar x filename.rar
```
assuming you have already installed unrar from the repos.

---

### Post by trak87 on 2007-05-04
You can install the 'rar' package from Synaptic. Make sure multiverse is enabled. Then, at the command line, run

rar e filename.rar

---

### Post by Delkster on 2007-05-04
> **trak87 said:**
> You can install the 'rar' package from Synaptic. Make sure multiverse is enabled.

Technically, the full rar utility is shareware and should be registered after a 40 day evaluation period.

If you only need to be able to *extract* rar archives, not make them yourself, you can do with the free-of-charge unrar-nonfree package, also found in Synaptic (multiverse still needed).

Edit: Correction -- looks like the package name is just "unrar"

---

### Post by zhinker on 2007-05-04
I'm still a noob at Linux, could you tell me the exact command to install that package?

---

### Post by taurus on 2007-05-04
```
sudo aptitude update
sudo aptitude install unrar
```

---

### Post by Angelbeast on 2007-05-05
I don't seem to be able to install unrar. i tried through a terminal and it seemed to work but i still can't open rar files. and i can't install it from add and remove because it won't let me check the box.

---

### Post by useLinux, on 2007-05-05
```
sudo apt-get install ark
``` I use Ark. Very good, user friendly, has a GUI and to extract, right click on a file, and extract here. :)

---

### Post by Angelbeast on 2007-05-05
> **useLinux, said:**
> ```
sudo apt-get install ark
``` I use Ark. Very good, user friendly, has a GUI and to extract, right click on a file, and extract here. :)

thank you thank you  :-)

---

### Post by useLinux, on 2007-05-05
> **Angelbeast said:**
> thank you thank you  :-)

No problem :) Everything work ok?

---

### Post by Campingman on 2007-05-05
Thanks useLinux,
I had not heard of Ark before
That seems to work quite well !

---

### Post by joneil1000 on 2007-05-05
Xarchive is on Sourforge, here is the URLL

[http://sourceforge.net/project/showfiles.php?group_id=141159](http://sourceforge.net/project/showfiles.php?group_id=141159)

   Click on "deb" package to install easily

---

### Post by Angelbeast on 2007-05-05
> **useLinux, said:**
> No problem :) Everything work ok?

actually it's giving me issue...i'll come bck to it later though...i'm trying to figure out how to change the permissions on a second hard drive so i can move stuff to it *LOL*

---

### Post by useLinux, on 2007-05-05
> **Campingman said:**
> Thanks useLinux,
I had not heard of Ark before
That seems to work quite well !

LOL weird, it was the first ever program i installed on ubuntu :P A mate told me about it. Yeh its really really good. I love it.

---

### Post by bagbiter on 2007-05-10
I am using Ark for extracting files as well, but even if I've installed unrar, I am not able to extract .rar-files. All I get is "an error occured while trying to open the archive"

---

### Post by apienk01 on 2007-05-10
The 'unrar' package supports Rar archives up to version 3.0. Yours is probably newer. Uninstall 'unrar' and install 'unrar-nonfree' instead from multiverse repository.

---

### Post by bagbiter on 2007-05-10
thanks mate, it's working now :)

---

### Post by Sweet Mercury on 2007-05-19
> **useLinux, said:**
> ```
sudo apt-get install ark
``` I use Ark. Very good, user friendly, has a GUI and to extract, right click on a file, and extract here. :)

Just a note on this, you still have to install **unrar** for Ark to be able to deal with *.rar files.

I installed Ark first, and whenn I tried to open a *.rar it gave me an error that said that the proper PATH wasn't installed, so I followed the commands to install unrar.

Now I can deal with *.rar in the native GNOME archive manger and in Ark.

---

### Post by loathsome on 2007-05-19
You should be able to unrar files with the built in archive manager (GNOME) after getting the 'unrar' package.

---

### Post by cika.mancic on 2008-07-04
I was just havin the same problem with .rar. This posts were a big help...
THANKS!!! :grin:

---

### Post by reddox on 2008-07-05
Personally, I prefer running the GUI Windows version of WinRAR through Wine. Prefere it to Archive manager and the lot.

Also, its Nag-ware not shareware. After 40 days, it will just keep asking you to buy it but you can click OK and use it.

---

