---
title: "Intermittent Internet/Broadband Issues"
date: 2006-06-30
forum: Absolute Beginner Talk
---

### Post by Danyl on 2006-06-30
Hi all

I'm an Australian user and since installing (the 32 bit version of) Ubuntu on my system, I'm getting an intermittent broadband connection issue. 

Occasionally (not always), after having booted up, I'll open Firefox and type in a url, however Ubuntu hasn't automatically connected to the internet.

I know the problem is software based as I dual boot to Windows and have no issues with it connecting to the web. Initially I tried the 64 bit version of Ubuntu (as I have an Athlon64) and this problem didn't occur at all under that installation, only now under the 32bit version has this problem started occurring.

To fix this problem every time it occurs, I'm going into Administration>Networking and selecting Ethernet Connection, deactivating it and then reactivating it which seems to solve the problem.

However come the next time I boot up, the problem will have reared its ugly head again! As the subject line states, its an intermittent problem so occasionally I'll boot up Ubuntu and connecting to the net won't be a problem.

I've searched the forums for other such scenarios however I couldn't find anything easy enough to follow.

Any assistance you guys could offer would be great!

---

### Post by simone.brunozzi on 2006-06-30
Hi Danyl!

(OT: compliments for the australian soccer team, you played very well, and most of us italian didnt' like the final free kick, it was not so evident, and we would have preferred to win in a more straight way)

I think that we can be of help with a log file... your description is fine, but without a log isn't easy to find a solution...
however, i'm not sure which kind of log we need... I'm using broadband behind a router since 2002, I lost familiarity with dialup connections :-)

Let me know

cheers,

---

### Post by Danyl on 2006-06-30
lol Thanks Simone in regards to the soccer....I know I speak for a lot of Aussies when I say we're proud of what the Australian Team accomplished.

Now in terms of the log, how do I generate one to help solve this problem? I'm relatively new to Linux so it might have to be a step by step process!

---

### Post by Apple 101 on 2006-07-01
This problem happens to me a lot too.  I've seen others with the same issue.  It is most likely a bug.  If anyone else knows where to find a log...?

---

### Post by Danyl on 2006-10-11
Bump.

Any help out there for this issue?

---

### Post by Apple 101 on 2006-10-12
The way I fixed this issue was to install the Network-Manager applet (search for network-manager in Synaptic).  Install the required dependencies.

The applet automatically starts your wired/wireless connections when needed, and will also switch from wireless to wired when you plug in a LAN cable.

---

### Post by Danyl on 2006-10-19
Fantastic! Thanks Apple, will try that.

---

