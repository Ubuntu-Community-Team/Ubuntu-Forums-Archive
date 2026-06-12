---
title: "Wine DirectX patch?"
date: 2006-05-28
forum: Absolute Beginner Talk
---

### Post by aktiwers on 2006-05-28
I just downloaded this Wine Patch:
[http://sourceforge.net/project/showfiles.php?group_id=134206](http://sourceforge.net/project/showfiles.php?group_id=134206)

But I have no idea how to install/patch it to wine?

I have Wine Installed allready.

This is the filename:
d3d8-wrap-wined3d-beta-os-1.patch

Anyone know how to do this?

Thanks a lot.

---

### Post by qamelian on 2006-05-28
The homepage recommends using a script found here:
[http://winecvs.linux-gamers.net/index.php/Main_Page](http://winecvs.linux-gamers.net/index.php/Main_Page)

Good luck!

---

### Post by aktiwers on 2006-05-28
Thanks for your reply!

I downloaded and used the script. It seams pretty good :)

But After picking the right thing I want to install, and getting ready to install it, I get this error:

> ===============================================================================

Profile menu

Here you can download new profiles, upgrade existing
or run existing


  g) Get a profile from [http://winecvs.linux-gamers.net/WineCVS]("http://winecvs.linux-gamers.net/WineCVS")
  c) Change command line action
  r) Run existing profile


=================WineCVS helpsystem (q will quit, b go back)=================

 Make your choice:
r








===============================================================================

List of profiles (b to go back):

0 ) dx9wine
Enter choice:
0


Running Profile : dx9wine
/home/aktiwers/.WineCVS/sources/dx9wine/wine













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

Checking out CVS ... May take a while




--------- Error log - file /home/aktiwers/.WineCVS/sources/dx9wine/ErrorLog : ---------
/home/aktiwers/.WineCVS/Functions/RunWineCVS: line 736: cvs: command not found


Error in CVS checkout

Try fixing the error based on the output above, and
run the script again, without paramaters (Eg: WineCVS.sh)


aktiwers@ubuntu:~/Mozilla Downloads$
 
Is there an error in the code?

This is what line 736 says:

```

# Get new version
            echo "Checking out CVS ... May take a while"
            test -e ~/.cvspass || touch ~/.cvspass
    
            i="0"
            while test "$i" -lt "20"
            do
                i=$[$i+1]
    
                TipsNInfoStart
                [COLOR=Red]**if cvs -d $CVSroot $CVSoptions $CVSmode $CVSCheckOutDir** >"$ErrorLogFile" 2>&1[/COLOR]
                then
                    TipsNInfoStop
                    DoneOK="1"
                    State="3"
                    i="9999"
                else
                    TipsNInfoStop

``` 


Sorry for all the quotes..  Hope someone can help me.

Thanks a lot for reading.

---

### Post by qamelian on 2006-05-29
Do you actually have cvs installed? From a terminal, type:

sudo apt-get install cvs

and enter your password when prompted. This should install the cvs components necessary for working with cvs repositories.

---

### Post by YokoZar on 2006-05-30
Just install the latest Wine (0.9.14) -- all this stuff is already included.

---

### Post by shannon.cummins on 2006-09-20
I have wine 0.9.21 and running GW does not work.  It looks for the DirectX and cannot find it.  I have made it as far as above but now I get this error

```
===============================================================================

Profile menu

Here you can download new profiles, upgrade existing
or run existing


  g) Get a profile from http://winecvs.linux-gamers.net/WineCVS
  c) Change command line action
  r) Run existing profile


=================WineCVS helpsystem (q will quit, b go back)=================

 Make your choice:








===============================================================================

List of profiles (b to go back):

0 ) cvscedega_head_old
1 ) dx9wine
Enter choice:
1


Running Profile : dx9wine
/root/.WineCVS/sources/dx9wine/wine
:pserver:cvs@cvs.winehq.com:/home/wine











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


    TIP: For a list of games working in WineX, go to this site:
    http://www.transgaming.com/searchgame.php
--------- Error log - file /root/.WineCVS/sources/dx9wine/ErrorLog : ---------
21 out of 21 hunks ignored -- saving rejects to file dlls/wined3d/directx.c.rej
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
Hunk #1 succeeded at 49 with fuzz 2 (offset -4 lines).
Hunk #2 FAILED at 107.
Hunk #3 FAILED at 130.
Hunk #4 FAILED at 250.
Hunk #5 FAILED at 458.
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
6 out of 6 hunks FAILED -- saving rejects to file dlls/wined3d/wined3d_private.h .rej
patching file include/wine/wined3d_interface.h
Hunk #1 FAILED at 282.
Hunk #2 FAILED at 383.
Hunk #3 FAILED at 413.
Hunk #4 FAILED at 514.
Hunk #5 FAILED at 1256.
Hunk #6 FAILED at 1278.
6 out of 6 hunks FAILED -- saving rejects to file include/wine/wined3d_interface .h.rej
patching file include/wine/wined3d_types.h
Hunk #1 FAILED at 427.
1 out of 1 hunk FAILED -- saving rejects to file include/wine/wined3d_types.h.re j

Patching FAILED
Try running the script with refresh:
WineCVS.sh refresh


Error in Configure

Try fixing the error based on the output above, and
run the script again, without paramaters (Eg: WineCVS.sh)

```

What's the deal??

---

