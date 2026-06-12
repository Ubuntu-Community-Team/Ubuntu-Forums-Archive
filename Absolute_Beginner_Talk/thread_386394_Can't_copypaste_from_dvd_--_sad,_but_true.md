---
title: "Can't copy/paste from dvd -- sad, but true"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by vicG on 2007-03-16
So I stick a data dvd that I burned under Windows into the dvd drive.  It's just data and code -- I've copied stuff from it on other boxes a few times, so I know things work.

On Ubuntu, a gnome folder browser automatically pops up, so it would seem to make sense that I could select all -> copy and then in another gnome folder-browser window, paste, right?  Apparently not.

It will only copy/paste the top-level folders, not the contents (using the gnome gui folder browser), and it puts a little lock icon on them, so I have to edit the permissions just to delete these empty folders.  

So I go to the terminal, cd to the same directory indicated in the gnome folder browser that popped up, and try cp -R.  Cannot stat, permission denieds on all the folders.

Tried the same thing from a root terminal.  Same result.  Can someone explain how root doesn't have permission?  Whatever.

Something this basic should not require help, but here I am.. I read the docs, and there are no instructions for copying and pasting, so I assume it should work in the normal way, yet it does not.  Maybe my installation is hosed?

Thanks for any help ending this nightmare :)

---

### Post by STREETURCHINE on 2007-03-17
i have done this many times and it works in edgy and dapper,unfortunatly i dont know how to fix your problem but you could open root nautilus
type into terminal

```
gksudo nautilus
```

it will open nautilus with root pemissions try to drag the files to there and copy them from there to your computer.

it is all i have to offer sorry

---

### Post by vicG on 2007-03-17
Thanks for the suggestion, but I guess it just can't be done for some reason:

```
** Message: Hit unexpected error "I/O error" while doing a file operation.
** Message: Hit unexpected error "I/O error" while doing a file operation.
```

Sat on "Preparing to copy" for about 5 minutes (for a lousy 300 meg cd!), then tried for about 30 seconds (could hear the disc spinning), then the error messages -- on the very first folder,  no less.

---

### Post by vicG on 2007-03-17
Here's the screenshot:

---

