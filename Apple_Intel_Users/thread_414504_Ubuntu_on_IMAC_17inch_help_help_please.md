---
title: "Ubuntu on IMAC 17inch help help please"
date: 2007-04-19
forum: Apple Intel Users
---

### Post by bigred3373 on 2007-04-19
I have been trying to install ubuntu on my IMAC 17 inch and i have totally messed up my hard drive as i am not sure as how to partition it right so i have both Tiger and ubuntu maybe the feisty can you please poke me in the right ](*,)  so i dont keep reformatting my MAC and its drive arrggggg](*,) ](*,) ](*,) 

Thank you all for reading this

RED

---

### Post by ronocdh on 2007-04-20
> **bigred3373 said:**
> I have been trying to install ubuntu on my IMAC 17 inch and i have totally messed up my hard drive as i am not sure as how to partition it right so i have both Tiger and ubuntu maybe the feisty can you please poke me in the right ](*,)  so i dont keep reformatting my MAC and its drive arrggggg](*,) ](*,) ](*,) 

Thank you all for reading this

RED
I'm afraid I don't quite understand that situation; can you rephrase more calmly? What functionality have you lost? How did you partition the drive?

---

### Post by bigred3373 on 2007-04-20
> **ronocdh said:**
> I'm afraid I don't quite understand that situation; can you rephrase more calmly? What functionality have you lost? How did you partition the drive?

Exactly as it says i need to know how to install ubuntu on my 17 inch IMAC i didnt partition the drive i was using bootcamp it had windows on it and i messed that up and deleted everything trying to get ubuntu correctly installed on the hard drive itself not using boot camp. i still have function with the computer its all one drive know running tiger i want to install edgy hope this helped

---

### Post by ronocdh on 2007-04-20
> **bigred3373 said:**
> Exactly as it says i need to know how to install ubuntu on my 17 inch IMAC i didnt partition the drive i was using bootcamp it had windows on it and i messed that up and deleted everything trying to get ubuntu correctly installed on the hard drive itself not using boot camp. i still have function with the computer its all one drive know running tiger i want to install edgy hope this helped
OK, as I understand it, you had a dual boot system with OS X and Windows XP. This setup got ruined, and you have since removed the XP installation, and now you just want to have OS X and Ubuntu. Also, OS X is still running fine. If I am mistaken about anything here, please correct me.

If you just want to dual boot between Ubuntu and OS X, you can use the Boot Camp Utility to partition the drive, allotting enough space for Ubuntu and leaving whatever else for OS X. This is no problem, and you may even still have a partition made (the one previously used for Windows XP). If that's the case, why not just install on there? You can boot up from the Live CD and choose the old XP partition (choose carefully!) and reformat it to ext3, then install on it.

I highly recommend you use Feisty Fawn for this, though. Edgy would indeed work, but it would take considerably more effort. Try [this guide]("https://help.ubuntu.com/community/MacBook") for more information on the specifics of the installation.

Post back with any other questions.

---

### Post by bigred3373 on 2007-04-20
> **ronocdh said:**
> OK, as I understand it, you had a dual boot system with OS X and Windows XP. This setup got ruined, and you have since removed the XP installation, and now you just want to have OS X and Ubuntu. Also, OS X is still running fine. If I am mistaken about anything here, please correct me.

If you just want to dual boot between Ubuntu and OS X, you can use the Boot Camp Utility to partition the drive, allotting enough space for Ubuntu and leaving whatever else for OS X. This is no problem, and you may even still have a partition made (the one previously used for Windows XP). If that's the case, why not just install on there? You can boot up from the Live CD and choose the old XP partition (choose carefully!) and reformat it to ext3, then install on it.

I highly recommend you use Feisty Fawn for this, though. Edgy would indeed work, but it would take considerably more effort. Try [this guide]("https://help.ubuntu.com/community/MacBook") for more information on the specifics of the installation.

Post back with any other questions. Hi agian i dont have the boot camp partition installed it is all one single drive, no boot camp nothing so its all fresh.

 I have tryed the boot camp to formatt then it asked for the windows install disk and will not go further so i restart then i have this partition empty and it still wants my windows cd and nothing else. This is a 17 inch IMAC not  a mac book :)

---

### Post by ronocdh on 2007-04-20
> **bigred3373 said:**
> Hi agian i dont have the boot camp partition installed it is all one single drive, no boot camp nothing so its all fresh.

 I have tryed the boot camp to formatt then it asked for the windows install disk and will not go further so i restart then i have this partition empty and it still wants my windows cd and nothing else. This is a 17 inch IMAC not  a mac book :)
No problem that it's an iMac rather than a MacBook, I linked you to that guide because you might have to force the installation to use GRUB rather than LILO, if you're using Edgy. Again, I recommend you try this with the final of Feisty Fawn, but it's your choice.

