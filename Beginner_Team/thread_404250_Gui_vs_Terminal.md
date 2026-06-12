---
title: "Gui vs Terminal"
date: 2007-04-08
forum: Beginner Team
---

### Post by spd106 on 2007-04-08
In my experience new users are coming over from other OSes where every task is achievable through purely gui dialog boxes and menus. Now some will say that's not the best or most efficient way on linux and that sooner or later you _will_ be faced with a terminal, so you should gain some familiarity sooner rather than later.

What I want to know is does/should the beginner team have a policy on pointing new users to gui applications in preference to terminal commands, even when it would be quicker and easier to just copy/paste a command.

An common example is installing new programs. The Add/Remove or Synaptic gui apps are very users friendly and show quite a breadth of information. But if all you need to do is install an app (say firestarter) quickly, then sudo apt-get install firestarter works far quicker and with less fuss.

There are examples of goals that can cannot be achieved without using a terminal or would be rather difficult and involve a longer process. Especially when someone has a problem and needs it to be fixed quickly. The broken wifi scan in network-admin on Edgy has been mentioned many times and forces the user to use iwlist scan or install Network Manager, which is difficult without a network connection.

All thoughts are welcome on this issue.

---

### Post by siciliancasanova on 2007-04-08
As a relatively new linux user, I have found a nice happy medium.  I understand the speed of the terminal once you have learned a few commands, but IMO if Ubuntu wants to eventually become the front running distro to compete with Apple and Microsoft, AND become a world wide open source solution for ANYONE, I believe that on a fresh install for a fresh Ubuntu user, GUI is mandatory and terminal is optional.

If it were to be that one needs to learn their way around the terminal to function at a level they were used to on a proprietary OS you would see a slow switch rate.  The learning curve would be too high.

If Ubuntu's goal is to be for everyone, especially those who have never touched Linux and are migrating from Microsoft or Apple, I really don't feel it's an option.  The GUI needs to eventually be capable of 95%-100% of achieving goals in Ubuntu.  Nevermind speed, mind the learning curve.

---

### Post by ncappel1 on 2007-04-09
I think that answers to problems should be addressed in two ways, one way with the GUI (if possible) and another way with the CLI.  This would promote using the gui, but also allow users to study the methods of the command line (if they choose to), leading to a deeper understanding of how everything works.

Getting used to seeing command line entries will also acclimate beginners to the idea that entering commands into a terminal will not "break the computer." like I was afraid of in the beginning :)

---

### Post by bodhi.zazen on 2007-04-09
> **spd106 said:**
> In my experience new users are coming over from other OSes where every task is achievable through purely gui dialog boxes and menus. Now some will say that's not the best or most efficient way on linux and that sooner or later you _will_ be faced with a terminal, so you should gain some familiarity sooner rather than later.

What I want to know is does/should the beginner team have a policy on pointing new users to gui applications in preference to terminal commands, even when it would be quicker and easier to just copy/paste a command.

An common example is installing new programs. The Add/Remove or Synaptic gui apps are very users friendly and show quite a breadth of information. But if all you need to do is install an app (say firestarter) quickly, then sudo apt-get install firestarter works far quicker and with less fuss.

There are examples of goals that can cannot be achieved without using a terminal or would be rather difficult and involve a longer process. Especially when someone has a problem and needs it to be fixed quickly. The broken wifi scan in network-admin on Edgy has been mentioned many times and forces the user to use iwlist scan or install Network Manager, which is difficult without a network connection.

All thoughts are welcome on this issue.

spd106 :

Thank you for posting and you raise a good question. Let me fist set a background if you will.

On one hand lets take users. If you are an Ubuntu user then Ubutnu can be 100 % GUI. I know several users in fact who are 100 % Ubuntu and never use the terminal. This is similar to other OS where someone has installed and configured the system for the user(s).

On the other hand lets look at sys admin. There are many GUI tools for sys admin, but sometimes it is faster to use a terminal.

Last there are Power users and tweaking.

So to answer your question regarding the policy of the Beginners Team :

Our goal is to help new users acclimate to Ubuntu. The preference is to start with GUI tools as much as possible, and refer to the CLI interface as a source of further information/options. In the event the CLI (terminal) is easier, the CLI will be used.

In implementation, however, as you point out, it depends on the format. On the forums it is easier to post a few commands then to attempt to describe the gui tools/mouse clicks ...

In wiki format, however, it becomes easier to post screen shots.

Thus we are starting a wiki. The goal is to provide answers in the forums and refer to the wiki for further information, including screen shots. The wiki will refer to further information on the CLI.

Hopefully we will provide a smooth transition into Ubutnu.

In my experience, yes the CLI is intimidating at first. As one gains experience, however, it becomes second nature. IMO learning the CLI is part of the transition process if one is to do sys admin or power tweaking. If one is a casual user, however, there is no need for the CLI.

---

