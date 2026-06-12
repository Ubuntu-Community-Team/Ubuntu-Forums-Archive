---
title: "Powerbook G4 tips?"
date: 2009-12-13
forum: Apple Hardware Users
---

### Post by frankwakeman on 2009-12-13
A friend has had some bother with her Mac.  I said I'd reinstall her OS this week, and also set it up to dual boot with Ubuntu or Kubuntu so that she could use that partition for internet and keep the Mac OS bit clear for her film-making hobby.

While she tried to reinstal Mac OS (10.3, I think) there was some last minute problem when it had been doing the task for some time.  I'm thinking that its file system has gone awry somewhere and that using GParted I can sort that out.

But, especially if someone here has got Ubuntu going on the same machine (a 17-inch, 1.5 ghz, 1gb one from 2004), is there anything else I should know or preparation I can make in the meantime?  I see I need a different version of Ubuntu than the ones I've been burning all year for my laptop.

I'm also not mad keen on using 9.10 as it has been a bit of a nuisance for me, and not the best version to 'sell' the product to my friend, taking the Linux plunge for the first time.  8.04 or 9.04 is likely, 8.10 at a push.

Is everything else the same as for PCs?  Downloading and installing Ubuntu Restricted Extras and so on?

Any reason why Kubuntu might be a problem?  Is the wireless support simple/immediate?  Is the latest Firefox working fine with a computer of that speed?

I think the machine has an ATI Radeon graphics chip, but I'm not certain.

Lastly is there a best and most reliable download site for the Mac's iso for someone in the UK?

Many thanks in advance.

---

### Post by rednose0607 on 2009-12-13
Hi,
I can share my experience. I've aluminium PB 15". 9.04 was a pain, due to the ATI issue, and I wasn't able to sort it out recompiling the kernel. Then I went for 9.10. I used gparted to repartition my hd, all ok (but I was ready to reinstall, backup done). With the last update it works reasonably well. The only major annoyance is the lack of flash ...
bye

---

### Post by frankwakeman on 2009-12-14
Lack of flash?  As in, there is no flashplayer facility?  That would make it not so useful for my friend.  Can you confirm this?

Or do you just mean it's not as 'flash'-looking as Mac OS?

Thanks.

---

### Post by linuxopjemac on 2009-12-14
there is no Adobe flash player, only open source variants like gnash. Flash/ppc is working badly.

---

### Post by rednose0607 on 2009-12-14
> **frankwakeman said:**
> Lack of flash?  As in, there is no flashplayer facility?  That would make it not so useful for my friend.  Can you confirm this?

Or do you just mean it's not as 'flash'-looking as Mac OS?

Thanks.

Yep I confirm, as already reported :( no official flashplayer support from adobe. ONLY for PPC AND LINUX flashplayer is not existing. Yes in other flavour, like linux and intel, or osx and ppc.

Mistery of big company ...

Bye

---

### Post by frankwakeman on 2009-12-14
Okay, thanks for that - and you've saved me a bit of time knowing that 9.04 wouldn't be the best choice in view of the ATI card.

It seems weird though that the Ubuntu .deb of Flashplayer won't work, after all the same file runs on laptops and pcs with many different configurations of chips.  Oh well, I can't pretend to understand.

---

### Post by linuxopjemac on 2009-12-14
you have a powerpc powered computer as opposed to all those Intel powered ones. Programs have to be compiled differently. That explains it all. .deb programs written for Intel chips don't work for your G4.

---

