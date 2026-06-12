---
title: "Having trouble with audio/video chat in Ubuntu"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2007-01-26
Hello!

I decided to write this post based on the fact that I feel disappointed from my Ubuntu...
I have been using Ubuntu for almost a year now...
And I have been following the "learning curve" involved...
I can't say that I am an expert, but every single day, I try to learn something...
I am trying to be a "good student" here, but I always get disappointments...
Don't be mis-leaded, I like my Ubuntu & the whole project being involved!
But every day I get more disappointed about it...

I try to file suggestion improvements for the coming Feisty Fawn & _every_ _day_, when I find/come up with/bump into something interesting I add it here:
[http://ubuntuforums.org/showthread.php?t=285910&page=12](http://ubuntuforums.org/showthread.php?t=285910&page=12)
(look under user "dvarsam").
I have even filed a spec for these (look for spec named "dvarsam"):
See here: [https://blueprints.launchpad.net/ubuntu/](https://blueprints.launchpad.net/ubuntu/)

So, what am I doing here complaining for...?
I decided to complain about this:

**Voice Chat in Ubuntu - Ugh *@#&^*$%)^#$%#$@!!! :(**

In the past I have read posts where people were suggesting about adding "tapioca" by default in Ubuntu, instead of "gaim" (for chatting), since "tapioca" was supporting voice chat (but "gaim" did not...).
So, I went & added this in my suggestions for Ubuntu coming Feisty Fawn...
One day, I found a thread providing a HowTo on installing "tapioca" in Ubuntu v6.10.
I was very happy, thinking that now I was able to audio chat with "tapioca"...
So, I installed it, but could not log-in, in my Hotmail or Yahoo accounts...
(See here: [http://ubuntuforums.org/showthread.php?t=291089](http://ubuntuforums.org/showthread.php?t=291089))
I asked for a solution, only to find nothing...
Another user was complaining that he could not log-in in his Gmail account!
So, I dumped the whole project...
Another day, I come up on a HowTo on installing "skype" in Ubuntu v6.10.
I was very happy, thinking that now I was able to audio chat with "skype" instead...
So, I installed it, but could not listen to what I was recording on the microphone!
(See here: [http://ubuntuforums.org/showthread.php?t=143512](http://ubuntuforums.org/showthread.php?t=143512))
I could only use "skype" to perform chat by using the keyboard...
... which is exactly what I could previously perform by using the embedded "gaim"!!!

Why on earth can't somebody from Canonical take a step forward & announce this:

[b]Audio/Video chat in Ubuntu is NOT currently possible!
Do NOT bother to search for a solution, as you won't find one at the moment![/b]

Why should I bother:

1. Change "sources.list" contents
2. Bother to download the packages ("skype" or "tapioca")
3. Follow the provided/suggested step-by-step installation methods.
4. Launch the programs I installed...
5. See that they don't work
6. Perform a search for threads on the same problem
7. Read those threads looking for a solution...
8. Realize that I am NOT the only one experiencing this... (a dozen of other users are experiencing the same problems like I did) - so there is NO solution!!!
9. Add a post in the thread (my desperate shout: "HELP ME, PLEASE, MY BOAT IS SINKING!!!") 
10. Get no response, since Nobody has found a way to make these programs work in Ubuntu v6.10
11. Go & modify the suggestion for improvements for the coming Ubuntu v7.04 Feisty Fawn (providing detail on the matter)...

Isn't this too tiring man...?
How would _you_ feel about it?
I had to do these twice (once for "tapioca" & once for "skype"!!!).
That is why I am pissed off... dude!
So, the _question_ is:

[b]Am I justifiably pissed off or NOT?
Wouldn't _you_ be pissed off, if you had to go all this way to find that it is NOT possible to audio chat in Ubuntu?[/b]


Thanks.

---

### Post by meng on 2007-01-26
> **dvarsam said:**
> Audio/Video chat in Ubuntu is NOT currently possible!
Do NOT bother to search for a solution, as you won't find one at the moment!
Of course it's possible! Ekiga, WengoPhone and others. I think you mean that it's not possible through Skype, MSN, etc.

---

### Post by Bachstelze on 2007-01-26
I never use any of those so I can honestly say that I don't give a crap and that I'm certainly not pissed off :p

---

### Post by dvarsam on 2007-01-26
[QUOTE=meng]Of course it's possible! Ekiga, WengoPhone and others. I think you mean that it's not possible through Skype, MSN, etc.[/QUOTE]

lol
Are you joking man?
Cause I am tired of all of this...!!!
Thanks.

P.S.> Where is the HowTo, to install these?

---

### Post by meng on 2007-01-26
1. Ekiga is installed by default. It's under Apps > Internet
2. Wengophone is in the universe repositories.
sudo aptitude install wengophone

---

### Post by r4ik on 2007-01-26
Ekiga.
H.323 and SIP compatible videoconferencing and VOIP/IP-Telephony application
that allows you to make audio and video calls to remote users with H.323
hardware or software (such as Microsoft Netmeeting) as well as SIP endpoints.

It supports all modern videoconferencing features, such as registering
to an LDAP directory, gatekeeper support, making multi-user conference
calls using an external MCU, using modern Quicknet telephony cards,
and making PC-To-Phone calls.

---

### Post by meng on 2007-01-26
I should warn you though, that your friends will have to use similar software - you can't just meet on MSN or Yahoo with these programs. So if you're committed to those networks, save yourself the effort and disappointment.

---

### Post by chettyk on 2007-01-26
> **dvarsam said:**
> 
[b]Audio/Video chat in Ubuntu is NOT currently possible!
Do NOT bother to search for a solution, as you won't find one at the moment![/b]


Well, I am now able to make voice calls, including paid calls, with Skype on my Dapper Drake system. I think I let Automatix install whatever was needed. But even then I had a similar problem. When I called the Skype test site, I could hear the recorded message but not record a message of my own. It took a fair bit of Googling and looking in the forum to figure what else was needed to get Skype working. I had to jump through a few hoops with the Volume Control box before I could make calls.

Unfortunately, it seems to be a bit of a hit and miss affair whether you can get Skype working on a Ubuntu release. I keep a dual-boot on my laptop, with Skype and some other Windows software loaded as a backup option.

---

### Post by lamego on 2007-01-26
dvarsam,
your joke reply when someone tells you about Ekiga which is available on Add/Remove programs represents that you don't care about solutions, you only care about the solutions YOUR solutions, with the VOIP services services YOU use.

I am happy that you are disappointed with Ubuntu, because that means the Ubuntu focus is kept on open solutions which can work for people which does not want to be tied to specific company centric services.

If you want support for your particular service, fill your complain or support request to your service provider, do not complain against the Ubuntu team or the open source developers because your service provides don't care about you.

---

### Post by MrHorus on 2007-01-26
> **dvarsam said:**
> Wouldn't _you_ be pissed off, if you had to go all this way to find that it is NOT possible to audio chat in Ubuntu?[/b]


Maybe it's not possible for YOU but please don't make blanket statements like that - I just installed Skype and it worked out of the box - I have had no problem talking to people (Windows users) in the US, Canada and here in the UK.

---

### Post by dvarsam on 2007-01-26
[QUOTE=meng]1. Ekiga is installed by default. It's under Apps > Internet
2. Wengophone is in the universe repositories.
sudo aptitude install wengophone[/QUOTE]

I found that Ekiga was already installed on my Ubuntu.
I probably did this a while ago...
Oops! I just noticed that (as you said), Ekiga is installed by default. Sorry for my mistake. :)
So, by mistake, I thought that **I** had installed it...
But the question is how do I use this thing?

[quote=meng]I should warn you though, that your friends will have to use similar software - you can't just meet on MSN or Yahoo with these programs. So if you're committed to those networks, save yourself the effort and disappointment.[/quote]

Don't worry...
I don't mind about that...

So, I created an account with Ekiga, named "dvarsam".
And I think that my address is "[color=blue]sip:dvarsam@ekiga.net[/color]"?

And where/how can I find other available pals to test whether voice chat is finally possible in my Ubuntu machine?
Example:
In skype you can perform a "search" & you can find a dozen of people that might be interested in chatting with you...
How can I perform a search like this in Ekiga?
OR Ekiga does NOT work like this?

Thanks.

---

### Post by Pobega on 2007-01-26
Sometimes things don't work in Ubuntu. That's what we lose in exchange for being free of Windows problems.

You can do **anything** in Ubuntu, but it takes time, commitment, and patience, none of which you seem to have. Just search the forums, or search Gentoo's forums (Sometimes I find some good answers there, even though I'm not on Gentoo). Mind you, you have to know what will work and what won't work to browse Gentoo's forums while running Ubuntu, but it's worth a shot for certain applications.

---

### Post by em007a on 2007-01-26
I don't think Ubuntu is making your life miserable, thats something only you can control. I find it a challenge every now and then to get something working but it is usually due to my lack of understanding. 

For the things I CAN do, I am grateful to have a free/low cost alternative to Windows. I find it hard to be disappointed with something that has been provided at no cost to the community. I know eventually I will be able to do everything I want in Ubuntu. In the mean time, if there is a program that I cannot live without, I can always dual boot into XP. It's a small sacrifice if you ask me.

YMMV

---

### Post by aysiu on 2007-01-26
I've retitled your thread to more accurately describe your problem.

---

### Post by dvarsam on 2007-01-26
[QUOTE=lamego]dvarsam,
your joke reply when someone tells you about Ekiga which is available on Add/Remove programs represents that you don't care about solutions, you only care about the solutions YOUR solutions, with the VOIP services services YOU use.[/quote]

Really?
I only putted a "lol" there, to show how much I have tried for a solution on this...
Don't forget that these Forums are filled with posts on "skype" & "tapioca"...
So, don't blame me for trying out those.
Give me a damn solution for this, and I will personally use it & suggest to others to use that instead!
IF I did NOT care for solutions, I wouldn't be here typing all day for one...
BUT one thing is for sure - we all want _easy_ solutions dude!!!
1+1=2
Give me an easy solution - not a riddle to solve...

[quote=lamego]I am happy that you are disappointed with Ubuntu, because that means the Ubuntu focus is kept on open solutions which can work for people which does not want to be tied to specific company centric services.[/quote]

You are happy that I am disappointed with my Ubuntu...
How mean is that?
Wow, what a person...
Regarding to open solutions, yes I am in fond of them too!!!
And you can go over my threads/posts to verify that...
However, when I am looking for a _single_ & _easiest_ solution, I don't check/verify which solution is open source & which is not...
And if you ask me which of these is open source or not:

1. skype
2. tapioca
3. ekiga
4. whatever else
5. etc etc

My answer is this:
I only know that skype is not free...
For the rest, I don't know anything (i.e. whether they are open source or not).
Give me options & I will go for free!
IF you don't provide options & I am left with only a closed-source option, then IF I want voice chat, I will have to stick with that...
It is all a matter of how many choices your are given...

> If you want support for your particular service, fill your complain or support request to your service provider, do not complain against the Ubuntu team or the open source developers because your service provides don't care about you.

I want a solution.
Bundled with minimum fuss...
And your suggestion to "file a complaint" does not help me solve the problem...
Besides, my disappointment" has already been filed in these Forums, right as we speak (by this thread)...
However, now I am looking for a solution...
So, can you bare with me & provide me one?
I don't care whether it is open-source or closed-source...
As I said, when we are NOT given many choices, we might stick to closed-source...
Thanks.

---

### Post by dvarsam on 2007-01-26
> **Pobega]Sometimes things don't work in Ubuntu. That's what we lose in exchange for being free of Windows problems.

You can do **anything** in Ubuntu, but it takes time, commitment, and patience, none of which you seem to have.[/quote]

I do have Patience!
IF I did not, I wouldn't stick to these Forums!
BUT every day is NOT the same is it?  said:**
> Just search the forums, or search Gentoo's forums (Sometimes I find some good answers there, even though I'm not on Gentoo). Mind you, you have to know what will work and what won't work to browse Gentoo's forums while running Ubuntu, but it's worth a shot for certain applications.

I will do that.
But until then, can somebody help me try to make "ekiga" work?
I am at the point where I have created an account - i.e. "dvarsam".

1. Where do I find other pals to voice chat with? Can I perform a search?
2. Is my address now "[color=dvarsam]sip:dvarsam@ekiga.net[/color]"?
3. Can somebody ring me in ekiga to see if voice chat works?

Thanks.

---

### Post by dvarsam on 2007-01-26
[QUOTE=aysiu]I've retitled your thread to more accurately describe your problem.[/QUOTE]

Even though your intentions were justified when doing this...
...Now nobody can identify my thread, because in their minds they remember the old Title of Thread...
Now, nobody is answering to my "desperate help requests"...

Thanks.

---

### Post by ragadanga63 on 2007-01-26
Have you tried gyachi?  it's a YM based chat client with voice and webcam support.

---

### Post by ragadanga63 on 2007-01-26
btw gyachi can be downloaded from:   [http://gyachi.sourceforge.net/](http://gyachi.sourceforge.net/)

---

### Post by dvarsam on 2007-01-26
Hello & thanks for your reply!

[QUOTE=ragadanga63]btw gyachi can be downloaded from:   [http://gyachi.sourceforge.net/](http://gyachi.sourceforge.net/)[/QUOTE]

I am willing to try _anything_ you want, but before I do so, don't you think I should first exhaust all possibilities with "ekiga"?
IF you are willing to help me, can you please pm me through "ekiga" to test audio chat?
Anybody?
Please....
Thanks.

---

### Post by jackrobinson on 2007-01-26
gyachi and amsn will both support sending and receiving webcams unless you are behind a router when sending might be an issue.
to fix it, go to your router control panel and go to advanced--> port forwarding
and forward ports 6890 to 6900.
on my belkin router, I need to type
[http://192.168.1.1](http://192.168.1.1) in my browser to go to my router control panel. in your case, the ip address might be something slightly different. (try 192.168.2.1 for example)
Voice chat works best on skype. On Open source alternatives like wengophone and ekiga the voice quality is pretty sad.
Voice on yahoo and msn wont work on linux simply because of the constant changes yahoo and msn make to their VoIP protocols which they never publish.

---

### Post by jfif on 2007-03-27
Ubuntu makes me feeling great.  
But I have to say that voice chat is indeed a headache. 
> Voice on yahoo and msn wont work on linux simply because of the constant changes yahoo and msn make to their VoIP protocols which they never publish.
Reply With Quote
I don't want to talk to Yahoo or MSN.  I want to talk to Google Talk. 
I tried _Jabbin _and_ Tapioca_ in Ubuntu 6.10. But sadly, no voice is there. 
And this seems to be a common problem as other users reported the same problem and no real solution is found. 
I guess the best thing is to pay a little more patience.

---

### Post by catch007 on 2007-03-31
Well, audio chat through skype is OK for me, albeit some typing problems (Not type words in English of course)

---

### Post by pencilcheck on 2008-01-26
Actually, you should really go to sourceforge.net and search for Voip. This site is a great open source site where most free apps are resided. 
:popcorn:

---

### Post by FrankVdb on 2008-02-06
If you want a system that is complete and that provides immediate productivity, get yourself a pile of cash and buy a Mac.

Ubuntu has come a long way, thanks to the people at Canonical and thanks to hundreds/thousands of other people who have sacrificed their time and energy to contribute to open source. 

I'm incredibly grateful for their work. Ubuntu will probably never be really finished. I agree that voice and video chat is a headache under Linux and it's been very frustrating for me too but it's a work in progress. But sooner or later it will be there.

Carpe diem.

---

### Post by gobbles414 on 2008-02-17
FrankVdb,

Do Macs support AV chat on the major IM networks (MSN, Yahoo, and Google)? iChat is basically just for .mac/AOL/AIM, yes? Why should dvarsam spend money on a Mac if his AV chat problems will still exist!?!

---

### Post by EmilyRose on 2008-03-20
I agree. Video chat SUCKS in ubuntu/linux. Theres no other way to say it. Sure, if all my family could only learn how to use skyp or ekiga then we could maybe video chat. But they aint about to do that just for me - none of them are computer people, and some of them are 80+ years old. They aren't learning a whole new confusing program. iChat is it. And since there is no video chat solution (over aim/ichat protocols), there is no hope for video chatting with my family - unless I care to install windows which I've come damn close to doing in the past. If we ever get high speed and theres still no option for video chat in linux I probably will. For ONE ******* thing. It sucks. But its true. And everyones response of "just use skype or ekiga or wengophone" is BS - *I* could use them, but not my family, so they're WORTHLESS!

---

### Post by MarkX on 2008-03-28
I totally agree with the OP.
It's a bad state of affairs for the whole open source community when something as basic and important to such a vast number of people is missing. 

Voice-webcam messenger support is stopping many from changing to Linux and it's also stopping me from installing it on numerous friends and family computers.
I've been using Ubuntu for a few months now and yes, it's nice not to have to worry about viruses etc but functionally it's way behind. Most apps are simply not as polished as they "should" be and usually instructions on how to actually use them either don't exist at all or presume extensive Linux experience.

---

### Post by _aXXe_ on 2008-03-29
I found the following site while searching for a solution to a no mic input in Ubuntu 7.10. This info is designed for laptops but I'm sure someone could confirm it will work with desktops as well. You will of course need to have your sound cards brand name and the kernel version of your Ubuntu OS. Make sure you READ ALL the INFO provided. Pay special attention to the permission to execute (sample line provided) so the darn thing will function.

BTW, what kernel does 7.10 use, or better, how do I find it? I looked at the install (ISO) CD but did not find the kernel version listed. I'm sure it's there I just got so tired at 0400 that I gave up. Dam chemotherapy really took it out of me.

Obviously if you try it and it works, please be so kind as to reply to this and other posts about Skype and other VoIP questions regarding no input from the mic to the recorder. Be sure to include your system info so others will know in what circumstances the fix works.

I'm really looking forward to trying this as soon as I get the kernel version of 7.10 and my sound card info.


[http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html](http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html)

As with anything regarding compiling or running scripts, please backup your install prior to running anything posted in forums unless you enjoy reinstalling.

Even though there were testimonials to praise and to gripe about this web info I urge caution.

---

### Post by _aXXe_ on 2008-03-30
Found this in another post. These are used in the terminal. You will need sudo or log in as root in Gutsy 7.10.


The first line will display your sound card info:

grep Codec /proc/asound/card0/codec#*

This command will display your kernel version.

uname -a

Just a quick note for those like me with no experience and two thumbs.

---

### Post by ragadanga63 on 2008-03-30
Gizmo5:  gizmo5.com

qnext: qnext.com

Personally tried Gizmo5 to audio chat with Yahoo buddy.  It works really well.

Also Gyachi-sidetrack with ekiga.  

Installation instructions is in their respective websites except for Gyachi which you can search in this forum.  A .deb file is available for this.

---

### Post by gobbles414 on 2008-04-22
> **ragadanga63 said:**
> Gizmo5:  gizmo5.com

qnext: qnext.com

Personally tried Gizmo5 to audio chat with Yahoo buddy.  It works really well.

Also Gyachi-sidetrack with ekiga.  

Installation instructions is in their respective websites except for Gyachi which you can search in this forum.  A .deb file is available for this.

Does Gizmo5 work well with audio chats on the MSN network? I have a friend who uses a Windows virtual machine in her Ubuntu just to audio chat in Windows Live Messenger. So if Gizmo5 would work for her, that would be great!

---

### Post by loell on 2008-04-22
gizmo uses a bridge or a gateway to call windows live messenger so the voice quality would probably be  a bit lower compared to Live to Live messenger conferencing, though i think its tolerable.

---

### Post by Claus7 on 2008-04-23
Hello - &#935;&#945;&#943;&#961;&#949;&#964;&#945;&#953;!

Ubuntu in general supports both audio and video support even for users who are using Dapper. I was also disappointed with skype some days ago, because even though I had all the dependencies installed, I wasn't able to use my camera. Now with this :
[http://ubuntuforums.org/showthread.php?p=4749162#post4749162](http://ubuntuforums.org/showthread.php?p=4749162#post4749162)
I have both audio and video chat and with a very good quality. 

The only thing that skype lacks now is the low light condition (Tools->Internet->Test Camera) where there such an option doesn't exist, whereas in windows is available, except if my installation didn't allow me to have such an option. Yet, a minor issue though because that way my backround is dark, yet not me!

In contrast to the above, in amsn I have the ability to adjust many things with my camera. I might say that the settings are even better than those in windows (at least I was able to configure my camera, so as to see that the configurations are realy good).
I hope that the reverse engineering effort from the people behind amsn will soon solve this issue of audio conversations. Mind that voice clips are working flawlessly though. 
This is what I have found out about msn effort installation in ubuntu forums, including mine, which I think is platform independent, because I install everything that I found out that was needed for amsn to work. [http://ubuntuforums.org/showthread.php?p=4555010#post4555010](http://ubuntuforums.org/showthread.php?p=4555010#post4555010)
Mind that after my first attempts I have never faced a log out. And with skype, amsn and other applications open in comination to a low memory, slow downs even then are scarce.

As far as the microphone is concerned you should see what is going on via alsa at first. Things that you should have in mind are:
have I plugged in the mic in the right sound card? Is this sound card the default in my alsa settings? And even if all these are ok, have I the mic not muted? These are problems that I faced myself, with the last one being one constant headache, because every time I opened skype my mic was muted. I had to configure alsa like that:
[http://ubuntuforums.org/showthread.php?t=227308](http://ubuntuforums.org/showthread.php?t=227308) in order to solve this issue.

There was also one more reason that I wasn't able to use mic, and that had to do with swiching the audio settings of skype from dps1 to dsp. I do not know why this was necessary, but it is a good reason why your microphone might not work. So check these settings.
I do not know about other programs like ekiga, because I do not using them, yet try the analogous settings.

FYI in hardy I think that the installation of both skype and amsn will be one click away and with flawless operation. 

I hope that in the end, you will solve the problems you are facing and that you will enjoy chatting. 

Regards-&#935;&#945;&#953;&#961;&#949;&#964;&#953;&#963;&#956;&#959;&#973;&#962;!

---

### Post by gobbles414 on 2008-04-23
> **loell said:**
> gizmo uses a bridge or a gateway to call windows live messenger so the voice quality would probably be  a bit lower compared to Live to Live messenger conferencing, though i think its tolerable.

Thanks! I'll probably install it on my Ubuntu laptop and try to voice chat with my friend. I'll report back...

---

### Post by gobbles414 on 2008-04-25
Hi all,

Well, I tried last night to voice chat with my friend -- the one who is using WLM in an XP virtual machine within Ubuntu in order to voice chat with her friends and family. She was using Windows Live Messenger and I was using the Ubuntu version of Gizmo5. We couldn't establish a voice connection. After searching the Gizmo5 website, I discovered that:

*A Yahoo or Hotmail user who wants to call your Gizmo account must first register with the gateway site. This page on gtalk2voip.com describes the process to register with the gateway and how to format the dialing information to make calls to Gizmo Project from those other services. To register, go to [http://gtalk2voip.com](http://gtalk2voip.com) and follow the directions at the site.*

That is clearly an unreasonable expectation for people like my friend! If she were to switch to Gizmo5, all of her contacts would have to register with the gateway. Neither my friend nor her contacts would even have a clue about how to register with a gateway. To them, Gateway is just a computer company! :)

Any other ideas...?

---

### Post by loell on 2008-04-25
in calling yahoo messenger, i didn't have to register the user to gtalk2voip. i just type [email]username@yahoo.com[/email] , click call and i can establish a call. I would assume this is the case with windows live messenger? try calling an msn user by typing [email]username@msn.com[/email] or have you already tried this?


yes because its a gateway, if those messenger would have to initiate a call to say gizmo or ekiga, they would have to register to gtalk2voip.

I agree its very inconvenient  for those users in those messengers to register if ever they want to call an outside voip network.

so for this kind of setup to work, the gizmo user will always be the one initiating the call.

---

### Post by gobbles414 on 2008-04-25
> **loell said:**
> in calling yahoo messenger, i didn't have to register the user to gtalk2voip. i just type [email]username@yahoo.com[/email] , click call and i can establish a call. I would assume this is the case with windows live messenger? try calling an msn user by typing [email]username@msn.com[/email] or have you already tried this?


yes because its a gateway, if those messenger would have to initiate a call to say gizmo or ekiga, they would have to register to gtalk2voip.

I agree its very inconvenient for those users in those messengers to register if ever they want to call an outside voip network.

so for this kind of setup to work, the gizmo user will always be the one initiating the call.

Thanks for your reply. Hopefully you can help. My friend and I both tried to initiate the call. Obviously, my friend trying to call me didn't work because she hadn't registered with the gateway. I tried to call her using the following procedure:

A. Add my WLM contacts
B. Restart Gizmo5
C. Start a text chat with my friend
D. Press the telephone button in the chat window

Is that a correct procedure? I heard ringing. But my friend did not receive a prompt or hear a sound asking her to answer my call. Any ideas on what went wrong...?

---

### Post by loell on 2008-04-25
yes that should be the correct procedure,  hmm, tried the manual way? like typing the username and domain to the call bar?  see if it can get through

---

### Post by gobbles414 on 2008-04-25
> **loell said:**
> yes that should be the correct procedure,  hmm, tried the manual way? like typing the username and domain to the call bar?  see if it can get through

I didn't try the manual way. But I will when my friend and I do our next test. Thanks for the advice.

---

