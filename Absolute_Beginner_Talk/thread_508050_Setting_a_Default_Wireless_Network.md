---
title: "Setting a Default Wireless Network"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by bunnyfly on 2007-07-23
Hello : ) Hopefully someone can help me...

I have about 5 wireless networks in range of my home. Ever since I installed Feisty Fawn about a week or so ago, things have been peachy on the internet front, but a couple days ago my connection went down for an hour. I switched over to one of my neighbor's networks, and later on, once mine went back up, I switched back to mine. But now, every time my computer boots up, it defaults to my neighbor's connection! It's unsecured, half as fast, and is someone else's - I would love to stop inadvertently using it...but I keep forgetting, and randomly throughout the day find that I'm connected to someone else's network!

Ideally, I would set MY network to be the default which always connects, and for the other networks to be used only if mine isn't working. I've searched around, but cannot find anything on the subject in the forums or the network manger's settings (I also looked at wifi radar, and that program doesn't appear to have a default network option either!)

Is there even a way I could tell my computer to ONLY connect to my network? Thanks,
[bunnyfly]

---

### Post by KyleBrandt on 2007-07-23
I can tell you how to delete that entry so it won't connect to your neighbors, but not how to set a preferred network:
1. Run gconf-editor
2. Go to System : Networking : Wireless : networks
3. Delete the keys to the networks you no longer want to use

Alternatively, you can go to the same directories I listed in step two.  They are all under the .gconf directory in your home directory and delete the networks that way.

---

### Post by bunnyfly on 2007-07-23
Great, thanks so much! That will work for now. I'm surprised they don't have that basic functionality of prioritized connections. Kindof strange for Linux.

Ever since my switch, I'm finding myself constantly baffled - half the time because of how incredible something is (Compiz, reliability, etc) and half the time because of how pathetic some lack of simple seems-too-basic-to-be-so-ignored functionality is (i.e. Linux music players/organizers!)
[bunnyfly]

---

