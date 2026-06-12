---
title: "Noob question about tv"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by Ripfox on 2007-01-21
I have a Winfast 2000xp tv card that works fine with TvTime. I heard you could record tv to mpeg with kaffeine or vlc. How do you do this? I downloaded Kaffeine, but it says "no dvb device detected" on setup. I don't know if that means my tv card, or what. Any help is cool. BTW, I don't want to mess with Myth, I am frustrated with it. (or freevo)

Thanks

---

### Post by crispy_420 on 2007-01-22
You may be out of luck if you don't want to use mythtv but you would be too if you went mythtv too. Let me explain.

Mythtv is best run on a mpeg (hardware) encoder card. That way the stress on the OS will be minimal since the card is doing the encoding. If you were to use a non-mpeg card, your processor would have to do all the work. So this would would render the system dead in the water for anything else at the same time. Assuming there was no problems that is. A small error in this could lead to a bad file or just garbage.

As far as those programs you mentioned. Have yet to try them to record on my similar card but I have the feeling I won't like the results.

So in my opinion, recording may not be your future. Sorry.

---

### Post by Ripfox on 2007-01-22
Well, that seems likely, as you say with myth. I do know that under windows, the card could record tv fine. Is this a Linux related problem then I assume? Also, it seems you don't have any information about how to even view tv with Kaffeine or VLC. If anyone knows how to do this I would appreciate the help. Thanks! :) (note that I can watch tv AND multitask quite well when using TvTime. My processor is an Athlon 3200 with 1.5 gig ram, if that helps anyone)

---

### Post by punx45 on 2007-01-23
yeah, sounds like a driver issue.

i did a quick google search and[ in one thread a guy said]("http://209.85.165.104/search?q=cache:BT7vwtehOIEJ:www.linuxquestions.org/questions/showthread.php%3Ft%3D166601+Winfast+2000xp+tv+card+linux&hl=en&gl=us&ct=clnk&cd=8&client=safari") he had the card running with the 2.6.3 kernel which apparently has built in support, and that the card did not work with an earlier 2.4.xx kernel.

i dont know what kernel you are on but i only have 2.6.15 with dapper.  i don't know what edgy comes with.   so it looks like you might need to find a driver or upgrade the kernel.  find out what your kernel is by executing 'uname -a' in a terminal.

find out as much specific info for your card as you can (run lspci in a terminal and then read through all the listings and find what looks like the card, then go from there with some forum/google searching.   also, even though you dont want to mess with MythTV, it has a very active community and good docs and wiki.   you will find alot of information on linux compatable PVR related hardware.

---

### Post by crispy_420 on 2007-01-23
You will be able to watch tv/multitask because you are just streaming data. There is no encoding going on. As far as windows and recording, very processor intensive. If not, it may use a win codec to record. Also keep in mind that the money windows has equals big support. As for recording in vlc, try to watch first. It is a massive pain to do, and not just in linux. And kaffeine wanting a dvb card, not going to happen with your current setup. Sorry to break the news. I wish it wasn't true and I hope that someone can prove me wrong cause it would solve my issues. Just give linux time, I remember when the bttv driver had to be installed manually and was not part of the kernel. That was just a few years ago. The linux multimedia world is slowly picking up steam and I can't wait to see where it goes.

---

### Post by Ripfox on 2007-01-23
Ok, so this doesn't give me an idea about "how" to watch tv with anything but tv time. I tried to use VLC, but have no idea what I'm doing. So, if anyone has a step by step or a few pointers, please help. Also, are there any alternatives to Myth out there for Ubuntu? A list of other pvr software to try out would be cool. 

Peace. 

Also the card I have IS working with TvTime "out of the box" if that helps.

---

### Post by punx45 on 2007-01-23
[linux pvr]("http://www.google.com/search?client=safari&rls=en&q=linux+pvr&ie=UTF-8&oe=UTF-8")

---

### Post by Ripfox on 2007-01-24
Deleted for my own rudeness. Sorry must have been having a bad day that day. :(

---

