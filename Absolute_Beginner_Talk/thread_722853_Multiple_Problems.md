---
title: "Multiple Problems"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by CarnageX3 on 2008-03-12
Hello,

Right now i am on windows because of these problems. I will list them from priority.

1). Dial-Up Randomly Disconnects "a lot" and now wont Dial-Up at all, this is the reason I'm on windows right now, i didn't seem to have this problem before, also it auto connects at startup, which i don't like.

2). I cant change my login screen resolution "1152x864 is the one i want"

3.) Compiz fusion (Excuse if i said it wrong) Custom Preferences wont open.

I might reinstall Ubuntu, So it may take me awhile to mark this as Resolved.

Thats all
For now.... :(

Thanks!

---

### Post by Tatty on 2008-03-12
1) I cant help im afraid

2)  a) have you got the correct drivers enabled for your device?
      b) use the "screens and graphics" dialog (think its in system->administration) to set up your screen resolution.
      c) if it still refuses you could try reconfiguring X with ```
sudo dpkg-reconfigure xserver-xorg
```

3) do you have compizconfig-settings-manager installed?  if not ```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by CarnageX3 on 2008-03-12
Thanks for the reply

2). Yes, my video card is a Inergrated Intel card
      B. Did that
      C. Did that

3) I did that, but the manager wont open.

---

### Post by glennric on 2008-03-12
On 3, what happens if you run
```
ccsm
```
from a terminal?  (ccsm is compizconfig-settings-manager)
What output do you get?

---

### Post by CarnageX3 on 2008-03-12
Hold on I'm on windows let me reboot and see. Stupid Dial-Up...

---

### Post by glennric on 2008-03-12
Wait.  Don't reboot.  I think you need to have someone help you with the dialup issues first.  Unfortunately I know nothing about that in linux.

---

### Post by CarnageX3 on 2008-03-13
I'm back, i reinstalled Ubuntu "For the 7th time :mad:", My Dial-Up works, but I'm afraid its not going to be in a little while (Thats how its been for all the other installs) But hopefully i can find a solution, I've googled like crazy, and still no answers, all my hopes are on you guys "No pressure though :)"

Best regards,

---

### Post by CarnageX3 on 2008-03-13
Bump -- Need Help!

---

### Post by spiderbatdad on 2008-03-13
Try using gnome-ppp or kppp for your dial-up. Either will work in gnome.

---

### Post by CarnageX3 on 2008-03-13
Thanks a lot for that program, You solved my #1 problem :), Although i still have the others facing me, at least you took something off my back.

---

### Post by Shazaam on 2008-03-13
1. Try kppp in the repo's. It's for kde but will work on gnome (Synaptic will install neeeded dependencies). As far as auto-dial on boot go to System>Administration>Network and uncheck "Modem Connection" in the "Connections" tab. Don't worry, dialup will still work. It might help the disconnect problem too.
As an aside, what kind of modem do you have?

---

### Post by CarnageX3 on 2008-03-13
Is kppp better then the other recommended program? Conexant modem, and I'm using dells driver. Also, there is no kppp in the respos.

---

### Post by CarnageX3 on 2008-03-13
This would be easier if i could talk to some on on gaim.

---

### Post by spiderbatdad on 2008-03-13
kppp and gnome-ppp are almost identical. Go to System>>Administration>>Software Sources and check the boxes. Reload package manager and you will find it. Use IRC freenode #ubuntu* to chat with people about ubuntu.

---

### Post by CarnageX3 on 2008-03-13
I found it... but wow it is 22MB...

---

### Post by spiderbatdad on 2008-03-13
Thats about 12 hours on dial-up?:(

---

### Post by Shazaam on 2008-03-13
No, about the same. Kudos to Dell and their driver. kppp IS in the repo's if you have your Sources list correct. Go to System>Administration>Software Sources and check everthing but cdrom and "Pre-released updates (gutsy proposed)" then go to Synaptic and hit Update.
I am on dial-up too so I feel your pain during updates.

---

### Post by CarnageX3 on 2008-03-13
102MB of updates :( 5 hours

---

### Post by pbpersson on 2008-03-13
I don't think that many people still have dialup.

How long did it take to download the Linux CD image?

---

### Post by CarnageX3 on 2008-03-13
I still need help with my login screen though :( , Compiz Fusion i guess can wait, its last on the list anyways.

---

### Post by CarnageX3 on 2008-03-13
I didn't download "Lord that would take a day, literally" i ordered a free CD, and it came to me within 2 weeks. I still cant get over Ubuntu, and how poorly designed windows is, I'm on a box with a 1.8 Ghz processor and a integrated Intel card, yet i can have windows with nice shadowing, Transparency, windows that wobble when i move them, and transitions when i minimize windows. If this was on windows, my computer would blow up. :)

---

### Post by Shazaam on 2008-03-13
> **CarnageX3 said:**
> 102MB of updates :( 5 hours
Yep but once you are done the weekly updates aren't much.
BTW, the repos have kget (download helper) that I use to download large files so I don't have to worry about dial-up disconnects. It has a resume download function that works great. You don't need it for Synaptic if you have gnome-ppp (or kppp) set up to auto-redial.

---

### Post by CarnageX3 on 2008-03-13
Shaazam, what is your MSN addy "If you have one" It seems your a pretty good expert on Ubuntu, plus you have dial-up like me, so I'm assuming you could help me out A LOT more. Also, dose Ubuntu include Kernel updates? Or are those manual.

---

### Post by Shazaam on 2008-03-13
Lol no addy sorry. But either I or others are here to help.

---

### Post by xeth_delta on 2008-03-13
compiz-fusion:
A previous user mentioned the compiz config settings manager. Make sure you actually have it installed in your system

---

### Post by CarnageX3 on 2008-03-13
Compiz, or the manager?

---

### Post by xeth_delta on 2008-03-13
> **CarnageX3 said:**
> Compiz, or the manager?

I meant the manager. I suppose you already have compiz.

---

