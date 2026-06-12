---
title: "K3b - Unable to find cdrdao executable"
date: 2005-08-24
forum: Absolute Beginner Talk
---

### Post by Lord Hammer on 2005-08-24
I'm very new to Kubuntu.

During startup K3b reports with the following masage:

  Unable to find cdrdao executable
  K3b uses cdrdao to actually write CDs.
  Solution: Install the cdrdao package.

I reinstalled the K3b but it doesnt help (aren't the packages suppose to automaticaly download dependancies ?)
Searching in Kynaptic doesn't find any cdrdao packages. The only thing it finds is existnce of the word cdrdao in description field of k3b and k3blibs package.

Ihave found the file "cdrdao-1.2.0.tar.gz" (SourceForge.net) which suppose to be cdrdao. When I open archive I end up with bunch of files wich will not install.

Instructions within the arcive are saying somethin about make, compile ... Sound to me like an winter project.

Any suggestion what the next easy step should be.
My be I should pop in my WinXP hard drive ?
But then I wont be able to use Kubuntu or I use Kubuntu without being able to write a cd ?

PLEASE Help

---

### Post by Lord Illidan on 2005-08-24
Ah, now, calm down...

First thing you want to do is look at the Ubuntu Guide. It is in my signature...

Enable the extra repositories. The guide is very helpful, do as it says..

By the way, to open a terminal, there is an entry in the menu called Konsole..

Then after you have done what it says, install synaptic instead of kynaptic, as synaptic is more functional,

by doing this : ```
sudo apt-get install synaptic
``` in a terminal

After that, open synaptic, by entering ```
sudo synaptic
``` in a console, and search for cdrdao. Then you can install it, as well as browse around for other packages..

Glad to help!

---

### Post by tikal26 on 2005-08-24
have you added the extra repositories 
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
I thik that after you do that you could probably find it in synaptic or kynaptic. whatever you use and istalled it.

---

### Post by Lord Hammer on 2005-08-24
Lord Illidan - thanks for quick response.

I have followed your instrictions to the letter (copy&paste).

Got synaptic running; reloaded package information, hit the Edit - Search, typed cdrdao hit Search button ---> "0 packages listed ??"

No "cdrdao" --> any further suggestions ?

r e g a r d s

ps
 I have not enabled "universe" sections (non-supported packages)

---

### Post by Kapre on 2005-08-24
LordHammer - suggest copying the repos on [this](http://www.ubuntuguide.org/#repositories) because cdrdao appears on my Synaptic

---

### Post by Lord Hammer on 2005-08-26
HI Capre

On which repository  can you find cdrdao ?
If I know that everyting else wil be easy.

Perhaps You have "Text List" of repositories for Debian ?

T h a n k s

---

### Post by Lord Illidan on 2005-08-26
Enable the universe repository...

---

### Post by Lord Hammer on 2005-08-26
Hi All

I had run synaptic again just now and this time it has found cdrdao.
Its up and running.

One other thing. Dispate the error massge that cdrdao is not installed I continued loading the app to see what happens.
Selected the image I have to burn in the first place and give it a GO.
It burned the image without a problem.
It also reported that it uses "cdrecord". Since this massage dissapeared pretty quickly I not 100% shure if the name is correct.

As far as the user guide is concerned (the one You are refering to) it is a pretty crapy thing; it might be 100% technicaly correct but presentation wise it is a disaster. Specialy for people comming from "Win World" (sorry for this one, but I guess being in MS camp for almost 20 years takes its toll).

I have red thousands of pages about Linux/Unix befor I had decided to give it a ggo, and they are, in a way, all the same: writen by Linux/Unix thinking people for Linux/Unix thinking people.

To my opinion this might be on of the reason of a slow Linux acceptance.

So, as I go along I will be writing my own manual for "Win thinking peole."
I'll have it posted/published when I'm done writing. (That is if I don't give up on Linux along the way).

That's it. Thank You all folks.

---

### Post by Lord Illidan on 2005-08-26
> 

As far as the user guide is concerned (the one You are refering to) it is a pretty crapy thing; it might be 100% technicaly correct but presentation wise it is a disaster. Specialy for people comming from "Win World" (sorry for this one, but I guess being in MS camp for almost 20 years takes its toll). 

Ok, so what are your problems with the User Guide? I agree that it might lack some presentation. So why not approach the maintainer and offer to improve it? That is the open source spirit after all..

---

### Post by Lord Hammer on 2005-08-26
HI Lord Illindan

What my problem is with the user guide I sad in an earlier post:

Writen by LINUX people for LINUX people, and I guess, most of the Linux people dont need it afterall.

I personaly wouldn't call it an ".User Guide".  It is a mere listing of some steps ( That is not to say that I do not admire the work of the author. He had put a serius amount of work in it).

The user guide should guide peple. It should have the begging an the end. For majority of the people the PC is only the tool. So explain how to use it not how to build it.

Fist of all it should describe the basic filosophy/concepts of the OS (how to do a basic things like file mangement tasks,  installing/removing the programs, hot to use built in help system (weak side ofthis  Linux),  where to find things and so on.

Most of all a Linux guide should help the people in understanding the concept of  repositories, packages and their maintenace, package installation and the like. I shouldn' merely list the some steps. How about, (in the introductory chapters), explaining the thing like tarbal, deb, rpm .... & ...
For most of the people it is useless to explain how to do things, before telling them what they are goint to do (typical for most seasoned Linux users that I personaly know).

For the more technicaly inclined people (like myself) how obout ponting them to the pleace where there can find all the info about recovery/ emergency boot disks, multi-boot...(we seasoned Win users didn't reformat our Win /dev/hd's, yet)

As far as the spirit of Open .... goes, as I said in the previous post the manual that I just started i'll release to commnity.

One other thing:
I have just finished reading the material obout GRUB; awsome stuff. I could begin the manual wit that one; it might point some Win users in th rigth direction.

Take care of yourself.

---

### Post by Lord Illidan on 2005-08-26
I am a Linux user and I do read the Ubuntu Guide...

Yes, maybe it needs some clarification... but who is going to do it? I am not an expert and I am not a teacher.... And no one is going to be paid for doing the job...

---

### Post by Lord Hammer on 2005-08-26
HI

As I mentined in one of my previous post, as I go along my new Linux trail I document the things; when I get there there will be enough material for a Linux(KDE) for WinXP people Guide. For now it looks that I have to assemble that under WinXP umbrella.

Certain things you do to try to help other people, and not to expect to be paid for that.

Or, perhaps if you won't to make a few bucks along the way you can allways try to publish  the material (people do get paid for that ?)

---

### Post by Lord Illidan on 2005-08-26
[QUOTE=Lord Hammer]HI

As I mentined in one of my previous post, as I go along my new Linux trail I document the things; when I get there there will be enough material for a Linux(KDE) for WinXP people Guide. For now it looks that I have to assemble that under WinXP umbrella.

Certain things you do to try to help other people, and not to expect to be paid for that.

Or, perhaps if you won't to make a few bucks along the way you can allways try to publish  the material (people do get paid for that ?)[/QUOTE]

I wish you success in your quest. It is good that newcomers have a good guide in front of them. However, keep in mind that Linux is not Windows and it is not intended to look or feel like it, neither.

---

