---
title: "Intro and Wireless Question"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by Quickened on 2007-04-09
Hello fellow users!

What i am going to ask is a question that you have no doubt seen before. I spent around sometime last night setting up Ubuntu and then countless more time browsing the internet and various forums to try and seek out a simple (hopefully) solution.

What i encountered was never a sure fire way (from what i saw). So it seems that i finally had to register with a board and i felt that this was probably the best one.

I am one of those people impressed by the beryl videos floating around. I've been on forums where people speak highly of linux but i've been in my microsoft comfort zone for quite a while. So needless to say .... i have zero linux experience. So i will probably ask questions that will make you think i am braindead ..lol please bear with me.

Now that we have that out of the way.....

I have wireless internet. The main computer (with the router and all) is my dad's. I bought the Netgear Wireless USB Adapter MA111 some time ago. When i went to install it ..low and behold i couldnt. Which brought me on my journey.

So i guess the main question is (from what i have been reading) will this link work with ubuntu 6.10. I dont want to assume it will so i thought i would ask... [the link is here...]("https://help.ubuntu.com/community/WifiDocs/Device/NetgearMA111?highlight=%28WifiDocs%2FDevice%29"). 

Also i am assuming i have to install prism2?

> First of all, install the linux-wlan-ng package to use this driver! It is included on all Ubuntu 6.06 CDs.

Would this then be included on 6.10? I got that from [this documentation...]("https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb")

So far i think that is all i should be asking so this can just be done a step at a time and i dont get ahead of myself. Glad for the dual boot here.... as i am running on the XP side right now :p  ;) 


Edit: I also had this idea that i could install "Wine" and it could just read the install disk but that probably wouldnt work hey?

---

### Post by siciliancasanova on 2007-04-09
Prism is the chipset.

I have rarely seen a person not get a wireless card to work.  There is a good chance it will not work right away.  You might need to update the driver, do some blacklisting, or something but most people eventually can get their cards working.

Even better than the older support docs, search your card or your chipset in the Ubuntu forums and find someone who had this issue already with Edgy and see how they did it.

---

### Post by Quickened on 2007-04-09
> **siciliancasanova said:**
> Prism is the chipset.

I have rarely seen a person not get a wireless card to work.  There is a good chance it will not work right away.  You might need to update the driver, do some blacklisting, or something but most people eventually can get their cards working.

Even better than the older support docs, search your card or your chipset in the Ubuntu forums and find someone who had this issue already with Edgy and see how they did it.

Ok i did a search and I found some things that i can try to get it working.

What do you mean by doing blacklisting?

---

### Post by Quickened on 2007-04-09
in one thread someone suggested

```
sudo apt-get install linux-wlan-ng
```

as part of something to do. When i inserted my live disk to explore it i noticed that linux-wlan-ng wasnt installed so i just did that manually. Then i was wondering "well what else wasnt installed" and i went through the list and grabbed anything that i thought would be of future use.

when i tried that code before it didnt work for some reason. Dont really know why.

The other steps included were

```
sudo gedit /etc/network/interfaces
```

and then ensure you have the following inserted
```

iface wlan0 inet dhcp
wireless-essid [your essid name]
```

and then perhaps add

```
wireless-mode managed
wireless-key [your encryption key]
```

and then the final steps were

```

sudo ifdown eth0
sudo if up wlan0
```

But i am not sure what any of this means or is doing. I feel like if i knew what was going on i could troubleshoot this better.

---

### Post by Quickened on 2007-04-09
actually i have another question of a different kind.

If i open up /etc/network/interfaces

i cant save the file after editing it. I even changed my account to root. So i figured to just log in with root but i found out you evidently cant do that. I got a message saying so.

So i guess my question would be "how do i edit that and get it to save" maybe i have been doing something wrong here.

I appreciate any help :)

---

### Post by Maestro23 on 2007-04-09
> **Quickened said:**
> actually i have another question of a different kind.

If i open up /etc/network/interfaces

i cant save the file after editing it. I even changed my account to root. So i figured to just log in with root but i found out you evidently cant do that. I got a message saying so.

So i guess my question would be "how do i edit that and get it to save" maybe i have been doing something wrong here.

