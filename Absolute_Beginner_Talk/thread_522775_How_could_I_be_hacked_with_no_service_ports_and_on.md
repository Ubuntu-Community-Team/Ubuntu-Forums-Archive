---
title: "How could I be hacked with no service ports and only trusted files/connections?"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by ubunuby on 2007-08-11
I switched to Ubuntu as a gaming desktop because of problems I had with windows and a specific person repeatedly hacking my system.  

I wanted to know **ALL** possible methods of entry that exist for this hacker, (besides the basic stuff)  First, let me explain some things first.

[LIST]
[*]I'm using PPPoE ADSL in the city, so I've got a fairly large IP pool, and I'm **not** using any wireless connections. From what I understand, this obscurity should be helping me a lot shouldn't it?  I have absolutely no need for any connections to the internet besides web browsing and game playing.
[/LIST][LIST]
[*]First thing I did after the GUI install of Feisty Ubuntu from my cd was close all services that were leaving open ports. I think there were 2 printer (cups and something) services and avahi-daemon.  
I had 2 ports in 2000 range from printer services then 32678 and 5353 from avahi.  Rebooted my machine, checked netstat and **no** ports open. 
[/LIST][LIST]
[*]Then I run the add/remove program manager to download firestarter. This leave me with a few minutes of uptime without a firewall but without any open ports, a random IP, and a short window I should be ok right? [/LIST][LIST]
[*]After setting up firestarter, and checking my iptables to make sure it worked I download all the updates.  *Note that I never added any additional repositories or downloaded from any 3rd party site. [/LIST][LIST]

[*]Also I get the NoScript and Adblock addons for firefox and I'm certain no websites I browsed would have led this particular hacker to me. Afterwards I get my nvidia drivers and wine setup,  I make a desktop account (non sudo and complex password), install and start playing some MMORPG games. *Note that I'm only playing on official servers and obtain the files themselves from the company website or original cd, so all these sources are trusted.  [/LIST]

Now when I used windows, this hacker had a habit of following me into any game I would play and making a username to mock me, like my login name, password, or what I googled 20 minutes ago.

I'll never be able to get rid of this paranoid feeling that I have, even after switching to Ubuntu and knowing that every file on my machine came from a trusted source. But, it would ease my worries to know **precisely** how I could still be hacked and what I could monitor to keep my system safe. I already read some guides, and know about stuff like chkrootkit and how to monitor my connections, and logs so I'm looking for something more advanced, but not totally esoteric. 

Please, If anyone can direct me or drop some advice It would afford me great peace of mind. 

Thank you.

---

### Post by Steveway on 2007-08-11
What games?
And are you using a wireless connection?
Maybe he is somewhere around and sniffing that connection.

---

### Post by ubunuby on 2007-08-11
I'm playing Planetside and EVE online right now, and have no wireless connections. I forgot to make that one clear.

---

### Post by splintercellguy on 2007-08-11
CUPS listens on loopback, so not really reachable ;). Perhaps you got a pesky roommate/neighbor who's sniffing traffic? If a retard is doing something like this better go to the cops :D.

---

### Post by bodhi.zazen on 2007-08-11
he he he ... If I listed all the ways you could get hacked you would have an apt-get moo

OK, no wireless, change the password on your router ...

and see if this cures your insomnia : [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by eentonig on 2007-08-11
One of the best methods of hacking, is social engineering. No matter how good you firewall, if you give them the key, they'll get in.

Besides that, how can you tell that you're hacked? Isn't this just some paranoia from your side?

---

### Post by ubunuby on 2007-08-11
Hi Bodhi, yes I've read your guide and many thanks for it, but I still want more info. 

Theres nobody else on the line or with physical access, and I bricked my router recently, so I'm not using one now, but I know I had that well configured too. I'm not using any mail or IM stuff either.

I thought DSL isn't a shared line so there's no sniffing there. 

I find it too good to believe that all It takes is closing off all remote admin ports or services and I'm safe from hacking. So yeah maybe I am being a little paranoid.

---

### Post by swiftnomad on 2007-08-11
Did you update everything And whAt fireWALL Are you using? I hAve security bAckround And this soUnds like the guy or gAl knows you. OR your indireCtly Asking people wAys to get root..
for thAt you wAnt stArt here:
[http://www.damnvulnerablelinux.org/](http://www.damnvulnerablelinux.org/)

You seem to know Alot Already.

sorry my keyboArd is messed up.. linux dont like it. =)

---

### Post by bodhi.zazen on 2007-08-11
> **ubunuby said:**
> Hi Bodhi, yes I've read your guide and many thanks for it, but I still want more info.

Hey, thanks for reading my guide then. If you have done all those things you are fairly secure.

My only other thought is ~ have you re-installed your OS ? Including /home or any other partition you may have ?

Other then that, well take a look at some of the links and work your way through them.

Heh, nothing wrong with a little paranoia, don't forget, ever paranoid schizophrenics have enemys :twisted:

---

### Post by ubunuby on 2007-08-11
I read so much about hacking it drives me crazy to think how easy I am to hack but really I barely understand the concepts. I understand how the security works but not the other way around. A lot of the guides that explain hacking methods to better understand security is written for server administration and thats where I start to get lost because they assume the reader understands admin stuff and has services running.

I guess I only wanted reassurance, and not some false sense of security all those windows software companies offer.

---

### Post by MenZa on 2007-08-11
Have you felt any intrusions since you re-installed your system with Ubuntu?

---

### Post by proalan on 2007-08-11
you could try 'traceroute' to see where your data packets are going. Then try and find out the suspect IP and block it.

Theres a whole bunch of  network tools at..

System -> Administration -> Network tools

---

### Post by ubunuby on 2007-08-11
No I haven't had any evidence of being hacked since I installed Ubuntu, but I never had any real evidence when I used windows either (using so much worthless security software). However I know for a fact I was being hacked on windows, which I now assume was because of untrusted files. 

This was more of a question of how secure my machine is after doing these things.  I read about so many different types of attacks but don't understand them fully, so I don't know which ones to worry about or not.  

There is so much software for windows that made me think I was safe when I really was not. So when I switched to Ubuntu and followed security procedures I was worried over how simple it seems.

---

### Post by switchcode on 2007-08-11
dude; you're connecting to an online game. Its down to the game server architecture as to if it hands out your current IP, but i believe that you will find that this person is discovering your IPs from the game/s your playing, and targeting you from that. You havnt yet described what the actual attacks are; Im assuming its either a child punching IPs into a flooder, or a (only very slightly) more advanced child exploiting a specific bug in the game.
  Either way, try renewing your IP and not playing any games for a day or so.. I bet that no attacks happen.

---