### Post by chakkaradeep on 2007-04-09
> **spd106 said:**
> 
What I want to know is does/should the beginner team have a policy on pointing new users to gui applications in preference to terminal commands, even when it would be quicker and easier to just copy/paste a command.


I would suggest we should have both GUI and Terminal, but by default, point Users initially to GUI as new Users would be comfortable with. If they encouter any unrecoverable problems, we could point them to Terminal methods...remember, terminal commands usually have **-v or --verbose** which could help us to debug :)

---

### Post by useResa on 2007-04-10
> **ncappel1 said:**
> I think that answers to problems should be addressed in two ways, one way with the GUI (if possible) and another way with the CLI.  This would promote using the gui, but also allow users to study the methods of the command line (if they choose to), leading to a deeper understanding of how everything works.

Getting used to seeing command line entries will also acclimate beginners to the idea that entering commands into a terminal will not "break the computer." like I was afraid of in the beginning :)IMHO, this is the proper way to go.
Provide both possibilities where possible and thereby making the new user familiar with the fact that there is something called a terminal and that things can be achieved by using a terminal.

If (s)he so desires (s)he will read up on the matter, try it and learn by doing.

---

### Post by chakkaradeep on 2007-04-10
I think this help can be merged with this [- Beginners/FAQ]("https://help.ubuntu.com/community/Beginners/FAQ?highlight=%28beginners%29#head-a651bed0d14d229d92250023c1c03e170be537aa") ??

---

### Post by teaker1s on 2007-04-10
good Idea, I think that whatever method is employed to help beginners, we should stick to the most straight forward, reliable and quick solutions

---

### Post by finferflu on 2007-04-10
I think it all depends on what you need to do. Sometimes clicking is quicker and easier than typing, sometimes you need to understand what's going on, thus you need a terminal. I think the question GUI vs Terminal should be addressed in relation to the task one has to perform. In fact, that's the Linux philosophy: everything is relative to what you want to achieve.

---

### Post by spd106 on 2007-04-10
Is there a way to edit a file owned by root without using a terminal command?

For example if I want to add a module to the /etc/modules file. The best I can do is *gksudo gedit /etc/modules*.

If there was a way to open as root from nautilus, then that might be an easier way. The trend at the moment appears to be to extend an existing system utility to make these changes. The problem is that there will always be a lag time between these options becoming available and the gui being updated to be able to take advantage of them. Network Manager on top of wpa_supplicant stands out as an example.

Whether a new user will need to take advantage of these more advanced settings is perhaps a more important point. I suppose new users should be restricted in the potential damage they could cause through a simple mistake.

---

### Post by teaker1s on 2007-04-10
```
gksudo nautilus
```:guitar: :guitar: :guitar: :guitar:

---

### Post by bodhi.zazen on 2007-04-10
Yes there are (several) ways of doing this, but I am not sure I want to post them. Perhaps someone else will ...

My objection is one of security ... Yes, ease of use vs security is an ongoing issue and, IMO, opening a terminal and entering gksudo ... is about as easy as I want to see it get.

Now you may or may not know what you are doing, but all too often a new users makes these types of changes to make it "easier" only to end up later with regrets ... Some of the potential changes can not be undone with out a total re-install.

IMO you are asking to make system files too far too easy to edit, without backups or an ability to easily restore such changes. Also, IMO, opening a terminal is not that difficult.

/rant :lolflag:

---

### Post by teaker1s on 2007-04-10
True a given terminal command in an beginners control if typed incorrectly=nothing.
```
gksudo nautilus
``` you give a greater margin of error damage- This then needs careful thought to avoid disaster when assisting

---

### Post by Ian-on-the-Trent on 2007-04-11
I'm a new Linux/Ubuntu user. I've been around PCs since DOS and am somewhat comfortable working towards an understanding of Linux, terminals, and tweaking systems using this.  That said, I still come from a Windows world.

I've worked a lot with small, not-for-profit organizations.  These groups with their minimal budgets, tend to have a correspondingly low level of technical savvy. BUT, this is one user group that really needs alternatives to the bloatware cycle that stems from using Windows-based systems.  

Typically, these groups only need basic office productivity software, basic web tools, and more commonly these days, a networked database of sorts.  There is no reason in the world that they need to ditch fully functioning P3 or AMD boxes in the 650Mhz to 1Ghz range. But they get sucked into the expensive spiral of upgrades. Friggin VISTA...what will this cost these groups.

Unfortunately for the Linux community, which sees itself as a potential option to MS, there is an orthodoxy, perhaps an arrogance, that turns its nose up to the pleebs who just want to get on with their job and not spend hours trying to understand Linux.  GUIs are for the masses for good reason...people are largely visual and work best with symbols. It just works.

Easy to use, graphical network management tools really are important for these small offices. There may be a trade-off with the potential for customization, but so be it.  These organizations want:
[LIST]
[*]data security
[*]data integrity
[*]software/hardware functionality
[*]ease of use
[*]low cost
[/LIST]
It doesn't have to be lighting fast, very pretty, gimmicky...just turn it on and go.

