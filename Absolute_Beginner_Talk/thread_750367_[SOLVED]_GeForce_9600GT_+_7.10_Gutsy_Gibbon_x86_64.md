---
title: "[SOLVED] GeForce 9600GT + 7.10 Gutsy Gibbon x86_64"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by mmillman on 2008-04-09
Ok guys, I am sorry, I know this has been answered a few times, however it is confusing to me as to which answer path is correct for me.

I'll start off by saying that I consider myself to be pretty knowledgable when it comes to computers, however this is my first experience with linux, and I have a few questions.

First thing's first... my hardware specs are

AMD Athlon 64 X2 4400+ Socket 939 (Toledo core)
ASUS A8N32-SLI Deluxe motherboard
Apevia Beast Power 680watt PSU
2 gigs Kingston HyperX PC3200 2-3-2-6-1T ram
XFX GeForce 9600 GT 512 mb 650mhz core clock

I am running Ubuntu 7.10 GG x86_64.

I had a few issues getting the live cd to run at first, it would power off my monitor and I couldn't get into the GUI, (my card has the dual dvi ports which I believe was causing the problem).  I worked around this by pressing F6 for the command line parameters, and removing the terms "quiet" and "splash" and adding the term "nosplash".  This allowed me to boot into the live CD using the vesa drivers...  After I successfully installed Ubuntu onto a primary partition, this problem seemed to resolve itself... now when I start up, the monitor powers off initially for about 1 second, and then powers itself back on successfully... strange behavior, but it seems to be working...

Anyway,  here is my question regarding the installation of the new 171.06 AMD64 forceware driver... which method of installing is the best/most reliable?  I have seen a couple of different work arounds, however the one that looks the most straightforward to me is [this one]("http://ubuntuforums.org/showpost.php?p=4558708&postcount=37").

Should following those steps successfully allow me to install the 9600gt proprietary drivers onto Ubunto 7.10 Gutsy Gibbon?  Sorry for the noobish questions... as I said before, I am COMPLETELY new to linux in general, so I need someone to hold my hand a bit =).

---

### Post by blazercist on 2008-04-09
i have the same card but i dont use 64bit....

the easiest and in my opinion best way to do it is:

1. download the driver to your home directory

2. press ctrl+alt+f1 (to reach a terminal)

3. sudo /etc/init.d/gdm stop  (to kill X)

4. sudo sh NVIDIA*

5. follow the onscreen instructions till it says complete

6. sudo /etc/init.d/gdm start

7. ctrl+alt+f7 to return to your X windows session (im not sure if this is necessary it may just start all on its own)

8. enjoy


the link you gave is not wrong either...YOU WILL NEED THE build-essential PACKAGE  but i think disabling the nv driver in restricted modules is not necessary.  Also, im not 100% sure if you need to (the installer may do it automatically) but you may need to "sudo gedit /etc/X11/xorg.conf and change the "vesa" or "nv" driver to "nvidia"

---

### Post by jseiser on 2008-04-09
I was unable to get my 9600 to work on ubuntu 64.  works fine on arch 64. Alsa, If you install the nvidia driver from their site, you are screwing yourself in the end, when your kernel changes you will need to re download and compile that kernel.  The restricted manager is supposed to work, it always did till the I threw the 9600 at it, So i am wondering if ubuntu just uses an old driver, I dont use ubuntu enough to have made it worth my time trying to get the card to work, I was just seeing if it would, it didnt, so I finished my normal arch install.  Oddly enough, that worked with the regular nvidia-driver, and the beta driver.

---

