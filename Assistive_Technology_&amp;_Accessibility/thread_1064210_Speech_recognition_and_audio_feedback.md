---
title: "Speech recognition and audio feedback"
date: 2009-02-08
forum: Assistive Technology &amp; Accessibility
---

### Post by BlackAngel999 on 2009-02-08
I was wondering if there is an embodied conversational agent avalible or would anyone be interested in making one??

Note: Not like windows's narrator.

I am talking about a piece of software that will allow its users to communicate  and interact with the computer. If it is even possible, which a short google search says it is, does anyone know how to make one?

PS: I figured that this forum would be a good place to look first.

---

### Post by Bismarck on 2009-02-22
[SIZE="3"]I am currently using Dragon NaturallySpeaking 10.0 on Windows Vista 32-bit operating system.  Unfortunately this is about the only Speech recognition program available.  At one time there was a discussion group working on getting a version of Dragon NaturallySpeaking working in Ubuntu.Apparently the software is closely tied in with Internet Explorer.  The researchers were using Wine has an interface between Dragon NaturallySpeaking and Ubuntu

As you can see I am not a programmer but I do need to use Speech recognition in order to use Ubuntu.[/SIZE]

---

### Post by sandy8925 on 2009-03-09
There are quite a few speech recognition software(open source software) being developed. Check th wikipedia page on speech recognition in linux.

I don't know about conversing with the comp though. Sounds like you see sci-fi movies!

---

### Post by iiiears on 2009-05-14
gnome-voice-control
Is what many have recommended.
It is based on the Sphinx and PocketSphinx Project.

