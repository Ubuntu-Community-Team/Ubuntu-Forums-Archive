---
title: "iPod woes"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by loswr86 on 2007-04-14
I have myself a dilemma. I have been a iPod user since '04, content with its features until recently. A few months ago I became a Ubuntu linux user, setting up my M$ desktop for a dual boot w/ ubuntu. The migration was fairly easy with the exception of iPod compatibility, as apple seems to ignore the existence of linux users when it comes to iPod. 

Anyannoyance, the more I toyed with ubuntu the more I regretted my iPod. I now want an mp3 player that will play OGG and FLAC formats, but alas I'm stuck with the pod. Well the combination of using the iPod w/ linux/windows/panasonic car stereo has killed it. This is my opportunity right? Wrong. I spent too much time and money setting up my car stereo to have seamless integration with my mp3 player, and the only thing that will work is the damn iPod's w/ dock connections. 

So it appears to me that I am stuck with apple, and my best option is to reformat my machine again, and create a larger shared partition for my music in order to continue using itunes for windows as my interface with a new ipod. 

Does anyone out there have a different idea?

---

### Post by lluisanunez on 2007-04-14
Have you ever tried GTKpod? It's been working with my ipods for ages, each version getting better.    Now it beats iTunes.

---

### Post by wataboutbob on 2007-04-14
actually, my main data partition (120 GB) is still under NTFS which is where my music folder is.

But since I've enabled read/write access for NTFS drives, my ubuntu installation happily reads the stuff from there and I can edit Id3 tages using EasyTag or Tag Tools in Ubuntu. Rythmbox supports syncing with iPod out of the box - nothing extra to install.

About the only time I boot into Windows is to play LAN games or when I want to sync Photo's to my 60 GB iPod Video using iTunes. I've turned off music syncing with iTunes though.

Works well for me. I don't have any personal files or anything saved under /home or anywhere. Ubuntu is my main OS, but all my files / video's / music and data are still sitting on a NTFS partition without any issues.

---

### Post by qpieus on 2007-04-14
I have a 30 gig ipod with the color screen (no video) and it works perfectly with Amarok for me. I'm using kubuntu 6.06 by the way. The ipod automounts when I connect it and to transfer songs to the ipod I simply drag and drop files into the amarok window.

So, to answer your concern - no, you are not condemned to using itunes as your interface. Once you get the ipod loaded up, your car setup still should work just fine.

Also, there are several apps for ipod users under linux besides amarok, you should be able to find something you like. Just do a search in the forums for ipod and you'll get lots of information.

---

### Post by heathen on 2007-04-14
also, since you want ogg support (dunno about flac though)

look into rockbox... I love it,  It takes a little getting used to but it works...

[www.rockbox.org](www.rockbox.org)

---

### Post by loswr86 on 2007-04-14
Thank you all for the replies, but I didn't state my problem correctly. My iPod is now dead. Gone. FUBAR. It isn't recognized by my Ubuntu Edgy setup, and windows knows something is plugged in, but will not recognize it. Therefore, I cannot repair/reset the apple firmware. 
And after using Ubuntu for a few months now, it is my newb opinion that ipod sucks as your dap if your running linux. I never figured out how to create and send playlists to it using amarok/rhythmbox/gtkpod. Through my trial and tribulations, I found only rhythmbox to work for me to load the ipod, and that was still a pain in the ****. 
Plus I would just prefer rip my cd's into ogg, rather than mp3, and as you know...not with iPod. And I don't believe that its a coincidence that my iPod died shortly after I started plugging it into linux/panasonic/windows. I mean really? Over 2 years its fine, and only after I start plugging it into my new car stereo it starts acting up? 

I am a total newb to linux, and I love everything about ubuntu when comparing it windows, but I just wish apple would support linux users. I know i'm not the only newb that has these problems.

---

### Post by loswr86 on 2007-04-14
heathen, thanks for the rockbox tip

---

### Post by tehmatticus on 2007-04-15
loswr, what kind of symptoms is your ipod showing?  Will it not power on at all or what happens?  I've corrupted my filesystem once or twice before, but as long as it still powers and has its internal firmware going, you should be able to fix it.  Try holding the center button plus menu until it resets and then holding the center button plus play to get it into disk mode.  From there you should be able to access it from linux or windows, and reformat the drive as you please.

I second the rockbox option too, i've been using it on my 4G B&W ipod for a while now and although it has its occaisonal mishaps, it runs fairly well.  Though be warned, battery life with suffer a great deal until they get the kinks worked out.

---

### Post by lamalex on 2007-04-15
amarok works with any ipod i've ever plugged into it. 3g, mini, 5g, and nano. it's in the repo. it's pretty similar to itunes or so I hear, i never actually used itunes.

---

