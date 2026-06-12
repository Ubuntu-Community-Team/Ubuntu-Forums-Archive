---
title: "DirectX"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-07-02
yes, i found it possible to install DirectX in Ubuntu.

[www.softpedia.com](www.softpedia.com)

however i go through the installation process, its all fine untill..the 'Make Depend' stage.

this is the whole output from my Terminal.

```

WineCVS.sh - Progress(u) : Green is current

   0 = Uninstall
   1 = Cleanup
   2 = CVS checkout
   3 = Configure
   4 = Make depend
   5 = Make
   6 = Make install
   7 = Finish up

-------------------------------------------

Configuring ...


    TIP: If you have a WineX related problem you can check the
    forums on http://www.transgaming.org/
--------- Error log - file /home/scott/.WineCVS/sources/dx9wine/ErrorLog : ---------each game.
20 out of 21 hunks FAILED -- saving rejects to file dlls/wined3d/directx.c.rej
patching file dlls/wined3d/drawprim.c
Hunk #1 FAILED at 1725.
Hunk #2 FAILED at 1784.
Hunk #3 FAILED at 1966.
3 out of 3 hunks FAILED -- saving rejects to file dlls/wined3d/drawprim.c.rej
patching file dlls/wined3d/stateblock.c
Hunk #1 FAILED at 64.
Hunk #2 FAILED at 379.
Hunk #3 FAILED at 402.
3 out of 3 hunks FAILED -- saving rejects to file dlls/wined3d/stateblock.c.rej
patching file dlls/wined3d/surface.c
Hunk #1 FAILED at 202.
Hunk #2 FAILED at 897.
2 out of 2 hunks FAILED -- saving rejects to file dlls/wined3d/surface.c.rej
patching file dlls/wined3d/swapchain.c
Hunk #1 succeeded at 52 with fuzz 2 (offset -1 lines).
Hunk #2 FAILED at 110.
Hunk #3 FAILED at 133.
Hunk #4 FAILED at 253.
Hunk #5 FAILED at 461.
4 out of 5 hunks FAILED -- saving rejects to file dlls/wined3d/swapchain.c.rej
patching file dlls/wined3d/utils.c
Reversed (or previously applied) patch detected!  Assume -R? [n] 
Apply anyway? [n] 
Skipping patch.
4 out of 4 hunks ignored -- saving rejects to file dlls/wined3d/utils.c.rej
patching file dlls/wined3d/wined3d_private.h
Hunk #1 FAILED at 231.
Hunk #2 FAILED at 541.
Hunk #3 FAILED at 884.
Hunk #4 FAILED at 918.
Hunk #5 FAILED at 1147.
Hunk #6 FAILED at 1169.
6 out of 6 hunks FAILED -- saving rejects to file dlls/wined3d/wined3d_private.h.rej
patching file include/wine/wined3d_interface.h
Hunk #1 FAILED at 282.
Hunk #2 FAILED at 383.
Hunk #3 FAILED at 413.
Hunk #4 FAILED at 514.
Hunk #5 FAILED at 1256.
Hunk #6 FAILED at 1278.
6 out of 6 hunks FAILED -- saving rejects to file include/wine/wined3d_interface.h.rej
patching file include/wine/wined3d_types.h
Hunk #1 FAILED at 427.
1 out of 1 hunk FAILED -- saving rejects to file include/wine/wined3d_types.h.rej

Patching FAILED
Try running the script with refresh:
WineCVS.sh refresh


Error in Configure

Try fixing the error based on the output above, and
run the script again, without paramaters (Eg: WineCVS.sh)

```

most likely it tells me whats wrong, but im oblivious to the most obvious.

the package is Wine CVS.sh

thanks!

---

### Post by Cypher on 2007-07-02
Looks like you have a broken package there. It is trying to apply some patches to the code base and having issues probably because the source and the patches from which they were were derived are no longer in sync and/our out-of-date.

Also, seeing things like "Reversed (or previously applied) patch detected!" is another indication of out of sync patches. Make sure you've gotten the latest version of the package..

Also, provide a direct link to the package so that others may try it out and provide some guidance..

---

### Post by skymera on 2007-07-02
ok i redownload the package and post the link...first look for it

[http://linux.softpedia.com/get/System/Emulators/DirectX-support-for-Wine-19484.shtml](http://linux.softpedia.com/get/System/Emulators/DirectX-support-for-Wine-19484.shtml)

found it.

---

### Post by cogadh on 2007-07-02
That's not DirectX, that's the old WineX CVS (now called Cedega) from two years ago. There is better DirectX support in the current version of Wine already.

---

### Post by skymera on 2007-07-02
it has DirectX.
u select it...

and if it already has it, can i play games that depend on directx?

---

### Post by cogadh on 2007-07-02
Most games that depend on DX can be played, but it really depends on the game. You should search Wine's AppDB for the particular game you want to play to see if it is tested and working:
[http://appdb.winehq.org/](http://appdb.winehq.org/)

---

