---
title: "Desperately seeking PPC &amp; Intel Testers for 14.10 release ASAP!!!  Now!!!!"
date: 2014-08-28
forum: Apple Hardware Users
---

### Post by este.el.paz on 2014-08-28
FW'd from lubuntu-user list-serve:

Subject: Testing begins for Lubuntu 14.10 Beta 1, due on 28 August!
 
Sorry, would have let you know sooner, but I just found out!

The alternates are beginning to get built and put onto the ISO QA
Tracker [1]. Now is the time to join testing [2], so download an ISO
and see what you can break.

Again, with 14.10, we're trying to do a bug fix release to get us
ready for the major innovation of LXQt, slated for 15.04, so test
hard!

I especially beg you PPC users to test (formally, with the tracker,
not through emails to the mailing list) so that we can fix those
nagging issues that prevents the release from being really solid.

Finally, an extra special request for anyone with an Intel Mac: please
test FIRST with the amd64 version. If you can't boot it, use the
amd64+mac version. Either way, i'd like to know what version of the
firmware you have.

If you have any questions or comments, feel free to email or find me on IRC.

Thanks!

wxl

[1] [http://iso.qa.ubuntu.com/qatracker/milestones/322/builds](http://iso.qa.ubuntu.com/qatracker/milestones/322/builds)
[2] [https://wiki.ubuntu.com/Lubuntu/Testing](https://wiki.ubuntu.com/Lubuntu/Testing)

---

### Post by este.el.paz on 2014-08-29
Folks:

Beta testing 14.10:

Bug report #1363180

for  the alt install:  During testing for PPC 14.10 alternate install CD on  iBook G4 the process got as far as the Yaboot window boot prompt . . .  entering various commands resulted in response: "claim error, can't  allocate e00000 at 0 x c2000000; claim error, can't allocate kernel  memory." Built 20140826.1 No further testing could be done.

for  live desktop:  Problem "replicated" using the desktop iso downloaded  today build 20140829 got to the Yaboot boot prompt window, entering  "live" and various other choices offered under "tab" brings identical  "claim error" . . . adding on some "radeonfb= items brings "invalid  device" . . . . So, I would again say that "testing failed" on the G4  iBook with 14.10 beta . . . could not proceed past the Yaboot window . .  . . 


Maybe for sh*ts & giggles I'll register the iMac 800 on QA and try to boot the iso's . . . .


e.e.p.

---

### Post by este.el.paz on 2014-08-30
> **este.el.paz said:**
> Folks:

Beta testing 14.10:

Bug report #1363180
for  the alt install:  . .  entering various commands resulted in response: "claim error, can't  allocate e00000 at 0 x c2000000; claim error, can't allocate kernel  memory." Built 20140826.1 No further testing could be done.
for  live desktop:  Problem "replicated" using the desktop iso downloaded  today build 20140829 got to the Yaboot boot prompt window, entering  "live" and various other choices offered under "tab" brings identical  "claim error" . . . adding on some "radeonfb= items brings "invalid  device" . . . . So, I would again say that "testing failed" on the G4  iBook with 14.10 beta . . . could not proceed past the Yaboot window . .  . . 
Maybe for sh*ts & giggles I'll register the iMac 800 on QA and try to boot the iso's . . . .
e.e.p.

Problem was replicated while trying to "boot" the live Desktop in my  iMac G4 800 Mhz w/1GB RAM . . . identical "claim error" and "invalid  device" responses as with the iBook.  Couldn't get the iMac registered  with QA because the Xubuntu/Lubuntu 12.04 system "could not find gist" .  . . took a while to get apt to suggest "yorick" . . . but then running  the long command to generate a clipit statement did not provide a URL . .  . .  Anyway, same failure to get past the Yaboot window was discovered  using daily build 20140829 on the iMac . . . .

---

### Post by xeno74 on 2014-09-03
Hi All, 

I have just updated my  Lubuntu 14.04 to 14.10 on my AmigaONE X1000 PowerPC.  I want to do some beta testing. Srtest also  has installed Lubuntu 14.10 on his AmigaONE X1000 PowerPC. 

Here our experiences:  [http://forum.hyperion-entertainment.biz/viewtopic.php?f=35&t=2614](http://forum.hyperion-entertainment.biz/viewtopic.php?f=35&t=2614) 

Unfortunately, 3D acceleration doesn't work.  And all unofficial Mesa  packages don't work either. 

[[IMG]http://forum.hyperion-entertainment.biz/download/file.php?id=1351&t=1[/IMG]]("http://forum.hyperion-entertainment.biz/download/file.php?id=1351&mode=view")

Rgds, 

Christian

---

### Post by este.el.paz on 2014-09-03
xeno74:

That's great, I appreciate your efforts, but the devs want "formal testing" . . . apparently they don't read the forum posts, so you have to go to those QA links in the first post . . . and install the "hardinfo gist and clipit" apps and register your computer(s) in the QA testing thingie . . . and then run through their various tests . . . and then ***file bug reports*** on Launchpad . . . they only see that way . . . .  It's a little more time consuming . . . but it would help support PPC development if they can see that there are more than two people with PPC computers using ubuntu . . . .

e.e.p.

---

### Post by xeno74 on 2014-09-04
> **este.el.paz said:**
> xeno74:

That's great, I appreciate your efforts, but the devs want "formal testing" . . . apparently they don't read the forum posts, so you have to go to those QA links in the first post . . . and install the "hardinfo gist and clipit" apps and register your computer(s) in the QA testing thingie . . . and then run through their various tests . . . and then ***file bug reports*** on Launchpad . . . they only see that way . . . .  It's a little more time consuming . . . but it would help support PPC development if they can see that there are more than two people with PPC computers using ubuntu . . . .

e.e.p.

Thanks a lot for your answer. I'll register my PPC computers. By the way, I updated Lubuntu 14.04 to 14.10 on my Sam440ep Flex PowerPC.
Link: [http://forum.hyperion-entertainment.biz/viewtopic.php?f=52&t=2617](http://forum.hyperion-entertainment.biz/viewtopic.php?f=52&t=2617)

[[IMG]http://forum.hyperion-entertainment.biz/download/file.php?id=1355&t=1[/IMG]]("http://forum.hyperion-entertainment.biz/download/file.php?id=1355&mode=view")

---

### Post by este.el.paz on 2014-09-05
> **xeno74 said:**
> Thanks a lot for your answer. I'll register my PPC computers. By the way, I updated Lubuntu 14.04 to 14.10 on my Sam440ep Flex PowerPC.
Link: [http://forum.hyperion-entertainment.biz/viewtopic.php?f=52&t=2617](http://forum.hyperion-entertainment.biz/viewtopic.php?f=52&t=2617)


@xeno74:

Great.  Thanks for taking the time to do "formal" registration; and thanks for the link to the detailed step by step upshifting to 14.10.  I'm mostly doing LTS these days, and I upgraded to 14.04 on my iBook through the GUI, seemed to take quite awhile in comparison to the CLI method . . . .

e.e.p.

---

### Post by xeno74 on 2014-09-05
Lubuntu 14.10 PowerPC beta with the unofficial Mesa.

[[IMG]http://www.supertuxkart-amiga.de/amiga/Lubuntu_14.10_kernel_3.17-RC3_A1-X1000_Mesa_unofficial-thumbnail.jpg[/IMG]]("http://www.supertuxkart-amiga.de/amiga/Lubuntu_14.10_kernel_3.17-RC3_A1-X1000_Mesa_unofficial.jpg")

---

### Post by xeno74 on 2014-09-07
> **este.el.paz said:**
> xeno74:

That's great, I appreciate your efforts, but the devs want "formal testing" . . . apparently they don't read the forum posts, so you have to go to those QA links in the first post . . . and install the "hardinfo gist and clipit" apps and register your computer(s) in the QA testing thingie . . . and then run through their various tests . . . and then ***file bug reports*** on Launchpad . . . they only see that way . . . .  It's a little more time consuming . . . but it would help support PPC development if they can see that there are more than two people with PPC computers using ubuntu . . . .

e.e.p.

My PPC computers are already registered (AmigaOne X1000 and Sam440ep Flex). Link: [https://wiki.ubuntu.com/QATeam/Hardware](https://wiki.ubuntu.com/QATeam/Hardware) :-)

---

### Post by xeno74 on 2014-09-07
Srtest's Lubuntu 14.10 PPC desktop:

[[IMG]http://forum.hyperion-entertainment.biz/download/file.php?id=1357&t=1[/IMG]]("http://forum.hyperion-entertainment.biz/download/file.php?id=1357&mode=view")

---

### Post by xeno74 on 2014-09-07
I have created a bug report because of the 3D acceleration problem.

Link: [Bug #1366556 PPC: libgl1-mesa-dri doesn't provide 3D acceleration](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/1366556)

---

### Post by xeno74 on 2014-09-08
Spectre660 also has installed Lubuntu 14.10 PPC on his Sam440ep Flex.

[[IMG]http://forum.hyperion-entertainment.biz/download/file.php?id=1358&t=1[/IMG]]("http://forum.hyperion-entertainment.biz/download/file.php?id=1358&mode=view")

Link: [forum.hyperion-entertainment.biz]("http://forum.hyperion-entertainment.biz/viewtopic.php?f=52&t=2084&p=29525#p29517")

---

### Post by xeno74 on 2014-09-08
Spectre660 has added his Sam440ep Flex to the Ubuntu hardware list. :-) Link: [https://wiki.ubuntu.com/QATeam/Hardware](https://wiki.ubuntu.com/QATeam/Hardware)

There are a lot of PowerPC computers. :-)

[TABLE]
[TR]
[TD] PowerBook3,5[/TD]
[TD] PowerPC 7455[/TD]
[TD] Laptop[/TD]
[TD] [Specification]("http://phillw.net/hardware/g4.ti.hwinfo")[/TD]
[TD] [Lars Noodén]("https://launchpad.net/%7Elarsnooden/")[/TD]
[/TR]
[TR]
[TD] PowerMac3,6[/TD]
[TD] PowerPC 7455[/TD]
[TD] Desktop[/TD]
[TD][Specification]("http://phillw.net/hardware/0TLWxB86")[/TD]
[TD][keith-z]("https://launchpad.net/%7Ekeith-z")[/TD]
[/TR]
[TR]
[TD] Powermac 10[/TD]
[TD]  PowerPC 7447A[/TD]
[TD] Desktop[/TD]
[TD][Specification]("http://phillw.net/hardware/sKbfgcu3")[/TD]
[TD] [jlking3]("https://wiki.ubuntu.com/jlking3")[/TD]
[/TR]
[/TABLE]

[TABLE]
[TR]
[TD] Sam440ep Flex[/TD]
[TD] PowerPC 440EP Rev. C[/TD]
[TD] Desktop[/TD]
[TD] [Specification]("http://www.xenosoft.de/pastebin_Sam440ep_Flex")[/TD]
[TD] xeno74[/TD]
[/TR]
[TR]
[TD] Sam440ep Flex[/TD]
[TD] PowerPC 440EP Rev. C[/TD]
[TD] Desktop[/TD]
[TD] [Specification]("https://gist.github.com/anonymous/a631f910c4b49e6aaef2")[/TD]
[TD] Spectre660[/TD]
[/TR]
[TR]
[TD] [AmigaOne]("https://wiki.ubuntu.com/AmigaOne") X1000[/TD]
[TD] PowerPC PA6T[/TD]
[TD] Desktop[/TD]
[TD] [Specification]("http://www.xenosoft.de/pastebin_AmigaOne_X1000")[/TD]
[TD] xeno74[/TD]
[/TR]
[/TABLE]

[TABLE]
[TR]
[TD] PowerBook6,8[/TD]
[TD] PowerPC 7447A[/TD]
[TD] Laptop[/TD]
[TD][/TD]
[TD] [wxl]("https://wiki.ubuntu.com/wxl")[/TD]
[/TR]
[TR]
[TD] PowerBook3,5[/TD]
[TD] PowerPC 7455[/TD]
[TD] Laptop[/TD]
[TD][/TD]
[TD] [gregfaith nm_geo]("https://wiki.ubuntu.com/gregfaith%20nm_geo")[/TD]
[/TR]
[TR]
[TD] PowerBook6,3[/TD]
[TD] PowerPC 7455[/TD]
[TD] Laptop[/TD]
[TD][/TD]
[TD] [doak-jackson]("https://launchpad.net/%7Edoak-jackson")[/TD]
[/TR]
[TR]
[TD] PowerBook6,4[/TD]
[TD] PowerPC 7447A[/TD]
[TD] Laptop[/TD]
[TD][/TD]
[TD] [JonathanMarsden]("https://wiki.ubuntu.com/JonathanMarsden")[/TD]
[/TR]
[TR]
[TD] PowerMac8,1[/TD]
[TD] PowerPC PPC970FX[/TD]
[TD] Desktop[/TD]
[TD][/TD]
[TD] [Roberto Innocenti]("https://launchpad.net/%7Erobyinno")[/TD]
[/TR]
[TR]
[TD] PowerBook5,6[/TD]
[TD] PowerPC 7447A[/TD]
[TD] Laptop[/TD]
[TD][http://pastebin.com/aiAUx4wY](http://pastebin.com/aiAUx4wY)[/TD]
[TD] [Roberto Innocenti]("https://launchpad.net/%7Erobyinno") [/TD]
[/TR]
[/TABLE]

---

### Post by xeno74 on 2014-09-10
Javierdir has added his Sam460ex PowerPC to the Ubuntu hardware list: [https://wiki.ubuntu.com/QATeam/Hardware](https://wiki.ubuntu.com/QATeam/Hardware) :-)

---

### Post by este.el.paz on 2014-09-10
> **xeno74 said:**
> 
There are a lot of PowerPC computers. :-)

[TABLE]
[TR]
[/TR]
[TR]
[/TR]
[TR]
[/TR]
[TR]
[/TR]
[TR]
[/TR]
[TR]

[/TR]
[/TABLE]


Looks like mine are "too old" to be recognized . . . there was some issue about adding the G4 iBook and/or the older G4 iMac . . . .

e.e.p.

---

### Post by estrella-ed on 2014-10-09
Hello i would like to join, i have an emac g4 1.25 ghz powerpc, this is the first time i would do something like been a linux tester. 
But right now i have a yaboot misconfiguration problem so i cant even boot to my lubuntu session. 
I will post this issue on this forum. Maybe someone will help me.

---

### Post by este.el.paz on 2014-10-09
> **estrella-ed said:**
> Hello i would like to join, i have an emac g4 1.25 ghz powerpc, this is the first time i would do something like been a linux tester. 
But right now i have a yaboot misconfiguration problem so i cant even boot to my lubuntu session. 
I will post this issue on this forum. Maybe someone will help me.

estrella-ed:

Thanks for playing, in terms of the Yaboot issue, you might find your answer on the PPCFAQ wiki page . . . I know at some point I also messed up my Yaboot config . . . possibly I was able to fix it, or I might have just re-installed the linux system to do it??  I think the PPC FAQ might show how to correct problems with Yaboot, you could search Google to find it or for your problem and then look for the FAQ in the results.

Or, if you get the SuperGrub2 app and burn it to CD you can try to boot the linux system that way.  SG2 is a great app, it finds bootable systems and you can select what you want to boot into.

e.e.p.

---

### Post by xeno74 on 2014-10-10
Get the new Mac-on-Linux for Lubuntu PowerPC 12.04 or higher.

[IMG]http://www.supertuxkart-amiga.de/amiga/mol-kvm-logo.png[/IMG]

Download: [mol-kvm_0.9.73.0-ubuntu_powerpc.deb](http://www.xenosoft.de/mol-kvm_0.9.73.0-ubuntu_powerpc.deb)

---

### Post by este.el.paz on 2014-10-12
reprinted with general permission:

> Testing will begin 17-20 October, so mark your calendars for the final push. Release is on the 23rd.
 The official announcement follows.
 Thanks for all your hard work! 
 wxl
 > Date: Fri, 10 Oct 2014 11:54:54 -0400
> From: Nicholas Skaggs >
> To: "[EMAIL="ubuntu-quality@lists.ubuntu.com"]ubuntu-quality@lists.ubuntu.com[/EMAIL]"
>         <[EMAIL="ubuntu-quality@lists.ubuntu.com"]ubuntu-quality@lists.ubuntu.com[/EMAIL]>
> Subject: Final Image Testing for Utopic!
> Message-ID: <[EMAIL="5438014E.9060705@canonical.com"]5438014E.9060705@canonical.com[/EMAIL]>
> Content-Type: text/plain; charset=utf-8; format=flowed
>
> We're just about a week away from the first RC images for utopic hitting
> the image tracker. Please plan to help test the images as they appear.
> RC images should appear on the tracker by Oct 17th and no later than
> October 20th.
>
> Never tested an image before? Checkout the information on the wiki,
> [https://wiki.ubuntu.com/Testing/QATracker](https://wiki.ubuntu.com/Testing/QATracker) and
> [https://wiki.ubuntu.com/Testing/ISO/Walkthrough](https://wiki.ubuntu.com/Testing/ISO/Walkthrough). You can sharpen your
> skills right now by testing a daily image. If you encounter any issues
> during testing please don't hestiate to ask for help. Don't forget, you
> can talk in realtime on IRC on freenode @ #ubuntu-quality.
>
> [http://webchat.freenode.net/?channels=ubuntu-quality](http://webchat.freenode.net/?channels=ubuntu-quality)
>
> A big thank you to all of you who have and will participate in making
> sure utopic is the best quality it can be. Happy Testing!
>
> Nicholas



---

### Post by este.el.paz on 2014-10-17
reprinted w/ permission:  Looks like the alt installer bug is fixed . . . plz test and report to QA

> more on the backstory here:
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1380774](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1380774)

Lubuntu can now get to testing on the Alternate images!
[http://iso.qa.ubuntu.com/qatracker/milestones/325/builds](http://iso.qa.ubuntu.com/qatracker/milestones/325/builds)
I've taken care of Lubuntu Alternate i386 guided myself to confirm
this bug fix on 20141017.1 :)

Ubuntu Server 20141017 does NOT have the fix. I'll leave it to the
Ubuntu Release Team to take care of that one.

wxl

---

### Post by xeno74 on 2014-10-19
Srtest added his AmigaONE X1000 PowerPC to the [Ubuntu hardware list](https://wiki.ubuntu.com/QATeam/Hardware). :-)

**Lubuntu 14.10** PowerPC with Mac OS X 10.4.11 and with the unofficial Mesa on an AmigaONE X1000:

[[IMG]http://forum.hyperion-entertainment.biz/download/file.php?id=1401&t=1[/IMG]]("http://forum.hyperion-entertainment.biz/download/file.php?id=1401&mode=view")

---