For example, my wife's organization has 25 PCs in 6 small offices.  They have a network in each and one centralized, web-based server for a common database.  But this system is costing them ten's of thousands of $$$ a year in both software licensing and hardware updates. They are paying an MS-authorized/licensed firm to look after their IT requirements. It's crazy.

However, is there an option that doesn't require a radical culture change and a leap of faith?

My $0.02 worth.

---

### Post by bodhi.zazen on 2007-04-11
> **Ian-on-the-Trent said:**
> I'm a new Linux/Ubuntu user. I've been around PCs since DOS and am somewhat comfortable working towards an understanding of Linux, terminals, and tweaking systems using this.  That said, I still come from a Windows world.

I've worked a lot with small, not-for-profit organizations.  These groups with their minimal budgets, tend to have a correspondingly low level of technical savvy. BUT, this is one user group that really needs alternatives to the bloatware cycle that stems from using Windows-based systems.  

Typically, these groups only need basic office productivity software, basic web tools, and more commonly these days, a networked database of sorts.  There is no reason in the world that they need to ditch fully functioning P3 or AMD boxes in the 650Mhz to 1Ghz range. But they get sucked into the expensive spiral of upgrades. Friggin VISTA...what will this cost these groups.

Unfortunately for the Linux community, which sees itself as a potential option to MS, there is an orthodoxy, perhaps an arrogance, that turns its nose up to the pleebs who just want to get on with their job and not spend hours trying to understand Linux.  GUIs are for the masses for good reason...people are largely visual and work best with symbols. It just works.

Easy to use, graphical network management tools really are important for these small offices. There may be a trade-off with the potential for customization, but so be it.  These organizations want:
[LIST]
[*]data security
[*]data integrity
[*]software/hardware functionality
[*]ease of use
[*]low cost
[/LIST]
It doesn't have to be lighting fast, very pretty, gimmicky...just turn it on and go.

For example, my wife's organization has 25 PCs in 6 small offices.  They have a network in each and one centralized, web-based server for a common database.  But this system is costing them ten's of thousands of $$$ a year in both software licensing and hardware updates. They are paying an MS-authorized/licensed firm to look after their IT requirements. It's crazy.

However, is there an option that doesn't require a radical culture change and a leap of faith?

My $0.02 worth.

1. Ubuntu (Linux) is not a drop-in replacement for Windows.

2. If these groups want to transition to Linux they will need to develop a transition plan that includes some training for new users and a plan for IT support. This is no different then Windows in that most people have received training on windows at some point in their education or work place, if not both.

3. That being said, if you have IT support, Ubuntu is no more difficult then Windows for the tasks you listed. None of the tasks you listed require any knowledge or use of the command line by the end users.

4. Knowledge of  the CLI is only required of sys admin. To be fair, the users of your wife's organization probably know nothing of windows sys admin either.

IMO your wife's organization could easily transition to Ubuntu, the hardest part would be finding someone to do sys admin. You should look into Edubuntu which would easily set up a Linux server and clients for minimal hardware/software costs.

