---
title: "multimedia issues"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by Ridgerunner9 on 2007-03-18
ok very new to ubuntu but so far so good however i have some multimedia issues maybe you can help. i can watch or listen to the examples but when i try to watch video from the net, or watch one of my dvds or even listen to my cd i get told i do not have the right codecs for this. i have about five differant multimedia controllers from the updates menu but my problem still is here. my machine is 2 gig with 1 gig ram 80 gig harddrive 128 meg video blah blah blah. i do have a few other issues that i am sure is user error but this one is the most important so i would like to start here. if i can't get the file from the updtaes please give me installation instructions.... as i said i am very new to ubuntu

---

### Post by oilchangeguy on 2007-03-18
what i did is to install automatix. [www.getautomatix.com](www.getautomatix.com). go to sound and multimedia and you should be able to install everything you need.

---

### Post by scxtt on 2007-03-18
you'll need to install the w32codecs package ... pretty common task, i'm sure there's 1000 different ways on the boards ...

it'll involve finding a repo that offers them, adding that repo to your sources.list, aptitude update, aptitude install w32codecs ...

[ for the record, i have no issues w/ people who use automatix (or anything similar), but they don't teach you much of anything ]

---

### Post by Ridgerunner9 on 2007-03-18
could you be a little more specific on how to add repos to list? i am totally lost and what is a repo and where do i find them?

---

### Post by oilchangeguy on 2007-03-18
scxtt, why make life hard? if you're a command line junkie, ok. most people aren't. and that's most peoples complaint with linux, is how difficult it is. that's why automatix was created. to make it easier to install new packages.

---

### Post by scxtt on 2007-03-18
a "repo" is a (software) "repository", basically a storage place for the .deb (sadly, think of .exe) files to exist so any people can install them using a package manager (i use aptitude myself) ...

i'll see if i can find which one has the w32codecs and tell you how to add it to /etc/apt/sources.list ...

EDIT:

use this site --> [http://medibuntu.sos-sts.com/repository.php](http://medibuntu.sos-sts.com/repository.php)
then after you've done "sudo aptitude update", do "sudo aptitude install w32codecs" ... :)

---

### Post by scxtt on 2007-03-18
> **oilchangeguy said:**
> scxtt, why make life hard? if you're a command line junkie, ok. most people aren't. and that's most peoples complaint with linux, is how difficult it is. that's why automatix was created. to make it easier to install new packages.and it will remain difficult as long as automatix does all the leg work ... like i said, i have nothing against those types of "do it all for me" scripts, just saying that for something like this - why not actually LEARN something ...

:)

---

### Post by jackrobinson on 2007-03-18
> **scxtt said:**
> and it will remain difficult as long as automatix does all the leg work ... like i said, i have nothing against those types of "do it all for me" scripts, just saying that for something like this - why not actually LEARN something ...

:)

because not everyone is a school/college kid/computer junkie and also wants to **use** linux?

---

### Post by Ridgerunner9 on 2007-03-18
I am the nuts and bolts kinda guy i want it to work and i would like to now how it works, that is why i leaning away from GATES. I want to be able to make it truly mine in all forms.

---

### Post by scxtt on 2007-03-18
> **jackrobinson said:**
> because not everyone is a school/college kid/computer junkie and also wants to **use** linux?eh, i'm not going to debate the merits of "tools" like automatix ...

if "you" (no one in this thread, specifically) can't handle editing a file and typing some text, "you" should re-evaluate your desire to use a computer @ all, independent of what OS you use ...

and kudos to Ridgerunner9 for wanting to learn something new :D

---

### Post by jackrobinson on 2007-03-18
> **scxtt said:**
> eh, i'm not going to debate the merits of "tools" like automatix ...

if "you" (no one in this thread, specifically) can't handle editing a file and typing some text, "you" should re-evaluate your desire to use a computer @ all, independent of what OS you use ...

umm.. do you know how to change the oil in your car (if you drive one?), and in case you do know, have you ever done it?
On the same lines, do you know how to cook Thai cuisine (in case you like it?) and in case you do know, have you ever tried cooking it instead of going to a restaurant and ordering it?

---