### Post by mmillman on 2008-04-09
Thank you, when I get home (I'm at work right now) I will try this method and see if it works... if it works I will be giving you thanks and marking this thread solved =).

Also, did you experience a similar situation with the monitor (no signal on the first live cd/install, and a brief cycle of no signal on normal start-up from  hard disk)?

To Jseiser: are you saying that everytime I upgrade my kernel I will have to repeat the above method to install my video card?  Because I can live with that...

---

### Post by blazercist on 2008-04-09
the reason the restricted driver doesnt work for the 9600 is because the 171.06 version is the first? or second? to support the 9600GT, they have yet to update the repos with a newer version of the nvidia driver...  yes if you manually install the driver from the nvidia site rather than using the repos you will have to reinstall it each time there is a kernel upgrade.

---

### Post by Neo0351 on 2008-04-09
I'd say go with mine, it's easy and works for most people, but not everyone.  it takes about 5 minutes.  if you have any questions, just ask.

---

### Post by Neo0351 on 2008-04-09
> **jseiser said:**
> I was unable to get my 9600 to work on ubuntu 64.  works fine on arch 64. Alsa, If you install the nvidia driver from their site, you are screwing yourself in the end, when your kernel changes you will need to re download and compile that kernel.  The restricted manager is supposed to work, it always did till the I threw the 9600 at it, So i am wondering if ubuntu just uses an old driver, I dont use ubuntu enough to have made it worth my time trying to get the card to work, I was just seeing if it would, it didnt, so I finished my normal arch install.  Oddly enough, that worked with the regular nvidia-driver, and the beta driver.

jseiser, how did try to install the driver?  i've been using mine on 7.10 x64 since they first came out using the 171.05 driver.  and all you have to do is keep a copy of the driver so you dont have to download it every time.  my way took me less than 5 min to install.

---

### Post by mmillman on 2008-04-09
I can see where you are coming from with that, I am new to linux, however it does make sense to me that you would wanna disable the  "restricted driver" if you are going to be installing a new one.  It's a simple case of redundency I suppose...  It's never a good thing to have two separate drivers active for the same device on the same machine no matter what OS you are on...

I will try tonight and hopefully I'll be good to go.

---

### Post by Neo0351 on 2008-04-09
i had to disable my restricted driver or it would keep changing my xorg.conf  and i know that was a problem with someone else i helped using x64 too.  you might not have to, but wont know until you install the driver and it couldnt hurt to disable it.

---

### Post by mmillman on 2008-04-09
I plan on trying the 171.06 x86_64 driver... this shouldn't cause me any problems should it?  I known newer isn't always better, but i'll try it anyway...

Also.. (sorry I'm a complete n00b)... how do I identify my current kernel version?

---

### Post by Neo0351 on 2008-04-09
yes, that is the correct driver, thats the one im using now.  for your kernel
```
uname -r
```

---

### Post by mmillman on 2008-04-10
Ok... so this is almost solved now... a couple quick questions.

First of all, the install went wonderfully, (I think).  The driver install appears to have worked, and I now have 24 bit 1280x1024 graphics =).  Also, played around with the advanced appearence/effects last night, and they all seem to work beautifully with no slow-down!  However, there is still something that confuses me...  If I navigate over to "screen and graphics", and click the video card tab, it comes up and still says "vesa [generic]" or something similar (sorry, I'm at work right now so I'm not in front of it)... but underneath it where it says driver it says "nvidia" and that is all the information it gives... for memory it just says automatic and is greyed out...

Also, under device management or hardware management or whatever... in the tree my pci-express bus expands and underneath it has "Unknown Device" or something like that, yet when you click on it, it gives all the correct information in the right window pane... correct manufacturer (xfx) device memory (512 mb) etc....

Why does it show up as "unknown" if clearly every piece of information is available to it?

And then, on top of all of that, if I click "Applications", the Nvidia Driver program is in there, and it properly detects all of my video card information...

I guess what I'm trying to say is I'm confused as to why three different screens show me three different pieces of information about the same device.... functionality is perfect, I'm just confused about the lack of uniformity between the different screens...


Also.. and this is the more pressing of the two issues... it seems that whenever I open a new window or a new program, it's default placement snaps straight to the top left corner of the screen... which would be fine by me, however they snap up there with the title bar inaccessable off the top of the screen, so I can't move them easily... and this happens with everything I open... I played with a lot of the compiz settings but couldn't get the correct functionality (no matter what I do, everything I open snaps too high up and I can't access the title bar)

Oh, and one more thing, isn't there a setting in Compiz that allows the open windows to appear physically raised out in front of the ones behind them while rotating the cube?  I couldn't find this but I've seen it in numerous videos demonstrating Beryl... was this functionality dropped when Beryl re-assimilated into compiz?

---

