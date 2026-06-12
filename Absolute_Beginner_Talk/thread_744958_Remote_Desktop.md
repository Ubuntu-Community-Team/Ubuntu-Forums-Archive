---
title: "Remote Desktop"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by teeleef on 2008-04-04
Ladies & Gents,  I have been using Linux solely for a few years now and at every opportunity  I show my friends Linux and try to explain the GNU/Linux history and community spirit.

I was introduced to a Dr and his wife, who (over a year ago) bought a hi-spec laptop with XP.  They got broadband and I set up email and introduced them to the computer experience.  They have never used a computer before.  

Anyway after 6 months  they bought another laptop with Vista so they now had one each.   Slowly but surely XP started to crawl... 4 minutes to boot up.  The new Vista experience consisted of so many pop-up prompts it became frustrating to them and was (in my mind) visually confusing.  

Anti-virus software was bought and installed.  Both of them seem bemused with the whole MS experience.... WOW:confused: 

I had Ubuntu on my laptop and they seemed quite enamoured by the simplicity of it all.  All they do is email, skype and surf.   I have suggested buying two small laptop drives to replace the originals in order to testdrive Ubuntu!    

My question is.... if they run with the Linux idea... I would like to remotely log on to their laptops (whilst talking down the phone to them) to nurse them through the experience.  I need a simple to use (and set-up) remote program so I see on my laptop 'their' screen and can move their mouse (just like the remote use on my XP machine at work by system admin).

I am certain that all will be well considering their demands on a PC.

I have put Linux on other machines with little follow-up required after the initial briefs.


They may not run with this but at least I can set the remote trials on my spare machines.   

Any ideas?



Teeleef

---

### Post by chewearn on 2008-04-04
What you want is something like ssh+vnc.

One simple method is connecting to the remote machine by ssh, with X forwarding.  Then, run "vncviewer 127.0.0.1" in the ssh prompt.  You have to install openssh-server and enable remote desktop on the target.  The drawback is the slow bandwidth intensive connection.

---

### Post by stefangr1 on 2008-04-04
What would probably be even more easy (since you need something to forward X to on the guest machine), is to login with ssh and use portforwarding to set up a tunnel to the host machine (you can use putty to do this), and then simply login using a vnc client.

---

### Post by teeleef on 2008-04-04
Thanks for the replies!   

Is using putty and vnc and portforwarding fairly straightforward or is it mainly command line stuff?



Teeleef

---

### Post by stefangr1 on 2008-04-04
Well, it's straightforward, but I guess it can be a puzzle if you don't know how it works.

Have a look at this topic on one possible way to set it up:

[http://ubuntuforums.org/showthread.php?t=738014](http://ubuntuforums.org/showthread.php?t=738014)

---

