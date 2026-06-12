---
title: "Successful Beryl install with ATI 256Mb Radeon X1300?"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by frotzed on 2007-03-11
I'm just curious about this one.  After getting my new Dell Dimension E520 computer and installing Edgy on it I found I needed to install the fglrx video card drivers for my ATI Radeon X1300 graphics card to get 3D acceleration working.  Then, I tried to install Beryl with XGL (even tried that automated script thing) and while Beryl installs well, and even the Beryl Manager shows up in my taskbar, when I go to switch to the Beryl window manager it visibly TRIES to run Beryl but for some reason it can't and then it goes back to Metacity.

Has anyone actually succeeded in running Beryl on this particular setup?  If so, I'd love to know how you did it.

---

### Post by Franco84 on 2007-03-11
I have a Dell Dimension E520 and decided to install Ubuntu 6.10 and Beryl this weekend. I also have the X1300. I used the wiki guide and got the drivers working, as well as Beryl installed. I can keep it in Beryl mode without it crashing, but none of the effects are working. If I hit CTRL+ALT+LEFT or RIGHT something pops up like ALT+TAB in windows. Not really much of a cube effect :-) Was there anything else I was supposed to do? I'm a noob when it comes to Linux, but I'm glad common sense got me this far.

---

### Post by freebird54 on 2007-03-11
I have Beryl working surprisingly well here - so it should be possible there.

Try double-checking that Xgl is REALLY working right, by running fglrxinfo.  It should have no complaints about Xfree.... missing, and it should NOT have any reference to mesa in it.

should also be able to run fgl_glxgears without a problem.


As for getting the effects sorted out - I suggest you go to the Desktop Environment forum - anyone who gets Beryl working is not an Absolute Beginner anymore!  (I found someone there who happily posted a list of suggested settings to get me started - confusing otherwise!)  To start you off, try holding <CTRL><ALT> and dragging with the left mouse button....


Good luck to you all

---

### Post by black_ice on 2007-03-11
so how can i customize  Beryl to get the best performance of graphics  ?

---

### Post by Tobster on 2007-03-11
To be honest this is something I gave up on but I think it will be included in the next Ubuntu upgrade which is happening in April.

Toby

---

### Post by frotzed on 2007-03-11
> **freebird54 said:**
> Try double-checking that Xgl is REALLY working right, by running fglrxinfo.  It should have no complaints about Xfree.... missing, and it should NOT have any reference to mesa in it.  should also be able to run fgl_glxgears without a problem.

Right.  Before I install Beryl fglrxinfo gives back perfect results and fgl_glxgears works fine too.  But then after I install Beryl fglrxinfo throws the exact error you pointed to and fgl_glxgears doesn't load due to the same error.

What wiki, exactly, did you follow?  link please.  I just want to be sure that I'm following the correct directions.

---

### Post by Franco84 on 2007-03-11
After I installed the ATI Drivers FGLRXINFO didn't have Mesa anymore but after I installed Beryl I never checked. I checked just now and it says Mesa again.  Me and Frozted are having the same exact problem

---

### Post by frotzed on 2007-03-11
> **Tobster said:**
> To be honest this is something I gave up on but I think it will be included in the next Ubuntu upgrade which is happening in April.

Toby

I'm not sure that's accurate.  [Mark seems to indicate]("http://www.markshuttleworth.com/archives/95") that it will definitely not be included in Feisty.

---

### Post by frotzed on 2007-03-11
> **Franco84 said:**
> After I installed the ATI Drivers FGLRXINFO didn't have Mesa anymore but after I installed Beryl I never checked. I checked just now and it says Mesa again.  Me and Frozted are having the same exact problem

I know that I had to jump through some hoops just to get 3D acceleration working on my Radeon X1300 card and there are a lot of others who had the same problem.  I'm just wondering if Beryl is simply incompatible with the Radeon X1300 card?  No biggie if it is incompatible, it's still pre-Beta software.  But I'd just like to know if there is someone who did get it working with this specific graphics card and then to know how they did it because Beryl is freakin' awesome!  I've installed it on two other boxes, both using Nvidia cards and I'm half tempted to spring for a new graphics card just so I can use Beryl.  IMHO it would be well worth it.

---

### Post by freebird54 on 2007-03-11
A couple of things:

1.  when you are NOT in Xgl - the fglrxinfo must work, no XFree or Dri missing errors showing.
2. when you are NOT in Xgl - the fgl_glxgears should run beautifully
3. when you ARE in Xgl - BOTH will appear to having a problem - but it doesn't matter by then (strange - but that's what happens on my machine)

This is the link I (mostly) used to get going - read it first, then step by step it :)

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL)

Once you are to the desktop, just select Beryl Manager from the Application->System Tools-> Beryl Manager

If you go to white screen - you need to add an entry to the blacklist so that conflicting modules are disallowed:

Code:
```
gksudo gedit /etc/modprobe.d/blacklist
```

and paste the following into the file

Code:
```
# causes fglrx to fail and mesa drivers to load
blacklist ati-agp
```


If it just goes back to Metacity - try setting Rendering path to Copy mode by right-clicking the Diamond, and selecting Advanced Beryl Options->Rendering path

This is slower, but works.

Final point - this thread is in the wrong place - the sticky at the top says NOT HERE! :)   Please go to Desktop Environment - there you can find some people who know a ________ lot more about Beryl than I do - I just run it when I don't need the programs that it breaks...

Good luck - and enjoy.

---

