---
title: "Remote desktop feature is really slow"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by transparent9 on 2007-06-17
Well, I guess I should say, it's almost real-time, if I'm looking at the machine (it's right next to me while I'm setting it up, eventually it will be headless).  But from my VNC client on my Mac, it's really slow. 

There's a little dot that represents the mouse in my client, and when I move that anywhere on the screen, it takes like 5 seconds for the actual mouse cursor to catch up.  There's a pause of 3-5 seconds, then it moves almost in slow motion in exactly the path I moved the dot on my client.  Button clicks and movement appear to be near real-time on the actual machine, but through my client, it looks like it's not doing anything for 5 seconds.  

I'm connecting to it through a router, but it should be at least 10Mb Ethernet, if not 100Mb.  I have it set for 256 colors.  I should say, when I'm connecting via the same VNC client to a Windows machine downstairs using RealVNC server, it's as fast as I expect it should be.  No lag.  Same thing when I connect to another Mac in the house with Remote Desktop enabled.  

Is this normal behavior?  Or do I have something set up wrong?  All I did was enable remote desktop support in the administration menu.  Ports etc are all standard.

Thanks for any help.

---

### Post by Damanther on 2007-06-17
I've also had some experience with the standard remote desktop being a little slow.

I installed the vnc4server and it is much more responsive with most vnc clients. (I typically use tightVNC or NetOp).

There is a good HOWTO at 
[Setup VNC]("http://ubuntuforums.org/showthread.php?t=122402&highlight=HOWTO+vnc")

---

### Post by transparent9 on 2007-06-18
Ok, I'll definitely give that a shot.  For a minute there, I thought it was something wrong with my client!

---

