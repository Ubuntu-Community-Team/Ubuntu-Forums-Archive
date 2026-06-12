---
title: "i need a wifi idiot guide plz"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by timofthec on 2006-07-14
right, so i've got unbutu installed and can now dual boot to either win98, winxp or ubuntu :D that’s a major achievement.

the next step is to get me wireless network up and running through ubuntu (it already works in xp).  now i've been combing the forums trying to find a simple guide on how to do it but i can't find one, just lots of posts of how difficult it is to get it working.  i found references to ndiswrapper and have downloaded it and worked out what it's supposed to do, however, i'm really still at a loss on what to do next and i'm beginning to feel at a complete loss](*,).  therefore, is there any smart and generous peeps out there that can give me a bit of an idiots guide on how i can get the wireless network running in ubuntu please.

the wireless card that i have is a belkin 54g F5D7000uk pci card that connects to a lynksys WRT54G broadband router.  

i've checked the device manager under ubuntu and the belkin card is recognised, although a lot of the info appears to be unknown (no surprise i suppose seeing as i haven’t installed a driver yet).

I would be grateful for any help and assistance with this

---

### Post by Ptero-4 on 2006-07-14
You may want to install ndisgtk which is a GUI for ndiswrapper. Also what you need is the .sys, .inf and .ini files from the driver that XP is using for your wifi card. Copy them to a folder in your home folder while on ubuntu and then point ndisgtk to that folder and it should activate your wifi.

---

### Post by NESFreak on 2006-07-14
[https://help.ubuntu.com/community/WifiDocs/](https://help.ubuntu.com/community/WifiDocs/)

---

### Post by timofthec on 2006-07-15
ok - so i've got a copy of ndisgtk, what do i do with it?

as the title of this thread intimated - i need an "idiots guide" to setting up me wifi.  maybe i should amend it to a "complete idiots step by step guide" on what needs to be done cus i aint got a clue ](*,) 

the one thing i have managed to sus out is that me belkin card has a broadcom chip which a notorious at being difficult to set up in linux - figures i suppose.

again any help would be greatly appreciated

---

### Post by wildseven on 2006-07-15
I didn't find it hard at all. Unless there is something i dont know lol.
I did:
```
$: sudo apt-get install wifi-radar
$: wifi-radar

```

Hope this helps.

---

### Post by timofthec on 2006-07-15
thanx for that wild7.

however, what exactley does it mean and wot am i supposed to do?

honest, wen i say complete idiot, its not an understatment :-D

---

### Post by wildseven on 2006-07-15
lol it's ok. i know what you mean.
Well it's a program i got from the repositories.
it detects any wireless and automatically connects you. you also have an option what to choose from.
the gui is started by 
```
$:sudo wifi-radar
```

edit// lol sorry, you also asked what does it mean.
well the command:
```
sudo apt-get install wifi-radar
```
^--this command will search the repoositories online ( think giant archive ) and install wifi-radar.

you can also uninstall by the:
```
 sudo apt-get remove <filename> 
```

hope that helps if that is what you meant.

---

### Post by timofthec on 2006-07-15
ok, now its getting reaaly reaaly frustrating - :confused: :mad: ](*,) 

I have read a number of how-tos and the posts in this thread as well as the posts in lots of other threads and i'm getting no where pretty damn fast](*,) ](*,)

Wild7 - thnx for the info and the posts but i can do nothing with "wifi-radar" as i can't find it or get it to do anything, even typing the code you provided.

i have been working through a how to written specifically for my belkin card and i have the driver that was recommended.  however, when i type the code suggested (i even copied and pasted the code out the guide and changed it to reflect my file locations) i get a message that the command is not known.

i'm beginning to suspect that i have not properly installed ndiswrapper1.8.  i've read the install instructions that came with it but it might as well be written in Chinese cus its complete gibberish to me](*,) 

therefore (taking a deep and calming breath) can anyone provide me with an idiots (and i do mean idiots) guide on how i should have or should install ndiswrapper.  If you also give me some insights as to how "ndisgtk" fits into the equation i would also be most grateful.

---

### Post by wildseven on 2006-07-15
hey, if you have AIM i can help you through that.

also, have you taken out the hashes in your /etc/apt/soruces.list ?
so you can use the repositories.

---

### Post by da1nonlymikeo on 2006-07-15
> **timofthec said:**
> ok, now its getting reaaly reaaly frustrating - :confused: :mad: ](*,) 

I have read a number of how-tos and the posts in this thread as well as the posts in lots of other threads and i'm getting no where pretty damn fast](*,) ](*,)

Wild7 - thnx for the info and the posts but i can do nothing with "wifi-radar" as i can't find it or get it to do anything, even typing the code you provided.

i have been working through a how to written specifically for my belkin card and i have the driver that was recommended.  however, when i type the code suggested (i even copied and pasted the code out the guide and changed it to reflect my file locations) i get a message that the command is not known.

i'm beginning to suspect that i have not properly installed ndiswrapper1.8.  i've read the install instructions that came with it but it might as well be written in Chinese cus its complete gibberish to me](*,) 

therefore (taking a deep and calming breath) can anyone provide me with an idiots (and i do mean idiots) guide on how i should have or should install ndiswrapper.  If you also give me some insights as to how "ndisgtk" fits into the equation i would also be most grateful.




you may be having the same proplem i had. i just got my wifi working last night, i used [http://ubuntuforums.org/showpost.php?p=1171008&postcount=67](http://ubuntuforums.org/showpost.php?p=1171008&postcount=67) and it worked like a charm. give it a try hope it works for you too.

---

