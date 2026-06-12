---
title: "getting so close"
date: 2005-12-16
forum: Absolute Beginner Talk
---

### Post by RBH on 2005-12-16
well, closer anyways. every question i have had so far i have finally gotten worked through. i got firefox updated to 1.5 and workin good with all my bookmarks, history, etc. i have learned how to mount my two extra ntfs formatted harddrives to read the files on them when i had them in a windows machine. i have two other things to work through, but i will start with the main one first.

  i have tried following a tutorial on connecting with my windows network so that i can see those pcs and they can see me. our main printer is hooked to one of these machines so i need to make a connection to the network in hopes of connecting to that printer. what i have is a linksys router. my local network is called home. now, in the tutorial it instructed me to install ssh server i think it was. anyways, i got that done. it then says to download something called winscp or something like that. well, when i attempt to do that, my machine locks up and i have to force firefox to close. can someone that has successfully joined a ms network help me or is this to advanced considering i have only used linux for a few days? any help would be appreciated!:D

---

### Post by Mustard on 2005-12-16
What tutorial are you using?

I would have thought that you would need samba to access windows shares on your local network.

[https://wiki.ubuntu.com/SettingUpSamba](https://wiki.ubuntu.com/SettingUpSamba)

ssh is used for remotely accessing a computer ie accessing your home computer from your office or other such uses.  So I think that might have been a the wrong direction to take.

Try reading over the Samba guide above and see if that is more like what you are after.

It is a bit advanced for someone who is new to linux.  There may be little obstacles along the way that cause you some grief due to terminology and a lack of familiarity with the way linux works.

You could try joining the ubuntu irc support channel at irc.freenode.net on channel #ubuntu.  In there you could ask questions as you move through the installation process and see if you can find others who have done it and are willing to help.  I think lately freenode might be using a different server called chat.freenode.net due to a rash of spambot attacks.  The X-chat irc client is installed by default in the Applications>>Internet menu.

---

### Post by RBH on 2005-12-17
holy moses..............ok, i had gone through trying samba before and had problems getting things to work. well, i went back through everything again and figured out how to stop and restart it and VIOLA! everything works perfect. i can browse those computers and everything as if i was on a windows machine. thanks for the help, because of your suggestion it made me revisit my prior steps and learned more then i did the first time. as soon as i get done playing with this new found knowledge i will post on my other problem. thanks again!

---

### Post by Mustard on 2005-12-17
Well done. :)

---

