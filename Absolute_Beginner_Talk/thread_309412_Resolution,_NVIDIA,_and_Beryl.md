---
title: "Resolution, NVIDIA, and Beryl"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by Hexydes on 2006-11-29
Hey all, long time Linux dabbler, but it has been a while. :)

This is my first time trying Ubuntu. The last distro I tried was....probably Lindows (before the name change) about 3 years ago, before, maybe Mandrake.

On to my questions. I got Ubuntu installed fine, looks really nice! Glad to see how much more usable at least the install and initial experience have come since my last try at Linux. I have an NVIDIA GeForce 6600, and am looking to get Beryl up and running, but first things first. I read that you need to install the latest NVIDIA beta drivers to get Beryl going. I did that (I'm using a Sempron 64 btw, if that makes a difference). When I restart X, I get the Nvidia splash screen for a second, and then get back to the desktop without any trouble. However, I still only have 640, 800, and 1024 as available resolutions. I have an extremely large/wide monitor, and need to use a higher resolution (I forget what it is off-hand, but in Windows I think it is 1920 x 1200 or something similar). How can I get this as an available resolution to use? Do I have to manually edit the....I think it was x86-config file (did I remember that right?), or is there a better/easier/faster way? If I have to edit it, how do I do that (I briefly tried with a text editor, but I can't save it since I'm not logged in as root).

Next question, assuming I can get all that going, what is the best/easiest/fastest way to get Beryl installed (the thing with all the neat effects that is floating around Digg/YouTube)? I've read some walkthough's, but they all seem pretty long and complicated. I'm going to try one when I get home, but what would be the easiest and most sure-fire method of getting it going (again, NVIDIA GeForce 6600 with latest drivers, AMD Sempron 64)?

Finally, I have a Creative Labs Live! sound card, but my sound isn't working. Is this maybe because Ubuntu didn't have a driver that works with the 64-bit version of the distro? Something else maybe? Any thoughts on how to get my sound up and running?

Other than that, Ubuntu looks very slick! I'm pretty impressed!

Thanks a lot in advance!

---

### Post by Hexydes on 2006-11-29
Oh, and P.S. if you need any more information (hardware, etc) just let me know and I'll dig it up when I get home. :)

---

### Post by Hexydes on 2006-11-29
Argh, sorry, spamming for membership here. :)

I saw this in two other posts:

```

sudo dpkg-reconfigure xserver-xorg

```

Would that let me choose some resolutions to use?

---

### Post by Rodneyck on 2006-11-29
> **Hexydes said:**
> 

