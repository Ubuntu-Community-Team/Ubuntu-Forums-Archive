---
title: "installing drivers and stuff without an internet connection?"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by threeonethree on 2007-07-24
my friend has a computer with ati redeon 9550 card and NO INTERNET CONNECTION.. he wants to ditch windows xp home and install ubuntu feisty fawn instead (he was impressed by compiz fusion and free games like battle for wesnoth/world of padman/warsow etc) ... is there any way he can install drivers for his radeon card without connecting to the net? (i just installed my nvidia ones by clicking on restricted driers and it dled and installed for me..

is there any .deb for them? i tried on get deb but cudnt find.. please help

---

### Post by wolfen69 on 2007-07-24
unless  you can write your own drivers, you NEED an internet connection. or a friend that can bring them over.

---

### Post by Cypher on 2007-07-24
One of the nicest features of Ubuntu is the ability to download application updates and drivers from the 'Net quickly and easily. Most applications usually also have dependencies and figuring out what they are and downloading them individually is going to be a pain.

Having access to the Internet will make your friend's life considerablly easier. Is there any particular reason he doesn't have 'Net access in Ubuntu??

---

### Post by threeonethree on 2007-07-25
yeah because he lives in a shitty third world country and doesnt have a phone line at his home to connect to the internet via dialup or adsl.. and yeah he doesnt even have some other  good cable internet providers in his area.. is that reason enough??

anyways isnt there ANY WAY to make ubuntu usable without a dam internet connection?


actually i do have a 2 mbps adsl connection, is there anyway i can download the drivers /dependencies etc on my computer than take my hard disk to his pc to install it? some guide please?

---

### Post by Mornedhel on 2007-07-25
Yes.

Have a look at apt-zip. It's for users familiar with the command-line though, but it will generate a script that downloads the necessary packages (to be executed on the computer with Internet access), and a script that installs them (to be executed on the other computer).

But ATI driver installation is pretty straightforward, find a guide that describes the installation procedure (there is one in the stickies, I believe) and uses apt-get only (no Restricted Drivers easy-to-use application), manually download the packages from packages.ubuntu.com, and install them in the required order, sticking as close as possible to the guide.

---

### Post by threeonethree on 2007-07-25
how do i download packages from packages.ubuntu.com ?? 

for example [http://packages.ubuntu.com/feisty/comm/asterisk-app-dtmftotext](http://packages.ubuntu.com/feisty/comm/asterisk-app-dtmftotext)

how would i download that package and install to my computer? there no link with a .deb?

---

### Post by Mornedhel on 2007-07-25
[amd64]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=amd64&file=pool%2Funiverse%2Fa%2Fasterisk-spandsp-plugins%2Fasterisk-app-dtmftotext_0.0.20060218-2_amd64.deb&md5sum=3b1f1ae3accaf881020c864dfa3ae854&arch=amd64&type=main") [[list of files]("http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=asterisk-app-dtmftotext&version=feisty&arch=amd64")]  13.8 72  [i386]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fa%2Fasterisk-spandsp-plugins%2Fasterisk-app-dtmftotext_0.0.20060218-2_i386.deb&md5sum=094257b06102fed217a4469c1ffb3223&arch=i386&type=main") [[list of files]("http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=asterisk-app-dtmftotext&version=feisty&arch=i386")]  13.4 68  [powerpc]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=powerpc&file=pool%2Funiverse%2Fa%2Fasterisk-spandsp-plugins%2Fasterisk-app-dtmftotext_0.0.20060218-2_powerpc.deb&md5sum=d7e0993d22ee185f024afcb22bb5a397&arch=powerpc&type=main") [[list of files]("http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=asterisk-app-dtmftotext&version=feisty&arch=powerpc")]  15.3 72
It's the i386 link.

---

### Post by threeonethree on 2007-07-25
thanks for help... one last thing i would like to know is that if he had internet he could have easily installed ati graphics drivers from restricted drivers..  but on my pc how can i know which packages i need to download for him to install ati drivers??

like for xgl i need xserver-xgl and i can search that on packages.ubuntu.com and download those packages. but what about the ati drivers?

---

### Post by Mornedhel on 2007-07-25
Once you know the name of the package you want to install, go to a terminal and type :

apt-cache show <package_name>

There is a section called Depends, which contains every package yours depends on. There is also a way to obtain a less cluttered list with dpkg, but I am not too confortable with it.

---

### Post by threeonethree on 2007-07-25
thats what im asking:-s how do i to know the name of the packages i need to install ati drivers?

---

### Post by Mornedhel on 2007-07-25
xorg-driver-fglrx , but first check in the description if it handles your card (some unlisted cards will be handled fine nonetheless)

---

### Post by threeonethree on 2007-07-25
thanks for ur help.. 


one of my friend has a ati 9550 card and other has ati x1900. i know it will work for both of them :-s.. ok now i know that that i need xorg-driver-fglrx  package and its dependencies downloaded on my computer then i just need to take my hdd to them :P

now that i have the name.. which method would u prefer to download these packages to the computer??

1) ubuntu.packages.com?
2) sudo apt-get build-dep -d xorg-driver-fglrx ?
3) the thing that u said :-s

