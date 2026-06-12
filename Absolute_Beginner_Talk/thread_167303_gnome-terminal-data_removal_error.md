---
title: "gnome-terminal-data removal error"
date: 2006-04-28
forum: Absolute Beginner Talk
---

### Post by fuscia on 2006-04-28
why do i get this and how do i fix it? (actually, if i can fix it, then i don't care why i get it.)

 [i]Removing gnome-terminal-data ...
/var/lib/dpkg/info/gnome-terminal-data.prerm: line 9: gconftool-2: command not found
/var/lib/dpkg/info/gnome-terminal-data.prerm: line 9: gconftool-2: command not found
dpkg: error processing gnome-terminal-data (--remove):
 subprocess pre-removal script returned error exit status 127
Errors were encountered while processing:
 gnome-terminal-data
E: Sub-process /usr/bin/dpkg returned an error code (1)[/i]

---

### Post by trent dillman on 2006-04-28
hmm... I'd try, in this order:
```
sudo apt-get -f install
```
```
sudo apt-get --reinstall install gnome-terminal-data
```

---

### Post by fuscia on 2006-04-28
[QUOTE=trent dillman]hmm... I'd try, in this order:
```
sudo apt-get -f install
```
```
sudo apt-get --reinstall install gnome-terminal-data
```[/QUOTE]

thanks for responding. i did the first one and then...

* sudo apt-get --reinstall install gnome-terminal-data*

getting...

[i]Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 1 not upgraded.
Need to get 709kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main gnome-terminal-data 2.12.0-0ubuntu2                                                                                                     [709kB]
Fetched 709kB in 2s (249kB/s)               

Preconfiguring packages ...
Selecting previously deselected package gnome-terminal-data.
(Reading database ... 37497 files and directories currently installed.)
Preparing to replace gnome-terminal-data 2.12.0-0ubuntu2 (using .../gnome-termin                                                                                                    al-data_2.12.0-0ubuntu2_all.deb) ...
/var/lib/dpkg/info/gnome-terminal-data.prerm: line 9: gconftool-2: command not f                                                                                                    ound
/var/lib/dpkg/info/gnome-terminal-data.prerm: line 9: gconftool-2: command not f                                                                                                    ound
dpkg: warning - old pre-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
dpkg: ... it looks like that went OK.
Unpacking replacement gnome-terminal-data ...
Setting up gnome-terminal-data (2.12.0-0ubuntu2) ...
/var/lib/dpkg/info/gnome-terminal-data.postinst: line 19: gconftool-2: command n                                                                                                    ot found
/var/lib/dpkg/info/gnome-terminal-data.postinst: line 19: gconftool-2: command n                                                                                                    ot found
dpkg: error processing gnome-terminal-data (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 gnome-terminal-data
E: Sub-process /usr/bin/dpkg returned an error code (1)[/i]

---

