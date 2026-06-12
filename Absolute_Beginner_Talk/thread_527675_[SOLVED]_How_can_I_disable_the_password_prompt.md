---
title: "[SOLVED] How can I disable the password prompt?"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by ScaredNoob on 2007-08-16
:Guys and Gals,

I absolutely hate the password prompt that comes up every time I want to get about with my 'bness'.  In the past I have disabled it editing the /etc/sudoers file, which worked great.  I can't remember how I did this, and when I search the forums I either get people trying to convince others not to do this or instructions I can't seem to follow.  Here's what I need:  Step by step, with no detail spared instructions on how to edit the sudoers file IN A TEXT EDITOR like kate or whatever the Gnome equivelent is.  I can only tolerate the terminel (Konsole) enough to open the sudoers file in Kate, editing this file is not going to happen for me within the command line.  A pirates chest of Karma to anyone who can help.  

P.S. The mass migration of Oodles of Windows users would be ensured if such instructions became common knowledge/stickied to the top of every Ubuntu Forum page.  Common users like myself do not work for the FBI or NASA, and I really don't care what consequences there might be for such an action, I only care enough about my privacy to NOT USE WINDOWS.  I want my girlfriend, her friends and anyone else physically on my computer to be able to connect to the internet, install new programs etc without my having to shout my password across the room.  Even worse is the waste of my valuable time in typing in my password 10,000 times per session when I know in my heart of hearts that nobody cares enough about me to somehow get into my computer.  Thanks and sorry I seem a bit agitated but this has been bugging me all the more because I was able to successfully edit the sudoers file in the past.

P.S.S.  sorry the subject title is a threat but I wanted to convey the desperation I'm feeling.

---

### Post by diatribe on 2007-08-16
there is a reason that you are prompted for a password, so people who are not knowledgeable about their system do not do something ignorant like remove their /bin directory or something like that. you should follow others advice and just type in the password when prompted

---

### Post by st33med on 2007-08-16
I think you have beebn told before, it is a great security risk. But, if you really want to, I won't stop you.

