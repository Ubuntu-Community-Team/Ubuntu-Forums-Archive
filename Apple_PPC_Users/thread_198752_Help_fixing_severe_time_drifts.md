---
title: "Help fixing severe time drifts"
date: 2006-06-17
forum: Apple PPC Users
---

### Post by daft_ska on 2006-06-17
My g3 500 iMac has this odd thing where the time drifts forward much faster than it is.  I updated the time about 11 AM today, and it's 4:17 PM, but my iMac would like to tell me it's 5:49 PM. I've tried using the "Periodically update time" and selected an ntp server, and I can see ntpd is running, but it just does not work.
In related problem solving, hwclock can't access the hardware clock via "any known method." I've seen hwclock attempting to be run during setup, however, and when I use the 6.06 liveCD on my iBook, it can't figure out what the time is.  I've searched like crazy trying to figure out what to do, and found adjtimex, but I just can't seem to get that doing some good.

Any thoughts?

---

### Post by BoneKracker on 2006-06-18
hwclock doesn't work on ppc.  the equivalent method is "clock".  I don't know why that's in the initscripts; it's annoying.

As to the drift, I'm not sure what the fix is.  Was your clock reasonably close to correct when you first installed and activated ntpd?

You might also want to try adding some servers.  Try the following:

server 0.us.pool.ntp.org
server 1.us.pool.ntp.org
server 2.us.pool.ntp.org

or better yet (I'm not sure if this works in Linux):
servers us.pool.ntp.org
(that would select a random group of eight)

Of course, try the man pages for ntp.  I recall seeing detailed discussion of how drift is managed.

---

### Post by nkbj on 2006-06-18
hwclock **does** work if you add this line to the top of /etc/modules:```
genrtc
```

---

### Post by BoneKracker on 2006-06-18
Good to know!  Thanks.

Too bad the installer doesn't set that up.

---

### Post by daft_ska on 2006-06-19
Thanks, guys! I have put genrtc in my /etc/modules
and I have synced the clock, and ran "sudo hwclock --systohc" and now am re-installing adjtimex, and will get ntpd up and running as soon as I get back home. We'll see if we can't just get this drift under control! I'll post with an update to help anyone else who may be experiencing this issue.

---

### Post by Ptero-4 on 2006-06-20
Check also your computer's PRAM battery. Constant time drifts means a dying or dead PRAM battery.

---

### Post by BoneKracker on 2006-06-20
So tell me if I've got this right and what you think we can pass up as suggested solution:

The initscripts are calling hwclock during boot up and shut-down, and this generates the "cannot access clock by any known method" because hwclock doesn't work on macppc without genrtc?

It seems to me, however, that ntpd (and ntpdate) have been working fine on my G4 without this driver, am I imagining this?

Other than telling each user to add the module, should the long-term fix be to:
  a) ask for a change to the initscripts so it makes use of 'clock' instead of 'hwclock' if running on the affected architecture
  b) ask for installer logic that adds the genrtc module for the machines that need it
  c) ask for genrtc to be added to the standard kernel config for powerpc

---

### Post by daft_ska on 2006-06-20
Here's the update, at least on this end, and some more food for thought:

1. As far as things go, adding genrtc to /etc/modules was, I think, perhaps just what the doctor ordered.  hwclock when run from the command line is giving me some off times, but the clock that is displayed in the top left of my screen has now been good, with one minor hiccup yesterday.  It still desparately needs ntpd to stay correct though, as unplugging it from the 'net causes severe drift.  PRAM _could_ be at fault here, but I'm not entirely sure how to tell.

2. My ibook G4, when run from the liveCD does indeed try to run hwclock, and upon being booted without the internet available is completely clueless as to what the time is, so I do think that something needs to be changed with that, and I would think that maybe genrtc in the ppc kernel config wouldn't be such a bad idea.

---

### Post by BoneKracker on 2006-06-21
If you want to test it (and possibly replace it) take a look at this thread from yesterday (although there may be better info if you search):

[http://ubuntuforums.org/showthread.php?p=1159866#post1159866](http://ubuntuforums.org/showthread.php?p=1159866#post1159866)

---

### Post by badgerclan on 2007-02-19
Running 6.10 on a Mac Mini PPC and having the same issues.  Have tried several fixes running an hourly script and syn with hwclock but prefer to fix the problem. An additional problem for me is my connection is via satellite with high latency.

Recommend running the genrtc module and installing adjtimex to fix the tick. Further information on the PPC tick problem can be found here: [http://ntp.isc.org/bin/view/Support/KnownHardwareIssues](http://ntp.isc.org/bin/view/Support/KnownHardwareIssues) at the NTP site which suggests some scripts to adjust tick. Also [http://lists.debian.org/debian-powerpc/2005/04/msg00725.html](http://lists.debian.org/debian-powerpc/2005/04/msg00725.html) shows a script which I have not tried.

If anybody knows a simpler methods thats as accurate please post and I'll work on a HOWTO

---

