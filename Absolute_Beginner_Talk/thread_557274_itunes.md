---
title: "itunes"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by ink'n bones on 2007-09-22
hello all im brand new to this forum and ubuntu , just getting into it for the first time so bare with me.  Im trying to get itunes installed i have already downloaded Wine , my real issue is just getting music on and off my ipod , im not concered about downloading music from the itunes just need the wretched software for my ipod  any help would be GREATLY  appretiated , id really like to not Have to keep booting windows to manage my music just for a tiny mp3 player  Thank! 


 Brandon

---

### Post by lonelyxpeople on 2007-09-22
ill have that same problem.
once i get the xserver (graphical user interface) to work.

you *may* have to boot windows for that, i doubt it but you never know.

---

### Post by cwood06 on 2007-09-22
Im not sure how itunes worked with wine, but i know there are alot of programs out there that will help with your music, I think Banshee has Ipod support. Amarok also supports Ipods. Hope this helps ya out.

---

### Post by ink'n bones on 2007-09-22
Awesome ill check into that , do you know if banshee or amarock will accemt the itunes format ( for like a current catalog of music )  or would i just be better off converting the whole library back into mp3's and start from scratch , i might be anwsering my own question as soon as i can dig into those two , but im filtered from allot here at work ...... damn web filtering

---

### Post by rfruth on 2007-09-22
I use Banshee with my older iPod nano but it must first 'format' (i.e all iTunes data gone) the iPod, ya can't switch between the two (without format)

---

### Post by ink'n bones on 2007-09-22
sweet ill do that as soon as i get home and try it out  its an ipod shuffle ,  about ... eh 2 mabye 2 1/2 years old

---

### Post by tie_dyed_sox on 2007-09-22
I use gtkpod. It's incredibly simple to use, unlike that hideous bloatware, iTunes.

[http://www.gtkpod.org/about.html](http://www.gtkpod.org/about.html)

System -> Administration -> Synaptic Package Manager
Search for "gtkpod" and install.
You should then find it in Applications -> Sound & Video -> gtkpod

---

### Post by Jeroen Vernooij on 2007-09-22
iTunes should work in Wine since 0.9.45: check release notes:
[http://www.winehq.org/?announce=0.9.45](http://www.winehq.org/?announce=0.9.45)

I don't think 0.9.45 is in feisty repo's so you should download it directly off winehq:
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)


But I really recommend using Banshee or Rhythmbox, because they can transport songs to your iPod just as well.

---

### Post by HokeyFry on 2007-09-22
banshee is really unstable, it always crashes for me. i do like the interface but i need something stable.

rhythmbox has support for mp3 players, but im not sure if it can write to them yet, and it most likely can't to an ipod

gtkpod works for the transfer of music on and off your ipod


to play the mp3s make sure you have the correct gstreamer0.10 package installed.
i dont remember which one it is, but i believe it is a part of the good, bad, or ugly plugins.
i would install all three of these, and then make sure you install the multiverse portions as well.


hope this helps

---

### Post by ink'n bones on 2007-09-22
Awesome , so if i go with gtkpod ,  i need to go for the gstreamer0.10 package ? and im assuming theres multiple plugins "good bad ugly" for this package am i right , ( i hate asking stupid questions that i can search for but im so restricted here at work im blocked from most content for like the next 9 hours )  Thanks for all the help this forum is awesome 

 brandon

---

### Post by n3tfury on 2007-09-22
> **ink'n bones said:**
> Awesome ill check into that , do you know if banshee or amarock will accemt the itunes format ( for like a current catalog of music )  or would i just be better off converting the whole library back into mp3's and start from scratch , i might be anwsering my own question as soon as i can dig into those two , but im filtered from allot here at work ...... damn web filtering

no no no, NEVER convert (transcode).  you'll ruin the sound quality of your entire library.

---

### Post by ink'n bones on 2007-09-22
Many thanks for the warning , sound quality is  ... EXTREMELY important to me , been reading a little on gtkpod seems it should accept my M4 itues files with no prob we'll see though

---

### Post by n3tfury on 2007-09-22
no problem.  unless you're converting to .wav, stay away from transcoding.  good luck, i'm sure one of the suggestions will work for you.

---

### Post by ink'n bones on 2007-09-22
yea , im really brand new to ubuntu like less than 24 hours but seems theres enough ppl with the same issue that have resolved it that i should be able to get it going now that im in the right direction ,

---

### Post by colinnwx on 2007-09-25
I'm really new to ubuntu too (couple of months) and been looking for a good itunes replacement because booting into windows is just a drag just to run the ipod.

I got the same Ipod Unplugged message with gtkpod but it eventually recognized it after a minute. However, i find it lags like hell and I can't even click on anything. When i do get music to play, it goes through a 3min song in 20 seconds with no sound.

I tried Banshee, which works and everything, but doesn't support playlists. As in, it doesn't write playlists onto the ipod (yet). So much for that.

I've also heard that you have to install a whole lot of stuff for Amarok to work on the ubuntu gnome desktop, which I'm quite sure isn't true, but I'm not really too sure about the whole state of affairs anyway. Can someone clarify this? If amarok would work for me that would be fantastic.

---

