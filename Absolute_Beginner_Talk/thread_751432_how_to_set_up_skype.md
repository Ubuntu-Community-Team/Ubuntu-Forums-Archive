---
title: "how to set up skype"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by cmay on 2008-04-10
hi .
i am a bit new to this whole internet thing but i have just been talked into buying a webcam and trying to install skype by one of my freinds. the main trouble i have is that i do not know so much about internet and i dont see that well anymore. i was operated in my eyes some years ago. i can give the webcam back tommorow to the store if i cant get it to work under linux. but i can honestly not even read the small print in the folder inside the webcam box. 
is there any one whit a coupel of spare minuttes that could help or guide me just a bit in the right direction. 

its ubuntu 7.10 i plan for this to have installed skype on. 
i just got me a new cheap computer i wanna use only for the internet.

thanks

---

### Post by tamoneya on 2008-04-10
what is the camera model number.  we will help you find the correct drivers and commands that you have to run if you can tell us which camera you have.

---

### Post by cmay on 2008-04-10
thanks a lot.
its a logitech quickcam connect it says whit big prints on the box
there is a skype mark on it and a vista ready mark but thats about all i can from lokking at it. that doesnt help that much does it?.
any way i will be happy to save some money on the phonebills if i could.

i will try read as good as i can on the manuals but i can not say for sure its the right info i cnan find out to post .
 thanks for the help apriciate it.

---

### Post by Fire_Chief on 2008-04-10
To install Skype for Linux, simply go to the Skype website, click on Download Skype and then select the Ubuntu 7.04+ option and it will download the latest Skype for Linux client ( 2.0.0.68 ). :guitar:

---

### Post by StRiFe10101 on 2008-04-10
I'm quite new to linux also, but the way I installed skype was by installingl the medibuntu repository then just use the synaptic package manager to install it.  

First you need to install the repository.  Open up a terminal.  and type or paste the following lines... with enter following each line.

sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list

then....

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

then....

sudo apt-get update

then....

sudo apt-get install skype

That should get skype installed.  From there we can work on the webcam.

Again, I'm kinda new also.  If I left something out I apologize.  I'm sure someone will correct me.

Also, I'm kinda ignorant and can't figure out how to put the code and quotes in the nice boxes to make things look nice and organized.  Can someone help me out with a link or something?

---

### Post by Fire_Chief on 2008-04-10
The code boxes are added by clicking on the # sign in the message composer window to the right of the hyperlink and other formatting buttons. :)

---

### Post by StRiFe10101 on 2008-04-10
Like this?

> The code boxes are added by clicking on the # sign in the message composer window to the right of the hyperlink and other formatting buttons. 

Thanks

---

### Post by cmay on 2008-04-10
thanks 
i will try see if ican get this skype right .
i am not new to linux if 2 years uf ubuntu usage  counts so this should be pretty easy for me to do. however i am getting a real bad headache from this reading so hard that i may quit in the middle of "die trying if i have too " .
should i not get back too you whitin that long i probely have gone too bed whit heavy migraine .
still you should know i am pretty gratefull for the effort and help .
any way here i go to the  terminal and start typing some apt-gets and see what goes like. 

oh by the way the computer guy that sold me this computer and webcam was pretty interrested in ubuntu. i wish i could go tell him it was a piece of cake installing it.

i get back too you if i succesed

thanks. a lot.

---

### Post by cmay on 2008-04-10
hi there again.
i have given up on the terminal on this and just downloaded skype for linux from the site.
its the feity fawn package and i snatched the debian etch packages while i was thee to be on the safe side.

i just dont know if thats all good or should i wait to some one can help get the exact right packages.

i will not be able to use the terminal i can see that.
i have used ubuntu for a some time i think but its noot before now i 
start really getting to know the commandline and stuff.
i have the menu bars and desktop really wide so i can see better but still the 
terminal i do not see good enough to do this job i am afraid.

i looked in the synaptic packagemanager but i could not find the skype whit search for function.
if these deb packages from skype is ok i can go on whit it 

any way 
thanks for the help.

---

### Post by StRiFe10101 on 2008-04-11
[SIZE="4"]I imagine that .deb package that you downloaded form skype would be ok considering what Fire_chief said....

> To install Skype for Linux, simply go to the Skype website, click on Download Skype and then select the Ubuntu 7.04+ option and it will download the latest Skype for Linux client ( 2.0.0.68 ). 

If you downloaded the .deb package to your desktop you should be able to double click on it and hit install with no problem without having to use the package manager.  Do you recall what location on your PC you downloaded it to?

I hope the size increase helps.
[/SIZE]

---

### Post by hyper_ch on 2008-04-11
google for "medibuntu", read there "howto" and you're set....