### Post by Neo0351 on 2008-04-10
> First of all, the install went wonderfully, (I think). The driver install appears to have worked, and I now have 24 bit 1280x1024 graphics =). Also, played around with the advanced appearence/effects last night, and they all seem to work beautifully with no slow-down! However, there is still something that confuses me... If I navigate over to "screen and graphics", and click the video card tab, it comes up and still says "vesa [generic]" or something similar (sorry, I'm at work right now so I'm not in front of it)... but underneath it where it says driver it says "nvidia" and that is all the information it gives... for memory it just says automatic and is greyed out...

Also, under device management or hardware management or whatever... in the tree my pci-express bus expands and underneath it has "Unknown Device" or something like that, yet when you click on it, it gives all the correct information in the right window pane... correct manufacturer (xfx) device memory (512 mb) etc....

Why does it show up as "unknown" if clearly every piece of information is available to it?

And then, on top of all of that, if I click "Applications", the Nvidia Driver program is in there, and it properly detects all of my video card information...

I guess what I'm trying to say is I'm confused as to why three different screens show me three different pieces of information about the same device.... functionality is perfect, I'm just confused about the lack of uniformity between the different screens...
just go with it, everything is fine, mine is the same why, no worries.  

as for compiz, the driver doesnt really play that nicely with it yet.  remember, this one is still a beta and i think, but not positive its built for nvidia's telsa system, whatever that is.  the 171.05 was for telsa, so im assuming .06 is too.  its not perfect yet, but im so much happier with my 9600gt than my 7300LE despite the few shortcoming of the drivers.  hope this answered your questions

---

### Post by mmillman on 2008-04-10
Are you saying that the windows automatically snapping to the top of the page with the titlebars inaccessable is something that I can't correct?  Because with the exception of that, everything else works fine with compiz...

Do your windows snap to the top incorrectly like that?  I'm just trying to figure out a way to make the windows not snap to the top at all when I open them... it's very annoying that every single window that I open snaps inaccessibly too far up...

I am going to give you thanks for that original post by the way... that doesn't lock the thread does it?

---

### Post by Neo0351 on 2008-04-10
mine didn't have that problem with compiz, but the way to find out if its compiz is to turn it off and see if it still happens.  but i dont think its a problem with the 9600gt because mine doesnt.  it might have to do with the ubuntu and you monitor.  mine did funny things like place windows half in one workspace, half in the other.  and opening some things it would make it really too big to fit in the screen and didnt have access anything i couldnt see.  i couldnt resize the windows that happened on.  but now the driver detects my monitor by name and i dont have that problem anymore.  marking the thread as solved lets everyone know that you problem is solved so they dont waste time reading through the thread to find out you have your answer, but doesnt lock it.  if you are still having problems with the windows, you may want to start another thread.

---

### Post by mmillman on 2008-04-10
Awesome... thank you so much for your help man, I'm not really sure how to mark it solved, but this specific issue is indeed solved... you are a lifesaver bro.

Edit: N/M figured it out =).  Thanks again.

---

### Post by Neo0351 on 2008-04-10
your welcome, glad i could help :)

---

### Post by fbg111 on 2008-04-18
> **blazercist said:**
> the reason the restricted driver doesnt work for the 9600 is because the 171.06 version is the first? or second? to support the 9600GT, they have yet to update the repos with a newer version of the nvidia driver...  yes if you manually install the driver from the nvidia site rather than using the repos you will have to reinstall it each time there is a kernel upgrade.
What's Ubuntu's objective on how quickly they update the Repo driver with the new ones from Nvidia?  Do they have a policy or anything on this?

---

### Post by Neo0351 on 2008-04-18
well as far as i know, the 8000 series still doesnt have support in the repos so the 9000 series could be quite a while before repos are updated.  however the 8000 series is supported by envy

---

### Post by fbg111 on 2008-04-18
Thanks.  8000 series probably more likely to be supported in the repo sooner too, so will look at picking up an 8800gt after 8.04 comes out.

---

### Post by Neo0351 on 2008-04-18
its really not hard to install the 9600gt.  it takes a few minutes install, really not that hard at all.  i wouldnt count it out for ease of install, i would look at price and performance.  they are both great cards though.

---