Boot Camp provides a nice graphical partition tool that many find useful; use it for this purpose only, if you don't intend to use Win XP. Once the partition is created in Boot Camp, you can exit out of the utility. Insert your Ubuntu live CD and then reboot your computer. Once the GUI installation wizard opens, you should be able to select the newly created partition and format it as ext3. Then install onto it.

Or, you can always use the terminal in OS X to partition. For more on that, try a guide such as [this one.]("http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu")

Good luck!

---

### Post by bigred3373 on 2007-04-20
> **ronocdh said:**
> No problem that it's an iMac rather than a MacBook, I linked you to that guide because you might have to force the installation to use GRUB rather than LILO, if you're using Edgy. Again, I recommend you try this with the final of Feisty Fawn, but it's your choice.

Boot Camp provides a nice graphical partition tool that many find useful; use it for this purpose only, if you don't intend to use Win XP. Once the partition is created in Boot Camp, you can exit out of the utility. Insert your Ubuntu live CD and then reboot your computer. Once the GUI installation wizard opens, you should be able to select the newly created partition and format it as ext3. Then install onto it.

Or, you can always use the terminal in OS X to partition. For more on that, try a guide such as [this one.]("http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu")

Good luck!

whew a lot to handle will get back to this as soon as i download feisty fawn okay
Its taking alot of time to download :(:(  then i have to burn image which that i don't understand.
Thank You you are great and have patients with me most don not care i am a  bit slow :) speaking of which i hope i am downloading the right file for POWER PC or is AMD and Intel? oh great no nothing will download from the site is there site over packed or something sorry thanks again

---

### Post by ronocdh on 2007-04-20
> **bigred3373 said:**
> whew a lot to handle will get back to this as soon as i download feisty fawn okay
Its taking alot of time to download :(:(  then i have to burn image which that i don't understand.
Thank You you are great and have patients with me most don not care i am a  bit slow :) speaking of which i hope i am downloading the right file for POWER PC or is AMD and Intel? oh great no nothing will download from the site is there site over packed or something sorry thanks again
You can use the i386 version no matter what. That is the safest option. If you are sure that you have a Core2 Duo processor (as opposed to just a Core Duo), then you also could use the AMD/64-bit version. Under no circumstances should you use the PowerPC build; that's for older Macs.

To create the CD, try using the application **Burn**. You can find it [here]("http://www.opensourcemac.org") along with a number of other really great open source apps for OS X.

Glad to be of help. Just remember to be as clear as possible when asking for help, so people will be able to give you pertinent advice. Good luck!

---

### Post by bigred3373 on 2007-04-20
> **ronocdh said:**
> You can use the i386 version no matter what. That is the safest option. If you are sure that you have a Core2 Duo processor (as opposed to just a Core Duo), then you also could use the AMD/64-bit version. Under no circumstances should you use the PowerPC build; that's for older Macs.

To create the CD, try using the application **Burn**. You can find it [here]("http://www.opensourcemac.org") along with a number of other really great open source apps for OS X.

Glad to be of help. Just remember to be as clear as possible when asking for help, so people will be able to give you pertinent advice. Good luck!

Hi there not giving an i386 on the page just the powe pc and others i just have core duo i got this in july of 06 the 17 inch MAC. I stopped the download and i am doubble checking everyting i having a problem restarting the computer to start with CD and not hardrive i keep pressing c on my keyboard and it still wont load goes directly startup OSX i am using a microsoft keyboard not the original apple one does this matter you think??? thanks agian!!!!! Do I use the standard build or amd
Standard personal computer (x86 architecture, PentiumTM, CeleronTM, AthlonTM, SempronTM)   PowerPC based Apple computers and OpenPower/Power5 computers   64bit AMD and Intel computers   Sun UltraSPARC based agian its not the core2 duo its the first core duo thanks.

---

### Post by ronocdh on 2007-04-20
> **bigred3373 said:**
> Hi there not giving an i386 on the page just the powe pc and others i just have core duo i got this in july of 06 the 17 inch MAC. I stopped the download and i am doubble checking everyting i having a problem restarting the computer to start with CD and not hardrive i keep pressing c on my keyboard and it still wont load goes directly startup OSX i am using a microsoft keyboard not the original apple one does this matter you think??? thanks agian!!!!! Do I use the standard build or amd
Standard personal computer (x86 architecture, PentiumTM, CeleronTM, AthlonTM, SempronTM)   PowerPC based Apple computers and OpenPower/Power5 computers   64bit AMD and Intel computers   Sun UltraSPARC based agian its not the core2 duo its the first core duo thanks.
The version you want is the first one you listed: **Standard personal computer (x86 architecture)**. Please describe more lucidly the issue with booting from a CD. Are you saying that while in OS X, you insert an Ubuntu live CD and then reboot, but you are not given the option to boot from a CD? I think that by default this is the case; someone correct me if I am wrong. I have [rEFIt]("http://refit.sf.net") installed and this always asks me whether I want to boot from a CD when I start up my computer.

Please try to be very clear in your explanations. When a post is worded ambiguously or is rushed, it is usually rather hard to figure out what the issue is, which makes diagnosing the problem all the harder.

---

### Post by bigred3373 on 2007-04-20
> **ronocdh said:**
> The version you want is the first one you listed: **Standard personal computer (x86 architecture)**. Please describe more lucidly the issue with booting from a CD. Are you saying that while in OS X, you insert an Ubuntu live CD and then reboot, but you are not given the option to boot from a CD? I think that by default this is the case; someone correct me if I am wrong. I have [rEFIt]("http://refit.sf.net") installed and this always asks me whether I want to boot from a CD when I start up my computer.

Please try to be very clear in your explanations. When a post is worded ambiguously or is rushed, it is usually rather hard to figure out what the issue is, which makes diagnosing the problem all the harder.

i m not given the option to boot from a cd :confused: i am sorry  it is not hurried just words to fast in head. which version of the rEFIt do you use?

---

### Post by ronocdh on 2007-04-20
> **bigred3373 said:**
> i m not given the option to boot from a cd :confused: i am sorry  it is not hurried just words to fast in head. which version of the rEFIt do you use?
OK, while in OS X, install the **Mac disk image** rEFIt package. [This link]("http://prdownloads.sourceforge.net/refit/rEFIt-0.9.dmg?download") should take you right to it. Once that is downloaded and completely installed, reboot once. When that is done, insert your Ubuntu live CD and reboot. You should be given an option on the rEFIt screen to choose either your internal hard drive, which has OS X on it, or the Ubuntu CD. If you see the latter, choose it, and you can install from there.

Right now it is difficult to install Feisty on MacBook Pros; I can't be sure whether you'll have the same problems on an iMac. If you do run into problems, you should find the solutions posted in this forum already.

Alternatively, you may be interested in running Ubuntu in OS X via a program like [VMWare Fusion]("http://www.vmware.com/products/beta/fusion/"). A Similar program, known as Parallels, has been giving a lot of Ubunturs difficulty, and AFAIK I know VMWare Fusion has treated them much better. Using this would enable you to run Ubuntu and OS X side by side, without having to reboot. Consider this option.

---

### Post by bigred3373 on 2007-04-20
> **ronocdh said:**
> OK, while in OS X, install the **Mac disk image** rEFIt package. [This link]("http://prdownloads.sourceforge.net/refit/rEFIt-0.9.dmg?download") should take you right to it. Once that is downloaded and completely installed, reboot once. When that is done, insert your Ubuntu live CD and reboot. You should be given an option on the rEFIt screen to choose either your internal hard drive, which has OS X on it, or the Ubuntu CD. If you see the latter, choose it, and you can install from there.

Right now it is difficult to install Feisty on MacBook Pros; I can't be sure whether you'll have the same problems on an iMac. If you do run into problems, you should find the solutions posted in this forum already.

Alternatively, you may be interested in running Ubuntu in OS X via a program like [VMWare Fusion]("http://www.vmware.com/products/beta/fusion/"). A Similar program, known as Parallels, has been giving a lot of Ubunturs difficulty, and AFAIK I know VMWare Fusion has treated them much better. Using this would enable you to run Ubuntu and OS X side by side, without having to reboot. Consider this option.

Thank you for all this information and i will once downloaded 7.04 will restart and burn the image and post at a later time  with all your help i should do fine you are great thanks agian maybe i posted another question related to ppc no has answered maybe you can here is the question

i have been trying to install dapper on my old clamshell 366mhz firewire 10gb 350mb ram it installs and goes through the normal process then goes black screen. How do i change the prefrences for the screen the refresh and vert for the screen to come back thanks agian i will learn all this!!!

---

### Post by ronocdh on 2007-04-21
> **bigred3373 said:**
> Thank you for all this information and i will once downloaded 7.04 will restart and burn the image and post at a later time  with all your help i should do fine you are great thanks agian maybe i posted another question related to ppc no has answered maybe you can here is the question

i have been trying to install dapper on my old clamshell 366mhz firewire 10gb 350mb ram it installs and goes through the normal process then goes black screen. How do i change the prefrences for the screen the refresh and vert for the screen to come back thanks agian i will learn all this!!!
This is a tricky one; I'm very unfamiliar with that hardware. I would recommend that once you get comfortable with Ubuntu and the command line interface, that you download the PowerPC alternate CD. Alternate CDs have text-based installers, which requires a bit more expertise, but oftentimes you can get further in the installation before having to deal with graphical issues.

In fact, I used the Feisty alternate (64-bit) to install on my MacBook Pro. 

Good luck to you! Post back in a new thread with any further troubles.

---

