---
title: "Azureus"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by Falc7 on 2007-11-03
I downloaded Azureus manually off their site, and everything worked fine, sure i had to open a text file in the terminal and keep it open every time and it was a little annoying, but no real problem.
Any way, later i found i could install Azureus using the applications -> add/remove programs way. So i did that, because i thought great, i can have Azureus in that convenient little window rather than manually have to find the file each time, however after i downloaded and installed Azureus this way, whenever i try to start Azureus from the applications -> internet menu, it tries to start, then asks me what language i would like to use for a second, then it completely disappears and nothing happens. 
Any way to fix this, i would like to have azureus working off the applications -> menu.

Also, is there a way to make shortcuts in Ubuntu?
THanks

---

### Post by rye_ on 2007-11-03
I nokw that what I'm about to say (?) is not quite what your looking for, but IMHO opt for deluge or ktorrent, I don't think azureus offers many advantages over these, and I had nothing but trouble with azureus.

Ryan

---

### Post by Pumalite on 2007-11-03
Uninstall from Synaptic, then download from sourceforge.net
(extract it to your /home to have it handy)

---

### Post by KOld Iron on 2007-11-03
I had a similar problem with Azureus. First it worked fine, then I could not start it anymore (same symptoms as you describe). When I started it from the console the messages seemed to indicate some problems with Java (I'm an Ubuntu newbie, so I did not really understand the problem). Anyways, what I did, was to uninstall it, then delete the /user$/.azureus directory and then re-install it. After that it started up fine again. I assume by deleting the directory I also got rid of some profile information that may have been the source for the problems. Give it try, maybe it works for you too.

---

### Post by Cochise on 2007-11-03
i would recommend deluge as the second poster said it kicks azureus´s a$$, did you remove the one you downloaded before installing from synaptic

---

### Post by gilgongo on 2007-11-03
Deluge? Last I used it, it looked and worked almost exactly like Azureus, only without the (very useful) plugins - like SafePeer. 

What's so good about Deluge?

---

### Post by poudin on 2007-11-03
i had the same problem with Azureus with crashing at language selection screen...so I scrapped it...using qBittorent v1.0.0rc6 now...and seems to work great for me....another option you can try

---

### Post by SOULRiDER on 2007-11-03
I suggets you open Azureus froma  Terminal by typing azureus and see what errors it spits.
I use rTorrent, its console based but its a lot lighter than any of the other clients.

---

### Post by nwadams on 2007-11-03
i used to love azureus, but lately i've been using deluge and it works great
I had the same problem as you and i tried everything so i looked for a new client

---

### Post by Falc7 on 2007-11-03
Thanks guys, in the end i decided to scrap it and i am now using deluge, which is working fine, i didn't try uninstalling it and deleting the directory, then reinstalling, but it sounds like it could work, if i go back to Azureus i will try that, thanks

---

### Post by por100pre1 on 2007-11-03
> **gilgongo said:**
> Deluge? Last I used it, it looked and worked almost exactly like Azureus, only without the (very useful) plugins - like SafePeer. 

What's so good about Deluge?

The good thing about Deluge it that it works fine. There are daily posts about Azureus issues in these forums.

```
sudo aptitude install deluge-torrent
```

---

### Post by Falc7 on 2007-11-03
As i said i am using Deluge now, but can i download only a few files, rather than the whole thing?
ie, if i am downloading a cd, can i choose to only download one track from the cd?

---

### Post by Shunketsu on 2007-11-03
Hi, if you do decide to go back to Azureus and still get the same problem, see if you have the java runtime environment installed. It's either in the add/remove programmes list or the synaptic package manager.

---

### Post by odinb on 2007-11-03
> **por100pre1 said:**
> The good thing about Deluge it that it works fine. There are daily posts about Azureus issues in these forums.

```
sudo aptitude install deluge-torrent
```

...and what repository did you have to add to get that to work? Is it updated frequently when new builds of deluge are released?

---

### Post by Cochise on 2007-11-11
> **Falc7 said:**
> As i said i am using Deluge now, but can i download only a few files, rather than the whole thing?
ie, if i am downloading a cd, can i choose to only download one track from the cd?

down the bottom pick files and choose what you want, if its not there click plugins and add it.

---

