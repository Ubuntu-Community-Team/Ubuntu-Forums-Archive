---
title: "Why Ekiga &quot;sucks&quot;!"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2007-02-02
Hello!

I tried to use "**ekiga v2.0.3**" to perform VoIP.
All that on a Local LAN.
Involving 2 [color=red]Ubuntu v6.10 Desktop[/color] PCs. 

_Test_:
So, on both machines, I open up "[color=blue]Applications\Internet\Ekiga Softphone[/color]".
On the **1rst** machine, on the "[color=blue]sip:[/color]" address line, I type the local IP of the 2nd PC & I can listen to it ringing.
I visit the **2nd** PC & see a popup window saying that the 1rst PC wants to VoIP with me...
I click on "OK" & start speaking...
On the **1rst** PC I have put a Digital Voice Recorder to pick up any speaker talk...
So, from the **2nd** PC, I start talking...
The Digital Voice Recorder on the **1rst** PC should be picking up the audio...
But when I put it to play, I can't hear a thing...!!!
So I though, maybe the **1rst** PC's mic drivers could be bad...
And I thought to do things the other way around...
So, I put the Digital Voice Recorder on the **2nd** PC.
I go on the **1rst** PC & start talking.
Nothing is picked from the Digital Voice Recorder...!!! 

_Conclusion_:
I can manage to get the "ring" through, but can NOT manage to perform VoIP.
So, even though the "initiation" process works OK, there is NO real communication involved... :(

_Part 2_:
Then I said, what the heck, I will try to "**chat**" with these LANed PCs!
I thought that "chatting" is at least one of the things that work in Ubuntu...

So on the **1rst** machine I click on the button named "[color=blue]Open text chat[/color]".
I type something...
And go visit the **2nd** machine.
Nothing!!! :(
Am still on the **2nd** PC & click on the button named "[color=blue]Open text chat[/color]".
As soon as I open that window, I can _see_ the **1rst** Pc's message...
Hip...hip hurray...!!!
So, I decide to type something.
I visit the **1rst** PC & see that it worked!
Since I am on the **1rst** PC, I type something & then close the Chat window.
I visit the **2nd** PC & verify that what I checked has arrived...
Everything is looking fine!
Now on the **2nd** PC I type something...
(Remember: the chat window was intentionally closed on the 1rst PC!!!)
I go back on the **1rst** PC to see what happened...

Looks like nothing has arrived...!!! :confused: 
There is NO popping up of the Chat window...
My goodness, there is NO "initiation" process involved here...
And when I decide to click on the button "[color=blue]Open text chat[/color]", I can see the text I sent from the 2nd PC... =D>  

_Conclusions_:
1. Initiation Process works OK with VoIP, but no actual voice goes through...
2. Initiation Process does NOT work with Chat, but the actual chat goes through...

I can't understand one thing man:
IF you have already managed the initiation process (that "ring") to work successfully for VoIP, why can't you figure out the initiation process to work successfully for chat?
I mean you have managed to send the chat messages through the Network...
...when somebody has the chat window closed, why can't you open/pop it up (i.e. "initiate"), when a guy on the other end types something? :-\"
Is it so hard dude?
No wonder why I claim it sucks...
And you know what is even worse?
That Ubuntu has added it **by default** on every installation of Ubuntu v6.10 Desktop...
Fantastic!
Super!
Now we are ready to go **Enterprise**!!! :lol:


Thanks.

P.S> And don't try to suggest to me to try using "[color=blue]skype[/color]", cause "skype" hijacks the alsa audio drivers & turns the mic into a "gadget" than a functional PC part...!!!

---

### Post by lamego on 2007-02-02
1. Did you reported the problem to the Ekiga authors, or have you reported it on launchpad already ?
A lot of software sucks because some dumb people which experience a problem on open source software, just complaint about it but don't report it so that the next dumb people will not complain about it.

2. Are you aware that bugs are triggered on specific conditions and that you may experiencing a specific condition which none of the ubuntu/ekiga testes was able to reproduce ? 

Best regards,

---

### Post by dvarsam on 2007-02-02
[QUOTE=dvarsam]...One thing is certain:
**Do NOT use** "[color=blue]skype[/color]" as it conflicts with alsa & then you need to re-compile the audio drivers to make things work normal again...!!!
[/quote]

Hm......
I have more NEWS to submit!
In order to fix the Mic problem, I decided to re-install Ubuntu v6.10 again!!!

I installed the package "[color=blue]tapiocaui0.3[/color]" & all these got installed altogether:

01. farsight0.1-plugins-rtp_0.1.3-11indt1_i386.deb
02. gstreamer0.10-plugins-farsight_0.10.2-0ubuntu1_i386.deb
03. libfarsight0.1-0_0.1.3-11indt1_i386.deb
04. libgsm1_1.0.10-13_i386.deb
05. libjinglebase0.3-0_0.3.10-0ubuntu2_i386.deb
06. libjinglep2p0.3-0_0.3.10-0ubuntu2_i386.deb
07. libjinglesession0.3-0_0.3.10-0ubuntu2_i386.deb
08. libjinglexmllite0.3-0_0.3.10-0ubuntu2_i386.deb
09. libjinglexmpp0.3-0_0.3.10-0ubuntu2_i386.deb
10. libtapioca0.3-base-0_0.3.9-1indt1_i386.deb
11. libtapioca0.3-client-0_0.3.9-1indt1_i386.deb
12. libtapioca0.3-core-0_0.3.9-1indt1_i386.deb
13. tapioca0.3_0.3.9-1indt1_i386.deb
14. tapioca0.3-xmpp_0.3.9-0indt1_i386.deb
15. tapiocaui0.3_0.3.9-0indt1_i386.deb

BTW: I had NOT installed "[color=blue]skype[/color]" after the Clean install of Ubuntu v6.10.
Only "[color=blue]tapiocaui0.3[/color]" were!

I then tried to record on the mic...
I could hear my recording very very low...
Even if you boost the speakers to max, you will not be able to improve the mic recording...
So, maybe the problem is NOT "skype" overall... :-k 
I mean, when I had this problem previously, both "skype" & "tapiocaui0.3" were installed...
So, I can't be certain that "skype" is the one to fully blaim...
And now, on a clean install without "skype" but with "tapiocaui0.3", I get a problem!!!
So, it could be "tapiocaui0.3" overall...
OR
It could be both!!! :-k 

I also used "[color=blue]arecord[/color]" & "aplay" because I have been told that they work better than "[color=blue]Applications\Sound & Video\Sound Recorder[/color]".

```
dimitris@dimitris-desktop:~$ arecord -d 6 a.wav
Recording WAVE 'a.wav' : Unsigned 8 bit, Rate 8000 Hz, Mono
dimitris@dimitris-desktop:~$ aplay a.wav
Playing WAVE 'a.wav' : Unsigned 8 bit, Rate 8000 Hz, Mono
```

I then decided to open up everything in "alsamixer".

Nothing!!!
I used both "[color=blue]arecord-aplay[/color]" & "[color=blue]Applications\Sound & Video\Sound Recorder[/color]" (the later with everything activated!).

So, I guess now is the time to uninstall all the 15 packages above & see whether I get any improvements...

I will keep you updated...

---

### Post by dvarsam on 2007-02-04
I un-installed all the 15 packages above & got NO improvement...
In fact, I rebooted my Ubuntu & can NOT even hear the Ubuntu sound during Boot!
I guess I will need to perform another Format...

Thanks.

---

### Post by shareMenaPeace on 2007-02-04
You had sound after you installed?
Search the forum for you soundcard

---

### Post by dvarsam on 2007-02-04
[QUOTE=shareMenaPeace]You had sound after you installed?
Search the forum for you soundcard[/QUOTE]

Hello & thanks for your reply!
Well, as I said before, I formatted my Ubuntu for a 2nd time...
Basically I have the following Motherboards:

1. Intel D865 PERL (supporting Intel AC'97 Audio)
2. Asus P5LD2 (supporting Intel HDA - High Definition Audio)

In the 1rst PC, in a freshly installed Ubuntu v6.10, the mic works fine!!!
However, IF I install the program "tapiocaui0.3" ("skype" possibly too!!!), the mic stops working!
So I have avoided installing any of the 2 programs...

In the 2nd PC, in a freshly installed Ubuntu v6.10. the mic does NOT work...
So, I need to compile the drivers & only after that the mic works...
However, installing "[color=blue]skype[/color]" or "[color=blue]tapiocaui0.3[/color]" turns the mic into NOT working!!!

So, somebody needs to fix those mic drivers or "skype" * "tapiocaui0.3"...

Since I managed to get the mics working, I used "Ekiga" to VoIP between those 2 PCs on a Local 100Mb LAN.
The voice did NOT come out good...
The quality of sound was so bad, that it did NOT worth using "ekiga" at all...!!!
So Voice Chat in Ubuntu is at infant stage...

Thanks.

---

### Post by petermck on 2007-02-09
I recently had a very similar problem setting up a VoIP system and it turned out to be a router on the LAN causing the problem. It had a proprietry SIP proxy feature enabled by default and to make matters worse, there was no mention anywhere in the documentation or the GUI interface that this was the default. I had to disable it via the command line. Once I did this everything worked fine.
This may not be your problem, but it is worth excluding the possibility before tinkering with the PC's.

---

### Post by MrHorus on 2007-02-09
> **dvarsam said:**
> 
The quality of sound was so bad, that it did NOT worth using "ekiga" at all...!!!
So Voice Chat in Ubuntu is at infant stage...



Please don't make sweeping generalisations like that - you assume that every single Ubuntu user has problems which are seemingly quite unique to you.

Personally I've never had a problem with Skype and it worked flawlessly out of the box but that doesn't mean that voice chat in Ubuntu is at an advanced stage - merely that i've not had any problems.

---

### Post by Matze on 2007-02-23
> **petermck said:**
> I recently had a very similar problem setting up a VoIP system and it turned out to be a router on the LAN causing the problem. It had a proprietry SIP proxy feature enabled by default and to make matters worse, there was no mention anywhere in the documentation or the GUI interface that this was the default. I had to disable it via the command line. Once I did this everything worked fine.
This may not be your problem, but it is worth excluding the possibility before tinkering with the PC's.

How have you done this??
Thanks...

---

### Post by sad_iq on 2007-11-24
> **dvarsam said:**
> 
_Conclusions_:
1. Initiation Process works OK with VoIP, but no actual voice goes through...
2. Initiation Process does NOT work with Chat, but the actual chat goes through...

 Hi...just looking for the same thing(voip over lan)...so just subscribing here. Also...maybe you need to open some ports for the ekiga or chat app???

---

