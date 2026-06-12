---
title: "Please help with remote control"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by johnnyphive on 2007-05-13
Here is my situation

I'm very used to being able to RDP from work to home using XP Pro on both ends.  Doing so basically locks my home PC and i take over the session.  Anything that was open when i left for work in the morning is now accessible to me, and anything i leave open when i leave work and get home is as well.  Same session, same user, same everything.  I have 2 monitors at home but only 1 at work, so when i log in from work, the 2nd screen basically gets temporarily deactivated and everything takes place one the 1st.

I'm trying to get this setup with my new linux system.

I'm still running XP at work.

I've successfully gotten xdmcp to work with xming running on an XP machine, but only from my own network.  The only problem is i'm logging in as a second user / second instance of myself and i don't have access to the stuff i already have running on my first instance.

Whenever i try to access like this from work, all i get is the b/w hatch marks and no connection in xming.  I've noticed in the log file that the LAN ip of the xming machine is being displayed.  Is this where the linux machine is trying to talk back to?  Obviously this is not going to work as it is a private address.

VNC is not an option, as like i said before i have 2 monitors at home and only 1 at work, so this would make for A LOT of scrolling around.

Is what i'm want to do possible?  I've searched these forums for days and can't seem to find anything helpful on the subject.

Please keep in mind i haven't learned all the linux lingo yet, so go easy on me if you do have some suggestions.

Another thing, i have tried VNC and again can get it to work from within my home network, but not from work.  I'm wondering if my employer is blocking the required ports???  I've read some things about using SSH first and then getting in through xming / xdmcp but didn't really understand it all.

Please help, as this is my only major hold back on linux, and i really want to get away from windows.

---

### Post by hendysg on 2007-05-14
Hi Johnny,

I don't have an answer for you problem. I actually have a question for you. :)

Can you tell me how to use xming and xdmcp to connect from xp to ubuntu?
Or just point me to a page where I can get more info about this.

Thanks,

- hendysg

---

### Post by johnnyphive on 2007-05-14
Come on, somebody has to know something

---

