---
title: "Rar"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by Roen hayden on 2007-10-23
hello i'm using ubuntu 6.06 LTS how can i open .RAR files?

---

### Post by Steveway on 2007-10-23
Install the unrar package from Synaptic.
Then you can open .rar files with the archive-manager.

---

### Post by Roen hayden on 2007-10-23
> **Steveway said:**
> Install the unrar package from Synaptic.
Then you can open .rar files with the archive-manager.

ok that does not work any other ideas?

---

### Post by evilregis on 2007-10-23
7zip (in the add/remove program list) should open rar files.

---

### Post by Roen hayden on 2007-10-23
> **evilregis said:**
> 7zip (in the add/remove program list) should open rar files.

ok thats not in the add/remove.....

---

### Post by droppedd on 2007-10-23
system -> administration -> synaptic package manager
For GUI rar file manipulation, try installing xarchive or xarchiver and use them to open your file,.

For command-line rar manipulation, you'll probably want "rar" and "unrar." You may need to have the universe/restricted/multiverse repositories turned on to see it.

see [http://tips.webdesign10.com/how-to-open-a-rar-file-in-linux](http://tips.webdesign10.com/how-to-open-a-rar-file-in-linux).

---

### Post by evilregis on 2007-10-23
Do you have "All available applications" selected in the "Show" drop-down menu?  It's not listed in "Supported applications".

---

### Post by Roen hayden on 2007-10-23
> **droppedd said:**
> system -> administration -> synaptic package manager
For GUI rar file manipulation, try installing xarchive or xarchiver and use them to open your file,.

For command-line rar manipulation, you'll probably want "rar" and "unrar." You may need to have the universe/restricted/multiverse repositories turned on to see it.

see [http://tips.webdesign10.com/how-to-open-a-rar-file-in-linux](http://tips.webdesign10.com/how-to-open-a-rar-file-in-linux).

ok i have all of that installed and it still will not open the files are not corrupt because the archive manger says it does not support rar and so does xarchive & xarchiver.

---

### Post by Roen hayden on 2007-10-23
ok so so far nothing has worked and i have downloaded every thing that deals with .RAR from add and remove and the package mangier

---

### Post by kellemes on 2007-10-23
> **Roen hayden said:**
> ok that does not work any other ideas?

You didn't explain why.. unrar is made for it.

---

### Post by PHuN on 2007-10-23
This has worked for me on more than one system.

open terminal, copy paste:

```
sudo apt-get install rar unrar
```



**EDIT:** I forgot to mention that one of the programs, can't remeber which, is shareware.
After 30 days it asks for a small donation, yet continues functionality after the date. **EDIT**

---

### Post by Roen hayden on 2007-10-23
> **kellemes said:**
> You didn't explain why.. unrar is made for it.


what i mean is that i have unrar installed but archive manger does not open the the .rar the error message i get is that rar is not supported

---

### Post by kellemes on 2007-10-23
Well, I'm not gui-minded myself..  but from terminal you can simply.

unrar file in current directory
```
unrar e file.rar
```

unrar file with full path
```
unrar x file.rar
```

For help type unrar.

---

### Post by Roen hayden on 2007-10-23
command not found but its says it is installed in the synaptic package manger

---

### Post by Roen hayden on 2007-10-23
Do you think a whole reinstall of the OS will do the trick?

---

### Post by kellemes on 2007-10-23
> **Roen hayden said:**
> command not found but its says it is installed in the synaptic package manger

Well..
Replace unrar with /bin/unrar
It should be there..

---

### Post by stchman on 2007-10-23
> **Roen hayden said:**
> hello i'm using ubuntu 6.06 LTS how can i open .RAR files?


So I am going to assume that you already installed rar and unrar via the package manager.

Ok, try installing ark (KDE version of File Roller)

sudo apt-get install ark


Tell us if that works.

---

### Post by zvacet on 2007-10-23
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=rar&searchon=names&subword=1&version=dapper&release=all]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=rar&searchon=names&subword=1&version=dapper&release=all")

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=unrar&searchon=names&subword=1&version=dapper&release=all]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=unrar&searchon=names&subword=1&version=dapper&release=all")


both of them


[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=p7zip&searchon=names&subword=1&version=dapper&release=all]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=p7zip&searchon=names&subword=1&version=dapper&release=all")


For every package install dependencies first(marked with red ball).Also,you can chek in synaptic if you allready have them

