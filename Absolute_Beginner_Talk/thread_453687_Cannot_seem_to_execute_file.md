---
title: "Cannot seem to execute file"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by DaveFP on 2007-05-24
Hi guys. I'm trying to set up a Half-Life dedicated server on Feisty (server edition, 64 bit) following the instructions on this page: [http://www.webhostingtalk.com/archive/index.php/t-343796.html](http://www.webhostingtalk.com/archive/index.php/t-343796.html)

However, when I get to step 5 I get the following error:

```
hlds@Atlantis:~$ ls
[COLOR="Lime"]hldsupdatetool.bin[/COLOR]
hlds@Atlantis:~$ ./hldsupdatetool.bin
-bash: ./hldsupdatetool.bin: No such file or directory
```

This puzzles me because the file is there clear as day and it is definately executable (I set the permissions with chmod) and anyway that would generate a different error. So far all the searches I've done come up with answers where people have forgotten the "./" in front of the file name. It's rather frustrating.

I'm convinced that I've missed something elementary but I don't know what so I figured I'd ask the community.
Thanks!

---

### Post by dbott67 on 2007-05-24
Try using 'tab-completion':

Type the following:
**./hld** and then press TAB.  The rest of the file should complete automatically.

If not, just type ./h and press TAB. 

-Dave

---

### Post by benanzo on 2007-05-24
try using the absolute path:
```
/home/hlds/hldsupdatetool.bin
```

---

### Post by DaveFP on 2007-05-24
> **dbott67 said:**
> Try using 'tab-completion':

Type the following:
**./hld** and then press TAB.  The rest of the file should complete automatically.

If not, just type ./h and press TAB. 

-Dave

Tried that... tabbing completes the filename as expected, but I still get the same error. Thanks anyway!

> **benanzo said:**
> try using the absolute path:
```
/home/hlds/hldsupdatetool.bin
```

Ok, I tried the absolute path as you suggested it and that didn't work either. Should the example above work as-is, or would I need to modify it to suit my system (It's a fresh install, I've not modified anything)?

---

### Post by l3f3vr3 on 2007-05-24
what is in this file?  Who owns it?  Do a
```
ls -al hldsupdatetool.bin
```

if you own it and have permissions to it also check what the file is doing.

```
less hldsupdatetool.bin
```

It may be binary but the first few lines may tell you what it is trying to execute.

---

### Post by rapolas on 2007-05-24
Did you tried to do this step: 
5a) If you see an error about not finding /bin/uncompress type ln -s /bin/gunzip /bin/uncompress && ./hldsupdatetool.bin

---

### Post by DaveFP on 2007-05-24
> **rapolas said:**
> Did you tried to do this step: 
5a) If you see an error about not finding /bin/uncompress type ln -s /bin/gunzip /bin/uncompress && ./hldsupdatetool.bin

Yes, I did. Still no luck. I'm going to try re-downloading the file and start from scratch, see if that works.

---

### Post by dbott67 on 2007-05-24
[COLOR=Black]I'm wondering if this is one of those dash vs. bash problems that happens to 6.10 users. Issue the following command in a terminal to display current shell:
```
echo $SHELL
```*(borrowed & modified from **abmorissun**)*

After a clean install of Ubuntu 6.1, you'll have a Terminal application that uses **/bin/dash** by default instead of **bash** (which the script may be expecting). I had this problem when I was trying to install the ATI proprietary binaries.

There are a few hacks out there, but this one seems less drastic:

In Terminal, click **Edit > Current Profile...**

On the "**Title and Command**" tab, under the "**Command**" section, select "**Run a custom command instead of my shell**".

Enter **/bin/bash** beside "Custom command:"

Close the dialog and restart your Terminal and try installing again.

-Dave

PS - Some further info regarding shells:

To see a list of all installed shells:
```
dbott@thedrake:~$ cat /etc/shells
# /etc/shells: valid login shells
/bin/ash
/bin/bash
/bin/csh
/bin/sh
/usr/bin/es
/usr/bin/ksh
/bin/ksh
/usr/bin/rc
/usr/bin/tcsh
/bin/tcsh
/usr/bin/zsh
/bin/sash
/bin/zsh
/usr/bin/esh
/bin/rbash
/usr/bin/screen

```To change your shell for your login, use **chsh**:
```
dbott@thedrake:~$ chsh
Password:
Changing the login shell for dbott
Enter the new value, or press ENTER for the default
        Login Shell [/bin/bash]:

```[/COLOR]

---

### Post by dbott67 on 2007-05-24
I just found something else I posted a while ago while helping someone else with 64-bit architecture that wouldn't run a script from a few months ago:

[http://ubuntuforums.org/showpost.php?p=2092095&postcount=16](http://ubuntuforums.org/showpost.php?p=2092095&postcount=16)

> [COLOR=Blue][B][I]Tintazul
December 11th, 2006, 06:24 PM[/I][/B][/COLOR]

Thanks, Dave! Your solution didn't solve the problem, but after much fussing and trying and searching the net, [COLOR=Red]here's the answer - since my architecture is 64-bit, I have to install the 32-bit compatibility library ia32-libs[/COLOR]. It's now working fine! The solution was found on this thread of the Folding Community forum: 64 Bit Linux Needs 32 bit compatibility libraries? [YES] ([http://forum.folding-community.org/viewtopic.php?t=17223](http://forum.folding-community.org/viewtopic.php?t=17223))

The deanhopkins guy who started this thread had the same architecture upgrade, but I don't have MSN to let him know of the solution. He might have figured it out by now.

:D Thank you very much! You've helped someone who's not only fairly new to Linux, but also a virgin in terms of x64 architecture.

---

### Post by DaveFP on 2007-05-24
Ha-ha! Thank you Dave, you've nailed it. The problem was indeed the 32/64 bit incompatibility and the fix you linked to solved it. I've installed the 32bit compatibility drivers and everything seems to be working now. Thanks again!

---

