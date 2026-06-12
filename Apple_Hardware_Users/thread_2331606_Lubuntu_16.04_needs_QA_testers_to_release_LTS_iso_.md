---
title: "Lubuntu 16.04 needs QA testers to release LTS iso for PPC users!!!"
date: 2016-07-23
forum: Apple Hardware Users
---

### Post by este.el.paz on 2016-07-23
Folks:

Anyone still using PPC flavors of ubuntu should be aware that there are less and less options available to run on our machines.  In Ubuntu there is the mini installer option, which provides a base system to which a DE can be added; there is Ubuntu-MATE; and there has been Lubuntu.  Lubuntu provides the integrated base and DE generally the lightest option in the Ubuntu family, but, due to lack of testing there is now no LTS release for 16.04 under the Lubuntu banner.  Likely this would be the ***last*** version of Lubuntu available to PPC users.  On my iBook G4 the beta of Lubuntu runs better and w/o boot params than 14.04 did.

So, anyone interested in the "full release" version the Lubuntu team is requesting that testers run through the QA testing process . . . after that they can qualify it to full release . . . .  Please scroll through this page and find your way to "Lubuntu 16.04 QA Testing" and give them some feedback ASAP.

Edit: Looks like only the daily Xenial Lubuntu PPC desktop is available for testing, the others appear to be archived?

[http://iso.qa.ubuntu.com/qatracker/milestones/351/builds/126662/testcases](http://iso.qa.ubuntu.com/qatracker/milestones/351/builds/126662/testcases)

[https://wiki.ubuntu.com/Lubuntu/Testing#Milestone_releases](https://wiki.ubuntu.com/Lubuntu/Testing#Milestone_releases)

---

### Post by sudodus on 2016-07-25
After release, a version is archived - and no longer available for testing. This is general for all Ubuntu flavours and versions if I understand correctly. But there are several (current) daily iso files,

- ***for the next version***, now (July 2016) Yakkety Yak to be released as 16.10.

- ***for the LTS releases*** with yet another point release to be developed and tested

. ***16.04 LTS*** (16.04.1 LTS was released less than a week ago.) Unfortunately the powerpc iso files were not tested, so they were not released [1]. But if we get them tested, the following point releases should be OK, 16.04.2 LTS ... 16.04.5 LTS.

Notice that the original Lubuntu 16.04 LTS was released with a desktop iso file and an alternate iso file for powerpc. It is possible to install it and update & dist-upgrade to the current 16.04.1 LTS version, but would be much more convenient to start from the 16.04.1 LTS or other newer iso file. See this link,

[cdimages.ubuntu.com/lubuntu/releases/xenial/release](http://cdimages.ubuntu.com/lubuntu/releases/xenial/release/)

. ***14.04 LTS*** (14.04.5 LTS will be released soon). There is a daily iso file for testing (a powerpc desktop iso file). Welcome to test it :-)

[COLOR="#606060"]. ***12.04 LTS*** (no more point release, so no daily iso file to test).[/COLOR]

[hr][/hr]
[1] Lubuntu 16.04.1 powerpc was not released, but there are ***work-arounds*** for 16.04.x LTS. Please notice that these files are not officially recommended, only suggested by me as a fellow Lubuntu user and tester.

- The daily iso files of July 24 are available at [http://phillw.net/isos/lubuntu/xenial/testppc/](http://phillw.net/isos/lubuntu/xenial/testppc/) and these files are very similar to those of July 20 (which would have been released if tested and verified).

- The best alternative for many of us is probably the current daily (alternate) and daily-live (desktop) iso files, that you find via the testing tracker (the links in *este.el.paz*'s post #1).

These current daily and daily-live images cannot be recommended like released versions for beginners, because they are new and not tested.

In the best of worlds, you, who own PowerPC computers, will get interested enough to keep testing the current xenial iso files, so that they will be tested and released as Lubuntu 16.04.{2,3,4,5} LTS when the time comes for those releases (starting with 16.04.2 six months from now).

Please start reporting test results as soon as possible but at least a few weeks before each deadline to give the developers time enough to fix bugs before the release :-)

---