---

### Post by Roen hayden on 2007-10-23
> **stchman said:**
> So I am going to assume that you already installed rar and unrar via the package manager.

Ok, try installing ark (KDE version of File Roller)

sudo apt-get install ark


Tell us if that works.

already have it installed says the same thing.  So i'm out of ideas.

---

### Post by Roen hayden on 2007-10-23
i get this error message when i try to open the .rar file in ark "the utility  unrar is not in your path"  does this help?

---

### Post by kellemes on 2007-10-23
> **Roen hayden said:**
> i get this error message when i try to open the .rar file in ark "the utility  unrar is not in your path"  does this help?

```
locate unrar
```
This will show you the path.. probably /bin/unrar
Change the path in whatever gui you're using.

---

### Post by Roen hayden on 2007-10-23
> **kellemes said:**
> ```
locate unrar
```
This will show you the path.. probably /bin/unrar
Change the path in whatever gui you're using.

how do i change the path in ark?

---

### Post by ItsMitsHere on 2007-10-23
ok buddy, no heart feelings but how do you say that rar and unrar are installed. just because u see rar and unrar in synaptic does not mean they are installed. they are suppossed to be having an olive green check-box instead of a blank one. if this is not the case, search synaptic for rar and remove all the applications concerned with .rar files. then install rar and unrar by **sudo apt-get install rar unrar** then try to open your file by whatever way u feel comfortable. it should be working!!!

---

### Post by Roen hayden on 2007-10-23
> **ItsMitsHere said:**
> ok buddy, no heart feelings but how do you say that rar and unrar are installed. just because u see rar and unrar in synaptic does not mean they are installed. they are suppossed to be having an olive green check-box instead of a blank one. if this is not the case, search synaptic for rar and remove all the applications concerned with .rar files. then install rar and unrar by **sudo apt-get install rar unrar** then try to open your file by whatever way u feel comfortable. it should be working!!!

ok so yea in synaptic it says that unrar is installed but no program can open the file.  I have done every thing that people have said to do and i still cant get it to work.  i may reinstall the whole system doesn't matter to me cause its on a test PC.

**sudo apt-get install rar unrar** and when i run that command it can not find them says they changed there name. something along the lines of that.

---

### Post by Maestro23 on 2007-10-23
> **Roen hayden said:**
> ok so yea in synaptic it says that unrar is installed but no program can open the file.  I have done every thing that people have said to do and i still cant get it to work.  i may reinstall the whole system doesn't matter to me cause its on a test PC.

**sudo apt-get install rar unrar** and when i run that command it can not find them says they changed there name. something along the lines of that.

They are there.  Make sure your Universe and Multiverse Repos are enabled.

System>> Admin>> Software Resources

---

### Post by ItsMitsHere on 2007-10-23
> **Roen hayden said:**
> ok so yea in synaptic it says that unrar is installed but no program can open the file.  I have done every thing that people have said to do and i still cant get it to work.  i may reinstall the whole system doesn't matter to me cause its on a test PC.

**sudo apt-get install rar unrar** and when i run that command it can not find them says they changed there name. something along the lines of that.

to the best of my knowledge (which is not much!!!) along with unrar, u need to have rar. plus i think ur system has been clumsy and some dependencies are broaken. if u can just update system with **sudo apt-get update** and clean a little bit with **sudo apt-get clean** and fix broaken things with **sudo apt-get --fix-missing** u might be more at ease. if still the problem is persistant, post back with exact error messages, so that we can try it on our systems as well...

---

### Post by Roen hayden on 2007-10-23
ok thanks alot guys i finally got it to work i didn't have all the repo selected thanks agian lol

---

### Post by c4s on 2007-10-25
its not rar unrar, its just sudo apt-get install unrar  do that and it should work fine, as it did for me, then go to open your .rar file and it will autimatically run unrar on it :)

---

### Post by Qwerty_ on 2007-10-25
[http://ubuntuforums.org/showthread.php?t=271143](http://ubuntuforums.org/showthread.php?t=271143)

---

### Post by rabidus on 2007-10-29
```
sudo apt-get install rar unrar
```

The above worked for me.  Thanks Phun!

---

### Post by catch_22 on 2008-06-04
in the Synapsis it is written that the recommended package, "unrar" if free for 40 days only and then requires registration.
Will i need to pay for it after 40 days?
Do I have any free alternative? ("unrar-free" did not work for me...)

---

