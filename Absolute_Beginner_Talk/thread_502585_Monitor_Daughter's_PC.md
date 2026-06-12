---
title: "Monitor Daughter's PC"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by Jamester64 on 2007-07-16
I have recently installed Ubuntu on all of my PC's and I had a program to monitor my 
13yr old daughter's online activity for Windows, so is there anything like that for Ubuntu ?

---

### Post by richie42 on 2007-07-16
maybe you should be more trusting. . .

---

### Post by jkeyes0 on 2007-07-16
If you're concerned about your child's internet usage, you might consider installing Ubuntu Christian Edition on their PC (well, not even necessarily all of that, just some of the software packages they use, like Dansguardian - [http://dansguardian.org/](http://dansguardian.org/))

Alternately, you could set up a "proxy server" being the only system that has internet access (controlled by your router), and point the rest of the computers in the house to that machine through Firefox. There's a great linux distro called IPCop that you can add extra packages into like Advanced Proxy and Dansguardian, so you can monitor what your kids are seeing and block what you don't want them to see.

---

### Post by TheMono on 2007-07-16
You might want to have a look into Ubuntu Christian Edition - whether you are christian or not, I gather it has tools for that sort of purpose - it at least has blocking filters and the like.

Edit: Got beaten to it.

---

### Post by Jamester64 on 2007-07-16
Ok, perhaps a keylogger for Ubuntu ?

---

### Post by jordanmthomas on 2007-07-16
[http://packages.ubuntu.com/feisty/utils/lkl](http://packages.ubuntu.com/feisty/utils/lkl)

linux key logger...is this what you're looking for perhaps?

---

### Post by huzzak on 2007-07-16
Sorry, all of my searches came up blank.  I don't know if that means that there isn't a Linux solution or if there simply isn't a well-known one.

This article has at least some practical suggestions, though none which are software based and usable on a Linux based computer.

[http://www.synergymx.com/page.php?Title=Keeping_Your_Kids_Safe_Online/](http://www.synergymx.com/page.php?Title=Keeping_Your_Kids_Safe_Online/)

Sorry.

---

### Post by Jamester64 on 2007-07-16
> **jordanmthomas said:**
> [http://packages.ubuntu.com/feisty/utils/lkl](http://packages.ubuntu.com/feisty/utils/lkl)

linux key logger...is this what you're looking for perhaps?

Yes, now if I could just find one with a gui to setup and will be able to autostart.
As i am just learning Ubuntu.

---

### Post by poohbear1616 on 2007-07-16
Or for a simple alternative, you'll have to turn on remote access on your daughters
puter. Give it a hard password with comas and periods and such.

Then on your puter use terminal server client to connect to it. Ubuntu has this installed
by default. I am behind a firewalled router so I just use VNC as the protocol to connect.

I do this when my 4 yr. old is on my Ubuntu system. It puts a carbon copy of his screen
and what he's doing on my monitor.

---

### Post by jordanmthomas on 2007-07-16
Actually, I just tried that one out (on Arch, not Ubuntu) and it didn't seem to work too well anyway.  It slowed down any typing I was doing and recorded most of the strokes as NULL.

Anyway, keyloggers are meant to be discrete and so I doubt you'll be able to find one that has a nice usable interface.  Here's how you run lkl if you'd like to try:
```
 sudo lkl -l -k /usr/share/lkl/keymaps/us_km -o /path/to/log.file
```


*one last thing...not to question your parenting or anything but I surely hope you at least let your daughter know you are mointoring everything she types.  I know I wouldn't like the idea of someone logging my keystrokes without me knowing.

---

### Post by dpar on 2007-07-16
It kind of amazes me that people think it's perfectly ok and normal to spy on your kids computer use, but the same people would get quite upset if their boss did it at work.:)

---

### Post by Auax on 2007-07-16
A little aside here: While I commend you for worrying about your daughter's saftey on the internet, I hope you let her know you're watching.

---

### Post by Jamester64 on 2007-07-16
Yes, I told her that I log everything and I do random checks once in awhile
to make sure she is behaving, and still I have caught her in a few lies.
Plus she uses myspace quit a bit and a parent can't be to carfull these days.

---

### Post by jordanmthomas on 2007-07-16
This one doesn't have a gui either, but it seems you can run it as a normal user so you'll be able to autostart it with no troubles.

[http://distrojockey.com/2005/ultimate-linux-keylogger-uberkey.190.linux](http://distrojockey.com/2005/ultimate-linux-keylogger-uberkey.190.linux)

```
sudo apt-get install libc6-dev build-essential
```
^^ do this before you try what that site says...and ignore the part about the init script.

---

### Post by ramjet_1953 on 2007-07-16
Did you check out Dan's Guardian, as previously suggested?

[http://dansguardian.org/](http://dansguardian.org/)

It may just do what you want.

Regards,
Roger :cool:

---

### Post by Jamester64 on 2007-07-16
no luck with any of those apps.

Since I had her dual booting XP and Ubuntu maybe I just leave her on XP from now on,
or would that be child abuse :)

anyways, thanks for all the help and maybe I will find something that works good in the future.

---

### Post by jpuhalski on 2007-07-17
> It kind of amazes me that people think it's perfectly ok and normal to spy on your kids computer use, but the same people would get quite upset if their boss did it at work. :) 

it is ok, that's just a part of parenting, and at work I have a laptop and it is monitored.  Everything gets logged and we dont get upset.  It's just  basic human nature that, given the opportunity, we will do what we know we should not be doing.   But as Auax said, they should know that they are being monitored.

> Plus she uses myspace quit a bit and a parent can't be to carfull these days.

I agree, when I started using Ubuntu CE it blocked my daughters myspace, and with good reason.  The sad part is I see many young people growing up these days thinking foul language and perversion is just normal.  Myspace is a good place to keep children away from.

john

---

### Post by bobbocanfly on 2007-07-17
If my parents tried to do this to me the first thing i would do would be to break out my LiveCD and do a clean install, then set my own password for the Root account so that my parents couldnt do anything to it.

In other words, lock away your LiveCDs. Just to be safe you might also want to unplug your computer, disconnect it from the phone lines, cut all the wires inside you computer, blowtorch the hard drives, put CCTV cameras in every room in your house, ya know. Just to be extra safe,

---

### Post by cobrn1 on 2007-07-17
It's true folks, anything you can do they can undo better!

If she doesn't clear the history you could just look in that.

Does anyone know if there is a way of setting the permissions so that you can read and write to files in your histroy folder, but can delete them? I'd guess not due to the write ability, but heh, you never know...

As an aside, what are the parental controlls in vista like? Are they any good. How easy are they to overcome.

For once, MS has the right idea, if you want parental controls that are difficult to overcome then you need them baked into the core of the OS.


_ANYWAY_, let her know you are watching, have a look about every-so-often for anything obviously amiss, and maybe try some of the software being suggested above. However, what I said at the start is still true. Clean install and she'll be laughing...(at you) and there's little that can't be effectively and easily overcome.

Do you have to resort to technological means to parent. I don't want to sound judgemental, but she'll only respond in kind and defeat them. Like I said before, look around everyso often, educate her about the online dangers and tell her what you expect. THat's the best way to act like a parent in this case (IMO).

---

### Post by Austin_KW on 2007-07-17
> **Jamester64 said:**
> I have recently installed Ubuntu on all of my PC's and I had a program to monitor my 
13yr old daughter's online activity for Windows, so is there anything like that for Ubuntu ?

If you have to ask then chances are that a teenager can defeat anything you can do ;)
Any kid with physical access to the hardware can bypass anything you can do. The most secure solution is some sort of proxy/gateway that limits access but don't be surprised when they re-cable your home 'cause they don't like been spied upon Or worse still they might start logging what you are doing;)

---

### Post by rickycodie on 2007-07-17
i think it's great that he's interested in keeping his daughter safe, way to be a good parent

---

### Post by mjwhitfield on 2007-07-17
> **jpuhalski said:**
> Myspace is a good place to keep children away from.Myspace is a good place for everyone to keep away from, but not for the reasons you've listed.

Have you tried something simple, like just editing her hosts file to block out the websites you don't want her visiting?

---

### Post by mike555 on 2007-07-17
If your afraid of porn , you could set up openDNS on your router to block all porn on all your computers .... or even block certain sites ....   [www.opendns.com](www.opendns.com) .......

---

### Post by Austin_KW on 2007-07-17
> **rickycodie said:**
> i think it's great that he's interested in keeping his daughter safe, way to be a good parent

I agree, and it is a long time since I was a teenager, but locking me out of something was a sure way of getting me obsessive of beating the lock. 
If nothing else you will make your kid an IT/networking expert.

---

### Post by Austin_KW on 2007-07-17
> **mike555 said:**
> If your afraid of porn , you could set up openDNS on your router to block all porn on all your computers .... or even block certain sites ....   [www.opendns.com](www.opendns.com) .......

An excellent illustration of my point, thanks, something that will stop all the adults from accessing something that kids could bypass in 30 seconds

---

### Post by rickycodie on 2007-07-17
it's the fact that he's willing to try in a time when so many men are on montel williams that i'm commending.

---

### Post by walkerk on 2007-07-17
I didn't read all three pages but I hope you choose not to install a keylogger on your daughters computer. Its one thing to monitor what she does (web pages and such..), a whole other creepy thing to want to know everything she types. perhaps she uses her computer as a diary.. where is her privacy?

plus.. you probably don't want to know **everything**.

---

### Post by Jamester64 on 2007-07-17
> **walkerk said:**
> I didn't read all three pages but I hope you choose not to install a keylogger on your daughters computer. Its one thing to monitor what she does (web pages and such..), a whole other creepy thing to want to know everything she types. perhaps she uses her computer as a diary.. where is her privacy?

plus.. you probably don't want to know **everything**.

Well I do have a keylogger installed on her XP and true I don't want to know everything,
but as I stated before she is aware that everything she does is monitored on my network and I also
told her that I occasionally do random checks. 
May I add she is a very pretty 13yr old girl and my one and only Daughter that I very much want to trust
and hope she is not influenced by the wrong kinda people .

Loving Dad

---

### Post by cleverselfreferentialname on 2007-07-19
I think it's probably more important that you talk to her, tell her what's out there and what she ought to avoid, and why. Your kid should have some privacy.

When I first got a computer, my parents said that they had no interest in monitoring me, that being able to read what you want to read and such is a right. In order to deprive someone of the right to read whatever they like, in the united states (in mental health facilities) in order to deprive somebody of the right to read what they want to, for fear that it could lead them to harm, they have to have the mental age of about eight. So why shouldn't a 13-year-old be able to read what she wants?

And yeah, I know, there's other things on the internet besides text, but it's about the same point. Just tell her to never meet anyone in person she spoke with online, tell her that people do have a tendency to maliciously link to shock sites, tell her what you think of porn and how degrading it is to women (at least, usually? I dunno).

---

### Post by macogw on 2007-07-19
> May I add she is a very pretty 13yr old girl and my one and only Daughter
Makes me want to ask if you treat your boys the same way as you treat the girl, assuming you have sons, that is.

---

### Post by playme123 on 2007-07-19
I have a friend wh kept the history on msn to monitor her daughter as she used it alot, and she caught her daughter a cropper, while I admired her wanting to keep and eye on her, I also said is she allowed any privacy(they were talking about sex and stuff).  But she said you should of heard what they were talking about.  I said it would be nothing different to what they would be talking about in the playground.  I also pointed out once she has figured out how you turned the history on, she will turn it off.  My advice to her was to keep the pc in the living room were she could keep an eye on here and believe you me she would be carefull what she is typing.  That seemed to off worked and everyone is happy.
I would not allow my daughter a pc in her bedroom, you dont know what she could be viewing, and I also think it would isolate the child

---

### Post by Spike-X on 2007-07-19
> **Jamester64 said:**
> 
May I add she is a very pretty 13yr old girl...

Too bad she's not ugly. Then nobody would want to touch her and you wouldn't have to worry! 

Seriously, what do her looks have to do with anything?

> **Jamester64 said:**
> and my one and only Daughter that I very much want to trust


Perhaps you should have her followed by a private detective whenever she leaves the house. Can't be too careful, you know!

---

### Post by mjwhitfield on 2007-07-19
This thread has taken a worrying turn.  The guy asked for advice on how to check various parts of the usage history, not social comment.

---

### Post by Austin_KW on 2007-07-19
> **mjwhitfield said:**
> This thread has taken a worrying turn.  The guy asked for advice on how to check various parts of the usage history, not social comment.

Yes but, asking a group of people who use an OS that presupposes a philosophy of freedom, he was bound to get some comment.

---

### Post by AZzKikR on 2007-07-19
> **cleverselfreferentialname said:**
> I think it's probably more important that you talk to her, tell her what's out there and what she ought to avoid, and why. Your kid should have some privacy.

When I first got a computer, my parents said that they had no interest in monitoring me, that being able to read what you want to read and such is a right. In order to deprive someone of the right to read whatever they like, in the united states (in mental health facilities) in order to deprive somebody of the right to read what they want to, for fear that it could lead them to harm, they have to have the mental age of about eight. So why shouldn't a 13-year-old be able to read what she wants?

And yeah, I know, there's other things on the internet besides text, but it's about the same point. Just tell her to never meet anyone in person she spoke with online, tell her that people do have a tendency to maliciously link to shock sites, tell her what you think of porn and how degrading it is to women (at least, usually? I dunno).

I couldn't agree more with this point. I wanted to mention the same thing while reading the first posts, until I came across yours. 

You should really talk to your daughter, and telling her the dangers of the internet, and what she should do and should not do and what she should avoid. How would you feel when your activity (whether it is online or real-life) is constantly monitored? 

I certainly would feel trapped in a corner, and angered somehow. For instance, I don't want my parents to know everything from me, like I don't want to know everything from everybody. And I do not want my boss to know everything I am doing, even though I got nothing to hide.  

Privacy is scarce these days, and even your baby girl needs her privacy. I don't think it's a good way to 'teach' your daughter what she can and can not do on the internet, by blocking her access to certain websites and whatnot. It's all into education from your side, and gaining experience from her side. 

I can imagine how you might feel regarding the dangers of life and such, but that's all about parenting. I am not a parent myself, but I can imagine how you are feeling. She is of course your beautiful girl and you want to protect her. That is okay of course, but I *think* the best approach to her safety is to inform her about things, and make sure she understands them. 

Again: I am not a parent, but I am just telling you my point to of view. I am just 22 years old, but I am thinking how I would have felt when I was younger and my parents would do this with me. This is a very delicate topic to discuss about, by the way...

---

### Post by LouisvilleLIP on 2007-07-19
I don't think its anyone's business how he intends to monitor his daughter's actions.  You don't know him, her, or the reason that he feels it's necessary.

I have a daughter.  She is too young to use a computer right now, but when she is old enough, I will be paying attention to what she is doing.  It doesn't take much searching on the interweb to find stories about "good" kids who get into trouble because their parents weren't aware of the dangerous things they were doing.  

Yes, if she really wanted to, she could defeat anything he does.  But does that mean you shouldn't try?  

And BTW, if you don't have children, you don't have much credibility on the subject.  Your perspective isn't the same, and your opinion is very likely to be ignored.

---

### Post by AZzKikR on 2007-07-19
> **LouisvilleLIP said:**
> And BTW, if you don't have children, you don't have much credibility on the subject.  Your perspective isn't the same, and your opinion is very likely to be ignored.

True. But I have been a child in the computer-age too. Been using computers since the age of 11 or something. Internet came to me at the age of 14 or 15 or something. So I am just telling how I would feel on this subject, from my perspective as a child.

I just think knowing point of views from both sides (parent and child) should result in a better solution.

---

### Post by stalker145 on 2007-07-19
I can see both sides of the way this discussion has gone and both have merit. I, however, fall squarely into the camp that cares for, instructs, and monitors my children.

As a child myself, I was one of the ones that defeated most every attempt that my father made at controlling me. That led me right into a lot of heartache and a couple of run-ins with the law. Did my father placing restrictions on me and monitoring me make him a bad parent? I don't think so. Hindsight being 20/20, I have to say that it showed that he cared and didn't want me to experience the pain that I did.

What should we do? Should we allow our children to run wild through this world where people are looking to take advantage of the weak/immature/ignorant or should we guide our children by our words and deeds? Should we fully trust our children 24/7 or should we put controls in place that will allow us a peek at what the truth is?

How many out there trust what any person says every moment of every day? Would you believe me if I told you that a certain string of characters typed into the terminal would **not** wipe your hard drive (we know the string) but would make your computer run faster (or keeping a grain of truth: would give you more free space)? Quite the contrary, we research advice, we question motives, and we check up on people. Maybe not overtly, but this is true with much of society (and I've experienced more than one).

@jamester64: Thank you for taking an interest in your daughter. Parenting (at least in the U.S.) has, to a large degree, turned away from teaching and guiding our children and moved toward putting them on their own.

Both methods, I feel, should be used in concert. Check up on your children - whether by popping in on where they claim to be or monitoring their computer time and also give them space to prove that they are making sound decisions. A parent can not control every aspect of a child's life, not should they. This will not teach the child the self-sufficiency that will be needed to move into the adult world safely.

I submit for your consideration an acronym that has been with me for 14 years (and the military for much longer):
```
**BAMCIS**
**B**egin the planning, 
**A**rrange for reconnaissance, 
**M**ake reconnaissance, 
**C**omplete the planning, 
**I**ssue the order, 
**S**upervise
```

I'm sure by mentioning that this is a military acronym some will be immediately turned off. I simply ask that you consider how this can be used in civilian life. You may find that it occurs without your even knowing it. The last line is key: supervision. Without that, your plan (raising children) will not turn out the way you hope.

**Background**: I am the proud father of a 5 year-old boy and a 14 year-old boy. The five year-old is beginning to learn about computers and the 14 year-old has already found many of the more questionable sites on the internet. I have monitored the history in his browser (which he has begun clearing), checked up on his habits by keeping the router log, begun using OpenDNS, removed him from access to the household computers, and sat over his shoulder while he was working. All of this, along with myself and his mother sitting down and talking to him about our feelings on pornography, have caused him to rethink his actions... until we aren't watching and he reverts. 
We have spoken to him about honor, respect, integrity, and so many other 'good' moral traits that I think he can recite them all back to us. Peer pressure is stronger than parenting pressure. ***This*** is why we, as parents, must strengthen our resolve to keep our eyes on our children and raise them properly, not giving in to those that wish their children into adulthood.

**Disclaimer**: All of the above is my personal experience and opinion. You are entitled to disagree with that opinion.

---

### Post by hyper_ch on 2007-09-12
Depending on where you are from you should also know that your children do have rights:

[http://www.unicef.org/crc/](http://www.unicef.org/crc/)

most notably:
> 
Article 13
1. The child shall have the right to freedom of expression; this right shall include freedom to seek,
receive and impart information and ideas of all kinds, regardless of frontiers, either orally, in writing or
in print, in the form of art, or through any other media of the child's choice.
2. The exercise of this right may be subject to certain restrictions, but these shall only be such as are
provided by law and are necessary:
(a) For respect of the rights or reputations of others; or
(b) For the protection of national security or of public order (ordre public), or of public health or
morals.


An interesting thing is, although many states have signed and ratified this treaty, the US is not among those...

While I see that oversight is needed I think a constant monitoring does not do well... here in Switzerland constant monitoring at works is - with a few exceptions - forbidden. Its against our fundamental rights that we have.

---

### Post by jordanmthomas on 2007-09-12
I'll take one ticket to Sweden please.

---

### Post by CaptainInsaneO on 2007-09-12
> **Austin_KW said:**
> I agree, and it is a long time since I was a teenager, but locking me out of something was a sure way of getting me obsessive of beating the lock. 
If nothing else you will make your kid an IT/networking expert.

Funny you should say that. When I was a teenager my father had dial-up with a password on it, and only my parents knew the password. That's when I first figured out the wonder that is keylogging. :)

And now I'm a networking expert and do it everyday for a living. lmao. Thanks dad. :lolflag:

(When I told my mom a few years ago what the password was, she looked at me in disbelief and still has no idea how I figured it out.)

---

### Post by hyper_ch on 2007-09-12
> **CaptainInsaneO said:**
> (When I told my mom a few years ago what the password was, she looked at me in disbelief and still has no idea how I figured it out.)
Tell her you peaked over her shoulders as she typed it ;)

---

### Post by zetsumei on 2007-09-12
Lets see, are there any tools that would let me monitor a Windows XP computer without installing nothing on it.  I need to monitor my parents computer as they're dumb and tend to get viruses a lot -_-

---

### Post by hyper_ch on 2007-09-12
the only thign you can monitor without installing anythign would be the network traffic to and from that computer if you are in the same lan - otherwise, without installing, I don't think you can monitor anything.

Well, you could setup a video camera/webcam that is pointed towards the screen, so you can records what they do and watch it ;)

---

### Post by LowSky on 2007-09-12
> **zetsumei said:**
> Lets see, are there any tools that would let me monitor a Windows XP computer without installing nothing on it.  I need to monitor my parents computer as they're dumb and tend to get viruses a lot -_-


just set up remote desktop (it already installed), but i dont know if you can remote in to a windows computer using ubuntu

---

### Post by zetsumei on 2007-09-12
well what's a good windows, secret monitoring program I could install XD.  One that doesn't require a lot of memory, etc.  They refuse to let me optimize their PC.

---

