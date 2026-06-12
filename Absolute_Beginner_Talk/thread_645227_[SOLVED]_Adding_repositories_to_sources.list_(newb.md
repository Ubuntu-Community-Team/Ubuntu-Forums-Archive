---
title: "[SOLVED] Adding repositories to sources.list (newb question)"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by Mark20 on 2007-12-19
Hi all,

I've been looking around the forums, and googling for a while, but I'm having trouble adding repositories to my sources.list file.

Here is an example,
I want to add a repository so that I can use apt-get to install the libgtkspell0 package.

I found the file at packages.ubuntu.com, so I added packages.ubuntu.com, as well as the mirror to my sources.list file as shown below:
```

deb http://packages.ubuntu.com/gutsy main universe
deb http://mirrors.kernel.org/ubuntu main universe

```

I then update.  Then, I use the command below to download my package
```

sudo dpkg -i libgtkspell0

```

It gives me the following error:
```

dpkg: error processing libgtkspell0 (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 libgtkspell0


```

I'm running Kubuntu Gutsy.  Any idea why it can't find the package??

Thanks,

Mark

---

### Post by bobplano on 2007-12-19
Did you already download it from the repositories and you just have it in a folder? otherwise, you need to use the aptitude command to download things from the repositories. the dpkg command is for packages on the system.

---

### Post by bodhi.zazen on 2007-12-19
Try :

sudo apt-get update
sudo apt-get install libgtkspell0

---

### Post by RomeReactor on 2007-12-19
Hi. Since you found the package you were looking for in **packages.ubuntu.com**, there's no need to add that as a repository; also, to install software with dpkg you need to have a .deb package, so use Apt to install libgtkspell0:
```
sudo apt-get install libgtkspell0
```

It would ba a good idea to disable or remove the lines you just added to your sources.list; open Konsole and enter:
```
kdesu kate /etc/apt/sources.list
```
find the two lines you added:
```
deb http://packages.ubuntu.com/gutsy main universe
deb http://mirrors.kernel.org/ubuntu main universe
```
and delete them--but don't modify anything else in the file. Save the file, close Kate, and--still in Konsole--run:
```
sudo apt-get update
```
and after that finishes:
```
sudo apt-get install libgtkspell0
```
You can manage your repositories in Adept: open it, go to "Adept->Manage Repositories", and on the first tab (I think) you can enable **Universe** and **Multiverse**; on the "Third Party Software" tab, you can add extra repositories. More on that [here]("https://help.ubuntu.com/community/Repositories/Kubuntu").

---

### Post by Mark20 on 2007-12-19
Hi all,

Yeah, I meant to use the command apt-get install, I don't know what I was thinking lol.

I know that I can manually download the packages...it's just really frustrating hunting for 10-20 packages, to be able to install 1 program.  There has to be an easier way.

I really don't even care about this libgtkspell0 package.  I just need it (along with about 20 others) to be able to install pidgen so that I can use MSN for linux.

Does anyone know an easier way?

---

### Post by RomeReactor on 2007-12-19
If you're running Gutsy and you have internet access, the just run:
```
sudo apt-get install pidgin
```

---

### Post by Mark20 on 2007-12-19
That doesn't work for me, because as I mentioned early I am missing some of the packages.  Here is the result.
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
pidgin is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  pidgin: Depends: libgtkspell0 (>= 2.0.2) but it is not going to be installed
          Depends: liblaunchpad-integration0 (>= 0.0patch26) but it is not going to be installed
          Depends: libpurple0 (>= 1:2.2.1) but it is not going to be installed
          Depends: gconf2 (>= 2.10.1-2) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

### Post by RomeReactor on 2007-12-19
Did you try running apt-get -f install?:
```
sudo apt-get -f install
```

---

### Post by Mark20 on 2007-12-20
Wow ```
sudo apt-get -f install
``` worked perfectly!  I could have sworn I tried that before, I guess not.  Thanks a lot man!

---

