---
title: "Root log in"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by Ziggyz on 2007-07-08
I am trying to access folders that are under my user name, and for the life of me I cant figure out how to log in correctly. Can anyone help a noob?

---

### Post by taurus on 2007-07-08
What is the name of that directory?  Try something like

```
cd **directory**
```

---

### Post by Ziggyz on 2007-07-08
Well Its like cd /home/ziggyz/files/<file I want to install with wine>

thing is I cant get it without root to get into my user name

# edit
Ok, I logged into root, I can tell because it says #, but I still cant get into my user directory.

---

### Post by eternalsword on 2007-07-08
from a terminal, it should open to your home directory which is /home/yourusername/  and the shorthand for this is ~/  you can ```
ls
``` in the terminal to list files and directories.  ```
ls -a
``` will include hidden directories and files, the ones beginning with a period.  If you want just a list of directories, you can use ```
find . -mindepth 1 -maxdepth 1 -type d | sed -e 's/^\.//' -e 's/^\///' -e '/^$/d' | sort -f
``` and similarly for just files, you can use ```
find . -mindepth 1 -maxdepth 1 -type f | sed -e 's/^\.//' -e 's/^\///' -e '/^$/d' | sort -f
```  As taurus pointed out, ```
cd some/direcotry/path/here
``` will change directories.  ```
cd
``` by itself will change to your home directory.  Hope this helps.

---

### Post by eternalsword on 2007-07-08
> **Ziggyz said:**
> Well Its like cd /home/ziggyz/files/<file I want to install with wine>

thing is I cant get it without root to get into my user name

you cannot change directories to a file.  what you want is probably ```
wine /home/ziggyz/files/<file you want to install with wine>
```

and never run wine as root!!!

There's no reason whatsoever that you would need to be root to access files in your home directory.

---

### Post by Ziggyz on 2007-07-08
Ok ill give it a try.

#edit

Now it says it cant find the directory, I type wine /home/ziggyz/files/<file you want to install with wine>

and now it says it cant find it.

---

### Post by eternalsword on 2007-07-08
please post the results of ```
cd && ls -l | grep files
```

---

### Post by Ziggyz on 2007-07-08
Nothing happened, like another example is im doing "~/.wine/drive_c/windows/system.ini"

and its saying permission denied

---

### Post by eternalsword on 2007-07-08
then you have no directory called files in your home directory.  You aren't still logged in as root are you?

---

### Post by taurus on 2007-07-08
What are you trying to run in /home/ziggyz/files/?

```
cd /home/ziggyz/files
ls -la
```

---

### Post by eternalsword on 2007-07-08
> **Ziggyz said:**
> Nothing happened, like another example is im doing "~/.wine/drive_c/windows/system.ini"

and its saying permission denied

can you please explain exactly what you are trying to do here?  you cannot run ~/.wine/drive_c/windows/system.ini as that is just a configuration file

---

### Post by Ziggyz on 2007-07-08
```
ziggy@ziggy-desktop:~$ ~/.wine/drive_c/windows/system.ini
bash: /home/ziggy/.wine/drive_c/windows/system.ini: Permission denied
ziggy@ziggy-desktop:~$ cd /home/ziggyz/files
bash: cd: /home/ziggyz/files: No such file or directory
ziggy@ziggy-desktop:~$ 

```

I am trying to install ventrilo and programs with wine, but I am having troubles getting access to the files in the ziggyz folder. In my home folder lies ziggyz, I put the folder in ziggyz. (i used ziggyz but ziggy is my actually desktop)

---

### Post by eternalsword on 2007-07-08
are you positive you didn't put it in /home/ziggy/ziggyz/files or /home/ziggy/files?  Your username is ziggy, so your home directory is /home/ziggy not /home/ziggyz

and of course permission is denied for ~/.wine/drive_c/windows/system.ini as that is just a configuration file and is not executable.

---

### Post by Ziggyz on 2007-07-08
i used

```
sudo gedit ziggy@ziggy-desktop:~$ ~/.wine/drive_c/windows/system.ini

```

and it worked and I was able to edit that text file.

and yeah I am sure, I just posted ziggyz as a example even though it is ziggy.

---

### Post by eternalsword on 2007-07-08
> **Ziggyz said:**
> i used

```
sudo gedit ziggy@ziggy-desktop:~$ ~/.wine/drive_c/windows/system.ini

```

and it worked and I was able to edit that text file.

and yeah I am sure, I just posted ziggyz as a example even though it is ziggy.

you shouldn't have needed to use sudo to edit that file unless you perhaps ran wine as root which is not the best scenario.

Did you replace ziggyz then with the correct location when you were trying our commands?

---