[http://doc.ubuntu.com/edubuntu/handbook/C/](http://doc.ubuntu.com/edubuntu/handbook/C/)

---

### Post by Ian-on-the-Trent on 2007-04-12
Thanks for replying bodhi.zazen.

This likely should be another thread...this said, would you have a link I could pass along *vis a vis* a transition plan.  This is beyond my level of knowledge. (Post it here or thru email would be great.)

Thanks again.

---

### Post by bodhi.zazen on 2007-04-12
> **Ian-on-the-Trent said:**
> Thanks for replying bodhi.zazen.

This likely should be another thread...this said, would you have a link I could pass along *vis a vis* a transition plan.  This is beyond my level of knowledge. (Post it here or thru email would be great.)

Thanks again.

No problem.

I am not aware of any specific link to a transition plan, this will need to be determined by your wife's organization.

As a general outline, start with a demo of the Live, desktop CD. If that looks viable, discuss the option with whoever has the power to make such a decision (in your wife's organization) and again demo the desktop (live) cd.

If that then looks good, identify who will provide IT support.

From there you can likely use the hardware you already own so schedule a time for Ubuntu (or Edubuntu) install, hardware testing, install/configure workstations.

Last schedule training (1-3 hours) with volunteers on the new system.

This plan could include installing open source applications on their current systems like say Firefox and OpenOffice so when if they go live with Ubuntu the applications are not so foreign.

Installing Firefox and OOO also gives them time to build trust / test open source solutions.

I am sure you will get support from many of us here at Ubuntu. If you like you may open a new thread in the Beginners Team Section and I am sure you will get support from my team.

The mods will move the thread if they deem it should be located elsewhere.

By starting a new thread, others will be able to contribute and benefit as well.

---

### Post by teaker1s on 2007-04-12
bodhi.zazen
+1 


Ian-on-the-Trent
I agree, I would do a phased conversion to ubuntu as it builds user understanding and the** IT guy **can learn along the way. 
I suggest this method as I understand your dislike of licencing costs, but you must have a competent person to manage the system.

I wish you luck with your project and welcome to the forums
:guitar:

---

### Post by jpyanowski on 2007-04-18
This is a very interesting and informative thread. I've been on computers since the early IBMs and DOS. I've used used Windows 3.0 and 3.1, 95, 98, 98SE, ME, XP and Vista. I can remember Steve Jovs takling about the CLI on OSX. I think that anyone who is going to work with Linux would want to learn the terminal and how powerful it can be. Knowledge is power.:-D

---

### Post by Ian-on-the-Trent on 2007-04-19
Thanks all for your input.

Nothing is free and I don't expect any organization to exist on freebees. That said, there seems to be the overwhelming desire by many MS-type businesses to maintain a monopoly.  And with a monopoly comes the stifling of innovation and high prices. (Bare witness to the US steel industry prior to the 70's).

I suppose this is getting somewhat political/philosophical...my apologies, However, I sometimes think that an analogy to an operating system is air.  We all need it, the quality of what we breathe effects us intimately, and what you do to it effects me.  (The "other guy" really would like to own it all and charge us for it.)  In an O/S context, the Linux community strives to make sure we can all breathe a little easier.

Of course, to go along with this clean air we need food.  Each of us decides if we want to grown our own, buy organic or make our purchases from a market.But we pay for this and thus determine the value of that purchase.

Yes, a perceptive IT contractor would be of great assistance to organizations such as my wife's.  A huge component of their job would be to re-educate users on the benefits and effectiveness of software that just keeps on working.

Please excuse my rambling.

---

### Post by o0splitpaw0o on 2007-04-20
Watch this video and maybe get a perspective how some feel about gui vs. terminal. it's an honest debate with a little humor to it. but maybe gives a perspective who your dealing with as a new user 

[http://www.youtube.com/watch?v=VSCNpzD37l4](http://www.youtube.com/watch?v=VSCNpzD37l4)

There's also this presentation that helps determine how and when maybe is the best to practices on helping a new user I think breaks down things.

[https://wiki.ubuntu.com/OhioTeam/NewUserTeam?action=AttachFile&do=get&target=profilinguser-ubuntu-ohio.odp](https://wiki.ubuntu.com/OhioTeam/NewUserTeam?action=AttachFile&do=get&target=profilinguser-ubuntu-ohio.odp)

---

### Post by spd106 on 2007-04-21
Thanks for the links.

Not sure about the video, I thought it was too much of a rant with very little substance. The same arguments we've all heard may times in the Linux vs Windows/OSX debate.

In contrast I think the odp presentation was very good and well worth a read. Since it's in the wiki I'm assuming it's under the same CC licence?

---

### Post by o0splitpaw0o on 2007-04-22
yes, the presentation is. If you look at it and review the video again you could definitely see how these two guys fit in one of those profiles. It wasn't scripted or anything. This is a consistent debate at my store, and they are both right in some ways. 

1. Some like not to know how it works, just work.
2.Some feel they should contribute, some don't
3. Some like to have full control of their system., some don't mind what's available.



all in all,  knowing who your dealing with based on their experience, patients, & commitment on change really helps out. I don't approach every person the same. some  knowledge from my times working in phone support years back from past training. Works every time, and reduces people from switching back.

---

### Post by bodhi.zazen on 2007-04-22
> **o0splitpaw0o said:**
> all in all,  knowing who your dealing with based on their experience, patients, & commitment on change really helps out. I don't approach every person the same. some  knowledge from my times working in phone support years back from past training. Works every time, and reduces people from switching back.

Words of wisdom.

---

### Post by carloslosgrande on 2007-05-27
As a long term beginner, I can say that gui is easier for me as there is usually an explanation window to help me decide whether to proceed and for feedback after.
I now know there are man pages and sometimes I can follow them, there is also output which is sometimes sweetly clear, other times mudlike.
When I had/have difficulties and some nice expert directs me to the terminal with clear instuctions I feel confident to enter as directed. Along the way I pick up bits and pieces and copy them to my howto and fixit files.
Slow but sure is winning my race.

---

### Post by mac173 on 2007-06-01
I am a new user of ubuntu who has played around with Linux versions for years. At one time I had 4 OS's on a machine, just for playing around. 

HOWEVER....

I have found that the great majority of people WILL NOT bother with command line interfaces. As a previous poster pointed out, todays users are attuned to visual stimulus, and "point and click". 

As the worlds most prolific OS, Windows has constantly moved AWAY from command line in favor of GUI. Dispite the bugs and bad programming, Windows consistently outsells everything else. This is because very few people want to learn the details. People want it to WORK, with as little a learning curve as possible. 

As long as Linux in general, and ubuntu specifically, keeps this attitude that if you want to use linux you HAVE to learn command line, it will forever be a novelty instead of a main replacement for Windows.

---

### Post by cunawarit on 2007-06-01
> **mac173 said:**
> IAs the worlds most prolific OS, Windows has constantly moved AWAY from command line in favor of GUI. Dispite the bugs and bad programming, Windows consistently outsells everything else. This is because very few people want to learn the details. People want it to WORK, with as little a learning curve as possible. 

I think it is important to highlight that Windows is the world's most prolific DESKTOP OS. And on the desktop environment Microsoft has indeed tried to shield the user as much as possible from the command line, however, MS has recently made a huge deal of the big comeback of the command line with [PowerShell being shipped as standard with Windows Server 2008]("http://www.microsoft.com/windowsserver2008/powershell.mspx"). 

And I agree, beside MS occasional dirty tactics that have helped it gain more ground than its fair share, Windows sells because it simply works phenomenally well as a desktop OS. 

IMHO, on the desktop users should not have to use the command line at all. Admins on the other hand should be comfortable doing things on the command line, and write scripts to automate as many tasks as possible... You would be shocked to see how many so called Windows systems administrators do everything on the GUI!

---

### Post by anotherbigal on 2008-01-27
Hi all.

This thread started with a request for information about a beginners policy approach. There have been (as usual) a lot of good points made in what follows but I feel one major thing has been totally overlooked. For whatever reasons more and more single users are going out to buy their first computer. They do not have any formal Windows training, as was suggested by bodhi-zazen in one of his posts, and probably never will have. They take the box home, unpack it and switch on. What they get, at least in the UK, is Windows. They click on something and it works. They have no idea and do not care about how or why. That is the way computers are portrayed in the media. Switch it on and go.
   
  What do they want from this box? Internet, email, messaging, DVDs and music. With time they will probably use Word as well. Then they need a printer, or as is now becoming vey popular, a multifunctional printer that scans, copies and prints excellent photos from their digital camera. It stops there.
   
  To expect this type of user, and make no mistake they are the bulk of users,  to even try to learn a CLI is pie in the sky. They might, please note – might, be persuaded to try Linux. Hopefully Ubuntu, but if the GUI does not work “out of the box”, forget it. Their experience will stop there and back to Windows they will go. We have got to realise that the bulk of computer users are not “interested”. They just want something that works.

---

### Post by carloslosgrande on 2008-01-28
[FONT="Comic Sans MS"]Anotherbigal, I agree with what you say but I'd add that all the windows users I've met, only use it because there isn't any alternative. They curse it daily, as it doesn't work, at least not to the extent they want or were led to believe.
Mac is too expensive and "linux - what's that? I have enough trouble with this now, I don't need another program"
I think Ubuntu is getting much closer to usability for them.[/FONT]

---

### Post by anotherbigal on 2008-01-28
At least Michael Dell is bucking the trend offering Ubuntu systems in the United States. Why not world wide though? Anyone know what the take up has been?
   
  What I do not understand is peoples approach to computers. When they start driving they all go out and invest a lot of time and money on driving lessons. When they buy a computer they somehow expect to know it inside out and backwards without any effort on their part. Yes, that’s right, they all then curse Microsoft, but will they consider starting with anything else? No Even if it is so much better. Huhh?

---

### Post by p_quarles on 2008-01-28
> **anotherbigal said:**
> At least Michael Dell is bucking the trend offering Ubuntu systems in the United States. Why not world wide though? Anyone know what the take up has been?
   
  What I do not understand is peoples approach to computers. When they start driving they all go out and invest a lot of time and money on driving lessons. When they buy a computer they somehow expect to know it inside out and backwards without any effort on their part. Yes, that’s right, they all then curse Microsoft, but will they consider starting with anything else? No Even if it is so much better. Huhh?
Ubuntu Dell's are available in the UK at this point, though for unfortunate prices.

Not entirely sure about the analogy to driving. I got my license in 1997, and nothing about driving has changed since then. On the other hand, I started using Windows with 3.1, and have used everything up through Vista. The changes with each major Windows update are enormous by comparison to driving.

All the same, the differences between Windows 98 and Windows XP are, I think, less than the differences between Windows XP and Ubuntu, or between Windows XP and Mac OS X. That doesn't mean that any of them are inherently more difficult to use, but those differences do tend to make many people stay with what they know.

---

### Post by anotherbigal on 2008-01-28
> **p_quarles said:**
> Ubuntu Dell's are available in the UK at this point, though for unfortunate prices.

Not entirely sure about the analogy to driving. I got my license in 1997, and nothing about driving has changed since then. On the other hand, I started using Windows with 3.1, and have used everything up through Vista. The changes with each major Windows update are enormous by comparison to driving.

All the same, the differences between Windows 98 and Windows XP are, I think, less than the differences between Windows XP and Ubuntu, or between Windows XP and Mac OS X. That doesn't mean that any of them are inherently more difficult to use, but those differences do tend to make many people stay with what they know.

 I have used 3.1 up to XP but have not got enough beef for Vista yet. Yes, any change involves a learning curve but with Windows the feel is that it is based on something we already know. I am going to stick with driving. We go from push bike to moped, moped to motorbike, motorbike to car then possibly on to larger things. Traffic signs change, road layouts change both locally and nationally (I hate to admit that I can remember the coming of motorways). But it is all based around our personal "history". It grows from something we know. To change to a different OS is a step into the unknown. Scary.

We are users. I my case only very modestly, but how can we convince others that it IS better? I suppose word of mouth and by example are best. We have got to generate the demand. Push for major software to be ported to Ubuntu. I am thinking of things like Sage and Intuit accounts packages. Dreamweaver, popular games with well known, familiar names. Also, to go back to the training issues what about chasing local colleges for evening classes linked to CLAIT training.

---

### Post by UnixDream on 2008-02-02
[LEFT][FONT="Book Antiqua"][COLOR="DarkOrchid"][B][B][FONT="Book Antiqua"]Greetings. I just joined the forums this eveining. This thread seems to be directly focused to determine what should be presented to new users of Linux OS Ubuntu. 
Understand, I consider myself just barely above novice when it comes to computers and the operating systems and languages that make them work. 
In my job I am in constant contact with people who just want their electronic devices (cell phones in my job) to work right now. To them computers, cell phones, etc should all work the moment they come on. They do not want to have to think; they just want to do. 
Present GUI for the majority.
For those like myself and my friends, include the terminal option for command line. I love graphics, but I also like to be able to tailor my system to my standards and what I want. 
Now, here comes the novice. Is CLI short for Command Line Interface? Also, concerning the forum itself: what is the difference between sticky and normal posts?
[/B][/B][/COLOR][/FONT][/LEFT]

---

### Post by LaRoza on 2008-02-03
> **UnixDream said:**
> 
Now, here comes the novice. Is CLI short for Command Line Interface? Also, concerning the forum itself: what is the difference between sticky and normal posts?



Yes, CLI is short for Command Line Interface.

A sticky post is a post that is "stuck" to the top of the forum. A normal post are the posts that you see on the forum.

The stickies are made because they are useful enough to make them always visible.

It says "Sticky Threads" above them, and they are highlighted.

Stickies are usually worth reading.

---

### Post by anotherbigal on 2008-02-03
Welcome to the world of Linux UnixDream.

Your comments are on the button. The modern world is buy and use. Fine to start and learn from new but most of us are changing over when it comes to Linux. The OS might be new but the operator comes with baggage - and wants that baggage to be "cut and pasted" in  and, if you are like me, cannot afford to just forget the old and start again. I run small mail order company. My records are in Windows. Move them? Yes. Throw them away? No.

For Ubuntu, or for that matter any version of Linux to become popular it must be able to simply import from the majority of popular MS software.

As much as I would like to, there are not enough hours in the day to sit down and learn command line stuff. (Yes, I accept that it is a powerful and extremely useful tool). GUI and a file system with names that makes sense. Most of the applications I have looked at have some really odd names.

---

### Post by bodhi.zazen on 2008-02-03
> **anotherbigal said:**
> Welcome to the world of Linux UnixDream.

Your comments are on the button. The modern world is buy and use. Fine to start and learn from new but most of us are changing over when it comes to Linux. The OS might be new but the operator comes with baggage - and wants that baggage to be "cut and pasted" in  and, if you are like me, cannot afford to just forget the old and start again. I run small mail order company. My records are in Windows. Move them? Yes. Throw them away? No.

For Ubuntu, or for that matter any version of Linux to become popular it must be able to simply import from the majority of popular MS software.

As much as I would like to, there are not enough hours in the day to sit down and learn command line stuff. (Yes, I accept that it is a powerful and extremely useful tool). GUI and a file system with names that makes sense. Most of the applications I have looked at have some really odd names.

LOL

Ubuntu / Linux is NOT a drop in replacement for Windows and more then likely your data transfer issue is a problem with WINDOWS. By that I mean if the data can not be imported it is because it is on a proprietary, closed database. Ubuntu / Linux is able to handle a wide range of open data bases, like sql.

Second, it takes time to learn a new OS. You have been using Windows for how many *years* ??? It takes 3-6 months to become familiar with a new OS, and the best way to learn it is to use it.

In terms of the command line, it is possible to use Ubutnu without ever needing to do anything in the command line.

However, the command line is very helpful and I would encourage you to learn to use it. Windows hides the command line from you, and as with anything new it is intimidating at first.

BUT, the command like allows you to sys admin much easier then the gui. In fact gui tools are limited in any OS, including windows. When the gui tools fail in windows, you are either stuck (with no solution) or will have to drop to the command line.

99.99 % of people using windows accept being "stuck", with no solution, as normal and acceptable. :lolflag:

Ubuntu offers another solution, but I would expect a transition period, and we are here to help with the transition.

---

### Post by LaRoza on 2008-02-03
> **bodhi.zazen said:**
> 

However, the command line is very helpful and I would encourage you to learn to use it. Windows hides the command line from you, and as with anything new it is intimidating at first.

BUT, the command like allows you to sys admin much easier then the gui. In fact gui tools are limited in any OS, including windows. When the gui tools fail in windows, you are either stuck (with no solution) or will have to drop to the command line.


I use the CLI on Windows more than I do on Linux. Although Windows is crippled compared to Linux in this way (most ways, actually) its CLI is most useful.

---

### Post by UnixDream on 2008-02-03
> **LaRoza said:**
> Yes, CLI is short for Command Line Interface.

A sticky post is a post that is "stuck" to the top of the forum. A normal post are the posts that you see on the forum.

The stickies are made because they are useful enough to make them always visible.

It says "Sticky Threads" above them, and they are highlighted.

Stickies are usually worth reading.

[COLOR="DarkOrchid"][B][FONT="Book Antiqua"]Thank you for answering my questions. I will continue to read through the sticky notes. 
I have two books in our household that I will be using in addition to the forums. Ex-Windows is a part of our household and this is what he is doing as well. 
My ultimate goal is to build my own computer system from the ground up. 
The books I mentioned: The Official Ubuntu Book (Benjamin Mako Hill and Jono Bacon, Corey Burger, Jonathan Jesse, Ivan Krstic) published 2007 & Unix for Programmers and Users 2nd Edition (Graham Glass; King Ables published 1999)
Though the second book is about 10 years old, I figured it would still be useful to me. 
My next acquisitions, I am hoping, will be a book on the C & C++ language and an updated book for Unix. 
I feel like this community forum is a friendly place. I look forward to reading the many threads and learning as much as possible.
As I learn, I hope that I'll be able to help others too. 
[/FONT][/B][/COLOR]

---

### Post by LaRoza on 2008-02-03
> **UnixDream said:**
> 
My next acquisitions, I am hoping, will be a book on the C & C++ language and an updated book for Unix. 
I feel like this community forum is a friendly place. I look forward to reading the many threads and learning as much as possible.
As I learn, I hope that I'll be able to help others too. 

Before buying books on C, look in [http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

There is too much online for free to start out with buying books :)

---

### Post by UnixDream on 2008-02-03
> **LaRoza said:**
> Before buying books on C, look in [http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

There is too much online for free to start out with buying books :)

[COLOR="Purple"][FONT="Book Antiqua"]I just popped over to the link you shared. I'll come back in after the super bowl :popcorn:to check out more of the language threads. It is awesome!! Thanks! [/B][/FONT][/COLOR]

---

### Post by LaRoza on 2008-02-03
> **UnixDream said:**
> [COLOR="Purple"][FONT="Book Antiqua"]I just popped over to the link you shared. I'll come back in after the super bowl :popcorn:to check out more of the language threads. It is awesome!! Thanks! [/B][/FONT][/COLOR]

I am going to bed. See you later :)

---

### Post by Ian-on-the-Trent on 2008-02-27
[SIZE="3"]**A sign of the future....?**[/SIZE]

***Situation: ****I have 5 boxes in my house; the newest is XP-based for my teenagers' gaming/multimedia/homework, my office 'puter is Ubuntu as is the heavily used kitchen laptop, I'm working on an Ubuntu LAMP server (slowly learning how to set one up), and my on-the-road laptop is XP (I unsuccessfully tried to install 3 different distros on it--an old but completely functional Acer Travelmate 213TE-  but then I needed Macromedia software installed so I reinstalled XP).*

**Observations: **I'm watching my 17 & 18 year old sons play BF2 on the gaming computer. While one is taking his turn the other is texting on his cell phone or running up to the kitchen to use "ugly" aMSN or doing something on Facebook.  Both are comfortable bouncing back and forth between either an XP or Ubuntu box. They also have experience on Macs.

In between rounds I ask them about the differences between the computers. I didn't frame my questions around "Linux" or "Windows", just about their experiences accessing the things they need to. These are a summary of their comments:

[INDENT]*Homework: *Doesn't really matter what computer they use. All of the home boxes use Firefox (with add-ons), Thunderbird, OpenOffice 2.2, and have access to chat.

*Playing Games:* There is no choice. BF2 kicks *** compared to steering penguins down a hill. Gotta have XP.

*Multimedia:* Both boys have i-PODS. XP is a must. Finding files is easier in Windows as well. (This could be the way I set up Windows though...each lad has his own partition. We all use a common login for gaming.) 

*Aesthetics: *98% of everything just looks a little better (or sometimes a lot) on our XP pc's. However, the entire family really likes the way Gnome uses larger thumbnails for movies and images on the desktop. [/INDENT]

***The future: ***They have heard other family and friends regulary curse Vista, "it is such a pig".  My kids also have a pretty good idea about my computing perspectives and know their dad-tweaked gaming computer, even though a budget box, is faster than their friends much newer Vista-based systems. So I asked them, if I gave you $1500 to buy yourself a good computer, what would you do? Their replies: [LIST=1]
[*]"Get a Mac...oh, can I play COD4 and BF2 on it?"
[*]Can't play games...then try to get a Windows box with XP. But then again, "Vista looks pretty cool."
[*]"Linux system? No thanks Dad...I'm not a computer geek. But if you want to build me one to do homework on..."
[/LIST]
[SIZE="2"][B]

My recommendation to Ubuntu and other distros: Pay close attention to today's tech-savvy kids.[/B][/SIZE]
[LIST=1]
[*]For desktop acceptance get games ported to Linux. CRITICAL!! (Do this very well and many kids will instantly make the switch *provided that...*
[*]...their i-Pods and brethen will work seamlessly on the Ubuntu box. And MSN looks good.
[*]Getting Ubuntu/Linux boxes into schools is HUGELY important. My kids have no issues at all using Ubuntu-based boxes for their school needs.[/LIST]

Neither son is headed into the IT world and neither will ever want to use a CLI in the foreseeable future. They are strictly plug'n play guys. *Therefore, a perfect GUI is a must.*

For what it's worth.
Ian.

---

### Post by skippi90 on 2008-02-27
I tend to use both, depending on what I need to do. The Terminal is pretty good for getting things done quickly if you know the commands you need.

---

### Post by eddVRS on 2008-07-07
I found when I was beginning with Ubuntu, that my friend already using the OS would show me both ways,  through the GUI, and also using CLI; but then he had the time to do this for me...

I think it important for beginners to learn that you can do things both ways, and both can have their own advantages. GUI can be more intuitive for beginners, but CLI can be (alot) quicker.

---

### Post by stwert on 2008-07-07
I am very new to Linux and have only done a very little bit of command line and terminal stuff. I am really happy to learn to use the terminal over GUI because, as I understand it, it is faster and gives more control to the user. However, using the GUI, it is much easier to see what is actually going on. A whole bunch of scrolling text is difficult to interpret for the beginner. Also, when people are providing help on forums and such, it seems as though most of the solutions are in the format "type this >whatever into the terminal", which is fine, except that I would prefer a bit more explanation as to what the components of the commands actually do. I can intuitively grasp some of the commands, but I find it helpful when people state explicitly what the meanings of the bits of text are.

---

### Post by bodhi.zazen on 2008-07-07
> **stwert said:**
> I am very new to Linux and have only done a very little bit of command line and terminal stuff. I am really happy to learn to use the terminal over GUI because, as I understand it, it is faster and gives more control to the user. However, using the GUI, it is much easier to see what is actually going on. A whole bunch of scrolling text is difficult to interpret for the beginner. Also, when people are providing help on forums and such, it seems as though most of the solutions are in the format "type this >whatever into the terminal", which is fine, except that I would prefer a bit more explanation as to what the components of the commands actually do. I can intuitively grasp some of the commands, but I find it helpful when people state explicitly what the meanings of the bits of text are.

If you have questions re: commands / code, just ask.

It is easier to enter commands then describe menus and mouse clicks :twisted:

Yes, gui tools are the way to go initially, over time as you learn the commands many people find the terminal very helpful.

See also :

	[http://www.unixguide.net/linux/linuxshortcuts.shtml](http://www.unixguide.net/linux/linuxshortcuts.shtml)
	[http://www.reallylinux.com/docs/admin.shtml](http://www.reallylinux.com/docs/admin.shtml)
	[http://www.reallylinux.com/docs/guru.shtml](http://www.reallylinux.com/docs/guru.shtml)
	[http://linuxcommand.org/](http://linuxcommand.org/)

---

### Post by ajmorris on 2008-07-07
> **bodhi.zazen said:**
> If you have questions re: commands / code, just ask.

It is easier to enter commands then describe menus and mouse clicks :twisted:

Yes, gui tools are the way to go initially, over time as you learn the commands many people find the terminal very helpful.

See also :

    [http://www.unixguide.net/linux/linuxshortcuts.shtml](http://www.unixguide.net/linux/linuxshortcuts.shtml)
    [http://www.reallylinux.com/docs/admin.shtml](http://www.reallylinux.com/docs/admin.shtml)
    [http://www.reallylinux.com/docs/guru.shtml](http://www.reallylinux.com/docs/guru.shtml)
    [http://linuxcommand.org/](http://linuxcommand.org/)

And if you dont mind a LOOONG read, you could see my tutorial:
[http://ubuntuforums.org/showthread.php?p=5272437](http://ubuntuforums.org/showthread.php?p=5272437)

---

### Post by aysiu on 2008-07-07
Never retype terminal commands. Paste them. Less room for error. Less work.

---

