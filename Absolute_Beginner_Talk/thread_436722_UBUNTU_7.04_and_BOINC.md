---
title: "UBUNTU 7.04 and BOINC?"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by Sparky Jim on 2007-05-08
Guys and Gals, I am sorry if this seems a really stupid question to you guys but I am using Linux for the very first time and I think I may be being blonde.:confused: 

I run BOINC on several machines and this installation of Ubuntu is a test to see how it fairs against Winblows XP Pro (Sorry for swearing). So far it is VERY positive, however I have hit a snag, I have downloaded BOINC 5.08.16 to my desktop but when I try to install it I get an error message stating that the coding is incorrect and that no matter version of coding I pick I get the same message.:( 

Am I doing something wrong or is this a software problem, have I got to do something different to get it to install?:confused: 

Your help in solving this glitch would be much appreciated. 

Thanks

Jim:popcorn:

---

### Post by rai4shu2 on 2007-05-08
It would probably be easier to install through Synaptic or Adept. Just load one of those package managers and do a search for "boinc".

---

### Post by KevinCole on 2007-06-19
If you're still not having much luck with BOINC, add the following two lines to your **/etc/apt/sources.list**
[INDENT][B][COLOR="Blue"][FONT="Courier New"]deb http://pkg-boinc.alioth.debian.org/ubuntu feisty universe
deb-src http://pkg-boinc.alioth.debian.org/ubuntu feisty universe[/FONT][/COLOR][/B][/INDENT]
Then with your favorite installer (**apt-get**, **synaptic**, **adept**, etc) update or reload, and now you should find boinc packages.

---

### Post by Papi-KB7VGW on 2007-06-19
Hi, I have boinc running on my Ubuntu notebook and it works ok.  The synaptic package manager shows both boinc client and boinc manager.  they are version 5.4.11.  good luck

---

### Post by Skip Da Shu on 2007-11-11
I just installed  7.10 and was able to get BOINC v5.8.10 installed with this:

sudo apt-get install boinc-client boinc-manager

Replacing the install command in this [WIKI]("https://wiki.ubuntu.com/BOINC") with the one above and then following the rest if his instructions worked for me.

Skip 'the super noob'

---

### Post by sabauma on 2008-01-16
Use the synaptic package manager. If you use the add and remove programs utility it will only install the graphical interface but not the client itself. Go to the synaptic package manager, do a search on BOINC, then select boinc-manager AND boinc-client for installation. This worked for me without a problem.

---

### Post by crawdaddyangry on 2008-01-19
Hi


Reply #5 just worked for me. Thank you  :)

---

### Post by coolbrook on 2008-01-22
There's also a most recent version made specifically for Ubuntu.  It's not yet in the repositories but you can download and install the version from Berkeley.

[http://boinc.berkeley.edu/download_all.php](http://boinc.berkeley.edu/download_all.php)

---

### Post by cavebear53 on 2008-02-13
> **sabauma said:**
> Use the synaptic package manager. If you use the add and remove programs utility it will only install the graphical interface but not the client itself. Go to the synaptic package manager, do a search on BOINC, then select boinc-manager AND boinc-client for installation. This worked for me without a problem.

Hi all New to Ubunto but old Boinc user . Thanks got it running tryed the add&remove but the client would not connect to LocalHost I could not fig out why. Thanks again. =D>

Ron

---

### Post by Jack Shaftoe on 2008-02-16
> **sabauma said:**
> Use the synaptic package manager. If you use the add and remove programs utility it will only install the graphical interface but not the client itself. Go to the synaptic package manager, do a search on BOINC, then select boinc-manager AND boinc-client for installation. This worked for me without a problem.

Hi, new here, new to Ubuntu as of this afternoon, similar issue.  I downloaded 5.10.28 build of BOINC and try to select it with Synaptic, but it is grayed out.  I also tried searching Synaptic for "BOINC" and it comes back with 0 results.  

:confused:

Thanks for any help.

---

### Post by Jack Shaftoe on 2008-02-16
I should mention I am running 7.10 x64.  Thanks,

---