---

### Post by Mornedhel on 2007-07-25
Overall, the best thing would be, since you haven't installed xorg-driver-fglrx for yourself :

sudo apt-get clean
sudo apt-get -d install xorg-driver-fglrx

then go to /var/cache/apt/archives and get all the .deb files there.

Then they'll miss dependencies only if you have installed some other stuff that also relies on some of those dependencies (let's hope not).

(The "other thing I said" was only to list the dependencies, not to retrieve any package.)

---

### Post by threeonethree on 2007-07-25
kartik@ubuntu:~$ sudo apt-get clean
kartik@ubuntu:~$ sudo apt-get -d install xorg-driver-fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  nvidia-glx
The following NEW packages will be installed:
  xorg-driver-fglrx
0 upgraded, 1 newly installed, 1 to remove and 31 not upgraded.
Need to get 6143kB of archives.
After unpacking 3965kB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.


it wants to remove the dam nvidia drivers from my pc lol :-s

would the command be sudo apt-get -d xorg-driver-fglrx?

im sure i dont need to put the "install" thing there? or should it be sudo  apt-get build-dep -d xorg-driver-fglrx 

so it builds and downloads dependencies too?

---

### Post by Mornedhel on 2007-07-25
build-dep is for sources, you don't need that for now. The command * is * install, but you shouldn't run it anyway.

I was afraid something like that would happen, but I was hoping you hadn't installed any drivers yet. Oh well. I'm not sure if accepting, going through the rest of the procedure, and finally reinstalling nvidia-glx would work, but anyway, while browsing Synaptic I found out xorg-driver-fglrx is available from the install CD, so your friends most likely already have the package somewhere (and its dependencies).

Edition : apt-get works this way :

apt-get clean removes downloaded packages from your cache, what's installed stays installed.
apt-get remove <package> removes the installed package, what's downloaded stays downloaded. Use apt-get --purge remove <package> to also remove some configuration stuff related to the software <package> is about.
apt-get install <package> downloads (if necessary) and installs a package, and downloads and installs whatever it depends on (if necessary). The -d switch was there so nothing would be installed, only downloaded, and I thought that would prevent conflicts with existing packages. Apologies. (Good thing you said "no", btw)

For the casual user, Add/Remove and/or Synaptic is better though (what with their being GUIs and all).

---

### Post by threeonethree on 2007-07-25
so what do i need to do now? :-s no solution? thanks for taking interest in my problem

---

### Post by Mornedhel on 2007-07-25
Sorry if I wasn't clear enough, English is not my first language.

The xorg-driver-fglrx package is already available on the CD you installed Ubuntu with. (And probably the dependencies are, too.) You can install it from the CD.

---

### Post by threeonethree on 2007-07-25
how?

---

### Post by Mornedhel on 2007-07-25
First make sure the CD is in the tray and the tray is closed. The tray needs to be attached to the computer you want to install packages on :P

Then go to Synaptic, mark relevant packages for installation (dependencies will automatically mark themselves), and Apply. I've never installed packages from the CD (apart from the actual Ubuntu installation procedure), so I don't know if there is some other manipulation involved, there are some options in Settings -> Repositories.

---

### Post by threeonethree on 2007-07-25
thanks ..i will try it :-s but if the drivers were already on the cd why does the sherlock restricted manager downloads them from the internet?

---

### Post by Mornedhel on 2007-07-25
That's the standard procedure. Debian based distributions are at their best with an Internet connection, but they can nonetheless work very well without one. The CD packages are just there in case, I guess. Plus, they're outdated compared to the ones you will find on the repositories.

---

