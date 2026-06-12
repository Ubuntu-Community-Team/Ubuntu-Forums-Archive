---
title: "Torrents + aMule + DC not working + sound prob"
date: 2006-02-10
forum: Absolute Beginner Talk
---

### Post by Cene on 2006-02-10
Hi,

I don't know should i post this here or what, guess this is beginner question.
I can't get torrents (tried the one program what came with this, Azureus and Bittornado), aMule or DC++ to work.

Torrents can't get connection. All the time it says tha tracker is offline. My firend can use the same tracker in the same time, tough.
Only difference is the one client what came with the installation (Sorry, don't know the name). It can't even connect. It just says connection timeout.

aMule won't start d/l'ing anything. Just "Waiting.." or something.

DC can connect to hubs, but cant find anything with search.

All the other Internet thingies works (Apache, browsers, wget, apt-get and so on...)

Then the sound problem:

I have 2 soundcards.
First one is integrated to motherboard. Second is SoundBlaster Live! 24-bit (this is what i would like to use).
Well, the problem: Ubuntu cannot find the Soundblaster. Only the integrated "NVidia CK2", so i have to use that card.
I tried disabling the integrated card from BIOS, but couldn't find anything. There was no option for disabling it. There wasn't even said anything about it.

Another one:
When i'm listening to music (I use XMMS), any other sound won't play (games etc..), and the other way too. If i'm playing something, i can't hear any other sounds (system sounds, music if i start XMMS after game).

Sorry for the bad english, it's not my main language.

Oh, and im using Ubuntu, the newest one.

---

### Post by pinkpanther01010 on 2006-02-10
Well for your torrents, certain ISP's have been disabling the standard ports for Azureus and other torrent progs etc.  So you could just try changing the port it uses from 8181 or whatever it is to like 4729, then just forward that port in your router also..that worked for me.

The reason they've been "throttling" the standard torrent ports is because it slows down their bandwidth so much with all of their connections..sure your paying for it and deserve it, but hey, they want it, and therefor they can control it.  :\    Hope that helped.

---

### Post by Cene on 2006-02-11
Okay, i changed the port and now Azureus can connect to tracker and says its online, but cannot connect to any seeders. My friend can still connect with the same torrent to seeds.

It's just strange that my ISP would have blocked those ports at the same time i installed Ubuntu?
Cos everything worked fine on Windows.

---

### Post by bugmenot on 2006-02-11
I think you got a low level networking config problem of some sort. But once that is sorted out you should check out MLDonkey which is a very advanced P2P suite that supports BT, "Emule", DirectConnect and others in one background daemon with several GUIs available.

---

### Post by Cene on 2006-02-11
Hi again,


Anyone knows how to fix the "config problem"?

And now i have one more problem too: Apache isn't working anymore. When someone tries to connect, they got an error message saying connection timeout.

---

