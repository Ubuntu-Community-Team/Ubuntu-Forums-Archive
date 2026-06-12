---
title: "Why gaming sucks on linux"
date: 2007-05-04
forum: Alabama Team - US
---

### Post by crimsontide on 2007-05-04
Does anyone besides me agree with Lynch? [http://www.extremetech.com/article2/0,1697,2063126,00.asp]("http://www.extremetech.com/article2/0,1697,2063126,00.asp")

---

### Post by dfreer on 2007-05-04
Hmmm. While I agree that that there are a lot of good games on windows that don't work in linux (I miss playing F.E.A.R. so much it hurts sometimes :D ), I do not think it is good enough of a reason to run windows instead of linux. Ubuntu has so much more to offer to me and it's eaiser for me to do pretty much anything else. kudos definitely should be given to wine for the amount of work they have done, although it's not perfect at least they are trying. 
Besides, between my windows friends and me, the only real games we play on a regular basis are Counter-Strike and CS:S, Starcraft, Unreal Tournament 2004, and the occassional Call of Duty. And all of those games run in linux for me, so I am happy. 
I'm really itching to try running virtualbox and seeing if it is indeed possible to run windows apps (games!) over the network on Feisty, it may be worth making a XP server dedicated just for windows apps.

[https://help.ubuntu.com/community/SeamlessVirtualization](https://help.ubuntu.com/community/SeamlessVirtualization)

---

### Post by crane on 2007-05-04
I disaggree to an extent. Linux under gaming is slow but too many writer just do not know how to write about gaming in Linux. By this I mean every artical I read pretty much makes it sound like Linux is the problem. Which is not true. It is the game devs and marketers that are at fault. It's not the fault of the OS if WoW was not built to  run in Linux. 
 Then it seems he spends the rest of his time cutting on the people who provide feed back. This is crap. If you write articles on a public site you will get flamed by some morons. What makes a person more reputable is their ability to rise above the idiots.
 I don't think the author meant to slam Linux, that is just how his choice of words made it sound.

 BUT!
This raises an idea for me. I have spoken with a couple people in the Bham LUG about having a LAN party. Maybe we could make it a little more interesting. If we have a Linux gaming show. Load up a couple computers to run a lot of the games people play. Then have it in a public place to show off the power of Linux.
 People would understand if we show them. Maybe I will bring this up at the next IRC meeting.
 This could really help advocate Linux, the Group, the community, and the cause.
 If anyone has some thoughts on this we should start another thread to get this going.

Also, isn't FEAR supposed to run in Cedega now? I so loved that game. (Just not enough to boot back and forth all the time). I may get Cedega and give it a try.

---

### Post by dfreer on 2007-05-04
> **crane said:**
> Also, isn't FEAR supposed to run in Cedega now? I so loved that game. (Just not enough to boot back and forth all the time). I may get Cedega and give it a try.

wait, what!?!? I JUST ditched cedega a month or two ago and now all of a sudden they decided to support FEAR? *runs to check the site*

EDIT: Yeah, it looks like cedega supports directx 9.0c and pixel shader 2.0 now, the latter of which was holding FEAR back. It looks like some people have definitely gotten it running but it's not exactly stable. *sigh* now I wanna go out a renew the subscription I just cancelled.

---

### Post by crane on 2007-05-04
LOL, I just recently canceled my WoW subscripion and my Q4 Server so I may be able to get me some Cedega sweetness myself! If we get it working we should hook up online!

---

### Post by reidms on 2007-05-17
Gaming does not "suck" on Linux, it is just that most of it has to been done through emulation.
A native Linux game could probably out do the same game on windows on the same computer.

---

### Post by crane on 2007-05-17
> **reidms said:**
> Gaming does not "suck" on Linux, it is just that most of it has to been done through emulation.
A native Linux game could probably out do the same game on windows on the same computer.

I agree, Windows moved away from OpenGL I believe because it was an open. I believe will will see a hard push from Windows in the future on the gaming front because if Gaming in Linux becomes equal to Windows I think there will be a big shift.

---

### Post by Abasher on 2007-07-06
To me THE reason games are blossoming on Windows, but not on Linux, is DirectX. Microsoft have put a huge amount of effort creating an API to help developers, and better compatibility for the users. Even the capabilities in the graphics cards are made to fit a particular DirectX version.

This gives so much to the developers, that it's almost retarded to develop a game for something else (consoles with their own APIs not included). Also, a DirectX game for Windows almost automagically works on the XBOXes, due to them also using DirectX (I do realize that a fair deal of customizing is required, such as for input system, and profiling for running good on the hardware).

Does Linux have an equivalent? Kindawellnotreally. Some would argue for SDL. Having only done a bit of 2D graphics in it, I cannot speak for it's quality. The holy Grail is a DirectX compatible translation layer. This is sort of what [Cedega]("http://www.cedega.com") and [The Alky Project/]("http://www.fallingleafsystems.com/sapling/") are doing. They are however commercial products, and are a bit out of place in the Linux eco-system. Also, they don't seem to aim for full DirectX compatibility, just working with popular games.

What I see need for is an ambitious open source project which aims to accurately translate each available DirectX instruction to the equivalent SDL/OpenGL/OpenAL instructions. Something like this is what we're seeing with the Mono project, which aims for full .NET compatibility. This works with .NET due to it's open architecture, but how are the licenses for DirectX? Seeing what companies like Cedege are doing, the licenses should allow this. There seems to be some push for WINE to support DirectX, but I'm not holding my breath.

I'm not standing on a soap box here, and saying that someone must do this, just not me. I'm saying this would bring Linux gaming into the ballpark. The Open Source movement does not have the funds (and are too late) to bring their own thought-out games API - so it should rather adapt, and  follow the already accepted standard.

---

### Post by dfreer on 2007-07-06
> **Abasher said:**
> Does Linux have an equivalent? Kindawellnotreally. Some would argue for SDL. Having only done a bit of 2D graphics in it, I cannot speak for it's quality. The holy Grail is a DirectX compatible translation layer. This is sort of what [Cedega]("http://www.cedega.com") and [The Alky Project/]("http://www.fallingleafsystems.com/sapling/") are doing. They are however commercial products, and are a bit out of place in the Linux eco-system. Also, they don't seem to aim for full DirectX compatibility, just working with popular games.

**What I see need for is an ambitious open source project which aims to accurately translate each available DirectX instruction to the equivalent SDL/OpenGL/OpenAL instructions**. Something like this is what we're seeing with the Mono project, which aims for full .NET compatibility. This works with .NET due to it's open architecture, but how are the licenses for DirectX? Seeing what companies like Cedege are doing, the licenses should allow this. There seems to be some push for WINE to support DirectX, but I'm not holding my breath.

The Open Source movement does not have the funds (and are too late) to bring their own thought-out games API - so it should rather adapt, and  follow the already accepted standard.

ummm. isn't this EXACTLY what wine/cedega is doing? admittedly more so wine than cedega, but still. DirectX is not in any way "open", which is why wine has to work so hard. I don't think it is a case of "Let's make our own API instead of using DirectX", it's more of an "We cannot make DirectX API work in linux due to the closed nature, so let's try to make our own that will hopefully become as accepted as DirectX (hint: OpenGL)". Of course, I'm not a programmer so everything I say is merely IMO, feel free to bash.

---

### Post by johng4 on 2007-07-13
I use computers to make my life easier.  So for the time being I use my gaming machine with Windows, while everything else (including my ps3) run linux.

I've run a lot of games under linux, but honestly I don't run linux for games, so in the end I keep a machine around strictly for gaming.  Its locked down, so that there's virtually nothing else you can do on it except play games.  A monumental waste of money for the most part, but I've had it for a while now, and at least I still use it.

Lately I've been drawn back into console gaming thanks to the PS3.  I'm waiting for a good mmorpg to come out on the ps3, and then I'm all but abandoning PC games.  I don't see anything out there that I feel like I _have_ to play, so I've been wasting away in the land of Ninja Gaiden Sigma, and The Darkness.

---

### Post by crane on 2007-07-13
I have not played the Darkness. I am really looking forward to CoD4 and HL2 episode 2 on PS3. Both due out in October. The portal gun looks totally cool!
 I love my PS3, I just wish I had more time to play it. I haven't found a game yet that just owns me, I hear Rainbow Six is pretty cool as well. I spend time riding around the street on NFS|Carbon and the trails of Motorstorm.

---

### Post by johng4 on 2007-07-14
Joshb has Rainbow Six, and claims its the new hotness.  Ask him about it.  Personally I'm waiting for FFXIII more than anything.  If nothing else I just need a HDTV so I can use my linux install on it.  The NTSC resolution makes it useless for the moment.

---

### Post by crane on 2007-07-14
Agreed, I ran Ubuntu on it today with a standard TV and it was horrible looking.

---

