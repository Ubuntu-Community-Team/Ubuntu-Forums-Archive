---
title: "How to stream music in Audacious?"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by koreninja on 2008-01-08
Is that possible? I know I can do it with XMMS and streamtuner, but i really don't like XMMS and have just got audacious 1.45 working. Is there anyway to use streamripper/streamtuner with audacious or something very similar? 

Thanks in advance.
KN

---

### Post by linuxwizard on 2008-01-08
Open Streamtuner > Edit Tab > preferences > Applications > first line > Listen to a .m3u file > change XMMS to audacious (double clickon to highlight) > don't change anything else. Now you can use Streamtuner with Audicious

---

### Post by dag0 on 2008-02-09
> **linuxwizard said:**
> Open Streamtuner > Edit Tab > preferences > Applications > first line > Listen to a .m3u file > change XMMS to audacious (double clickon to highlight) > don't change anything else. Now you can use Streamtuner with Audicious

I get this message when I use streamtuner:
Unable to tune in - Error - audacious/tmp/streamtuner.shoutcast.W1565T.m3u  (no such file or directory)
I cut some text since it's in norwegian :-) Hope you understand

Dag

---

### Post by linuxwizard on 2008-02-09
It could be just a problem with the radio station you were trying. I have had errors with radio stations before.

---

### Post by dag0 on 2008-02-09
I tried alot of others now and I get the same msg:
```
Unable to tune in

Feil under kjøring av underprosess «audacioushttp://wm2.181.fm:6000/181-realcountry.ogg» (No such file or directory).

and this on another station

Unable to tune in

Feil under kjøring av underprosess «audacious/tmp/streamtuner.shoutcast.QVC85T.m3u» (no such file or directory).
```


So I think its something in my setup here. I installed audacious from synaptic then uninstalled, put this code to the source.list:
deb [http://backports.dereferenced.org/](http://backports.dereferenced.org/) gutsy universe 
To get the latest version of Audacious. To play mp3's from my hdd works great.

maybe I have to delete the new version and install the old one again?

Thanks for answer linuxwizard :-)

Dag

---

### Post by linuxwizard on 2008-02-09
On that first line where you changed xmms  it should look like this >  audacious %q  > just make sure when you highlighted xmms that you didn't remove %q

---

### Post by dag0 on 2008-02-09
In streamtuner it is set like this: audacious%q

I just tried to change to rhythmbox and totem with %q at the last in Streamtuner also but got the same msg: unable to tune. It miss that /******/tmp/*********m3u file. 
So I'll try to uninstall the prog and put it back again :-) 


I'm an beginner in linux. Not my strongest side this. But I'm learning


Thanks 

Dag

---

### Post by linuxwizard on 2008-02-10
Not for sure if it makes any different or not but their has to be a space between audacious and %q >  not like this > audacious%q > like this >>audacious %q

---

### Post by dag0 on 2008-02-10
Did not help to reinstall...

Streamtuner is looking for the m3u file and that file is located in /tmp/ @ the root of the hdd. Can this be that the program don't have the premission to pick up the file from outside my home directory ?

Dag

---

### Post by linuxwizard on 2008-02-10
I don't understand why Streamtuner is looking in your /tmp/. Did you change anything else in Streamtuner preferences ?

---

### Post by dag0 on 2008-02-10
> **linuxwizard said:**
> I don't understand why Streamtuner is looking in your /tmp/. Did you change anything else in Streamtuner preferences ?

No I did'nt. Only put audacious%q in streamtuner. It can be Audacious who is looking into the /tmp/ folder? to start the m3u radio file...This problem started after I installed the newest version of Audacious.
I uninstalled streamtuner and audacious and manually deleted the hidden folders also in my home directory. Reinstalled and the same problem. I think the problem is in the streamtuner since it's the same error with other apps too. 

Dag

---

### Post by lara22 on 2008-05-03
Hi, I had same problem as dag0, just by hit and trial method i added space between audacious and %q and it worked.

---

### Post by bluewhale on 2008-06-19
Linuxwizard:   I wasn't able to see a way to offer official thanks in this forum for your details on an XMMS replacement, so 


THANKS! 


=D>:-\"=D>

---

### Post by linuxwizard on 2008-06-19
bluewhale
You're Welcome
When you want to Thank someone for a useful post that helps you go to that post and look on the right side of that post and their is a yellow star click on that.

---

### Post by bluewhale on 2008-06-19
I thought so.  However in this case there  was no yellow star there for your name, at least for that posting. In looking at page two of this thread I see some have a star showing and some do not. 

Whom must one pay to have the yellow star visible?? :biggrin:

---

### Post by linuxwizard on 2008-06-19
I have never noticed that before. I see some that do have the Thank star and some don't. Not sure why that is.

---