### Post by scxtt on 2007-03-18
that's not a very creative (or logical) argument against editing a text file and running 2 commands ... and i change the oil in my car all the time, well every ~3000 miles ;) ...

---

### Post by jackrobinson on 2007-03-18
> **scxtt said:**
> that's not a very creative (or logical) argument against editing a text file and running 2 commands ... and i change the oil in my car all the time, well every ~3000 miles ;) ...

I can bet you dont change your oil **yourself** (you **get** it changed)... and its not about pasting two lines in a file (almost everyone can do that). You need to realize that whats obvious to you isnt obvious to everyone else. You will know what you are pasting in that file, the other person who has just started using linux will not. He will makes tons of mistakes and trust me , 80% of such people will give up. Why do you think in 16 years of existence, linux just has 1% of desktop marketshare (given microsoft's monopolistic marketing strategies). Automatix is making an attempt to keep those people interested. Automatix is also used by people who find it reliable and keep using it on hundreds of distro-installs. Its used by network admins for mass deployment. Try to start thinking about the possibilities. Its NOT just a tool for n00bs (learn to trust me on that). If you havent realized the full implications yet, I suggest you go and discuss with the automatix devs.  They will give you more exact stats about their clientele.
It started as a quick and easy setup script 1 and half years ago. At the pace at which its going and also in its current form, its a very cleverly designed package manager and only getting better. If you know python, look at its code. You will get the picture.

---

### Post by scxtt on 2007-03-18
> **jackrobinson said:**
> I can bet you dont change your oil **yourself** (you **get** it changed)... and its not about pasting two lines in a file (almost everyone can do that). You need to realize that whats obvious to you isnt obvious to everyone else. You will know what you are pasting in that file, the other person who has just started using linux will not. He will makes tons of mistakes and trust me , 80% of such people will give up. Why do you think in 16 years of existence, linux just has 1% of desktop marketshare (given microsoft's monopolistic marketing strategies). Automatix is making an attempt to keep those people interested. Automatix is also used by people who find it reliable and keep using it on hundreds of distro-installs. Its used by network admins for mass deployment. Try to start thinking about the possibilities. Its NOT just a tool for n00bs (learn to trust me on that). If you havent realized the full implications yet, I suggest you go and discuss with the automatix devs.  They will give you more exact stats about their clientele.
It started as a quick and easy setup script 1 and half years ago. At the pace at which its going and also in its current form, its a very cleverly designed package manager and only getting better. If you know python, look at its code. You will get the picture.after that long-winded bit of nonsense, i'm starting to feel sorry for you ...

and yes, i do change my own oil ... changed it for 6 years in my 2000 cavalier, but i won't change it in my 2006 Altima 3.5 SE until my "we'll change your oil for free for 2 years" certificate runs out ... only cause it saves me ~$10/pop ...

---

### Post by jackrobinson on 2007-03-18
> **scxtt said:**
> after that long-winded bit of nonsense, i'm starting to feel sorry for you ...
The feeling is actually mutual (if you didn't realize that already)

---

### Post by scxtt on 2007-03-18
:-({|=

---

### Post by ebozzz on 2007-03-18
> **scxtt said:**
> [ for the record, i have no issues w/ people who use automatix (or anything similar), but they don't teach you much of anything ]

I installed Automatix right after getting started with Ubuntu. Since that time my use of the CLI has increased. I now only use Automatix if I cannot find a way to accomplish what I need to get done int the terminal in a reasonable amount of time.  

> **scxtt said:**
> and it will remain difficult as long as automatix does all the leg work ... like i said, i have nothing against those types of "do it all for me" scripts, just saying that for something like this - why not actually LEARN something ...

I am in agreement with but some individuals are not interested in learning command-line skills. I certainly am but I don't I don't knock anyone who is not. What I have found is that I have a better understanding of how my machines work from using the CLI. Is it still confusing at times? Yes but the more you use it the easier it gets. ;)

---

### Post by ebozzz on 2007-03-18
The word is **Ubuntu**. Get with it people. :) 

Check this out. I have been able to pick up some CLI knowledge from watching the scripts during installations while using Automatix, Synaptic and the Add/Remove program function. How's that for learning and using tools like Automatix? :guitar:

---

### Post by Ridgerunner9 on 2007-03-19
Far be it from me to hijack your arguement but i am still looking for answers. i looked at automatrix and it looks cool if you understand what they are taking about. it tells me to type this then that(depending on build) and finally type something else..... but for us former windows junkies who are unfamiler with the terminalogy of linux it's like reading braile. i will use a program or type whatever is needed but please tell me where to type it and what it is doing when i type it. If you must argue form versus functionality please be my guest it is very informative but also please include answers to help the rest of us. you mentioned repo but not where to find them and a net search of linux repos turn up thousands and most mention debian build or Ksomeething or gnome etc. pretend for a moment you are taking to someone willing to learn but at the same time does not speak your language.
Thank you:confused:

---

### Post by scxtt on 2007-03-19
did you look at the directions i posted in [post #6]("http://www.ubuntuforums.org/showpost.php?p=2319553&postcount=6")?

open a terminal, and copy the following into it:
```
[font=courier]sudo wget http://medibuntu.sos-sts.com/sources.list.d/edgy.list -O /etc/apt/sources.list.d/medibuntu.list[/font]
```
(this will update your sources.list file (/etc/apt/sources.list), actually add another file to the sources.list.d directory - which will allow you to have another repository from which to get software)

then do:
```
[font=courier]sudo aptitude update[/font]
```
(this will allow aptitude to be aware of the new repo)

then:
```
[font=courier]aptitude install w32codecs[/font]
```
(this will install the codecs)

---

### Post by gnoel on 2007-03-19
Every time a new user wants to "do something" in Linux, it's complicated: complicated to learn (because there's never one answer), complicated to accomplish (typing meaningless commands is no more edifying than using automatix), and even more complicated the first few times when it doesn't work.

Those who have already invested their lifeforce and have succeeded in mastering the intricacies, kudos to you.  However there are countless others who are daunted by the steep initial learning curve.  When there is not enough pleasure to justify the pain, they go back to using that nasty old legacy OS.

Provide the nicer things up front and some people will stick around and learn command line stuff.  And even if they don't, they will be happy users.  Happy users = more users = Linux dominates.  I think a basic Linux user's bill of rights would include the right to have full multimedia connectivity and driver support, even if you have to go outside the Open Source community.

Failing to acknowledge this and debating the superiority of those who use command lines in a Beginner's forum just reinforces the stereotype of Linux as being the pimply-faced geek's OS.

---

### Post by Ridgerunner9 on 2007-03-19
I did read the post # 6 and i do thank you for explaining it further, i find it very difficult to type anything in the command line without undertsanding what it will (or is supposed to do) i guess you could say i have had to many bad experiances to run blindly into the fray. now that it is explained to me i will happily follow your instructions. thanks to all and please don't stop the debate on my account just stop short of hurling feces.:lolflag:

---

### Post by LanDan on 2007-03-19
mmm an ubuntu user blaming someone else for not working on the command line?
isn't ubuntu a south african word for "i can't configure debian" ???

if you want to learn and hack away use Slackware, this will be educational. if you have other things to do in your life use automatix.

just download for your version and click away ;)
[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

---

### Post by scxtt on 2007-03-19
@gnoel:

installing multimedia codecs IS NOT complicated - as a matter of fact, it's one of the easiest things to do and understand when you're new to linux ... and if you don't learn the basics, you won't get far - which goes for ANYTHING in life, not just Operating Systems ... i really don't see your point w/ that statement ...

@LanDan:

no one is blaming anyone for anything - esp. the OP, i'm happy he wants to learn :) ... additionally, if you consider editing a txt file and running TWO commands hacking, well, that's inane ... but i guess you'd be the same kinda person who thinks editing C:\windows\system32\drivers\etc\hosts to add an IP/hostname is a "hack" too ...

---

### Post by gnoel on 2007-03-19
scxtt:

Snarky comments about learning the fundamentals of life are not helpful.  Speaking of life, does it surprise you that some of us have other hobbies?  I ride bicycles and brew beer.  I work an IT job 40-50 hours a week.  I am married and maintain a healthy relationship with my spouse.  My fulfillment is not dictated by my Linux configuration prowess.  However, I would like to enhance our desktops before I spend the spring and summer on my bicycle.

In order to get to the point where I will choose to boot Ubuntu over XP 95% of the time, I need multimedia support.  If installing codecs is all it took, I would have a week of my life back.  If you really wanted to be helpful, you'd help beginners get the most out of Ubuntu as soon as possible and let them learn at their own pace.  A bodhisattva you're not.

---

### Post by scxtt on 2007-03-19
snarky?  nothing i've said has been "snarky" (and honestly, people who throw out all the complicated-isms you do are $.10/dozen ... "i don't need to learn something, i have a life") ... my point is simply: if you want to have an understanding of something (new or old), you've got to start w/ the basics ... if you want to get the most out of your FREE OS, learn a few of the basics before you start accepting the point-and-click of some other OS you're used to ... installing multimedia codecs is A SIMPLE TASK and can teach a new user a few basic aspects of using their new OS that can further help them develop more useful linux skills ...

excuse me for not finding it acceptable that some people want the anwer for everything to be "just install automatix" ...

and your "bodhisattva" comment is just ridiculous  ...

---

### Post by LanDan on 2007-03-20
> **scxtt said:**
> 

@LanDan:

no one is blaming anyone for anything - esp. the OP, i'm happy he wants to learn :) ... additionally, if you consider editing a txt file and running TWO commands hacking, well, that's inane ... but i guess you'd be the same kinda person who thinks editing C:\windows\system\drivers\etc\hosts to add an IP/hostname is a "hack" too ...

sorry for the rant, and maybe replied too fast but my experience is that most people don't want to learn anything, (i usually install ubuntu for them ;) ) this case might be different, how shocking it was indeed to find this out since i actually am the kind of person who does like the CLI.

p.s.

C:\windows\system\drivers\etc\hosts
what distro are you using?

---

### Post by scxtt on 2007-03-20
@LanDan:

it's ok - we all do that from time to time :) ... and i know, sometimes it is shocking when someone doesn't want the "automatix" solution, or is comfortable learning something new - i'm always happy to hear it ...

as for your "p.s." -- are you making fun of me for forgetting the "32"? :p

---

### Post by Ridgerunner9 on 2007-03-20
it looks to me like i stirred up a hornets nest and for that i do apologize but i would also like to thank all of you for your help i found adding apt to my sources list to be very gratifing and i am happier with my os. would you care to point out a few other repos that may have other useful items i might use? and as for automatix i also found that could have it's uses for the non-geek and will use it when i build systems for my children.

---

### Post by Larry Roll on 2007-03-20
Ladies and Gentlemen:

This is the Ubuntu Absolute Beginner's Forum.  It is not the Ubuntu Advanced User's Forum.  People posting here looking for help getting certain things in Ubuntu to "just work" (as the Ubuntu web site claims) want to achieve that goal as painlessly as possible.  Whether or not they go on to gain more advanced knowledge will vary based on personality types.  However, the goal of getting more computer users involved in Linux and Ubuntu should not be forgotten, and neither should be the basis of this particular part of the Ubuntu Forums.  

I am not a forum moderator, and don't feel compelled to take on that role here -- but I think it will be more useful to give simpler, more direct answers rather than engaging in "how many angels can dance on the head of a pin" arguments about the use of helpful tools such as automatix -- something I haven't tried yet, but intend to.  If it does the job painlessly and effectively, then where's the harm?  

BTW I bought the book "Ubuntu Linux for Non-Geeks" by Rickford Grant.  It has been enormously helpful in getting my multi-media applications working, but I still have a lot to learn and this book, with it's task-oriented format, is proving to be a very useful resource.

---

### Post by ebozzz on 2007-03-20
> **Larry Roll said:**
> BTW I bought the book "Ubuntu Linux for Non-Geeks" by Rickford Grant.  It has been enormously helpful in getting my multi-media applications working, but I still have a lot to learn and this book, with it's task-oriented format, is proving to be a very useful resource.

I personally like *Beginning Ubuntu Linux: From Novice to Professional* by Keir Thomas the most out of all of the Ubuntu books that I have put my hands on. Some of the books that I have read are written is such a way that is overly simplistic IMO. *Beginning Ubuntu* has a nice balance. It's a good read but still manages address the subjects very well. Although, it is a little more expensive than the book that you suggested.

---

### Post by zhongwei on 2007-03-26
The scxtt posts  are a good example of conceited arrogance lol

---

### Post by scxtt on 2007-03-26
care to actually back that up w/ something intelligent?

---

### Post by zhongwei on 2007-03-27
Sure.

Your comments are offensive. People learn at different speeds. You make yourself look conceited and arrogant with such comments. I am doing you a favor by pointing out such bad behavior. In life people often just look the other way and avoid interacting with such people. Learn to treat people with understanding and tolerance. 

conceited:

–adjective
1.	having an excessively favorable opinion of one's abilities, appearance, etc.
—Synonyms 1. vain, proud, egotistical, self-important, self-satisfied.

arrogant:

–adjective
1.	making claims or pretensions to superior importance or rights; overbearingly assuming; insolently proud: an arrogant public official.
—Synonyms 1. presumptuous, haughty, imperious, brazen. See proud.

I am a complete noob when it comes to linux, and have not had much education with regards to computers. It is a steep learning curve for people such as me. In order for  community minded projects like linux to survive it requires a steady supply of new people. Being rude, conceited and arrogant turns people away and goes against the open source projects founding principles. Just because you know a little more than some people doesn't give you the right to spoil the project. 

Thanks for your participation.

---

### Post by scxtt on 2007-03-27
your post above is completely irrelevant and a prime example of someone who uses the misguided "you're a linux elitist" argument ...

as i've stated before, while automatix may ease some tasks in linux, it's no substitute to actually learning something new that will DEFINITELY benefit a user in the future (1. command line editing of a config file (/etc/apt/sources.list), 2. adding repos for more software, 3. package management via CLI) ... this was a GREAT example of what's really a trivial task that could teach Ridgerunner9 some great linux/debian/ubuntu basics - and he was willing to learn!

i'm sorry, but i don't believe "install automatix" really needs to be some catch-all solution for EVERYTHING, sure it may have its place, but education can do a lot more ...

[quote=zhongwei]Your comments are offensive.[/quote]i'm sorry, but that's just nonsense ...

---

### Post by tommcd on 2007-03-27
Ridgerunner9, Go here:
[https://help.ubuntu.com/community/RestrictedFormats?highlight=%28formats%29%7C%28restricted%29](https://help.ubuntu.com/community/RestrictedFormats?highlight=%28formats%29%7C%28restricted%29)
Everything you need (all the codecs) are there. You want the gstreamer plugins, w32 codecs, java, flash, libdvdread, libdvdcss. 
Also see here for media players, and lots of other stuff:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)
If you still have problems with multimedia, post here and we can try to help. Good luck.

---

### Post by zhongwei on 2007-03-27
Come now, let go of your ego. 

How is the following a positive encouragement that is conducive to getting more people to use linux?


""""if "you" (no one in this thread, specifically) can't handle editing a file and typing some text, "you" should re-evaluate your desire to use a computer @ all, independent of what OS you use ..."""

I restate: 

This comment (among others from this thread) is a good example of conceited arrogance. And yes it is elitist. 

Ubuntu is about providing an open-source alternative that "all" people can use. All people includes people that find tasks, which you call trivial, beyond them, either because they lack technical capabilities or they lack the time to get grips with whats going on and don't want to break their system (and the productive downtime that ensues). 

They have just as much right to use computers as the technically savvy do. 

There are many things in life that we could all learn, that could be of real benefit to us, which we just don't learn for various reasons (such as command line editing). 

Perhaps something else needs to be re-evaluated? You definitely sound like you have some technical knowledge. Kudos to you. I have 10 days of linux under my belt lol. Perhaps I over stepped some hidden linux hierarchical structure. Apologies to all if that is so.

---

### Post by scxtt on 2007-03-28
in the context of this thread, and esp. [jackrobinson's post]("http://www.ubuntuforums.org/showpost.php?p=2319593&postcount=8"), what i said is not only true, but a general fact of life when it comes to computers ... it's not about anyone's "right" to own/use a computer - it's about people who will complain ( and the OP didn't complain at all :) ), thinking every solution should be point-and-click or "dumbed down" at the expense of learning something new which is a FUNDAMENTAL aspect of their newly adopted OS ...

there's really nothing elitist about it ...

---

