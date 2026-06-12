---
title: "How to install external programs?"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2006-11-11
Hi I've finally backed up my *usual* machine for 3D gaming etc. not just the crappy one for light Linux experimenting.  Now I'm really gonna take action and try to go "a 100% absolute Linux" without that Windows dual boot thing.

Now I've got some encrypted files that I want to open up in Ubuntu 6.06 so I went here: [http://www.truecrypt.org/downloads.php](http://www.truecrypt.org/downloads.php)
Downloaded the Ubuntu 6.06 x86 file, and then double-clicked the *.tar.gz file on my Desktop.
Then I did this and everything seemed to be OK but where's the TrueCrypt program that I just installed?
> 
Taco@Bell:/tmp$ **cd truecrypt-4.2a**
Taco@Bell:/tmp/truecrypt-4.2a$ **ls**
License.txt  Readme.txt  truecrypt_4.2a-0_i386.deb
Taco@Bell:/tmp/truecrypt-4.2a$ **sudo dpkg -i truecrypt_4.2a-0_i386.deb**
Selecting previously deselected package truecrypt.
(Reading database ... 78676 files and directories currently installed.)
Unpacking truecrypt (from truecrypt_4.2a-0_i386.deb) ...
Setting up truecrypt (4.2a-0) ...
Taco@Bell:/tmp/truecrypt-4.2a$
Did I miss some important step that's required to install and use this program?

---

### Post by llamakc on 2006-11-11
You can look for it with the Terminal command:

which truecrypt

provided "truecrypt" is the name of a binary. Also, you can see ALL files installed by any package with the command:

dpkg -L nameofpackage (which here would be "dpkg -L truecrypt")

That said, the binary is probably in /usr/bin/ /opt/bin or /usr/local/bin

---

### Post by findus on 2006-11-11
Have you tried ALT -F2  and entering the name of the software?

---

### Post by jingo811 on 2006-11-11
Nah Alt-F2 didn't do the trick although it seemed to identify its name before I even typed it all.
However it was located in /usr/bin where I could type its program name.  The bad news is, I think the Linux version of Truecrypt is CLI only without all that easy accessible GUI navigation :( 

I think I should investigate this matter more closely at Truecrypt forums before going to any conclusions.
But, what do you guys think about running Truecrypt under Wine?  Would that be wise when messing with encrypted partition files?
Oh by the way thanks for your assistance :-)

---

### Post by llamakc on 2006-11-11
Why not learn how to use the commandline?

---

### Post by jingo811 on 2006-11-11
Too scary man :) 
but opening the encrypted file wasn't that hard though, I just hope I don't have to do any more mumbo jumbo stuff.

---