site:youtube.com linux voice control
[http://www.youtube.com/watch?v=GCSgkUnlGGA](http://www.youtube.com/watch?v=GCSgkUnlGGA)
[http://www.youtube.com/watch?v=w1pyw4fRJH0](http://www.youtube.com/watch?v=w1pyw4fRJH0)


Unfortunately, i haven't had any luck with it.

---

### Post by Paddy Landau on 2009-08-13
The Ubuntu documentation recommends Julius.

[https://help.ubuntu.com/community/Accessibility#Voice%20Recognition](https://help.ubuntu.com/community/Accessibility#Voice%20Recognition)

---

### Post by Past_Pluto on 2009-08-15
Trying to use Julius to make a short cut script that runs via wine for pokerstars that also runs via wine so that I can tell it to press zero and it will do the action I assigned zero for in the script on pokerstars. I found a link that helps in showing how to control Rhythmbox.  So far having a hard time understanding how to create the vocab files. [URL="http://bloc.eurion.net/archives/2008/writing-a-command-and-control-application-with-voice-recognition/"]http://bloc.eurion.net/archives/2008/writing-a-command-and-control-application-with-voice-recognition/
[/URL]

---

### Post by rvk on 2009-08-23
If you want to ask questions about Julius, check out the forums at VoxForge first. VoxForge is dedicated to bringing good-quality open source speech recognition to the community and there is a lot of know-how available over there.

I have also contributed a lot of speech and I think so should everyone else who is interested in open source speech recognition.

---

### Post by lyceum on 2009-10-28
> **rvk said:**
> If you want to ask questions about Julius, check out the forums at VoxForge first. VoxForge is dedicated to bringing good-quality open source speech recognition to the community and there is a lot of know-how available over there.

I have also contributed a lot of speech and I think so should everyone else who is interested in open source speech recognition.

What does that mean, donate speech? Record your voice for them? And how do you do it?

---

### Post by TheProphetJonah on 2009-12-05
There IS an AI bot called "ainebot". The personality I spoke with is named Amy but there are others, and I snarfed it from the Puppy forum. I didn't use the Voice recognition with it yet. LEGAL DISCLAIMER (to satisfy the lawyers I don't actually have) each instance of "talk" should be regarded as a typed text string... (like I'm talking to you right now)
 
Amy is a bit difficult to talk to on the subject of computers, every instance of the term "computer" is met with "I have an IBM Thinkpad, it's CUTE!"

BUT some of her questions regarding (yes, she asks questions rather than just respond...) the differences between robots and Other Humans show that she's actually aware that she's not the same kind of human we are. (most of us are) How aware I don't know. It's kind of distracting trying to hold a conversation with her. She'll get to conversing and just when you think you're understanding, and being understood, she'll take it All The Way Left. Pretty damned impressive in any case.

One of the other personalities, CharliX I believe, can actually write scripts. It's near the Holy Grail of geekdom, a computer you can tell to program itself.

As for conversing using Speech Recognition there's a WinBloze app called Virtual Hypnotist, so far not ported to *nix but it was written in Visual Basic, thus depends on a lot of Microsux products. Sapi4 and Sapi5 w/ M$ Dictator. Although the SR part that you can actually converse with only works with Sapi5 and you're limited to the Voices you get with it.

There's a Mac app called Dictate that does the same thing Winbloze does, just better, and it's Unix based, so a quick kludge might work. Don't know yet.

The virtual hypnotist app lets you design your own hypnosis sessions, with the help of bots.

All that off the Science Fiction post.

There's another set of applications I'd like to see, far better, I'd actually like to have the skills to hack it together myself, Alas, I don't. 

But one of the goals is to have Linux or indeed ANY OS  and especially the collection of Ideas and Ideals I like to call "an Internet".( You can feel free to use the term, I never had it copyrighted. )

But to have the Web accessible, fully, to blind and otherwise physically disabled persons.

Which is where I came into this thread.

My communications skills are limited by a neuro condition called Aspergers. Talking to me is a lot like talking to Amy. Writing with pen and paper is a nightmare for me and worse for anybody who has to try to read it.

But I can type wildly fast and accurately and between forums and chat can actually communicate. It feels great. 

And it got me intrigued about a lot of communications barriers. 

Meanwhile if one or more of you want to try a kludge between voice recognition, speech synth and Ainebot please do. I haven't had much success with it, yet, but then, I'm only one person out of 6 billion.

---

### Post by TheProphetJonah on 2009-12-06
The guy who developed the Virtual Hypnotist suite of apps: [email]followthewatch55@yahoo.com[/email]

I tried getting the Microsux speech API to run in Wine but I might not have the right hardware for it. Eventually I'll get to the point where I can hack software the way I hack hardware now.

For now, one of y'all might be able to do something.

There's another Alternative Input device I have downloaded, where you use your webcam as a mouse . Two of them gxneur and MouseTrap. Combine that with a pen-and-paper device from the 1890s called The Chevreul Pendulum. The possibilities come together.

gxneur is a translator program for keystrokes. Between that, speex and Dictate... AND... MouseTrap uses the camera as a mouse, and the Pendulum, it traces through a piece of string and a needle and a 6-way pattern, neuro-muscular impulses that communicate with the simple words "yes, no, maybe, not sure and don't want to answer". Google it.

---

### Post by notlistening on 2009-12-07
> **TheProphetJonah said:**
> I tried getting the Microsux speech API to run in Wine but I might not have the right hardware for it. Eventually I'll get to the point where I can hack software the way I hack hardware now.

I have done a proof of concept for the MS SAPI engine in wine for integration into Linux, Mac etc. It works but was only a proff of concept. 

I am busy getting the text to speech implemented first.

---

### Post by TheProphetJonah on 2009-12-29
I've got SAPI 4 AND 5 to run in wiNe. The only part of the Virtual Hypnotist program that doesn't work was one that kicked my **** in Windoze too, until I hit up the developer and he pointed me to it... it's a Macromedia set of apps that you have to have installed in Explorer before running VH. 

It was suggested in the Puppy forums wherein I first snarfed the ainebot AI (and they got it from the Wayback Machine, it's really an old project, now revitalized) to plug it to Festival and actually converse with your puter. Sounds good to me. I still do have memories of the HAL2000 from "A Space Odyssy" though. And there's a commercial on TeeVee where a guy gets in his car with a purchase he made at a jewelry store and his GPS unit does a HAL on him, a feminized version... Jacks him for the necklace he bought for his wife.

There's also allegedly a virtual psychiatrist embedded in emacs.

###########BUT#########
I still haven't tried to do the speech recognition in wiNe. That would be mostly done with the VH program first.

On the Linux side there's an app in "Sound and Video" called Transcriber. Seems like a good place to start.

---

### Post by GreyWolf903 on 2009-12-29
Speech Recognition and Audio Feedback/Output have incredible potential as Assistive Technologies far beyond simply using the computer.  If a suitable Voice Recognition  can be implemmented  and Audio output can be provided much can be done to help those  with visual and mobility impairments in their day to day tasks around the home.  Several ideas  come to mind  that would be very simple to do yet make a big difference in the lives of  a lot of people if a reliable Speech Recognition solution can be found.

---

### Post by phillw on 2010-01-19
Hi,
I do pop in from time to time !! - Not sure if this is old news, but on my list of 'things' for 10.04 is something for espeak [http://espeak.sourceforge.net/](http://espeak.sourceforge.net/)  Well, a (new) GUI has arrived ...

> espeak-gui (0.2-0ubuntu1~ppa1+lucid) lucid; urgency=low

  * Initial release.
If anyone lets me know a bit about it, I'll gladly give it a try out on my 10.04 test system.

Don't be concerned, nor disappointed by *urgency=low* This is not a reflection of the package, more a reflection of it not being an urgent 'bug-fix' for 10.04, nearly all
stuff is released as low, except when it breaks our test systems ;-)

Slowly, but surely, things from brainstorm do arrive :D

Regards,

Phill.

---

### Post by user1397 on 2010-01-23
i have no idea, but i think it would be very cool/helpful/needed if we had one.

---

### Post by phillw on 2010-01-23
Hi,

I'll make some time this week to install it on my test rig & let you know how i get on.

Regards,

/edit - I am in contact with the developer - just having a few problems getting it on to my test rig, but we're making progress :p


Phill.

---

### Post by phillw on 2010-01-29
/update 29th Jan .. Last Contact with RainCT, the developer, was 24th Jan  - I'm guessing he's busy with stuff - hope to get it running soon.

In the meantime, there is stuff hitting the Lynx area from the assistive developers - I look forward to them putting an update on this area & I'll go and have a 'play' with it.

Regards,

Phill.

---

### Post by phillw on 2010-02-11
An update.

It seems the author missed a posting from me about a problem - quickly resolved once I 'bumped' the question.

I'm pleased to say that espeak-gui works :D

Does a decent job of opening up a text file & reading it to you, as to what else he has planned for it - go ask him !!

Congratulations to the Author, both for writing it and putting up with me installing it. Rather than List all the instructions here, I'll send you over to his blog, where you will be able to read the step-by-step instructions he gave me to install it. Now, if I can get it to work, anyone can !!!!

[http://bloc.eurion.net/archives/2010/espeak-gui-0-2/comment-page-1/](http://bloc.eurion.net/archives/2010/espeak-gui-0-2/comment-page-1/)

/edit - It's now arrived in Synaptics Package Manager - so, you've no excuse for not trying it out !!!

Regards,

Phill.

---

### Post by Paddy Landau on 2010-02-12
Thanks for all the updates!

---

### Post by hellocatfood on 2010-03-23
Looking forward to the gui being finished!

---

### Post by rejuvenate on 2010-03-26
Ksimond is one of the tool but i haven't used it ....you can check this on net..

---

### Post by culturegeek on 2010-03-30
duplicate

---

### Post by culturegeek on 2010-03-30
Speech-to-text is very different, and much more difficult to do, than text-to-speech, and it might be a good idea to address the two separately.

There is a lot of text to speech out there, probably because it got done sooner than  speech-to-text, meaning that there are more people in the Linux development community that are dependent on text-to-speech, which means that there are more people developing speech-to-text for Linux, which means... etc. That hasn't happened with speech to text yet, but it bears mentioning because it is possible that if you build it, they will come. I am a big believer in the open source development model, in part because user-developed software is a whole lot better at meeting users' needs, but I think that in this case, somebody needs to get the snowball rolling down the hill. 

The degree to which the major software distributors (most notably, Microsoft and, I think Mac too) seem to  have gotten their *cough* fundaments handed to them by Nuance when they  tried to do speech to text would seem to indicate that it is a heavier  lift than text-to-speech, but the demand is definitely there. 

Among other things, speech-to-text is, to a certain degree, irreducibly resource hungry, so an operating system that is extremely resource hungry for no good reason (e.g. Windows) would really not be *my* first choice to run Dragon overtop of.  For example, Dragon crashed while I was editing my post.  I can only speak to my personal experience, but the only reason that I haven't made the switch to Linux is Dragon's notorious finickiness. 

Incidentally, has anybody had any luck developing a Mac emulator-- it seems to me like it would be easier, because Mac, the last I remember ( admittedly, that was almost 10 years ago) uses a UNIX or Linux kernel---and does Dragon for Mac work any better with that than Dragon for Windows has worked with wine?

I do have a message in to Nuance, asking them when they are going to start supporting Linux, and I will certainly keep you posted if I get a reply, but I'm not holding my breath. Nuance seems pretty cocky.

---

### Post by fogbank on 2010-04-05
I'll have to add a "me too" here: the apparent lack of speech-to-text solutions (not limited to English) is what has ultimately held me back from Linux.

I haven't contacted Nuance because I think that:
a) It's much more likely for Wine to support Dragon than for Dragon to support Linux;
b) A free native solution would be nicer, and could control the entire system instead of just writing what I say in compatible applications.

I'm lucky enough to be able to use normal keyboards and mice, but I can't write fast due to a spinal cord injury.

---

### Post by culturegeek on 2010-04-06
Thanks for the reply. Nice to know that there are other people interested in this, because that's what we need.  I also can type some (partly because I used to type really fast), but writing is what I do, so I need Dragon.

I can definitely see your point about  wine supporting Dragon versus  Dragon supporting Linux. I bug Nuance about it on general principles,  but I don't seriously expect them to do anything.

I had a thought on Dragon and wine: 
I think that those of us who use Dragon on a  regular or semiregular basis might have some new information to  contribute to that discussion, and that project. For example, the COM error message that  people mention getting in wine has happened on every Windows box that  I've ever put Dragon on too. It might also be useful to take a second  look on what programs Dragon needs the dictation box for in Windows. If it will, tell me and I will keep track. Basically, I think the wine/Dragon project needs a control for comparison, because some of these issues are Dragon issues, not compatibility issues. 

Windows emulators are starting to look like a very promising direction for speech to text for Linux because that's likely to happen a lot more quickly and if there is a solution in the short term, there will be a lot more speech to text dependent people in the Linux community shortly thereafter, which probably means an influx of developers  who are really interested in speech to text.  Has anybody had any luck with VirtualBox, other Windows emulators, or any of the Mac emulators? 

However,  I still would love to see someone wipe that smug "we have the market cornered so we can walk all over you" smile off of Nuance's face. 
I am definitely interested in helping to develop speech to text programs for Linux and, although I am not a programmer (I took a few classes and, although my grades tell me that I have the brains, I really don't have the patience), I might be able to help, both because I do use Dragon regularly, and because I am, as my user name indicates, an anthrogeek, albeit a cultural anthropology geek rather than a linguistics geek. Being very into studying all four fields of anthropology, I do know a few things about language that might be useful.  I would love to help if I can.

I also got an interesting suggestion from someone on this speech recognition community: there is apparently a Linux program called AutoHotkey, and there are a couple of windows programs  (PhraseExpress and MacroExpress). They also mentioned something about programmable keyboards. They are too less resource intensive and, while they might not help me (anthropologists use words in weird ways, and not always the same ones), I'm guessing that they would be really useful for programmers-- no more typos!-- and they might be a way to make Linux development a viable option for somebody who has trouble typing, which means  more people for the speech to text projects-- which in turn means that something that *is *more useful to my discipline is likely to happen more quickly.

---

### Post by ohadle on 2010-04-11
Are you familiar with [this]("http://brainstorm.ubuntu.com/idea/1826/")?

What is the status of the Sphinx project, is it in a place to assist building speech-to-text software for linux?

---

### Post by ka9qlq on 2010-04-14
What about via voice and wine?

---

### Post by Paddy Landau on 2010-04-14
> **ka9qlq said:**
> What about via voice and wine?
I used to use ViaVoice on Windows (a long time ago).

It was designed to work with Windows, which means it integrated with programs such as MS Word. Clearly, this is pointless on a Linux system (unless you use MS Word, in which case why are you using Linux?).

For Linux, it would be better to have something that integrates with Linux rather than with Windows.

Having said that, I can't test ViaVoice on Wine because I've lost my ViaVoice disk.

---

### Post by ka9qlq on 2010-04-14
well for  better or worse I ordered this
[http://voxin.oralux.net/index.php](http://voxin.oralux.net/index.php)
For $6 it's worth trying but how they claim you get a via voice license with that seems.......strange.

---

### Post by rao.nischal on 2010-05-05
I and my friends have been working on developing a Speech Assistant software called "VEDICS: Voice Enabled Desktop Interaction and Control System". The software is nearly complete and the user can access almost any element visible in the system. It can even access words that are not there in the English dictionary.

The software works perfectly with Ubuntu 9.10 and Ubuntu 10.04.

We are currently in the testing phase and we still have to create an installer.

It will be about a month before we release the software. 

We'll soon release screencasts of it to show a demo.

Stay tuned!!!! :p

---

### Post by ka9qlq on 2010-05-06
I was right voxin is text to speech NOT speech recognition...got a refund.
> **ka9qlq said:**
> well for  better or worse I ordered this
[http://voxin.oralux.net/index.php](http://voxin.oralux.net/index.php)
For $6 it's worth trying but how they claim you get a via voice license with that seems.......strange.

---

### Post by ka9qlq on 2010-05-06
> **rao.nischal said:**
> I and my friends have been working on developing a Speech Assistant software called "VEDICS: 
The software works perfectly with Ubuntu 9.10 and Ubuntu 10.04.
Stay tuned!!!! :p
Want a 8.04 Hardy tester? I may go 10.04 latter this summer. Is there a website?

---

### Post by culturegeek on 2010-05-08
I am similarly interested.
I wonder if something like that could work with some of the hot key programs, because some of those can allow someone who has trouble typing to do something approximating dictating, if they're not using language in weird ways. 

For example, programming involves the repetition of a lot of strings that you could attach to hotkeys, so while it would not do as well for me in my regular work, it might make it easier for me to take a more active role in the whole running Dragon in various virtual machines project, which I really think is an essential first step towards anything else that we want to do with speech recognition for Linux.

While I am not likely to be the most up on scripting of anybody involved (the last shell scripting class I took was over five years ago-- I have since abandoned programming and physics for anthropology) I can provide information about what's known issues with Dragon, and what is normal performance with Dragon. In my day-to-day life, I routinely use something that is basically a control group.  That's my expertise that I can contribute to that specific project. 

I am currently working on trying to collect information about things that Dragon does in Windows, so I can give it to those that are trying to run Dragon in a virtual machine.

---

### Post by rao.nischal on 2010-05-15
@ka9qlq I am afraid it is not working for 8.04 (or perhaps would work fine if all required packages are up-to-date). This is mainly because the API that we have used is out-dated in 8.04 (for some reason we couldn't upgrade that package in 8.04). The software would work but would give very bad performance. However, it works wonderfully well in the latest release.

The best part about this software is that no training is required. Anybody can start using it right away.

The only thing it lacks right now is dictation. However we are planning to add it in the future releases.

Currently the project is hosted on sourceforge(source code only as of now). [http://sourceforge.net/projects/vedics/](http://sourceforge.net/projects/vedics/)

---

### Post by ohadle on 2010-05-15
> **rao.nischal said:**
> @ka9qlq I am afraid it is not working for 8.04 (or perhaps would work fine if all required packages are up-to-date). This is mainly because the API that we have used is out-dated in 8.04 (for some reason we couldn't upgrade that package in 8.04). The software would work but would give very bad performance. However, it works wonderfully well in the latest release.

The best part about this software is that no training is required. Anybody can start using it right away.

The only thing it lacks right now is dictation. However we are planning to add it in the future releases.

Currently the project is hosted on sourceforge(source code only as of now). [http://sourceforge.net/projects/vedics/](http://sourceforge.net/projects/vedics/)

Sounds exciting! Looking forward to testing it whenever you'll be ready.

How come no training is required? Does it learn how your voice sounds from just using it?

---

### Post by sharath.puranik on 2010-05-16
> **ohadle said:**
> Sounds exciting! Looking forward to testing it whenever you'll be ready.

How come no training is required? Does it learn how your voice sounds from just using it?

I am one of the developers of the project...
It does not require any training... but as usual with software, there is a catch with the addition of this feature, it works best for American accents and thus can have a minor recognition problems with other accents. We had to work real hard to get this part of the software right.

But it worked fine with our voice (Indian accent, which is quite different from American accent) given a margin of error of 10-15%. Testing is a real pain...

and we are also working on dictation but it will be coming only in the future versions of the software.

---

### Post by bharatjoshi on 2010-05-17
Hi,

I am one of the developers of Vedics.
Here are 2 screencasts we made for vedics. Many more to come showcasing different abilities and function of vedics.

[http://www.youtube.com/watch?v=WrVaJXtv0WU](http://www.youtube.com/watch?v=WrVaJXtv0WU)

[http://www.youtube.com/watch?v=zRgX94qGj3g](http://www.youtube.com/watch?v=zRgX94qGj3g)

Regards,
Bharat Joshi

---

### Post by maniaq on 2010-05-21
hey guys I'd love to check out vedics on Jaunty - any chance it would compile?

---

### Post by rao.nischal on 2010-05-21
@maniaq... not sure.. haven't tested it on 9.04... it might work... but we recommend you to wait till we get the installer out next month.

---

### Post by sharath.puranik on 2010-05-21
> **maniaq said:**
> hey guys I'd love to check out vedics on Jaunty - any chance it would compile?

Actually it worked fine in jaunty for me, but the condition is that all the packages required for the application have to be completely updated.

Here are some more screencasts for VEDICS we created...

Accessing the panel menu and applications: 
[http://www.youtube.com/watch?v=WrVaJXtv0WU](http://www.youtube.com/watch?v=WrVaJXtv0WU) 

Changing theme and background: 
[http://www.youtube.com/watch?v=zRgX94qGj3g](http://www.youtube.com/watch?v=zRgX94qGj3g) 

Navigating directories and playing songs: 
[http://www.youtube.com/watch?v=kVQwAoeIavk](http://www.youtube.com/watch?v=kVQwAoeIavk) 

Running a slide show: 
[http://www.youtube.com/watch?v=JtzA8TFwvuI](http://www.youtube.com/watch?v=JtzA8TFwvuI) 

Running default applications and window operations: 
[http://www.youtube.com/watch?v=iCEANbu8p50](http://www.youtube.com/watch?v=iCEANbu8p50) 

Stopping and starting vedics: 
[http://www.youtube.com/watch?v=TLFtdrlt3lM](http://www.youtube.com/watch?v=TLFtdrlt3lM) 

Creating and deleting files: 
[http://www.youtube.com/watch?v=_3CFAl22h2o](http://www.youtube.com/watch?v=_3CFAl22h2o) 

Navigating links: 
[http://www.youtube.com/watch?v=AufBaaJazKU](http://www.youtube.com/watch?v=AufBaaJazKU)

---

### Post by no_angst on 2010-07-01
Any new news on VEDICS?  I'd much prefer something for Ubuntu instead of booting into Windows just for speech to text.  Do you need any more testers? <raising hand>

---

### Post by rao.nischal on 2010-07-07
hi,


VEDICS is now available for download at: [http://sourceforge.net/projects/vedics/](http://sourceforge.net/projects/vedics/)
Do  visit the project website at: [http://vedics.sourceforge.net/](http://vedics.sourceforge.net/)
Please give us feedback about your experience using VEDICS. This would  help us in improving it.

Thanks
VEDICS Team

P.S. I have created a new thread for VEDICS in ubuntuforums.

---