On to my questions. I got Ubuntu installed fine, looks really nice! Glad to see how much more usable at least the install and initial experience have come since my last try at Linux. I have an NVIDIA GeForce 6600, and am looking to get Beryl up and running, but first things first. I read that you need to install the latest NVIDIA beta drivers to get Beryl going. I did that (I'm using a Sempron 64 btw, if that makes a difference). When I restart X, I get the Nvidia splash screen for a second, and then get back to the desktop without any trouble. However, I still only have 640, 800, and 1024 as available resolutions. I have an extremely large/wide monitor, and need to use a higher resolution (I forget what it is off-hand, but in Windows I think it is 1920 x 1200 or something similar). How can I get this as an available resolution to use? Do I have to manually edit the....I think it was x86-config file (did I remember that right?), or is there a better/easier/faster way? If I have to edit it, how do I do that (I briefly tried with a text editor, but I can't save it since I'm not logged in as root).

You can do either of two things. You should be able to see the nvidia settings manager in "system tools." There is an option in there to adjust your screen size, etc and then save it to xconf.org.  The second option, if you don't have the nvidia settings manager is to edit xconf.org yourself. There are how to's on this forum, just search. 

> **Hexydes said:**
> 
Next question, assuming I can get all that going, what is the best/easiest/fastest way to get Beryl installed (the thing with all the neat effects that is floating around Digg/YouTube)? I've read some walkthough's, but they all seem pretty long and complicated. I'm going to try one when I get home, but what would be the easiest and most sure-fire method of getting it going (again, NVIDIA GeForce 6600 with latest drivers, AMD Sempron 64)?


Read through my comments on this thread for installing Beryl, assuming your are using the latest Ubuntu (Edgy Eft.)

[http://www.ubuntuforums.org/showthread.php?t=309295](http://www.ubuntuforums.org/showthread.php?t=309295)

Best,
Rodney

---

### Post by Hexydes on 2006-11-29
Thanks a lot for the response, Rodney.

> You can do either of two things. You should be able to see the nvidia settings manager in "system tools." There is an option in there to adjust your screen size, etc and then save it to xconf.org. The second option, if you don't have the nvidia settings manager is to edit xconf.org yourself. There are how to's on this forum, just search.

I took a look in the NVIDIA settings manager briefly, but I didn't notice anything off the bat that would let me do this. I'll look again, and if that doesn't work, I'll try another method.

I'll try your Beryl guide when I get home. Thanks!

---

### Post by Rodneyck on 2006-11-29
Sometimes you have to add the Nvidia settings manger icon to your menus, so right click on the menu button and select "edit menus" and go in and see you can find the ican, then place a checkmark to add it.

No problem...and good luck. Beryl is great!

---

### Post by Hexydes on 2006-11-29
Yeah, no, I have the menu item and the application....just not a place in it to modify the resolution at all. :)

Definitely looking forward to checking out Beryl!

---

### Post by Hexydes on 2006-11-30
What do you mean when you say:

> *Add key*

"wget [http://beryl-mirror.lupine.me.uk/1609B551.gpg](http://beryl-mirror.lupine.me.uk/1609B551.gpg) -O- | sudo apt-key add -"

What does it mean to "Add key"? I tried putting it in the text file and saving it, but it complained when I proceeded to the next step. Does this line indeed go in the same file, and if so, what is the proper formatting? Anything special?

Thanks!

---

### Post by Rodneyck on 2006-11-30
Oh that one confused me at first. Just copy that part and past it in a Terminal, it should give you a few lines of feedback...with an "OK" if I remember, then continue to the next step.

---

### Post by Hexydes on 2006-11-30
Ok, will try that tonight and report back. ;)

Thanks!

---

### Post by Hexydes on 2006-11-30
Ok, so now when I get to the part about installing Beryl, I get returned:

```
ta emerald beryl-settings beryl-manager beryl beryl-dev emerald-themes
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package beryl-core
```

Looks like it had trouble downloading it possibly? Thoughts?

Thanks!

---

### Post by Hexydes on 2006-11-30
Hrm, ok I *think* that I got Beryl installed (any way to check that?), but I had to do it via Synaptic Package Manager (just checked all the packages and installed them, they seemed to line up with the ones listed in your guide). However, when I typed:

```
beryl-manager
```

The screen just kinda flashed for a second, it looked like it re-drew all the windows, and then I just had a partial window with a vertical scrollbar (no actual bar on it though, just the background). I could see my mouse in that small little partial-window, but nowhere else. I restarted X and it put me at the main graphical login. I logged in, and I was back at the good ol' desktop, but I'm thinking....Beryl is probably not running at this point (any way to confirm that?).

So, thoughts on what I did wrong, thoughts on how to get it going?

---

### Post by Rodneyck on 2006-11-30
I don't know about installing beryl with the Synaptic manager.  You might uninstall on those in Synaptic and try downloading again via the guide's method later, when the connection is up.

BTW, when you login in, Beryl is not active until you type "beryl-manager". You will know it is working because it pops up a cool beryl logo that is sort of wavy and changes the theme to a red-purple theme and the task bar and windows will have shadows under them.

Later, when you are sure everything is working correctly, you can put "beryl-manager" in the start up commands so you don't have to type it each time.

---

### Post by Hexydes on 2006-11-30
Yeah, I'm waiting to add it to startup until it is working. :D

Ok, so more information on the problem. When I run the command:

```
beryl-manager
```

I get the following in the terminal window:

```
username@Ubuntu:~$XGL Absent, checking for NVIDIA
Nvidia Present
Relaunching beryl with __GL_YIELD=Nothing
XGL Absent, checking for NVIDIA
Nvidia Present
[]
```

(the last thing is an empty square box)

That is on the screen in a terminal window. The taskbars are still all present, but I can't click on any of them, or the desktop. I can see my mouse, however if I move over the window, the mouse is hidden.

