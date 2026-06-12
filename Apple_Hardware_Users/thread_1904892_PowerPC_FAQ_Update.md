---
title: "PowerPC FAQ Update"
date: 2012-01-05
forum: Apple Hardware Users
---

### Post by rsavage on 2012-01-05
Hi All,
 
It's been over a year since the FAQ has had an update and I'm just wondering if anybody would like to help me bring it back to life?
 
I'm thinking of "retiring" from the Apple forum and it will niggle me if I leave the PowerPC FAQ in such a poor state.
 
I've never done any wiki editing before, it looks a little bizzare, so if you're a whizz at this sort of thing then your help will be greatly appreciated.  
 
I would very much like to hear ideas of what new things should be in there.  If I'm left on my own to update it then I'm liable to slash and burn large chunks of the current FAQ, so if you are particularly precious about a part of it then you better let me know!
 
Thoughts/suggestions/help appreciated.
 
Thanks

---

### Post by canhoto on 2012-01-06
It would be useful to address the issues regarding the 11.04 upgrade (slowness) and the 11.10 upgrade (not rebooting after upgrading).

---

### Post by rsavage on 2012-01-07
The solutions to these problems have been on the forum for a while now, but they are now on the Known Issues page too!  [https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

---

### Post by rsavage on 2012-01-14
Just an update....
 
I've tidied up the Downloads page and removed all old links. I've added the 12.04 CDs that are available for testing.
 
The Known issues page is now up-to-date. There is even a section for 12.04. Can people confirm the mirror archive/server problem still exists for 12.04 live CDs? I've put what I think the problem is from looking at the code. I'm a bit rusty at reading code though....
 
The PowerPC FAQ now has all the information that the Lubuntu thread has. It still needs a tidy up/spell check etc.

---

### Post by conal on 2012-01-14
Good work rsavage!

---

### Post by conal on 2012-01-14
Hi rsavage, was it you that added the bit about booting from USB? I found this very usefull as I wanted to try the 12.04 desktop cd but my cd drive is gubbed! 

Booting by holding down the option key did not work on my lampy, the way that worked for me was:

> ...restart the machine into openfirmware (hold down Command-Option-o-f while turning on). To boot the USB device type

boot usb0/disk@1:2,\\yaboot 

or something similar like "boot usb1/disk@1:2,\\yaboot", "boot usb1/disk:2,\\yaboot" or "boot ud:2,\\yaboot". 

Except that for some reason it saw my usb stick as usb-2a - so instead of the examples in the PowerPCFAQ I typed:

```
boot usb-2a/disk@1:2,\\yaboot
```

I worked this out by following the "how to boot" advice here: [http://ppcrcd.pld-linux.org/docs/usb_boot.html]("http://ppcrcd.pld-linux.org/docs/usb_boot.html") (except replaced tbxi with yaboot). 

Anyway, thought I'd share that for anyone else that might find it useful!

---

### Post by conal on 2012-01-14
Also, I managed to install from the live usb to the hard drive without the mirror archive/server problem you talk about.

Thanks!

---

### Post by rsavage on 2012-01-15
Thanks Conal for the feedback and the useful link.  I have ammended the FAQ USB instructions as I too couldn't get the option/alt key to work (when I briefly had a working G3 iBook over xmas).  I think it has something to do with the tbxi attribute or partitioning scheme used on the iso.  
 
I have now included the link you gave in the instructions.  That seems an easier way to find the openfirmware path - the output from the "dev / ls" command just looks way to complicated and scary I think.
 
If you have any other useful links up your sleeve then please do add them to the FAQ!!  I'm trying to get it in a state that will be easy for people to edit and keep up-to-date.  Hopefully, it will then be a good resource for anyone running PowerPC linux (whatever distribution they use - not just Ubuntu).  Well that is my aim anyway.  Posting stuff on forums is alright, but it is hard to find and easy to loose!
 
Since I haven't used a PowerPC machine properly for about 6 months now I'm relying on others to take over the FAQ's maintenance.  
 
I've added a comment on the Known Issues page that you didn't have the archive error.  That is strange because somebody posted just 4 days before you that they got it.  I can't see any changes that would have fixed the problem.  Maybe it is because you are in the UK?

---

### Post by conal on 2012-01-15
I don't know why I didn't get the archive error -  I looked at the bugs filed on this subject and other people said they were getting the error even if they weren't connected to the internet. The install did actually freeze near the end - no error message just totally frozen. I disconnected from the network, rebooted and carried on and it finished - very strange!

---

### Post by canhoto on 2012-01-15
> **rsavage said:**
> Just an update....
 
I've tidied up the Downloads page and removed all old links. I've added the 12.04 CDs that are available for testing.
 
The Known issues page is now up-to-date. There is even a section for 12.04. Can people confirm the mirror archive/server problem still exists for 12.04 live CDs? I've put what I think the problem is from looking at the code. I'm a bit rusty at reading code though....
 
The PowerPC FAQ now has all the information that the Lubuntu thread has. It still needs a tidy up/spell check etc.

Sorry for my ignorance... where are these pages? Is there a link (also for the FAQ's update)?

---

### Post by rsavage on 2012-01-16
> **canhoto said:**
> Sorry for my ignorance... where are these pages? Is there a link (also for the FAQ's update)?
 
[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)
[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)
[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)

---

