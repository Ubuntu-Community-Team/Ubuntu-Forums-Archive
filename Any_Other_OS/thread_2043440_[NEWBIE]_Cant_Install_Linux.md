---
title: "[NEWBIE] Cant Install Linux"
date: 2012-08-16
forum: Any Other OS
---

### Post by ZepFloyd on 2012-08-16
posted this is the general help section, but figure it could go here too. hopefully get some more eyes on my problem.

so i tried posting on linux mint forums and not getting any help so will try here.

i have tried installing 3 different linux distros and none have worked. ubuntu 12.04, mint 13 KDE, fedora 17 KDE. (i have mageia KDE as well, but havent tried an install)

i honestly didnt try the live disc of ubuntu before trying to install. so i can't speak to if that live cd might work. the other 3 (mint,fedora,mageia)all live cd's worked. i was able to navigate and play around with the distros. 

after playing around with all 3, i had decided on mint to install. so i hit the install button during the live cd session. run through the installation guide/wizard. it finishes, i reboot, i select mint 13 (i'm dual booting with vista) and nothing happens. think it just sat with a gray screen.

so....i delete and remove partitions and get rid of mint completely. decide i'll try fedora, again installation wizard was fine, it installs. i reboot, select fedora, and again just a black screen with like a gray line in the top left corner. 

i thought maybe i was screwing something up during the installation guide/wizard for partitioning. so i decided to try fedora again, but this time i'll create a partition before installing and then select the option to install fedora into that pre made partition. do that, everything works, go to reboot, boom same thing. black screen with a gray line in the corner. 

at this point i'm completely dumbfounded..i'm a complete linux newb, i kind of expected some problems once i got into working with linux, but not simply just trying to install it onto my hard drive. 

can anyone help me out?

heres some specs if that helps:

windows vista 64 bit
3 ghz processor
AMD radeon 6670 graphics card
4 gigs of ram


if you need more info, just ask i'll try to provide an answer.

---

### Post by drs305 on 2012-08-16
Here are a couple of things to try.

We need to know if the OS is getting past the bootloader. If it uses Grub2 (Ubuntu family), hold down the shift key during boot and see if the menu appears. Then select the OS and boot and let us know where the failure occurs. If it is after you make the selection, you may have a video driver failure and we can take steps to boot without it.

If you don't ever get a Grub2 menu, then we may have to reinstall Grub. You can install boot Repair from the LiveCD and let it try to fix Grub2. If it can't you can run the boot info script and post the link so we can take a look at your system setup. Link to Boot Repair in my signature line.

---

### Post by irv on 2012-08-16
Have you tried following the step by step install of Ubuntu 12.04. This is a good place to start if you are new to Ubuntu and Linux as a whole.
[https://help.ubuntu.com/community/GraphicalInstall]("https://help.ubuntu.com/community/GraphicalInstall")

---

### Post by ZepFloyd on 2012-08-16
let me add one more thing...forgot to mention. when i installed ubuntu...i was able to get to the login screen. but no further. after typing in my password and hitting enter. it wouldnt load any desktop.  if that means anything.

also at the moment i don't have any linux distros on my hard drive, i think i will just go with ubuntu. i'll re install and try what you suggested, drs305

also that way you you guys know we are working with ubuntu.

---

### Post by ZepFloyd on 2012-08-16
> **drs305 said:**
> Here are a couple of things to try.

We need to know if the OS is getting past the bootloader. If it uses Grub2 (Ubuntu family), hold down the shift key during boot and see if the menu appears. Then select the OS and boot and let us know where the failure occurs. If it is after you make the selection, you may have a video driver failure and we can take steps to boot without it.

If you don't ever get a Grub2 menu, then we may have to reinstall Grub. You can install boot Repair from the LiveCD and let it try to fix Grub2. If it can't you can run the boot info script and post the link so we can take a look at your system setup. Link to Boot Repair in my signature line.

is grub the screen where you select between the ubuntu and windows? if so, that screen always appears, appeared for ubuntu, fedora and mint. if that helps..

---

### Post by ZepFloyd on 2012-08-16
real quick update. decided to see if ubuntu ran from the live disc. i am currently posting from ubuntu live disc, so that works. i'm going to try the install again

---

### Post by irv on 2012-08-16
> **ZepFloyd said:**
> real quick update. decided to see if ubuntu ran from the live disc. i am currently posting from ubuntu live disc, so that works. i'm going to try the install again

I just want to say if it run OK from the Live disc, and you are posting on this forum, then you are on the Internet it should run and work the same from the install.

---

### Post by YannBuntu on 2012-08-16
Welcome among us :)

> **ZepFloyd said:**
> let me add one more thing...forgot to mention. when i installed ubuntu...i was able to get to the login screen. but no further. after typing in my password and hitting enter. it wouldnt load any desktop.  if that means anything.

Yes, that's important, that means this isn't a GRUB problem, so Boot-Repair won't help (except for adding kernel options to your install, if needed).

---

### Post by ZepFloyd on 2012-08-16
thats good to hear. i am currently in the process of installing. but i fear it might have stalled or stopped. i know installations can take awhile, but it was going fairly smoothly. the status bar is near the end and its suddenly slowed down a ton. i'm not sure how to exit out of the install...i mean i'd like to wait it out, but fear its froze, not exactly sure what to do

to give an idea, the status bar is installing system, which is normal i'm sure, but the staus orange bar has been in the same place for prob over an hour...prob closer to two hours now. 

what do i do now?

edit: went ahead and shut down my computer, and deleted ubuntu off. i really want to try this one more time, but i'm getting pretty fed up. i let that install go for near 2 hours, i dont buy it should take that long. maybe on an older system.

does anyone have any ideas what to do?

---

### Post by ZepFloyd on 2012-08-16
alright quick update. after that last attempt to install seemed to stall out or stop.

went to install again, and it installed much quicker. reboot the computer select ubuntu from the list. screen goes black for a minute then just turns some kind of beige/orange color and nothing else. didnt even get to the login screen.

i dont know if it matters but instead of going into the live cd and then clicking install, theres those 2 options before when the live cd boots up, i just chose install right away. not sure that matters or not. thought i'd throw that in there.

i am going to leave ubuntu on for the time being, currently using windows to write this post. so whatever info you need to ask, i'l try to answer, but thats what we have to go on.

to recap: live cd works. but once installed, boot loader loads up, but once ubuntu is selected hit enter, and screen just goes to a beige/orangish color. 

lets see if we cant figure this out. i'm extremely frustrated, i turn to the linux pros/community to help this newbie out.

thanks for all the help so far

---

### Post by craig10x on 2012-08-16
I would try ubuntu again and this time let it load in the live session....and if it is working ok THEN click the install Ubuntu button...that is the way i ALWAYS have done it and it had always worked fine when i did.... :)

