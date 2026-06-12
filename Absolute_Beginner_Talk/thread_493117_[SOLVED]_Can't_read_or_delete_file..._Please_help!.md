---
title: "[SOLVED] Can't read or delete file... Please help!"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by sab0403 on 2007-07-05
Ok, here it is. I reinstalled Ubuntu last night (it had some major problems with Songbird, which affected Nautilus... long story). First, though, I copied my XP Virtual Machine to my NTFS partition (which I can write to thanks to ntfs-3g), and I exported my bookmarks. So when I reinstalled, I tried to access my bookmarks, but it reported an "Input/Output error". Ok, no biggie, I had a backup. But then I searched for the VM... and it was nowhere to be found. I finally found what was supposed to be a 17.2 GB folder, but Ubuntu reports it's a 0 bytes file without extension (simply named XPPro, as the folder was).

The problem is that this file/folder IS taking up a whole lot of space (I had 23.5 GB free before copying the VM, the drive now reports 8.2 GB free), and I want to delete it. However I can't! When I do <Shift>+Delete in Nautilus, it acts like it's going to erase it (it asks me if I'm sure), but then it does nothing. When I go to the terminal, rm (even with sudo) reports:

```
rm: cannot remove `XPPRo': Input/output error
```

and the same happens with that bookmarks.html file, btw.

I found [this thread]("http://forums.gentoo.org/viewtopic-t-567137.html?sid=fbc59e4c0cb42430ff5cbc7aaa506739") while googling for the problem, and the same problem appears to have been solved by using a tool called dosfsck. However this tool only works with FAT/FAT32 partitions; mine is NTFS. Is there a similar tool for these partitions? Last resort seems to be reformat, but I have over 40 GB of data in that partition and I have no easy means to back it up (even DVDs, which I don't have at hand right now, are cumbersome for that amount of data).

Please help!

---

### Post by sab0403 on 2007-07-05
no one has any idea?

---

### Post by sab0403 on 2007-07-05
Ok... one last bump...

---

### Post by rodo-&gt;dave on 2007-07-05
I read that 'rm' does a stat() first.  I wonder if the stat is failing and the rm does not finish it.

you could write a little c app to do an 'unlink' 

int main(int argc, char **argv)
{
  unlink(argv[1]);            // argv[1] is the file name you want to remove 
  return(0);
}

don't know if it will work but it's worth a shot.

---

### Post by sab0403 on 2007-07-05
Thanks, but I run into trouble just trying to run the program... sintax error...

:(

---

### Post by rodo-&gt;dave on 2007-07-05
**[COLOR="Red"]Note: this will delete the file passed on the cli[/COLOR]**

Copy this code into your favorite editor

```

#include <stdio.h>

int main(int argc, char **argv)
{
	if (argc < 2) {
		printf("usage: %s file_to_remove\n", argv[0]);
		printf("ie. %s XX\n");
		printf("\twould remove the file 'XX'\n");
		return(-1);

	}
	unlink(argv[1]);
	return(0);
}

```

save it as xx.c
on the cli type: make xx

cd to the directory where your file is

on the cli type: xx file_to_remove

and see what happens :)

**[COLOR="Red"]Note: this will delete the file passed on the cli[/COLOR]**

---

### Post by sab0403 on 2007-07-05
Silly me. I forgot to compile...

Anyway, it apparently did the unlink, but no luck. rm still returns the same error.

:(

---

### Post by sab0403 on 2007-07-05
> **rodo->dave said:**
> **[COLOR="Red"]Note: this will delete the file passed on the cli[/COLOR]**

Copy this code into your favorite editor

```

#include <stdio.h>

int main(int argc, char **argv)
{
	if (argc < 2) {
		printf("usage: %s file_to_remove\n", argv[0]);
		printf("ie. %s XX\n");
		printf("\twould remove the file 'XX'\n");
		return(-1);

	}
	unlink(argv[1]);
	return(0);
}

```

save it as xx.c
on the cli type: make xx

cd to the directory where your file is

on the cli type: xx file_to_remove

and see what happens :)

**[COLOR="Red"]Note: this will delete the file passed on the cli[/COLOR]**

I'll try this. Thanks.

---

### Post by sab0403 on 2007-07-05
Same program. :P

Well, neither one did the trick... it does the unlink (apparently) but it doesn't erase the file (or would-be folder, whatever).

I'm guessing format is the only choice. :( Thanks for the help...

---

### Post by sab0403 on 2007-07-10
I finally had to format. Oh well... marking it as solved anyway...

---

