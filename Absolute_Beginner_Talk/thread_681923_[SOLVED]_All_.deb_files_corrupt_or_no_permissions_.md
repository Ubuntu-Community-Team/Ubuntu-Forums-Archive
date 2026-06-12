---
title: "[SOLVED] All .deb files corrupt or no permissions? Something wrong"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by mut80r on 2008-01-29
Ok so I'm not a total newbie, but I figure this is probably a stupid question.

I installed Ubuntu 7.04 Feisty today and have everything setup the way I want (I have used
Ubuntu 6.something before).

A section of my harddisk is encrypted with a program known as TrueCrypt (some of you may
have heard of it). There is a .deb available for Ubuntu 7.04 users, so I downloaded it.

double clicked it, popped up, listed it's purpose and author and everything so I was like "ok, 
install"... I accidentally closed file-roller while it was installing, so the .deb got deleted (it came in
a .tar.gz)

So I download, extract, THEN double clicked. now it said "There may only be one running
copy of the package manager" or something. Restarted, same error. Weird? Yes. Googled, and it told me to run

```
sudo dpkg --configure -a
```

So I did. And now I don't get that error :)

But now I can't open ANY .deb files...

it pops up, looks like it's doing something, and then regardless of the .deb file I get this

```
Could not open '<filename>.deb'
The package might be corrupted or you are not allowed to open the file: please check the permissions of the file.
```

and I've tried 

```
sudo dpkg -i <filename>.deb
```

I get the same thing in the console.

By this time I'm annoyed -.-

I check the permissions, says I have read/write.

I downloaded it several times, even cleared my browser cache and restarted again. Nothing.

Anyone help please?

I know how to browse the local filesystems and use the terminal and/or text editing, etc, dont worry.

Thanks in advance,

Aaron.

---

### Post by y-lee on 2008-01-29
> I check the permissions, says I have read/write.

It sound like ya might need execute permissions. try that :confused:

---

### Post by mut80r on 2008-01-29
> **y-lee said:**
> It sound like ya might need execute permissions. try that :confused:

Just tried it, didn't work.
Sounded like a good suggestion though =/

---

### Post by mut80r on 2008-01-29
Hmm. Fixed itself after another reboot and a

```
sudo apt-get clean
```

even though truecrypt wasn't in the list of deleted files...

consider this resolved

---

