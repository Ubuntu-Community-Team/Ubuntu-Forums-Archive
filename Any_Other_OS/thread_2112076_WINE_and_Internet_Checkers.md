---
title: "WINE and Internet Checkers?"
date: 2013-02-03
forum: Any Other OS
---

### Post by jamesaepp on 2013-02-03
[ZORIN OS 6.1 64-bit]

So I copied over the internet checkers files from a working windows 7 machine. (This is the files in C:\Program Files\Microsoft Games\Multiplayer\Checkers\ )
    These files include an exe, a couple dlls and inside a sub-folder "en-US" there is two .dll.mui files.

I cannot load these in wine. It appears as if a shell comes up, and instantly closes. Looks like a direct X issue, but I'm not sure.

Anyone have a solution?

(No, I'm not interested in an alternative program. This is for my father and he likes his Internet Checkers)

---

### Post by squakie on 2013-02-03
Open a terminal window and then:

wine "C:\Program Files\Microsoft Games\Multiplayer\Checkers\<put exe file name here>"   <press enter>

Also, be sure it doesn't need an active internet connection.  If so, I'm sure how to go about setting up network access in wine.  I do know that if you have a USB network adapter you won't be able to use it as wine doesn't support USB (at least it hasn't in the past except for "inherited devices" like the keyboard and mouse).

If it's having problems the error messages should now show on the terminal.  If you can't figure it out from those, post them back here.

---

### Post by oldos2er on 2013-02-03
Moved to Other OS/Distro Talk.

---

### Post by jamesaepp on 2013-02-03
after doing:

```
wine '/home/user/.wine/dosdevices/c:/Program Files/Checkers/chkrzm.exe'
```

I get this output:

```
winevdm: Cannot start DOS application C:\Program Files\Checkers\chkrzm.exe
      because the DOS memory range is unavailable.
      Try running this application with DOSBox.
```


It IS a windows 7 program. As for networking with Wine, I am not sure how to do so, and a google search didn't return anything particularly useful.

---

### Post by squakie on 2013-02-04
Try wine config and see if there is even a way to set it up as Windows 7.  It does say to use dosbox, and it is in the repositories, but the description shows Windows XP and if I remember correctly Windows 2000 and Mac.  Nothing there for Windows 7.  You can always try installing it and see if it works, but I don't think I'd keep my fingers crossed.

Another option might be to use VirtualBox and create a virtual machine (like a logical PC, not an actual physical one) and load in the version of Windows the program will run in.  If you go with a virtual machine you can also set the network adapter to NAT in the virtual machine settings and it will automatically use your adapter.

---

### Post by Mark Phelps on 2013-02-04
There's no rating for this checkers game in the WineHQ database and the only other checkers game there is rated Garbage.  Most likely, this is not going to work.

---

### Post by squakie on 2013-02-04
thanks Mark - I suspected it wasn't going to work but forgot to check the list.

---

