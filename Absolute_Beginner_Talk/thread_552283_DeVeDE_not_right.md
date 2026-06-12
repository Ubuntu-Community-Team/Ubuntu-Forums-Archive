---
title: "DeVeDE not right"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by trucker33377 on 2007-09-16
Hi Ive been working on for awhile now. Got most everything to work like i want to. Except , making a DVD from 2  files. i found a post that takes me thru all the steps to do this but its must be for a diff ver then i'm using. still its very close. I only get stumped when i have to use prop from the titles side of the menus left side. there no option to do this.

if i cant change these i get  1 file as a mpg and a folder with vob files in it. 

so how do i get all files added to 1 dvd disk? 

and where do i find the ver of devede that i have installed? thanks for all the help

heres the link to the how make, that im following
[http://www.my-guides.net/en/content/view/75](http://www.my-guides.net/en/content/view/75)

---

### Post by julian67 on 2007-09-17
[IMG]http://img366.imageshack.us/img366/1221/devedescreenshotfa2.png[/IMG]

at this screen add your movie file to title 1: 

[IMG]http://img381.imageshack.us/img381/9094/devedescreenshot2vv2.png[/IMG]

now add another title and add the second movie to it: 

[IMG]http://img399.imageshack.us/img399/7805/devedescreenshot3gm1.png[/IMG]

I can't promise this will work as am trying this with multiple vidos for the first time but this how the gui suggests to do it and it seems to be going along ok.

I am encoding now so in a couple of hours I will know :-) I'm using devede 2.9

---

### Post by julian67 on 2007-09-17
It didn't exactly work for me either. Devede gave me 2 separate mpeg files, one of each movie and also one folder with the VIDEO_TS & AUDIO_TS folders containing movie 1. The process failed before it could convert movie 2 to DVD structure.

---

### Post by Gavla on 2007-11-17
*bump* I'm getting exactly the same problem. That guide says to just change the name of the title to create menus, but the button is missing. 
A shame, 'cause other than that, this program seems perfect, with the ability to easily tweak it to work out the bitrate budget. Any help?
(64 bit Gutsy 7.10)

---

### Post by Gavla on 2007-11-17
Oh! I think I've fixed it for myself and for y'all!

The version in the repository is old, before the renaming titles feature was added to Devede. They keep the old version there because the newer versions have some issues with Ubuntu. It doesn't seem to be so for me, and others have found very easy workarounds.

Check these out:
[http://ubuntuforums.org/showthread.php?t=604475&highlight=devede]("http://ubuntuforums.org/showthread.php?t=604475&highlight=devede")
[http://ubuntuforums.org/showthread.php?t=524006&highlight=devede+sound]("http://ubuntuforums.org/showthread.php?t=524006&highlight=devede+sound")

I'm not yet holding my burned DVD in my hot little hand, so I'm not counting my chickens yet, but it smells like it's all alright.
Gee. I spent all day trying to assemble DVD ripping and creating applications. I wished I'd realised this a few hours ago.

---

### Post by kelvin spratt on 2007-11-17
Download the latest version here [http://www.getdeb.net/](http://www.getdeb.net/) and download the patch from Devede site, follow the instructions that will solve all the problems, This is a Ubuntu fault not a Devede fault with Mencoder or alternativly replace Mencoder with the older version 0.99+1 from the debian website then lock the version in Synaptic.The latest versions are as good as they come with menus etc.

---

### Post by xpod on 2007-11-17
When i used devede in feisty i had to apply the patch too to fix mencoder.
I only occasionally  made mpeg DVD`s so as to fit more than one on a disk,which was`nt possible with the iso option of course...(?)
Devede certainly made things nice and easy for someone who did`nt know jack about dvd encoding.

Since installing again in gutsy though the mpeg option seems to work fine again although i did have had trouble with the newer DivX feature.

All that encoding lark in a pain in the backside though so i prefer a 25Ft long TVout cable:)

---

### Post by Gavla on 2007-11-19
Thanks!
Mine worked peachy just by getting the latest Devede, and I'm watching DVDs at my TV.

---

