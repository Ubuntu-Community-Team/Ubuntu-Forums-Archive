---
title: "Kind of late to ask after already having setup dual boot"
date: 2008-05-08
forum: Apple Hardware Users
---

### Post by Brightbelt on 2008-05-08
Hi,
I've already set up dual boot with Ubuntu 8.04 on my iMac with OS X...

I read a post here earlier this morning which caught my attention really fast...Does this mean that I can no longer do any firmware updates on my Mac side??

If that's true, what am I really giving up by sticking with a dual boot and not updating firmware?

From what I read, the only fix is to reformat and reinstall OS X completely. Is that right?

I appreciate any clarification on these matters. Just want to know etc....
Frank B.

---

### Post by cyberdork33 on 2008-05-08
> **Brightbelt said:**
> Hi,
I've already set up dual boot with Ubuntu 8.04 on my iMac with OS X...

I read a post here earlier this morning which caught my attention really fast...Does this mean that I can no longer do any firmware updates on my Mac side??

If that's true, what am I really giving up by sticking with a dual boot and not updating firmware?

From what I read, the only fix is to reformat and reinstall OS X completely. Is that right?

I appreciate any clarification on these matters. Just want to know etc....
Frank B.no you are misreading something. you can perform firmware updates from OSX as long as you did not remove your GPT. Which, most people do not unless they really know what they are doing.

---

### Post by Brightbelt on 2008-05-08
Thanks Cyber!! Can you possibly help me with one more question? 

I do keep a LaCie external drive hooked up for Time Machine and I think this perhaps keeps rEFit from doing its boot menu consistently from the Mac side.

Whenever I reboot from the Mac side, I always have to run this code:
```
sudo /efi/refit/enable-always.sh
```

in order to get the rEFit menu to show up. If I'm rebooting from Ubuntu, there never seems to be a problem.

Is there anything I can do short of giving up the LaCie for my time Machine? (Which I'd obviously prefer Not to do)....

Many Thanks, and if we need a separate thread, I can start one,
Frank B.

---

### Post by cyberdork33 on 2008-05-08
having another drive hooked up shouldn't prevent refit from working.... usually for menu would appear if I just disconnected my external device (iPod).

I use Time Machine with a Network share so I haven't experienced your problem.

---

### Post by Brightbelt on 2008-05-08
What then can I do? I have to run the code I mentioned above ahead of time every time I reboot from the Mac side. If I don't, I don't see the rEFit menu, period.

I'm glad to hear that my Time Machine drive is ok with rEFit. 
And I've already tried reinstalling rEFit, BOTH at the command line and through the DMG package.

Is there anything else I can try?

Many Thanks, Frank B.

---

### Post by cyberdork33 on 2008-05-08
> **Brightbelt said:**
> What then can I do? I have to run the code I mentioned above ahead of time every time I reboot from the Mac side. If I don't, I don't see the rEFit menu, period.

I'm glad to hear that my Time Machine drive is ok with rEFit. 
And I've already tried reinstalling rEFit, BOTH at the command line and through the DMG package.

Is there anything else I can try?

Many Thanks, Frank B.
have you tried disconnecting first, then rebooting? do you have the same problem?

---

### Post by Brightbelt on 2008-05-08
Ok, Cyber...I tried:

Disconnecting everything;
Repairing Permissions & re-installing rEFit;
Re-booting an extra time to make sure....

None of these helped. Sometimes the answer to something like this will emerge later on its own. That's what I hope.  ;)

Many Thanks, Frank B.

---

### Post by russo.mic on 2008-05-09
Maybe I'm mis-reading, but did you accidently install rEFIt to the firewire harddisk?

Russo

---

### Post by Brightbelt on 2008-05-09
No, not that I'm aware. I was just mentioning that my external drive on firewire was my back up drive for Leopard's Time Machine. 

I was wondering if that was "confusing" rEFit...But Cyber says probably not.

Does that clear it up for you? Thanks, Frank B.

---

### Post by cyberdork33 on 2008-05-10
> **Brightbelt said:**
> No, not that I'm aware. I was just mentioning that my external drive on firewire was my back up drive for Leopard's Time Machine. 

I was wondering if that was "confusing" rEFit...But Cyber says probably not.Well, if you get the same problem with or without the drive attached, then I can't say that I think it is the source of the problem.

---

