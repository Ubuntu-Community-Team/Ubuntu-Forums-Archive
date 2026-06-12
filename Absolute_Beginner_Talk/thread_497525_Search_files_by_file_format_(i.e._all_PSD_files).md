---
title: "Search files by file format (i.e. all PSD files)?"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by trishacupra on 2007-07-10
Hi,

I can't find a PSD file I created for the life of me, and I've forgotten what I named it. Duh. This is rare for me, so I don't know how to dig it up successfully in Ubuntu.

It's important and I tried using Beagle to find it, with no luck. I need to search several partitions.

All I know is that it's a Photoshop file (.psd). Can I somehow search multiple partitions and get a list of all the PSD files there are in my filesystem?

Thanks!

---

### Post by Nekiruhs on 2007-07-10
Yep. You can. Just run ```
slocate -u
``` in a terminal and wait while it indexes (Should take less that a few minutes) then run ```
locate .psd
```

---

### Post by trishacupra on 2007-07-11
Okay, I must have some newbie knowledge gaps.

Here's how it went...

```
trisha@trisha-laptop:~$ slocate -u
slocate: fatal error: You are not authorized to create a default slocate database!
```

Okay, so I figured I should try doing that as root...

```
trisha@trisha-laptop:~$ sudo slocate -u
Password:
trisha@trisha-laptop:~$ locate .psd
/Recycled/Du9.psd
/Recycled/Du7.psd
/Recycled/Du6.psd
trisha@trisha-laptop:~$ 
```

That only showed up PSD files in my Trash. Should I be doing some kind of command to make it search the entire filesystem including all my partitions?

---

### Post by kvonb on 2007-07-11
put sudo in front of that:

sudo slocate -u

If that fails, try this one from a terminal:

cd /
find . -name '*.pdf'

Or use the desktop search tool, but put simply

pdf

as the search criteria, no dot.  (took me ages to figure that out!)

---

### Post by Nekiruhs on 2007-07-11
Woops. Sorry 'bout the root thing, forgot about that. Hmm. locate .psd should have done it. Hmm. try find. command is 
```
sudo -i
```
^ Fixes errors about permissions, sudo by itself wouldn't fix. basically its a safer sudo su
```
find / -iname *psd
```

---

