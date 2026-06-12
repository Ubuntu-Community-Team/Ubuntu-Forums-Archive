---
title: "Steps for Installing Kdevelop ???"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by killerfrog on 2006-10-07
Hi,

I'm somewhat a beginner (N00B) in Linux. I had to use Fedora core on my computer 2 years ago for programming C++ with my school and they were restricting us at using Kdevelop. Now, I've buyed a Dell Inspiron 9400 and fedora core 5 need too much configuration for what I'm able to do and what I want to : wireless don't work, modem don't work, resolution is streeched and 1440 x 900 isn't supported nor the sound etc etc. So a friend has spoken me about Ubuntu. I told me that, as beeing a Linux rebarbative that this distribution could be good for me. So I've tried both Kubuntu and Ubuntu over VMware (I still don't trust it as independent operating system) and tried to install Kdevelop because I still need it for my school. I just don't know how to do it !!! So if someone could tell me STEP by STEP what to do to install Kdevelop (I would prefer it running under Gnome because I prefer the look and because it supports my resolution without working around) on Ubuntu (or Kubuntu if impossible or too complicated over Ubuntu) this would be very nice. Plese keep in mind that I'm a N00B and I hate Linux because there is so much things to do on a command prompt and I HATE console !!

If this works well under VMware, I will consider installing it on a Linux partition because Ubuntu (at first impression) look a lot more a finished product as Fedore Core 5 !!

[COLOR="Red"]So as a resume for those that don't want to read the whole text :

Could some one tell me (a complety N00B) step by step for installing Kdevelop on Ubuntu (first choice) or Kbuntu if impossible on Ubuntu !![/COLOR]

Thx a lot in advance to everyone that could gimme and extra hand help !

---

### Post by jordanmthomas on 2006-10-07
System --> Administration --> Synaptic Package Manager
Settings --> Repositories
Make sure all the repositories are selected
Click Reload
Click once in the big list and begin typing kdevelop
You'll see it come up in the list
Double click it.
Because it's a KDE app, you will have to install a lot of stuff, but it will be done automatically.
Once you're done with that, it should be in your menus
If not, press Alt + F2 and type kdevelop 

Just a note, the look won't match your Gnome desktop because it's a KDE program

---

### Post by killerfrog on 2006-10-08
Thx a lot for your help,

There was one step missing in your explanations.

I had to go in synaptic preferences and click every update suppliers that were not installed as default. Without doing this, there were no kdevelop in the list !

I tried the hello word compilation.

Got and error telling me there were no make. So I installed it using Synaptic. 
Then now it tells me "error : np acceptable C compiler found in $PATH

What should I do now ?

---

### Post by podunk on 2006-10-08
Got to Synaptic and install 
build-essential

This has several compilers buit in.

---

### Post by mysticrider92 on 2006-10-08
For the C compiler, you should just be able to install GCC and G++ (I think that is their names). They should work fine.

---

### Post by killerfrog on 2006-10-08
With installing build-essential, it goes further, but there is still an error : "Cant' find X includes. Please check your installation and add the correct paths!"

---

### Post by jordanmthomas on 2006-10-08
You need X includes for a hello world program?
Maybe install the xorg-dev package?

---

### Post by killerfrog on 2006-10-09
I've installed xorg-dev and got a new error about QT4

So I've installed QT3.

Then tried to compile again and got

"in the prefix, you've chosen, are no KDE headers installed. This will fail."

I'm searching for a solution. If someone knows how to go around, would be nice to tell !

Thx

---

### Post by killerfrog on 2006-10-09
I've installed kdebase-devel and kdelibs-devel and now it compile !!

Yee this seems to finaly works

---

### Post by killerfrog on 2006-10-09
So here are steps for installing Kdevelop under Ubuntu (after a lot of workaround !!)

System --> Administration --> Synaptic Package Manager
configuration/depots and selec all of them
Settings --> Repositories
Make sure all the repositories are selected
Click Reload
Click once in the big list and begin typing kdevelop
Select everything that as "kdevelop" in it's name
Select build-essential
Select xorg-dev
Select qt3-aps-dev
Select kdebase-devel
Select kdelibs-devel
Select all automake

Now you should be able to compile Hello World ! (at least, this has worked for me !!)

Thx for every help I've got. Without it, I wouldn't be able to write down this resume !

---

### Post by tuvu on 2006-12-02
Sorry for bumping this old post, but I'm having trouble with Kdevelop installation. I searched around forum and couldnt find any solution.

I'm using ubuntu 6.10, and I cant install kdevelop using Synaptic Package Manager.

Here is my sources.list:
---------
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://kubuntu.org/hoary-kde341](http://kubuntu.org/hoary-kde341) hoary-updates main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) hoary main restricted
---------

I searched for kdevelop, then I select and install kdevelop (4.3.2.1). And I got this error:


Depends: kdelibs4 but it is not going to be installed
 Depends: kdebase-bin but it is not going to be installed
 Depends: kdevelop-data but it is not going to be installed
 Depends: kdevelop-plugins but it is not going to be installed
 Depends: kdesdk-misc but it is not going to be installed

When I tried to installed each component listed above, for example kdelibs4, I got another error:

kdelibs4:
 Depends: libcupsys2-gnutls10 (>= 1.1.20final-1)
 Depends: kdelibs-bin (= 4:3.4.1-0ubuntu0hoary1)

(And isnt it supposed to install all the dependencies automatically ?)

I think my problem is the sources.list (though I have the latest ubuntu distribution) Could anyone give me a complete sources.list or know what I did wrong here ? Thanks :D

---

### Post by qamelian on 2006-12-02
I think you just need to uncomment some of the repositories in your sources.list file.

---

### Post by tuvu on 2006-12-02
> **qamelian said:**
> I think you just need to uncomment some of the repositories in your sources.list file.

Thanks, it worked :)

---

