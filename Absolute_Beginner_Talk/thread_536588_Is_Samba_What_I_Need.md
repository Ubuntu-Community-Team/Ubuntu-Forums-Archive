---
title: "Is Samba What I Need?"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by skeating on 2007-08-27
I have an interesting project, but I am still pretty new to linux/samba/networking.

I've got a linux box running feisty fawn.  It has a wireless connection to the internet and a static ip address.  It does not currently have a good video card or a functioning sound card.

I also have a nintendo Wii.  It can browse the internet via Opera and is connected to a hi-fi stereo system and a television.

See where this is heading? :)

basically, I'd like to set up my linux box to host movies/music, and then access/browse/play them on my stereo/tv setup with my wii.

Will a samba share alone do this, or is there some other software that would make things easier?

Also, (complete noob question and I'd feel stupid asking my friends so i'm asking the forums) when i access a movie on the linux box via the wii, is the wii going to be loading the movie and playing it, or is the computer itself going to be doing all of the processing?

---

### Post by s[_]spect on 2007-08-27
Samba should do it provided the wii can access an smb share..and the two boxes are on the same subnet/network..
I do similar with my old xbox and will setup my ps3 to do it once i get the wireless working..

as for the second question: the linux box is just a file store.. the wii will be copying the file over the network and doing all the processing of codecs etc

---

### Post by skeating on 2007-08-27
ok.  thanks!  I'm worried that the wii's internal memory (512 mb) will not be sufficient for playing movies, but if I can get everything working I'll be sure to post results!

---

### Post by Gruelius on 2007-08-27
Does the wii have media centre capabilities?

---

### Post by KCPokes on 2007-08-27
If the Wii does have the capability to play movies, one would assume they'd have to be mpeg-2 as I cant' see the Wii having any other built-in codecs.  I've not heard of anyone else using the Wii as a media center player.

---

### Post by skeating on 2007-08-27
> **Gruelius said:**
> Does the wii have media centre capabilities?

the wii can browse the internet using a modified version of opera.  I need to test if the browser can play mp3s and video, i guess.

---

### Post by KCPokes on 2007-08-27
> **skeating said:**
> the wii can browse the internet using a modified version of opera.  I need to test if the browser can play mp3s and video, i guess.

To use Opera to play the media, it would have to be embedded in a page.  As far as I know, there isnt a way to just browse and play media directly from Opera.  You'd need a true media player to accomplish this.  Then again, maybe someone has a creative way around this.

---

### Post by s[_]spect on 2007-08-27
You could.. (in theory) run an apache server on the linux box and setup two web pages to run the videos.. one to list the available titles with links to the second passing the requested title as a parameter. This would be a little more difficult to setup than what the post originally required..
Can the wii even browse smb shares?

---

### Post by fastpakr on 2007-08-27
Jinzora sounds like exactly what you need for audio.  I believe it also supports video, but I've never tested that...

---

### Post by skeating on 2007-08-27
> **'s[_]spect said:**
> You could.. (in theory) run an apache server on the linux box and setup two web pages to run the videos.. one to list the available titles with links to the second passing the requested title as a parameter. This would be a little more difficult to setup than what the post originally required..
Can the wii even browse smb shares?

that depends--can an smb share be accessed like a webpage?  If so it should work.  I can't get to my wii right now b/c we currently have a roommate "temporarily" crashing in our living room :/

---

### Post by KCPokes on 2007-08-27
> **skeating said:**
> that depends--can an smb share be accessed like a webpage?  If so it should work.  I can't get to my wii right now b/c we currently have a roommate "temporarily" crashing in our living room :/

I don't think it would recognize SMB by default.  If you are going to pursue the route of a webpage, internally, for serving up your media (which is a good idea) then you might just pursue setting up a simple webserver for internal purposes.  As it would be only internal, even IIS on your Windows box would suffice.

---

### Post by s[_]spect on 2007-08-28
It is really application specific.. IE obviously does, firefox doesn't..Opera probably wont..
The xbox has a media centre app that does.. so too PS3.. so I dont think the app in question is suitable without going down the web server path.. Good luck

---

### Post by skeating on 2007-08-28
> **KCPokes said:**
> I don't think it would recognize SMB by default.  If you are going to pursue the route of a webpage, internally, for serving up your media (which is a good idea) then you might just pursue setting up a simple webserver for internal purposes.  As it would be only internal, even IIS on your Windows box would suffice.

thanks for all the help, guys!

I might have a solution cobbled together, provided schoolwork lets up.

---

