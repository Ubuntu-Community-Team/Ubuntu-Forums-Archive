---
title: "tried to move directory with mv command"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by DrewB on 2007-01-15
Hello,
I'm new to Linux and running Ubuntu 6.10 on an AMD64 laptop.
I tried to move a directory to the /tmp directory using the mv command, i.e:
mv apb_dir /tmp
However I have mow realised that this was probably the wrong as the apb_dir has completely disappeared and I'm worried that I may have corrupted the /tmp directory in some way (though it doesn't look it.)
Can anyone tell me what happened to the apb_dir directory and how to get it back?
Thanks a lot.
Drew

---

### Post by misterpms on 2007-01-15
Hmm, it should be in the /tmp directory: /tmp/apb_dir

You can always use the find command to search for the directory
```
sudo find / -name apb_dir
```

---

### Post by rccharles on 2007-01-15
> **DrewB said:**
> Hello,
I'm new to Linux and running Ubuntu 6.10 on an AMD64 laptop.
I tried to move a directory to the /tmp directory using the mv command, i.e:
mv apb_dir /tmp


/tmp stands for temporary

"The /tmp directory is cleaned of stale files each day by the tmpwatch command.  A stale file is any file not used after 10 days."  Ubuntu Unleased.


From my limited testing, the mv command didn't appear to change the dates on the file when moved.

I used these two commands to show the dates:
ls -lT
ls -luT

Robert

---

### Post by DrewB on 2007-01-16
Hi thanks for your replies, the directory disappeared as soon as I executed the command and didn't appear in the /tmp directory. I tried searching for it from the root directory using find but to no avail. It just seems to have been erased from the disk.

---

### Post by akiro.yamamoto on 2007-01-16
To move or copy a directory I think you have to use the -R switch.
For example

mv -R /home/user/Images /home/user/archive/

I think -R is for recursive...
Hope this helps.....

---

### Post by RedSquirrel on 2007-01-16
> **DrewB said:**
> Hi thanks for your replies, the directory disappeared as soon as I executed the command and didn't appear in the /tmp directory. I tried searching for it from the root directory using find but to no avail. It just seems to have been erased from the disk.

I apologize in advance if I'm being too obvious here, but... I just thought I'd ask to cover this case:

Are you sure you typed:

```

mv apb_dir /tmp

```or is it possible that you did:

```

mv apb_dir tmp

```The latter would **rename** your "apb_dir" to "tmp" 

The reason I ask is that I find it odd that 'find' didn't find your directory at all, which means it's gone (or renamed...) ... 

(I just used the word "find" three times in that sentence. Yikes.)

---

### Post by RedSquirrel on 2007-01-16
> **akiro.yamamoto said:**
> To move or copy a directory I think you have to use the -R switch.
For example

mv -R /home/user/Images /home/user/archive/

I think -R is for recursive...
Hope this helps.....


Actually, -r or -R is not an option for the mv command.

If both *source* and *target* are existing directories, you can just do:

```

mv *source* *target*

```which results in *source* becoming a subdirectory of *target*.

If *target* doesn't exist, then *source* gets renamed to *target*.

---

### Post by rccharles on 2007-01-16
> **DrewB said:**
> Hi thanks for your replies, the directory disappeared as soon as I executed the command and didn't appear in the /tmp directory. I tried searching for it from the root directory using find but to no avail. It just seems to have been erased from the disk.

You could try the history command:
history

It will list what commands you issued.  While the history command lists commands from prior logons, you will have to be in the same logon session. The actual file the commands are saved in is: 
.bash_history


Robert

---