[http://ubuntucat.wordpress.com/2007/07/31/creating-a-passwordless-account-in-ubuntu/]("http://ubuntucat.wordpress.com/2007/07/31/creating-a-passwordless-account-in-ubuntu/")

---

### Post by ScaredNoob on 2007-08-16
Diatribe... I refuse!!!  I know enough not to do anything stupid like that, and anyways if I do I can always mount my ext3 hd in windows and get back anything I lost and then reinstall Ubuntu.

ps  I declare conspiratorial schenanigans on this topic.  Why are Ubuntu Forum users so anti editing the sudoers file.  Information should be open source as well as software.  Just tell me what I want to know and I promise I will help convert 10 windows users to Ubuntu.  If this is not enough, private message me and we can negotiate a deal.

St33med... you are more constructive, Step by Step, command line leading to graphical text editor, save and bam!  That or something I can copy and paste with a changed user name would also put a smile on my face.   Please help a brother out.

---

### Post by st33med on 2007-08-16
Alright, I will go one more, drastic step. Logging in as root.

```
sudo passwd root
```

That will enable root logins. It will not ask you for password. At anytime.

---

### Post by Shazaam on 2007-08-16
So you want to make Linux insecure just like Windows? Why? As for other users make them their OWN accounts. Can they tie shoelaces? They should be able to remember passwords. Since you are hell bent on destroying your Linux installation I have a few links for you....

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[http://www.pixelbeat.org/cmdline.html](http://www.pixelbeat.org/cmdline.html)
[http://www.linuxquestions.org/questions/index.php?](http://www.linuxquestions.org/questions/index.php?)

---

### Post by ScaredNoob on 2007-08-16
st33med... your number is also my favorite number from back in the day... for that I commend you.  However, your most recent post was out of context (think W5) and I don't know what to make of it.  I know there are a few fixes for disabling the dreaded password prompt... and your solution might be a nice one if I hadn't already configured auto login and a few other things that are specific to my user name.  I don't want to be Root at all times... I even like typing in sudo before doing important things in the command line.  What I despise is having to type the password in.  If I am being unreasonable, I will give you a few of my beans for your further help.  Thanks for guiding this stubborn old mule out to the pasture that is open source bliss.

Shazaam... If customizing my system the way I want it is in your eyes hellbent, then so be it.  I haven't given you're links a read yet but believe you me I will have a few quips for you when I'm done constructively reading them...

---

### Post by st33med on 2007-08-16
> **Shazaam said:**
> So you want to make Linux insecure just like Windows? Why? As for other users make them their OWN accounts. Can they tie shoelaces? They should be able to remember passwords. Since you are hell bent on destroying your Linux installation I have a few links for you....

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[http://www.pixelbeat.org/cmdline.html](http://www.pixelbeat.org/cmdline.html)
[http://www.linuxquestions.org/questions/index.php?](http://www.linuxquestions.org/questions/index.php?)

I think he doesn't want to be persuaded. He already has his mind set on doing this, and I would not suggest telling him otherwise.

If he wants to do this, it is his own decision, and he accepts the consequence.

---

### Post by Sye d'Burns on 2007-08-16
Might I suggest Vista? Even Microsoft is slowly coming to the conclusion that implied consent isn't a good way to manage a file system.

---

### Post by Paul133 on 2007-08-16
st33med, he's threatening us by saying he'll go back to Windows because he dislikes verification. Sure we can show him how to do it in Ubuntu, but he'd probably be happier in Windows, where he doesn;t have to adapt to the *nix way of doing things.

---

### Post by euler_fan on 2007-08-16
Usually it helps to be polite when asking people for help doing something which they disagree with.

IMHO you are lucky there is a community standard against the answers "RTFM" and "STFW".

As for the rest of us: Let's leave this thread be. It's flamebait. Further, let's let the OP suffer the consequences of their actions.

I'm flagging this thread for closure/deletion.

---

### Post by steveneddy on 2007-08-16
Windows users just want to point and click. He will go back to Windows soon enough.

---

### Post by st33med on 2007-08-16
> **Paul133 said:**
> st33med, he's threatening us by saying he'll go back to Windows because he dislikes verification. Sure we can show him how to do it in Ubuntu, but he'd probably be happier in Windows, where he doesn;t have to adapt to the *nix way of doing things.

That could be true, but let's let him explore Linux, see if he likes it. Just because he wants password prompts disabled doesn't mean he won't like it. There is other stuff in Linux that makes it better than Windows. Speed, for instance.

And, he already likes open source.

Oh, yeah, Vista has more annoying ways of verification. They pop-up when you just want to change your desktop.

---

### Post by vambo on 2007-08-16
You'll need your password to do that ;)

---

### Post by blithen on 2007-08-16
At least he lives up to his name. :)

---

### Post by SunnyRabbiera on 2007-08-16
the thing is that the passwords DO protect from installing things that can harm your OS.
Really though its not as bad as you think, Vista is FAR worse

do I want to make a reply to this topic, cancel or allow?

you are about to post on a forum, cancel or allow?

you are about to move your mouse, cancel or allow?

et cetra

---

### Post by ScaredNoob on 2007-08-16
Good Grief... I just got a message saying my post has been renamed.  Open Source doesn't translate to Freedom of Information and Freedom to post catchy subject titles I guess.  What a bunch of mularchy.  Anyways, I await anyones constructive response to this new, less catchy subject title with baited breath.  After that I will delete my user account and leave you guys all alone, since my frustration seems to be rubbing off on everyone.

---

### Post by Arthur Archnix on 2007-08-16
> **st33med said:**
> Alright, I will go one more, drastic step. Logging in as root.

```
sudo passwd root
```

That will enable root logins. It will not ask you for password. At anytime.

Now you're just being mean. :twisted:

---

### Post by ScaredNoob on 2007-08-16
P.S. this forum is corrupted by the same hierarchy that plagues society.  What gives someone with Super Bean powers the right to submit my post for deletion/rename it etc.  So what if I was baiting people's response.  That's the only way to get direct answers in this world is to make yourself stand out in the crowd.  Linus must be rolling over in his grave...

---

### Post by heimo on 2007-08-16
> **ScaredNoob said:**
> P.S. this forum is corrupted by the same hierarchy that plagues society.  What gives someone with Super Bean powers the right to submit my post for deletion/rename it etc.  So what if I was baiting people's response.  That's the only way to get direct answers in this world is to make yourself stand out in the crowd.  Linus must be rolling over in his grave...

Do you really feel that your trollish approach is helping you? Did you get your answer? No? Then do us a favor and leave already or start acting like a grown up.

---

### Post by ScaredNoob on 2007-08-16
I have only become trollish because, if my original post hadn't been modified, you guys would see that I had done this (edited the sudoers file in Kate) in the past and it is really really really really bugging me that I can't figure out how to do it again.  And why do I get called a troll everywhere I go on the net?  Can't a person be frustrated anymore?  Linux is not as easy to figure out as Windows, or maybe its me just getting more stubborn with age.  Anyways, I will be more respectful in the future, as I don't want the chocolate bean police out to get me anymore.  You guys need to come to the realization that not all Linux users (nor Ubuntu Forum posters) will be friendly or polite, but in order to progress your agenda of Open Source as a way of software living you need to deal with the trolls out there as well.  You know the Jesus quote about teaching a man to fish, well I'd teach anyone anything I knew about Ubuntu if, in my time of need, others were there to teach me.

---

### Post by Arthur Archnix on 2007-08-16
> **ScaredNoob said:**
> I have only become trollish because, if my original post hadn't been modified, you guys would see that I had done this (edited the sudoers file in Kate) in the past and it is really really really really bugging me that I can't figure out how to do it again.  And why do I get called a troll everywhere I go on the net?  Can't a person be frustrated anymore?  Linux is not as easy to figure out as Windows, or maybe its me just getting more stubborn with age.  Anyways, I will be more respectful in the future, as I don't want the chocolate bean police out to get me anymore.  You guys need to come to the realization that not all Linux users (nor Ubuntu Forum posters) will be friendly or polite, but in order to progress your agenda of Open Source as a way of software living you need to deal with the trolls out there as well.  You know the Jesus quote about teaching a man to fish, well I'd teach anyone anything I knew about Ubuntu if, in my time of need, others were there to teach me.

:-({|=

---

### Post by Shazaam on 2007-08-16
Chocolate Bean Police! lol.
Did you read my first link?

---

### Post by st33med on 2007-08-16
We can help, and we will help. But you need to be a bit more friendly. Please, don't threaten or flame. Criticizing makes it even worse.

---

### Post by ScaredNoob on 2007-08-16
st33med... you've got my back, and I appreciate that.  Should I log out and create a new user name so that I can leave all this baggage behind me?

---

### Post by SunnyRabbiera on 2007-08-16
well just calm down kay?
me i was joking with my reply so i hope you were not offended.

---

### Post by st33med on 2007-08-16
Maybe :)

---

### Post by ScaredNoob on 2007-08-16
I've actually had a bit of a grin on my face during this whole ordeal.  I was hoping to get views/responses so I could fix this issue before my clothes went out of style, but I guess some more forum digging might be needed on my part.  As for my first retort, the trollis maximus one, I edited out most of the troll parts and pondered by stroking my beard for awhile, so I hope that can get me some favorable beans or whatever.  This whole been thing.... well I better not go there...

---

### Post by Sye d'Burns on 2007-08-16
> **ScaredNoob said:**
> I have only become trollish because, if my original post hadn't been modified, you guys would see that I had done this (edited the sudoers file in Kate) in the past and it is really really really really bugging me that I can't figure out how to do it again. **And why do I get called a troll everywhere I go on the net?** Can't a person be frustrated anymore? Linux is not as easy to figure out as Windows, or maybe its me just getting more stubborn with age. Anyways, I will be more respectful in the future, as I don't want the chocolate bean police out to get me anymore. You guys need to come to the realization that not all Linux users (nor Ubuntu Forum posters) will be friendly or polite, but in order to progress your agenda of Open Source as a way of software living you need to deal with the trolls out there as well. You know the Jesus quote about teaching a man to fish, well I'd teach anyone anything I knew about Ubuntu if, in my time of need, others were there to teach me.
 
Man, it must be my slow night. I laughed so hard at that. :lolflag:

---

### Post by Paul133 on 2007-08-16
Scared, that might be a good idea. Sorry if my post came across as "RTFM". I just figured you'd be going back to Windows. It wasn;t because you wanted to get rid of the password prompt. That's a reasonable, if unwise, choice. But you were threatening to go back to Windows if we didn't help you. We are volunteers here. And threatening to go back to Windows is a way to get our attention, but not necessarily our help. I wrote you off because I figured you weren't really that interested in Ubuntu or Linux. Sorry. But in the future, please use a less-trollish/flamebaiting title.

---

### Post by ScaredNoob on 2007-08-16
As yall can see, I'm new to this whole posting thing and I didn't know the forum etiquette here.  In the multiplayer gaming community I hail from, anything goes and being a troll is often a way to create a likeable character everyone comes to love (as long as you reform yourself).  We'll see if the Ubuntu Forums community is that different a beast after all :)  I guess the only reason I became upset was that it seemed like all the posts I read before posting myself and then even my own post seemed to only get 'holier than thou' responses, as if I'm some 80 year old granny that is just learning what a mouse is.  I offically undeclare the schenanigans that I posted so very long ago.  I hope we can all move past our little tiff, and wish everyone taking their own precious time to read and reply to this as much Karma as the fattest person in the world weighs.

Ok, back to 'bness'.  Anyone got any ideas?   I'm up for anything that accomplishes my goal in full (even if it involves the dreaded terminel for more than copying and pasting).

---

### Post by steveneddy on 2007-08-16
shrew

---

### Post by st33med on 2007-08-16
Nothing here.

---

### Post by steveneddy on 2007-08-16
> **st33med said:**
> :x Not nice.At all.

Don't care. He's in my inbox. Put it on the forums if you need to tell me something. Stay out of my inbox. I didn't tell him to IM me. 

I'll change the post.

---

### Post by ScaredNoob on 2007-08-16
Geez Neddy even coming from a reformed troll I consider that a bit harsh.  I like Linux the way I like it, and maybe someday my modifications will find their way to the kernel or something.  I have the utmost respect for you, because you cared enough to write and because you pull rank on me with your 10 inch bean pole.  Teach me everything you know and then we can create a world where people who like linux the way it is can wallow in LiveCD bliss and users like me can change the heck out of every last thing to our liking.

---

### Post by ScaredNoob on 2007-08-16
Again, Neddy, I didn't know the forum etiquette here and was only messaging you in case you chose to leave my life forever and never look at the awesome convo we got going here.

---

### Post by Bachstelze on 2007-08-16
Okay, everyone please calm down. ScaredNoob asked a question, though not in a very pleasant way indeed, so let's try to answer it.

ScaredNoob, all you need to do if you want sudo not to ever ask for your password anymore is add a NOPASSWD statement in your sudoers file. However, please, please, *please* edit the file from the command line using the command *sudo visudo*. This is not to annoy you or because the terminal is so much more |33t, it is for a *reason*. The reason is that *visudo* will check your sudoers file for syntax errors before saving it and, if errors are found, will refuse to save it. This is *very* important because if you do one syntax error in the file, you will not be able to use *sudo* anymore. And *please* don't tell me "I'm not that stupid !", *everyone* can make a typing mistake.

So just open up your terminal, type *sudo visudo*, go to the line that starts with %admin and add NOPASSWD: before the last ALL, like this :

```
%admin   ALL=(ALL) NOPASSWD: ALL
```

then save the file (Ctrl+O, Enter to confirm) and exit nano (Ctrl+X), you're there :)

---

### Post by ScaredNoob on 2007-08-17
Sorry If I seem like a dummy for needing to post again after that succinct, calm and constructive response but I am still having issues.  Under this post is a pasted version of what I'm looking at here in the sudo visudo.  Do I add ALL=(ALL) NOPASSWD: ALL after: # Members of the admin group may gain root privileges or in the root part, and also do I need to uncomment that part afterwards?  Thanks again.

GNU nano 2.0.2            File: /etc/sudoers.tmp                    Modified

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
                               [ Read 20 lines ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell

---

### Post by Bachstelze on 2007-08-17
Scroll down a bit, you will see the "%admin" line.

---

### Post by ScaredNoob on 2007-08-17
whoops sorry I didnt realize that I could scroll down to find that admin part you were talking about... Well I feel like a fool now, but thanks again for the help and thanks to everyone else that helped or tried to.  You've all restored my faith in this wonderful thing we call Linux.  Should I put a (Solved) thing in the subject line now?  It seems that's the hip thing to do around here but I'm not sure and I don't want to step on anybody's toes.

---

### Post by Bachstelze on 2007-08-17
> **ScaredNoob said:**
>  Should I put a (Solved) thing in the subject line now?

Done :)

---

### Post by ScaredNoob on 2007-08-17
HymnToLife I can't thank you enough, I can only hope that this series of posts demonstrates to new Ubuntu Forum users that the Golden Rule should always be applied and that even though some people are stubborn and misguided in their quest to have things their way, sometimes they need to find things out for themselves.  I'll end on one of my favorite quotes:

"Good Judgment is Learned through Experience;  Experience is Learned through Bad Judgment"

---

### Post by bodhi.zazen on 2007-08-17
+1 HymnToLife , you stole my thunder (I had to scroll through several pases to see if the OP question had been answered)

ScaredNoob : You are welcome in the Ubuntu forums, it seems you struck a nerve with some here though. You are free to sys admin the way you please.

If you are still open to a piece of advice, use these ticks :

```
sudo -i
```

That will ask you password, but then you will be logged in as root and away you go. this offers both convenience and security ....

Or,: ```
gksu nautilus
```

This also asks a password and opens nautilus as root.

====

To the others : This is not a huge security hole, just a small one. Don't forget physical access is bad news, how may of you have disabled booting to recovery mode ? 

Heh, see, physical access = root access , no password needed.

---

### Post by Arthur Archnix on 2007-08-17
Ha! Not only have I disabled recovery mode, I've also taped my passwords to the BACK of my monitor.

Check and Mate.

8)

---

### Post by bodhi.zazen on 2007-08-17
> **Arthur Archnix said:**
> Ha! Not only have I disabled recovery mode, I've also taped my passwords to the BACK of my monitor.

Check and Mate.

8)

hahahahahahaha ....

NICE

BUT not quite ... That setup is still easily cracked by a number of techniques 

he he he ... don't make me flash your BIOS :twisted:

soooo close though

You need to encrypt / :guitar:

---

### Post by Wharf Rat on 2007-08-17
I would like to set up Ubuntu to load a default user account -- WITHOUT a password.  Is this possible?   I have a Ubuntu machine set up in the office for public use, internet browsing, etc.

The Windows machine gets trashed all the time.  I was hoping Ubuntu would work better.

No SUDO available to the casual user. :)

---

### Post by bodhi.zazen on 2007-08-17
Yea, that is a snap :

Edit: Even easier 

Go to System -> Administration -> Login Window

Under the security tab select auto login and user name

You might also want to enable timed login with the same name (otherwise this works only at boot or with restarting gdm)

---

### Post by Wharf Rat on 2007-08-17
bodhi.zazen,
Thank you very much.

---

