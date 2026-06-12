---
title: "I need AptOnCD and all its packages"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by medya on 2007-11-29
hey I dont have internet on ubuntu , so I can't use synaptic package manage to download  AptOnCD ,

I tried to download Apt-On-CD manualy in windows, but it told me some librarys are missing,
I downloaded those libs and now it says some other thigns are missing .

can somebody kindly give me AptOnCD and all its related packages , to download,


I need it .

thank you.

---

### Post by PmDematagoda on 2007-11-29
I realise that this does not answer your question, but why don't you have internet on Ubuntu?

---

### Post by ugm6hr on 2007-11-29
Also not strictly an answer to your question - but you can download updates / programs from outside Ubuntu, and then transfer using this:
[http://nonetdebs.homeip.net/](http://nonetdebs.homeip.net/)

How it works etc is explained here:
[http://ubuntuforums.org/showthread.php?t=572819](http://ubuntuforums.org/showthread.php?t=572819)

But I second the question - why does internet not work on Ubuntu?

PS: Apt-On-CD is presumably version specific - might be best to specify if which version of Ubuntu you are using.

---

### Post by PmDematagoda on 2007-11-29
In addition to what ugm6hr said, I would also like to say this:-

If you do not have internet on Ubuntu then you cannot use AptOnCD at all unless you use it on another Ubuntu PC which does have internet access since it requires the internet to download all the packages in the repos before converting them to the CD. 

So basically even if you get AptOnCD installed on Ubuntu it still would not work since it must have the internet to perform it's function.

---

### Post by medya on 2007-11-29
I used to have ADSL internet, now in iran they no longer have that internet for my house... I use dial up again .
and my dial up modem doesnt work in ubuntu.

actually I wanna back up all my installed packageas using AptOnCD and then install the new version of the ubuntu (7.10)

---

### Post by PmDematagoda on 2007-11-29
From what I know about AptOnCD, that is not what it does, what it does is that it gets all the packages in the repositories and transfers them to a CD so that they can be carried around and be used to install packages on Ubuntu or Debian PCs without access to the internet.

---

### Post by medya on 2007-11-29
PmDematagoda is right, actualy it is the philosphy of AptOnCD .  :)

---

### Post by medya on 2007-11-29
in ubuntu packages here is its page 
[http://packages.ubuntu.com/feisty/admin/aptoncd](http://packages.ubuntu.com/feisty/admin/aptoncd)

but I wan a simple way to download all the dependencies.... without downloading each one manualy -and each of them has its own dependency- so it will go until 3-4 levels of dependenices....

---

### Post by natehatewindows on 2007-11-29
i think it just gets the packages you installed. it looks in your /var/cache/apt folder and burns that stuff

---

### Post by natehatewindows on 2007-11-29
if it does acces the repo i want to know how to do it....i just tired and there is not even an option to connect to a repo.

---

### Post by PmDematagoda on 2007-11-29
You are right natehatewindows.

> With APTonCD you be able to...

Backup
    Backup all downloaded packages (via apt-get, aptitude and synaptic) to restore later.

Transport
    Take with you all your favorite packages, in a removable repository where you can install then all on anytime, anytime.

Download
    Get an entire repository, or a specifc section. Simply point-and-click, and in few time you'll have an CD(s) or DVD(s) with entire main, restricted, universe, multiverse, contrib, etc.

Share
    Share your packages with your friends without Internet conection. Also, send a meta-package for him to install the same set of packages that you have.

Thanks for the correction:).

---

### Post by medya on 2007-11-29
yeah it uses your cache , but it also makes them organized, to be used in Synaptic P. manager

I know what it does . I just need AptOnCD and all it is dependeniceis to download :(

---

### Post by natehatewindows on 2007-11-29
it would be sweet if you could download whole repos and put them on disks or drives.....

---

### Post by natehatewindows on 2007-11-29
not promising anything but let me see what i can do. Also just a tip, go [here](http://packages.ubuntu.com) and you can downlaod them one by one. i had o do this to get kppp to get my dialup modem working.....its a pain but worth it.

---

### Post by medya on 2007-11-29
can somebody give me all its files in a single zip file  ? I am sick of this I have been far from ubuntu for months just because of this :(

---

### Post by natehatewindows on 2007-11-29
pm me your email

---

### Post by natehatewindows on 2007-11-29
nevermind, this wont work....apton doe not include its self in it own list. WTF? thats crazy...looks like you going to have to do it the long way.. plus im using gusty so i doubt it would work anyways.

---

### Post by forestpixie on 2007-11-29
have you checked that you've not got the dependencies first - 

[http://packages.ubuntu.com/feisty/admin/aptoncd](http://packages.ubuntu.com/feisty/admin/aptoncd)

you can just download the deb from here, it's only 170kb in itself - [http://www.ubuntu-hr.org/proba.php](http://www.ubuntu-hr.org/proba.php)

---

### Post by plucky on 2007-11-29
Hi medya,

you can download the debian package from [here](http://aptoncd.sourceforge.net/index.html)

If you get the Feisty version, that should install with all dependancies, not sure if the latest version will install on Feisty,but you can give it a try.

Cheers

Peter

---

### Post by medya on 2007-11-29
sigh...so nobody can do this favor for sme ?

---

### Post by forestpixie on 2007-11-29
what favour?

---

### Post by medya on 2007-11-29
giving me aptoncd and all its dependecies in a ZIP file

---

### Post by plucky on 2007-11-29
Medya,

Click on the link in my previous post,it will take you to the AptonCD home page.
Download the **.deb** package in windows. Copy the file to USB stick or boot Ubuntu and copy the file from your windows partition to your Ubuntu desktop.

Double click on the AptonCD deb file and it will install it for you and all dependencies should be satisfied.

Peter

---

### Post by medya on 2007-11-29
plucky , I have tried it, first it says I need Yelp , then I try to install yelp and it says I need to isntall something else...
after satistifying yelp,  something else wants ....


the only solution is, the person who has installed it on his fesity , give me all the packages .

---

### Post by ruibernardo on 2007-11-29
Hi medya,

the packages you need to download and install depends on which ubuntu release, kernel and updates you already have installed on your system. 

Please send me a private message with the file "/var/lib/dpkg/status" from your offline ubuntu. That file will be used on a chroot in which I'll run "apt-get install aptoncd --print-uris". I'll post then the links to the packages you need to download.

If you want any other links of other packages files you need/want, feel free to say, I'll post the links to them too.

---

### Post by plucky on 2007-11-29
Medya,

> actually I wanna back up all my installed packageas using AptOnCD and then install the new version of the ubuntu (7.10)

I don't think this will work,because the packages you are using are for Feisty and the dependencies might be different in Gutsy.AptonCd was meant to be used to transfer packages between machines using the same release versions. The repositories for Feisty and Gutsy are different.

I could be wrong,maybe the experts will correct me.

---

### Post by Irihapeti on 2007-11-29
You can use Synaptic to generate a script for downloading the dependencies for any program that's in the repositories. Select your program, then choose "generate download script" from the File menu. That gives you a text file with a series of Wget commands in it. You can easily edit out the "wget -c" from the beginning of each line, and you then have a set of URLs that can be loaded into a download manager.

I quite often do this because I want to download files at night, and have the computer terminate my dialup connection when I'm finished.

---

### Post by ruibernardo on 2007-11-29
> **plucky said:**
> I don't think this will work,because the packages you are using are for Feisty and the dependencies might be different in Gutsy.Oh, I've overlooked this. You're right plucky. If medya installs his packages from Feisty in Gutsy, some things will definitely break. Never tried that, can't confirm, but it is very probable to happen. 

I can get aptoncd links and dependencies if medya wants, but what plucky said will probably happen. Medya should use aptoncd to transfer packages from another Gutsy box.
> **Irihapeti said:**
> You can use Synaptic to generate a script for downloading the dependencies for any program that's in the repositories.
Medya doesn't have an internet connection.> **medya said:**
> hey I dont have internet on ubuntu ,So he doesn't have the lists of the repositories and can't use Synaptic to create the script to download aptoncd.

---