Then I restart X, log in, and everything is fine again (until I try to launch Beryl, of course). =\

When installing Beryl, did I have to specify anywhere that I am using an AMD64 processor?

Thanks for all the help!

---

### Post by Hexydes on 2006-11-30
Oh, and also, Beryl/Emerald are available in the "System >> Preferences" menu, and I can change all the options and whatnot, but of course this has no affect, since I can't launch Beryl...

---

### Post by Rodneyck on 2006-11-30
No need to specify processor. It is all very strange and sounds like something did not install correctly or at all. I would uninstall and start again via the guide.

---

### Post by tiptip on 2006-11-30
I tried to work by the guide you posted and got an error as well when i tried to run it.
"Sorry the program 'glxinfo' closed unexpectedly".

So many people have problem with Beryl, a "HOWTO for nubs" that has **_everything_** is needed.

---

### Post by Rodneyck on 2006-11-30
Yeah, maybe something is down link-wise in the guide which happened to me following the main how-to on this forum. I would suggest doing some googling for other guides, asking for help on the main thread, posting on the beryl forum or just waiting for the Feisty release. I hear they are going to include it in that release and imagine that the devs will make it an easier.

One last thing I would check is the correct version of your drivers.

---

### Post by Hexydes on 2006-12-01
Here's a question in the meantime. When Feisty is released, how do you go about updating Ebby to that version, without having to re-install? What is the standard process for doing this (can it be done graphically)?

---

### Post by igknighted on 2006-12-01
There is a special repo to add the x64_86 packages of beryl, did you make sure you got the right one?

---

### Post by tiptip on 2006-12-01
> **igknighted said:**
> There is a special repo to add the x64_86 packages of beryl, did you make sure you got the right one?
I dont know about the thread opener but i used
```
deb http://3v1n0.tuxfamily.org edgy beryl-svn
```
since
```
deb http://ubuntu.beryl-project.org/ edgy main-edgy
```
doesnt work atm.
But i still get
```
XGL Absent, checking for NVIDIA
Nvidia Present
Relaunching beryl with __GL_YIELD="NOTHING"
XGL Absent, checking for NVIDIA
Nvidia Present
beryl: No composite extension

```
and "Sorry, the program 'glxinfo' closed unexpectedly"

](*,) ](*,) ](*,)

---

### Post by Rodneyck on 2006-12-01
Are you using the guide I listed?  This guide...

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Beryl.2FAIGLX_.28Nvidia.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Beryl.2FAIGLX_.28Nvidia.29)

And using these instructions listed under " How to install Beryl/AIGLX (Nvidia)?"

If so, I do not see the deb you listed anywhere on that page.. (you listed above, "deb [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) edgy beryl-svn".

---

### Post by Hexydes on 2006-12-01
I'll try un-installing Beryl this weekend (I can just un-check these in Synaptic and apply it, right?). Once I have done this, I'll try re-installing via your guide again.

Someone mentioned that you do indeed need a special package for 64-bit...is that the case? If it is, I have a Sempron 64 and the 64-bit version of Ubuntu installed.

Thanks!

---

### Post by Rodneyck on 2006-12-01
What I would do is start with the drivers. Uninstall the nvidia drivers and reinstall with the instructions on the same guide, " How to install Beta Graphics Driver (NVIDIA)"

Once that is done and you have rebooted, then use the guide/link I mentioned above and install as directed. There is a link for additional repos if you find the one in the guide is not connecting, just follow the link for the list.  As for a different guide or whatever for 64 bit, the one  on that guide says the deb you add is for both, so I do not think there is a difference.  Maybe the poster who mentioned this can clarify this.

best..

---

### Post by Hexydes on 2006-12-01
Hell yeah, got it working! I just un-installed Beryl, re-installed it from the instructions (still didn't work), and then re-installed the NVIDIA drivers. The drivers appear to have been the trick. Thanks a lot Rodney, you've been a big help in the whole process!

---

### Post by Rodneyck on 2006-12-02
Yeah, I figured it was something with the drivers.  Enjoy!!!

---

### Post by Hexydes on 2006-12-02
Oh I am. Just got my dock up and running as well. :)

Thanks again!

---