---

### Post by ZepFloyd on 2012-08-16
> **craig10x said:**
> I would try ubuntu again and this time let it load in the live session....and if it is working ok THEN click the install Ubuntu button...that is the way i ALWAYS have done it and it had always worked fine when i did.... :)

i did that last time, and it froze/stopped during installation. i'm having a hard time believing its anything from the installation. i think it simply might be hardware related, more specifically my graphics card. maybe not the right drivers or something. it shouldnt matter which way i chose to install it.

---

### Post by drs305 on 2012-08-16
If you still have the installation that stalled at the tan screen, you could see if it's a video problem. From the boot (Grub) menu, highlight Ubuntu and press "e" to enter the edit mode.

Cursor to the end of the 'linux' line and remove everything after "ro". Then type *nomodeset* so the line ends with *ro nomodeset*

Press F10 or ctrl-x to boot. If it boots to the Desktop, you will need to install the video driver. If you installed 12.04, press the screen's top left DASH icon and type "additional drivers".

---

### Post by irv on 2012-08-16
Are you trying to install the 32 or 64bit?
Did you check the download for error?
I have installed Ubuntu 12.04 on a few computer and did the install on one computer 4 times and never had any problems installing any of them so I am starting to thing you might have a bad download. I don't think it is hardware because the live OS works just find.

---

### Post by ZepFloyd on 2012-08-16
> **drs305 said:**
> If you still have the installation that stalled at the tan screen, you could see if it's a video problem. From the boot (Grub) menu, highlight Ubuntu and press "e" to enter the edit mode.

Cursor to the end of the 'linux' line and remove everything after "ro". Then type *nomodeset* so the line ends with *ro nomodeset*

Press F10 or ctrl-x to boot. If it boots to the Desktop, you will need to install the video driver. If you installed 12.04, press the screen's top left DASH icon and type "additional drivers".

i will try this and report back. thanks

---

### Post by ZepFloyd on 2012-08-16
> **irv said:**
> Are you trying to install the 32 or 64bit?
Did you check the download for error?
I have installed Ubuntu 12.04 on a few computer and did the install on one computer 4 times and never had any problems installing any of them so I am starting to thing you might have a bad download. I don't think it is hardware because the live OS works just find.

64 bit, didnt check download for errors, not sure how to do that. but when i burn the distros i have the burner verify the data on the disc. also i'm having problems with numerous distros...so i dont think 4 different distros all downloaded badly

---

### Post by ZepFloyd on 2012-08-16
okay! that worked, and i'm into the desktop, what do i do once the additional drivers pops up? 

there are two options. theres ATI/AMD proprietary FGLR graphics driver (post-release updates)

and ATI/AMD proprietary FGLR graphics driver

do i select either or and click activate?

---

### Post by ZepFloyd on 2012-08-16
i decided to go with just the normal graphics driver the one not with post-release updates. that worked. rebooted and am now posting from ubuntu! 

thanks for the help.

though i do have another question...am i going to run into problems with updates all the time? or should this take care of that for the most part?

---

### Post by drs305 on 2012-08-17
It shouldn't happen with normal updates. It's possible you will have to reinstall the drivers if the kernel (linux-image) is updated), But at least now you know the procedure.  ;-)

When you don't have any other questions please mark the thread SOLVED via the 'Thread Tools' link near the top right of the original post. It let's others know there is a solution somewhere in the thread and allows the helpers to concentrate on unresolved threads. (It's reversible if needed.)

Happy Ubuntu-ing !

---

### Post by YannBuntu on 2012-08-17
> **ZepFloyd said:**
> i dont know if it matters but instead of going into the live cd and then clicking install, theres those 2 options before when the live cd boots up, i just chose install right away.

That should not matter.

> **ZepFloyd said:**
> went to install again, and it installed much quicker. reboot the computer select ubuntu from the list. screen goes black for a minute then just turns some kind of beige/orange color and nothing else. didnt even get to the login screen.


I am not sure, but it may be a graphical driver problem, or a Unity (Ubuntu new desktop) problem.
If I were you, I would try installing an older version (eg Ubuntu 10.04) and/or another distribution (eg Mint).

---

### Post by ZepFloyd on 2012-08-17
> **drs305 said:**
> It shouldn't happen with normal updates. It's possible you will have to reinstall the drivers if the kernel (linux-image) is updated), But at least now you know the procedure.  ;-)

When you don't have any other questions please mark the thread SOLVED via the 'Thread Tools' link near the top right of the original post. It let's others know there is a solution somewhere in the thread and allows the helpers to concentrate on unresolved threads. (It's reversible if needed.)

Happy Ubuntu-ing !

will do. thanks again for all the help!

---

