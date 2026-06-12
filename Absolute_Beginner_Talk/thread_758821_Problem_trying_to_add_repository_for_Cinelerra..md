---
title: "Problem trying to add repository for Cinelerra."
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by pastoraaron on 2008-04-18
I was trying to add a repository to install cinelerra and now my synaptic package manager is giving me an error message.

The message I get is:
E: Type '--12:10:52--' is not known on line 1 in source list /etc/apt/sources.list.d/akirad.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

I used these commands in terminal to try to add the repository:
sudo wget [http://repository.akirad.net/dists/gutsy.list](http://repository.akirad.net/dists/gutsy.list) -O /etc/apt/sources.list.d/akirad.list

and then:
wget -q [http://repository.akirad.net/dists/akirad.key](http://repository.akirad.net/dists/akirad.key) -O- | sudo apt-key add -

Can this error be corrected?  I am a noob.  Any help would be appreciated.

---

### Post by Bachstelze on 2008-04-18
Please paste the contents of /etc/apt/sources.list.d/akirad.list.

---

### Post by pastoraaron on 2008-04-18
chadwick@chadwick-desktop:~$ /etc/apt/sources.list.d/akirad.list
bash: /etc/apt/sources.list.d/akirad.list: Permission denied

I guess I really messed things up.  I noticed too that my add/remove programs function doesn't work.

---

### Post by Bachstelze on 2008-04-18
To view the contents of a file, you can use the **cat** command, like this :

```
cat /etc/apt/sources.list.d/akirad.list
```

If you just type the name of a file, that means you're trying to execute it as if it were an executable (think of EXE files in Windows), which obviously doesn't work on a plain text file.

---

### Post by pastoraaron on 2008-04-18
chadwick@chadwick-desktop:~$ cat /etc/apt/sources.list.d/akirad.list
--12:10:52--  [http://repository.akirad.net/dists/gutsy.list](http://repository.akirad.net/dists/gutsy.list)
           => `gutsy.list.2'
Resolving repository.akirad.net... 66.7.206.3
Connecting to repository.akirad.net|66.7.206.3|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 199 [text/plain]

    0K                                                       100%   18.87 MB/s

12:10:52 (18.87 MB/s) - `gutsy.list.2' saved [199/199]

---

### Post by Bachstelze on 2008-04-18
I think you made a mistake when typing the first command, be sure to type **exactly** that :

```
sudo wget http://repository.akirad.net/dists/gutsy.list -O /etc/apt/sources.list.d/akirad.list
```

Also, please use CODE tags when posting the output of a command or the contents of a text file.

---

### Post by pastoraaron on 2008-04-18
Thank you.  That resolved the problem.  Can you explain to me what a CODE tag is so I will understand the next time I post some output information.

---

### Post by Bachstelze on 2008-04-18
[*code]This is code.[/*code]

without the asterisks gives :

```
This is code.
```

which is more readable for outputs of commands or config files.

---

