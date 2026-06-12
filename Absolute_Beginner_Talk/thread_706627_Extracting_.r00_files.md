---
title: "Extracting .r00 files"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by MissingHorcrux on 2008-02-24
Hi all! I just made the switch from XP to Linux this past Friday! I can't wait to start getting the hang of my new Ubuntu machine! <3

Now, onto my question. I have an .avi file that's been archived in the .r0* format. To figure out how to extract the file, I've saught help at these two websites, and done what they've suggested:

[http://ubuntuforums.org/showthread.php?t=254093](http://ubuntuforums.org/showthread.php?t=254093)
[http://techiegeeks.com/?p=78](http://techiegeeks.com/?p=78)

However, I'm still left with a rather odd problem: it will extract the file from one of the .r0* files, then prompt for my password, delete the file, and begin extracting all over again. It seems stuck in an extracting loop. :/ Before I install anything else, is this maybe just an error that could be fixed?

Thanks in advance!

---

### Post by mali2297 on 2008-02-24
Is this what you tried?
```

unrar e example.r01

```
Do you get any explicit error message?

---

### Post by asmoore82 on 2008-02-24
```
sudo apt-get update
sudo apt-get install unrar
unrar e *<first_file_of_archive(maybe_*.rar_or_*.r00)>*
```

---

### Post by mivo on 2008-02-24
When you have installed the unrar package, you can also simply click the .rar file in Nautilus and extract it (the .r## files just mean that it's one large archive file split up in smaller parts).

---

### Post by MissingHorcrux on 2008-02-24
> **mali2297 said:**
> Is this what you tried?
```

unrar e example.r01

```
Do you get any explicit error message?
mali2297: I have tried that. It tells me "No such file or directory. No files to extract." But there's clearly a file it's extracting - I see 300MB before it resets.

---

### Post by MissingHorcrux on 2008-02-24
> **mivo said:**
> When you have installed the unrar package, you can also simply click the .rar file in Nautilus and extract it (the .r## files just mean that it's one large archive file split up in smaller parts).
mivo: I have done the right-click method. It behaves the same way - extract, delete, extract, delete, etc. :/

---

### Post by mivo on 2008-02-24
You need to extract the *.rar file, not the individual parts. There is almost certainly one that has the same name but ends in .rar. :) It will automatically find the needed parts and extract them properly -- it's not done by hand.  Also, open Synaptic and search for "unrar". Make sure you have the *unrar* package installed, not *unrar-free.* Try it in Nautilus by double-clicking the *.rar file. No luck?

---

### Post by justleen on 2008-02-24
from usenet by any chance?

par check with 
```

sudo apt-get install par2
par2repair <parfile.par2*>
unrar -e <files.rar / r*>

```

---

### Post by MissingHorcrux on 2008-02-24
> **mivo said:**
> You need to extract the *.rar file, not the individual parts. There is almost certainly one that has the same name but ends in .rar. :) It will automatically find the needed parts and extract them properly -- it's not done by hand.  Also, open Synaptic and search for "unrar". Make sure you have the *unrar* package installed, not *unrar-free.* Try it in Nautilus by double-clicking the *.rar file. No luck?

Yep, I'm extracting the .rar file, not one of the .r0* files. And I can double-click on the .rar and see the .avi just fine. It's got no problem accessing the .rar file, only extracting the file within it. And yep, I also have unrar, not unrar-free. However, I also installed rar, according to the suggestion of the following site:

[http://techiegeeks.com/?p=78](http://techiegeeks.com/?p=78)

Do you think it's conflicting with unrar?

---

### Post by MissingHorcrux on 2008-02-24
> **justleen said:**
> from usenet by any chance?

par check with 
```

sudo apt-get install par2
par2repair <parfile.par2*>
unrar -e <files.rar / r*>

```

Usenet? No idea. Also, I got the install par2 working correctly, however you'll have to be more specific with what to type on that second command. (Be gentle with me, it's only my third day of Linux. :P)

---

### Post by mivo on 2008-02-24
Well, there is the possibility that the file you have is damaged. I extract movie files in split rar archives quite often (always find it annoying ;)), so it really should work. If this is the only file you have tried, and problems with, it might just be a corrupted file.

Not sure if there may be conflicts. I don't think it's likely, though everything is possible. I'd probably uninstall the "other stuff", since you really only need the *unrar* and *rar* packages from the repository. :)

---

### Post by MissingHorcrux on 2008-02-24
> **mivo said:**
> Well, there is the possibility that the file you have is damaged. I extract movie files in split rar archives quite often (always find it annoying ;)), so it really should work. If this is the only file you have tried, and problems with, it might just be a corrupted file.

Not sure if there may be conflicts. I don't think it's likely, though everything is possible. I'd probably uninstall the "other stuff", since you really only need the *unrar* and *rar* packages from the repository. :)

That could be a possibility. Though I've tried it with two sets of split .rars, they're both from the same author, so that could be what I'm running into. Everything else in Ubuntu works just fine, as far as I know, so I might try again later with a different author's set. 

Thanks for your help, mivo. :) If you think of anything else, feel free to message me!

---

### Post by mivo on 2008-02-24
I think the next step is to verify whether the files you have are corrupted or if it's an installation/software problem. I dropped you a private message to follow up on this. :)

---

### Post by kaiju on 2008-03-01
> **MissingHorcrux said:**
> ...I'm still left with a rather odd problem: it will extract the file from one of the .r0* files, then prompt for my password, delete the file, and begin extracting all over again. It seems stuck in an extracting loop.

are you sure your password is right?
i've seen similar behavior when trying to extract passworded rar files using the wrong password.
e.g. when extracting a directory with multiple files you can see the individual files being created and then erased one at a time.

---

### Post by sharris203 on 2008-03-01
Here's what works for me. 1. Installed the unrar through apt-get. 2. Installed Gpar2 through Add/Remove Programs

I can right click on ANY of the .r0* files and choose Extract Here, and it will extract it. HOWEVER, if any of the files is damaged, it will quit/get error saying that a password is required. Then I have to repair the files with Gpar2, THEN it will extract just fine. Applicable only if you have par2 files... But if you got it off Bittorrent, it may be that there are files that are corrupted, and without par2 files you can't repair them.

---

