---
title: "Ibook g4 not fully recognising ram"
date: 2008-07-02
forum: Apple Hardware Users
---

### Post by HappilySavage on 2008-07-02
Hi all, 

Im running Kubuntu 8.04 Hardy on a 12" ibook g4. i just purchased 1gb of pc2700 ram for it, and installed it. though its only showing that i have 700odd meg installed.. the built in 256, and half of the new 1gb stick.. is this bizarre? cos it seems so to me. 

i researched about the ram that would work with my ibook and it claims to support 1.25 total ram. 

any ideas people?

cheers
HS

---

### Post by stream303 on 2008-07-02
Will it recognize the full 1gb stick all by itself in the main slot?  Maybe swapping the ram positions around will get you the full 1.25gb?

---

### Post by HappilySavage on 2008-07-02
hmm i dont think i can get to the main slot can i? all ican see is the expansion one under where the airport space is

oh and some great news.. i reset the pram and the pmu on the ibook as per some other forum, and now kdm is crashing when it tries to load! 

Cheers
HS

---

### Post by stream303 on 2008-07-02
You're right - it only has one slot.  I was thinking of my G5..

Can you get to a virtual terminal, CTRL-ALT-F1

I ran into a similar problem on my iBook, but it would crash after gdm because the date was wrong.  Not sure if this helps, but check your date:

[https://help.ubuntu.com/community/UbuntuDateBug](https://help.ubuntu.com/community/UbuntuDateBug)

Also, does

```
free -m
```

show any difference now?

---

### Post by HappilySavage on 2008-07-02
hmm yep i can get to a terminal. 

but free -m still tells me i only have 754mb of physical memory. 

what can i do from the terminal to get it to boot again? it wouldnt work after the pmu reset.. 

thanks for the help
HS

---

### Post by stream303 on 2008-07-02
The date is correct in the terminal right,
```
date
```

---

### Post by stream303 on 2008-07-02
As a side note: now that you have added a significant amount of ram, your swap partition may no longer be sufficiently large enough, ie typically 1 - 2.5 times ram.

While you can run with a swap partition smaller than your installed ram, especially with a pretty large amount to begin with, I'd still make that swap partition at least 1x your ram sometime in the future.

---

### Post by HappilySavage on 2008-07-02
awesome, that date change tipoff was money. ive now got it booting again which is mint.. now to see if the ram gets recognised after a pmu and pram reset.

edit: free -m still reports 754mb of ram. gutted. i guess the stick is shoddy, will try a frsh one. 

thanks for the help, if theres any other ideas why my ibook isnt recognising more than a half of this 1gb stick, id be keen on trying stuff out :) 

Cheers
HS

---

### Post by stream303 on 2008-07-02
Great - yeah, with my ibook every time I zapped the pram, I had to reset the date per that faq.

That ram stick may be bad, but depending on the hassle / cost of replacing it, 745mb of ram isn't too bad!

Also, is the video in your ibook ATI or Nvidia?

With my late-2004 ibook with nvidia, Network Manager was eating up 100% cpu time as shown by top (and the fact that it was just sluggish, running hot with the fans coming on :)  I had to disable NM (rather than remove it) so it might be wise to run top, or download and run Htop to make sure you don't have any runaway processes after a new install.

[https://help.ubuntu.com/community/NetworkManager?action=show&redirect=WifiDocs%2FNetworkManager#Disabling%20NetworkManager](https://help.ubuntu.com/community/NetworkManager?action=show&redirect=WifiDocs%2FNetworkManager#Disabling%20NetworkManager)

After this I had to reconfigure my network and all was well - although I don't run wireless.

---

### Post by mikael.gron on 2008-10-05
From the Apple website, on the page where you can identify your laptop, you might get the idea that the iBook late 2004 model is compatible with PC2700 RAM. But, other websites more or less clearly states that the late 2004 model only accepts PC2100 RAM... So that's what I bought!

I too am running Ubuntu on a late 2004 iBook G4. the 1GB PC2100 arrives by mail tomorrow, so I'll let you know how well it works!

Mike

---