I appreciate any help :)

If you are using gedit

> gksudo gedit /etc/network/interfaces

The file is owned by root.  Therefore you need the "sudo" command.

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Quickened on 2007-04-09
> **Maestro23 said:**
> If you are using gedit



The file is owned by root.  Therefore you need the "sudo" command.

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

ah! That makes sense! Thanks for the post and the link.

Is there a way that i can start in "safemode" and some how use root to create another user account.

This will sound silly but i somehow changed something to where i cant login with my other user account. Completely my fault. I didnt take into consideration that what i was going to do might screw up the system



edit: or should i just try to reinstall ubuntu? perhaps that may be easier.

---

### Post by siciliancasanova on 2007-04-09
It depends.  If you're using Edgy, you might as well reinstall with Fawn.  If you're using Dapper, you might want to stay there.

---

### Post by Quickened on 2007-04-09
Yeah i had just downloaded Edgy the day i started this thread. I saw that fawn was beta but i overlooked that the release would be this month. Perhaps i should google some information on that :)

I see that you are a fawn tester (under your bean count) how does it compare with Edgy?

---

### Post by siciliancasanova on 2007-04-09
Fawn is pretty much out, in my opinion.  I first started using Ubuntu a month ago and installed Edgy.  I got everything working (Beryl, Wifi, etc.)  I then figured I would just install Feisty a week later and found no difference.  It doesn't crash or anything like that.  It's supposed to be out in 10 days so it is as stable as Edgy.

Support really is the key.  Everyone will be upgrading though and you will see a lot of people with Feisty questions.  If you want to get your video card working on Feisty for Beryl, I have found more support for Feisty Video Card drivers in general on the Beryl site, just because video cards are one of the key components to beryl.

Between the two there is no difference like I said before.  If you have edgy you are as likely to crash as you are on Feisty.

Some good things is that it comes with Network Manager installed and some other tweaks.

---

### Post by Quickened on 2007-04-09
Yeah i was just browsing over [http://www.ubuntu.com/testing/feistybeta](http://www.ubuntu.com/testing/feistybeta) before i refreshed. I guess because its so early in the game i might as well switchover. You make a great point about beryl aswell.

This would lead me to a newer question if you dont mind. 

You might laugh at this but here we go! Since that one post of mine i installed edgy again (before we started talking about fawn) and now i have two edgy installs on my computer. If i am installing Fawn how can i make Edgy just disappear without reformating my entire HD?

Would that have to do with partitioning? Thats one of those terms that i had heard of but never really bothered to look at until starting this switching process.

---

### Post by siciliancasanova on 2007-04-09
If you just want fawn on your computer?  Download the gparted live disk.  Boot up into the live disk and delete the partitions you have.  Create a swap partition 1.5 -2.0 times the size of your RAM and use the rest for an EXT3 partition.  If you want to do a home partition just make 2 ext3 partitions.  One for the system files and one for the /home (documents, media, etc)

Then boot into Feisty live and do a manual install.

You will have SWAP partition

Mount Feisty in the EXT3 partition you made for it with "/"

Mount the home partition in the other EXT3 partition with "/home" and click forward.

Voila.  You can use Feisty's partitioner to erase and create the partitions but gparted has a lot more control and frankly it's a good tool to just have sitting in your stack of cd's

---

### Post by Quickened on 2007-04-10
Ok cool! I will probably be trying that in the morning.Got about 1:28:42 on the download + My eyes are probably fryin from sitting behind this screen for so long today.

I thought i did delete the old partitions when i was reinstalling Edgy. Not sure where i went wrong there but hopefully this will clean things up a bit.

I appreciate the dialogue in this thread. Hopefully tomorrow i can get this all up and running and i can branch off into really using and testing this thing :) This thread is like my training wheels lol

---

### Post by siciliancasanova on 2007-04-10
Good luck, let us know how it turns out.

---

### Post by Quickened on 2007-04-11
Well i learned a pretty good lesson in all of this so far lol.

I ended up screwing something up when i was deleting partitions. Basically when i went to load up the computer i got an error and i basically reformatted everything. Thats ok though because i had alot of useless garbage sitting on there.

Back to square one!

---