---

### Post by idoisler on 2008-04-21
Hi i did everything that was written but still i can't get skype to work 
i have a 64 ubuntu 7.10

and this is what it tells me 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting skype-static instead of skype
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  skype-static: Depends: ia32-libs (>= 1.6) but it is not installable
                Depends: lib32asound2 (> 1.0.14) but it is not installable
                Depends: lib32gcc1 (>= 1:4.2.1) but it is not installable
                Depends: lib32stdc++6 (>= 4.2.1) but it is not installable
                Depends: libc6-i386 (>= 2.6-1) but it is not installable
                Depends: dbus-x11 (>= 1.0.0) but it is not installable
E: Broken packages


any ideas ???

---

### Post by montgoja on 2008-04-22
Hi,
Other users have posted to visit the website and download the Ubuntu 7.04+ package directly.  It gives you what is called a .deb package (which is, in a nutshell, like the .exe install files that Windows uses) and if you double click it, it will build the package and install it to your computer all by itself (which saves you the trouble of working through the command line and downloading all the additional dependencies and everything else by hand).

I've already installed Skype and it works like a charm - at least to chat with.  I haven't had the chance to test out the webcam.  I, too, have just purchased a Logitech QuickCam (Camorama says it's a QuickCam EC) and I'd like to make sure that I can get this to work on Skype.

I've installed both Cheese and Camorama to test this cam out, and I'm slowly but surely getting some responses from the programs.  Camorama has been my most successful attempt so far - I've gotten a very dark blue video image of myself before the program has hung up.  I'll keep trying to putz with the programs I can find, but I thought I'd throw this all out here to see if there's any advice on making this new adventure run smoothly.

---

### Post by Machin.Truc.Bidule on 2008-05-19
I would say you need to install or upgrade a few dependencies, such as libasound2. 

> **idoisler said:**
> The following packages have unmet dependencies:
  skype-static: Depends: ia32-libs (>= 1.6) but it is not installable
                Depends: lib32asound2 (> 1.0.14) but it is not installable
                Depends: lib32gcc1 (>= 1:4.2.1) but it is not installable
                Depends: lib32stdc++6 (>= 4.2.1) but it is not installable
                Depends: libc6-i386 (>= 2.6-1) but it is not installable
                Depends: dbus-x11 (>= 1.0.0) but it is not installable
E: Broken packages

any ideas ???

Skype says you need the following extra packages installed as well as the kit provided:
    * Qt 4.2.1+
    * D-Bus 1.0.0
    * libasound2 1.0.12

The mentioned package of libasound2 is no longer available. But later versions are available ... [http://packages.debian.org/etch/libasound2](http://packages.debian.org/etch/libasound2)
Which in turn may have other dependencies, e.g. to libc6

Well, this is where I am stuck. Having tried Synaptic to fetch me a new version of libasound2, but keep getting versions too old. My next move will be trying to install libasound2 using a version downloaded myself from Debian.

BTW, Synaptic did not work for me to install Skype so I had to install Gdebi package installer... works much better with .deb files on your local PC.

---

### Post by jklm988 on 2008-05-19
[&#32593;&#31449;&#20248;&#21270;](http://www.asp100.cncn)&#21487;&#20197;&#20026;&#32593;&#31449;&#36816;&#33829;&#24102;&#26469;&#21738;&#20123;&#25928;&#26524;?&#32593;&#31449;&#20248;&#21270;&#19982;[&#25628;&#32034;&#24341;&#25806;&#20248;&#21270;](http://www.ckcf.com.cn)&#26159;&#20160;&#20040;&#20851;&#31995;?&#20026;&#20160;&#20040;&#35828;[&#32593;&#31449;&#20248;&#21270;](http://www.ce36.cn)&#26159;&#33853;&#21518;&#30340;&#26041;&#24335;?&#25552;&#20379;&#26368;&#19987;&#19994;&#30340;&#32593;&#31449;&#20248;&#21270;&#20998;&#26512;&#19982;&#32593;&#31449;&#20248;&#21270;&#35299;&#20915;

---

### Post by Alan Coleman on 2008-05-20
ok. I got skype following above info. But when I try to make an address it wont have it. Have filled in all the boxes with the little red stars next to them and the sign up box remains grayed out. Is there something im not getting here???

---

### Post by montgoja on 2008-05-23
> **Alan Coleman said:**
> ok. I got skype following above info. But when I try to make an address it wont have it. Have filled in all the boxes with the little red stars next to them and the sign up box remains grayed out. Is there something im not getting here???

It could be a number of things.  Have you tried making a different name for yourself?  The one you want may be already in use.  Also, make sure your password is typed the same in both boxes.  They're simple answers, but it's all I can think of.

---

