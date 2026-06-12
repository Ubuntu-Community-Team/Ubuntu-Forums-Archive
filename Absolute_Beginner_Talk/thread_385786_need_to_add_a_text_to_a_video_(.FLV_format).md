---
title: "need to add a text to a video (.FLV format)"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by medya on 2007-03-16
Hi Guys,in the past I have several times tried to succefully edit a video file but I was no succesfull.

all I want to do is , adding a Simple Text to a FLV Video ,
I remember I had downloaded Kino, Live and... stuff but all of them were so hard for me and I didn't mange to work with them , 

can somebody please guide me , where to start to learn ?
is there any good tutorial that teaches me Adding a Simple Text (let say my site's URL) to a FLV video .


Thanks in advance.

---

### Post by Kobalt on 2007-03-16
Hello,

Have you tried [KDEnlive]("http://kdenlive.sourceforge.net/") ? It's very powerful and simple and has a good wiki/doc...

---

### Post by medya on 2007-03-16
thanks I will check it out , can it Edit FLV files too?

---

### Post by Kobalt on 2007-03-16
[QUOTE=KDEnlive doc]all formats supported by ffmpeg should work[/QUOTE]
As far as I know ffmpeg can handle .flv videos, so it should work :)

---

### Post by medya on 2007-03-16
is there any installation guide for ubuntu ? it is for kubuntu.

---

### Post by Kobalt on 2007-03-16
You can install KDE (aka Kubuntu) applications under Gnome (aka Ubuntu) just fine... The install process is the same : just download the .deb files, double-click on them, and you're done.

---

### Post by medya on 2007-03-16
it has a GPG key... how to install it ? [http://kdenlive.sourceforge.net/index.php#gpg](http://kdenlive.sourceforge.net/index.php#gpg)

---

### Post by Kobalt on 2007-03-16
It only means that the packages are signed with this key, you need to download it if you use the repos. In the KDEnlive wiki, there is a section for Ubuntu installation, with a [direct link]("http://www.mediafire.com/?ammoqj12nzn") to downloading the three .deb packages you need. Just download and install them (there is an order in which you must install them, for dependencies, Gdebi will prompt you what is required before what) with a simple double click. 
The GPG keys of the packages are included in the archive you'll download.

---

### Post by medya on 2007-03-16
hey I insatled it , it looks GREAT but it keeps on exiting the program without any notice... :(

---

### Post by P_Badger on 2007-03-16
> **medya said:**
> hey I insatled it , it looks GREAT but it keeps on exiting the program without any notice... :(

It does with me too, but in my case a crash report pops up. 

It should be said that kdenlive is a fair ways off from being usable. : (

---

### Post by Kobalt on 2007-03-16
Is it now ? 
Well it's a shame so... I used to play a little with it a while ago, before 0.4 was released, and it did work fine. 
I'm sorry so, if I advised something buggy.

---

### Post by Kobalt on 2007-03-16
Have you tried launching it from a Terminal (open a console and type in 'kdenlive') and checking the messages it gives you before crashing ?
Could you guys please post that output here ?

---

### Post by P_Badger on 2007-03-16
Probably not much help, but here's the output:

> kdenlive: +++++++++++  Generating scenelist start...  ++++++++++++++++++
kdenlive: Creating new document
kdenlive: deleting contents...
kdenlive: ****************  INIT DOCUMENT VIEW ***************
kdenlive: Mlt inited
kdenlive: ****************  INIT DOCUMENT VIEW 1***************
kdenlive:  +  ++ + ++ ++ PREPARE VID THUMB
kdenlive:  +  ++ + ++ ++ PREPARE AUDIO THUMB
kdenlive: ++ FOUND CLIP
kdenlive: WARNING: Got a request for a changed clip that is not in the document : Boots are made for walking.flv
kdenlive: *** DOCUMENT adding clip: Boots are made for walking.flv
kdenlive: ++++++++++++  DOC SELECT NEW ITEM: 0
KCrash: Application 'kdenlive' crashing...
kdenlive: Fatal IO error: client killed
ICE default IO error handler doing an exit(), pid = 7038, errno = 9
Unable to start Dr. Konqi


All I did was attempt to import the clip into the project tree.

---

### Post by Kobalt on 2007-03-16
You would need to contact the KDEnlive dev team then ask them what's an error n°9... So far I can't figure out what could cauuse this crash...

---

### Post by P_Badger on 2007-03-16
I've already posted one issue to their list, never got responded to, so left it at that. I'm sure they're aware of what's wrong with their program. Hopefully 0.5 brings some fixes.

---

### Post by Kobalt on 2007-03-16
I hope so...

---

### Post by medya on 2007-03-16
hey guys running the problem from terminal made it working better for me...

---

