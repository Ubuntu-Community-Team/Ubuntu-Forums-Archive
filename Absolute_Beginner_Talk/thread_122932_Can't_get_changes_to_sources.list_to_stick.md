---
title: "Can't get changes to sources.list to stick"
date: 2006-01-28
forum: Absolute Beginner Talk
---

### Post by griz on 2006-01-28
Hi all,
I was having trouble with sources being ignored and not available so followed directions from here [http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php) .
I changed the sources list using kwrite and, when I tried to use Automatix, it reverted to the previous file.  Tried saving the new file to a different name, deleting the original sources.list and then cp new file to that name.  Again, file reverted to original.  Anyone else had this problem? Or am I doing somethin wrong?

Griz.

---

### Post by Who on 2006-01-28
I think the key is in
> when I tried to use Automatix

This program has it's own idea about what a sources.list should be (this is necessary because it uses dpkg/apt to install a lot of it's software) and in my experience isn't very diligent about putting your system back to the way it was. It DOES however make a backup in the format sources.list_backup[date]

So you could just restore that.

I think i understood you correctly, but I have some doubt - so please tell me if I'm wrong

---

### Post by griz on 2006-01-28
Thanks Who,
I thought I was going a bit crazy for a while.  I'd change the file and then it would revert to a previous one with missing mirrors.  I was just abou to call the men in white coats :p Anyway, thanks for clearing that up.  I suppose I won't be able to use Automatix if I want to keep a decent sources.list then.  Oh well, at least there's always more than one way to do things in Ubuntu.

Griz.

---

### Post by Who on 2006-01-29
Isn't automatox the type of tool you only need to use once?

I used EasyBreezy on my brothers' PC instead, and it seems to have done a fairly good job (though I did have to write my own sources.list back afterwards....)

---

