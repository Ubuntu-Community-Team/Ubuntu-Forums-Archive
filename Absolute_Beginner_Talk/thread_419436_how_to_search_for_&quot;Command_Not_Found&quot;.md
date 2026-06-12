---
title: "how to search for &quot;Command Not Found&quot;"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by outofmymind on 2007-04-23
Hi,

How do I search the forums for "Command Not Found"?  That is the error message I get when I tried to sudo /etc/init.d/samba restart 
on a fresh install of Feisty.

Actually, I get  [FONT="Courier New"]sudo: /etc/init.d/samba:  command not found
[/FONT]

When I try to search for "command not found" here in the forums, even with the whole thing in quotation marks, it thinks I mean  [FONT="Courier New"]Key Word(s): command, -found  ;[/FONT]

It says under Advanced Search:
> Our search system has a number of options:
    * All Words - search all words you list in the search box 

But gives no example of how to do that.  I tried typing in All Words Command Not Found
and that didn't get me anywhere.

---

### Post by freebird54 on 2007-04-23
I'm not sure how the search thing would work - but all it's telling you is that samba is not in that location under that name.  Try an ls instead of sudo for a look in the directory first :) - or use command completion (tab key) to get the possibilities presented to you.

EDIT:  just tried      **error  "command not found" **  and it turned up a pile of entries...

---

### Post by MyR on 2007-04-23
to run a file like /etc/init.d/samba , you need to precede the path with a period. so the command would be ```
sudo ./etc/init.d/samba
``` (assuming that the file actually exists at that path of course)

---

### Post by devnulljp on 2007-04-23
You just need to install samba by the looks of things

sudo apt-get install samba smbfs

HOWTO is here: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Samba_Server_for_files.2Ffolders_sharing_service](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Samba_Server_for_files.2Ffolders_sharing_service)

Agree with freebird54 though, ls on the directory to see if the file you're trying to callis actually there or not. Command not found means exactly that--and you'll need to install it.

---

### Post by dreadlord_chris on 2007-04-23
> **MyR said:**
> to run a file like /etc/init.d/samba , you need to precede the path with a period. so the command would be ```
sudo ./etc/init.d/samba
``` (assuming that the file actually exists at that path of course)

actually you wouldn't. This is due to _path expansion rules_. A period expands to the **current working directory**

So, in other words, if you are in _/home/blah_:
```

./etc/init.d/samba

```
would expand to:
```

/home/blah/etc/init.d/samba

```
Probably not what you're wanting...

A couple more expansions:
**~** expands to your $HOME directory. So:
```

chris@HAL421:/usr/local/bin$ cd ~
chris@HAL421:~$ pwd
/home/chris

```
btw, _pwd_ is the command to *print working directory*

**..** expands to the *parent* of the current working directory
```

chris@HAL421:/usr/local/bin$ cd ..
chris@HAL421:/usr/local$ 

```

There are many other expansions that (can) happen at the CLI - it's just too early in the morning here for me to remember any more....

---

