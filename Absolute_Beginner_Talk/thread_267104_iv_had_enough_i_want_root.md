---
title: "iv had enough i want root"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by uk_sphinx on 2006-09-28
right before i ask for an answer please dont bother telling me its dangerous coz im sick to my back teeth of not being able to do anything like delete files by right clicking.

can someone give me the code to make my account the super user please
i dont want the sudo -i command coz thats rubbish

i know the conciquences and i dont care if i have to install from scratch coz i cant even install a download thats on my desktop.

root root root

](*,) sooooooo frustrated](*,) 

p.s do any of the symantec progs work?
i installed flash player from there but i cant get a movie on the go.

---

### Post by wieman01 on 2006-09-28
That's it:

[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by bluefrog on 2006-09-28
if you don't have the right to delete files by right clicking it means you shouldn't delete them.

For all the rest you have sudo.

If you are not able to enable root access to gdm on your own you definitely have to stay away from root login.

James

---

### Post by uk_sphinx on 2006-09-28
what i shouldnt be allowed to delete a file I downloaded to the desktop?
sounds peculiur to me!

---

### Post by Kilz on 2006-09-28
> **uk_sphinx said:**
> right before i ask for an answer please dont bother telling me its dangerous coz im sick to my back teeth of not being able to do anything like delete files by right clicking.

can someone give me the code to make my account the super user please
i dont want the sudo -i command coz thats rubbish

i know the conciquences and i dont care if i have to install from scratch coz i cant even install a download thats on my desktop.

root root root

](*,) sooooooo frustrated](*,) 

p.s do any of the symantec progs work?
i installed flash player from there but i cant get a movie on the go.


So its rubbish to use the cli and you want windows antivirus programs to work? Before enabeling root try 
```
gksudo nautilus
```
This will launch the nautilus file manager as an admin. You will be able to click and delete, drag and drop files, and change file permissions in a gui.
Second Antivirus (symantec is antivirus maker)on Ubuntu or any linux is a total waste of time and money. Dont even bother. Some people who come over from windows cant get over the fact that viruses are a windows thing. But a few months into it learn that its not needed, Save your cash.

---

### Post by wieman01 on 2006-09-28
> **bluefrog said:**
> if you don't have the right to delete files by right clicking it means you shouldn't delete them.

For all the rest you have sudo.

If you are not able to enable root access to gdm on your own you definitely have to stay away from root login.

James
For a new installation this is questionable because there is little risk, but I have to agree... Linux is secure because of this concept. So you need a bit of process discipline to get used to it, but once you know what you can do and what you cannot with your normal user, Linux is just beautiful. I would never log on to the system as root anymore, but I certainly did in the beginning...

---

### Post by uk_sphinx on 2006-09-28
> If you are not able to enable root access to gdm on your own you definitely have to stay away from root login. 

if you cant read what people write in there posts then you shouldnt reply to them just to get a few more poxy beans!
i told you not to reply!

i think i can tell the difference between somthing i know about and somthing i dont.
if i am 100% sure i downloaded it i'e music etc il delete the hell out of it to my hearts content.
if i dont recognize the file il steer clear!
???hows that then???

---

### Post by Kilz on 2006-09-28
> **uk_sphinx said:**
> if you cant read what people write in there posts then you shouldnt reply to them just to get a few more poxy beans!
i told you not to reply!

i think i can tell the difference between somthing i know about and somthing i dont.
if i am 100% sure i downloaded it i'e music etc il delete the hell out of it to my hearts content.
if i dont recognize the file il steer clear!
???hows that then???

Im sure your going to get lots of help on the forums with that attitude. ](*,)

---

### Post by uk_sphinx on 2006-09-28
get you now.....

synaptic. i meant. or were you being clever?
i was hammering the keys with frustration.

---

### Post by wieman01 on 2006-09-28
Hey Guys, just calm down a bit. I know this is a hot topic and I have seen this kind of conversation a million times... Root is bad, but each of us has to decide whether it's a good or a bad thing. 

Just leave it, ok? Lecturing won't get us anywhere. We're are team, a community of like-minded people. Don't forget that.

---

### Post by uk_sphinx on 2006-09-28
>  If you are not able to enable root access to gdm on your own you definitely have to stay away from root login.  

dont like your attitude of telling me what i am and aint capable of doing when i specifically said i didnt care for your opinion.

---

### Post by uk_sphinx on 2006-09-28
i was too harshe

soz people i was in frustration

im going to get a bucket of coffee and chill out

soz again

---

### Post by Kilz on 2006-09-28
> **wieman01 said:**
> Hey Guys, just calm down a bit. I know this is a hot topic and I have seen this kind of conversation a million times... Root is bad, but each of us has to decide whether it's a good or a bad thing. 

Just leave it, ok? Lecturing won't get us anywhere. We're are team, a community of like-minded people. Don't forget that.

Like minded people try to find out why the person wants root and suggests ways of doing the needed thing.  Without automaticly linking to the instructions to enable root.

---

### Post by wieman01 on 2006-09-28
> **Kilz said:**
> Like minded people try to find out why the person wants root and suggests ways of doing the needed thing.  Without automaticly linking to the instructions to enable root.
Question of interpretation... I have my views, you have your own.

---

### Post by kvonb on 2006-09-28
I know exactly how you feel uk_sphinx, I've been there myself and it can be a real pain in the arse!

Here is a link to everything you will need:

[http://ubuntuguide.org/wiki/Dapper#User_Administration](http://ubuntuguide.org/wiki/Dapper#User_Administration)

Look down the page, it also has instructions on how to enable root login for X (Gnome etc').

The one thing that got me hooked on Ubuntu was the way that people gave help without giving a lecture, belittling you, or giving useless replies like RTFM.

It seems like the good old days are slowly vanishing!  sigh.

Regards,

Kev :)

---

### Post by xpod on 2006-09-28
> if you cant read what people write in there posts then you shouldnt reply to them just to get a few more poxy beans!
i told you not to reply!

> get you now....

Get WHO??????????????????????????

Sorry my friend(?) but you needs to take a step back and take some deep breaths..
New too and i got more posts than most at this point and i NEVER just reply simply to "get beans"

These guys are giving you good advice and in a bit of time when you have got more of a feel for the thing you TOOOO will realise how much sense their making.

This is by far the most friendly helpful place you could possibly be with your problems but you wont get much assistance if you snap at the guy`s like that..

I am usually constantly frustrated at some aspect of not just Ubu but computers in general but think how good you`ll feel when realistation eventually dawns on you:mrgreen: ..
It`s only a computer mate.......sorry for the rant myself....BUT

The daft jock

---

### Post by Kilz on 2006-09-28
> **kvonb said:**
> I know exactly how you feel uk_sphinx, I've been there myself and it can be a real pain in the arse!

Here is a link to everything you will need:

[http://ubuntuguide.org/wiki/Dapper#User_Administration](http://ubuntuguide.org/wiki/Dapper#User_Administration)

Look down the page, it also has instructions on how to enable root login for X (Gnome etc').

The one thing that got me hooked on Ubuntu was the way that people gave help without giving a lecture, belittling you, or giving useless replies like RTFM.

It seems like the good old days are slowly vanishing!  sigh.

Regards,

Kev :)

Telling people how to enable the root login without finding out why they need it is a security risk. If you ask them most of the time its because they want a gui to move files around.
Enabling the root account is a security risk. Telling the person dangerous information at first to solve a simple problem isn't being nice . Its being irresponsible. No one was belittled, told to read the manual, etc. But suggesting the safest way to accomplish something is something everyone should do.

---

### Post by wieman01 on 2006-09-28
> **xpod said:**
> Get WHO??????????????????????????

Sorry my friend(?) but you needs to take a step back and take some deep breaths..
New too and i got more posts than most at this point and i NEVER just reply simply to "get beans"

These guys are giving you good advice and in a bit of time when you have got more of a feel for the thing you TOOOO will realise how much sense their making.

This is by far the most friendly helpful place you could possibly be with your problems but you wont get much assistance if you snap at the guy`s like that..

I am usually constantly frustrated at some aspect of not just Ubu but computers in general but think how good you`ll feel when realistation eventually dawns on you:mrgreen: ..
It`s only a computer mate.......sorry for the rant myself....BUT

The daft jock
xpod, you've got a point, ok? But don't forget it's mutual. I can understand both sides (having been on both side at some point) and that tells me that beginners are very often given the impression that they are looked down up - if you know what I mean. I am not an expert either (althout I used to be a software developer), perhaps because of this I understand that being lectured is a painful experience. 

And you can write in one way or the opposite way... Sometimes people tend to forget that they used to be where uk_sphinx is right now. That's all.

So again, it's mutual.

---

### Post by wieman01 on 2006-09-28
> **Kilz said:**
> Telling people how to enable the root login without finding out why they need it is a security risk. If you ask them most of the time its because they want a gui to move files around.
Enabling the root account is a security risk. Telling the person dangerous information at first to solve a simple problem isn't being nice . Its being irresponsible. No one was belittled, told to read the manual, etc. But suggesting the safest way to accomplish something is something everyone should do.
I agree here. But look at the original post. I think the guy has been through all this. But again, you have a point. Just finding the right way to "wrap" the message is equally important.

---

### Post by orb9220 on 2006-09-28
To get over my frustation of sudo was learn how to use it.

I did this by dragging home to a panel to create shortcut there. And then I changed command to gksudo -g nautilus so I could copy,delete,rename,etc... But you have to be careful of not deleting anything in the filesystem area.
Note: the -g option tells it not to darken the screen on password prompt.

For the terminal I just use sudo or gksudo for graphic apps. The only annoying thing I had to get use to is entering my password everytime I  need sudo but I got use to it.

The reason for this way instead of running an account is you open your whole system up to attacks,corruption of files,and unrecoverable errors that could cause you to have to do a reinstall.

Take my suggestion for creating a shortcut to nautilus that has sudo automatically everytime you click on it and will save you gobs of frustration. This will leave your system in a safer state than having a wide open system.

Hope this helps and others don't consider my suggestion to drastic. But I really did get frustrated with the standard nautilus trying to get things done.

---

### Post by Kilz on 2006-09-28
> **wieman01 said:**
> I agree here. But look at the original post. I think the guy has been through all this. But again, you have a point. Just finding the right way to "wrap" the message is equally important.

For some strange reason the gksudo nautilus command isn't easy to find. It should solve 90% of the reasons why someone wants to log in as root.
Some have said I come off as blunt. Sorry if it looks that way, it isn't intended. :D

---

### Post by uk_sphinx on 2006-09-28
i meant i got what killz was meaning by installing xp antivirus
i mispelt synaptic and referred to the antivirus corporation for windows
guess it wasnt thought out sooo well.

just had a quick browse through the info
is the reason i cant delete things by right clickng and the cli(i have tryed both) because the file system is read only?
i was using sudo -i
to change from user to root and it always wouldnt let me delete or do anything.
i was just trying to install a flash plugin for firefox.
i downloaded it my self so it aint important to delete(especialy if i cant install it)
its like the extraction tool.
when i opened that plugin and tryed to install it to / bang  access denied.
but it would let me extract the contents to desktop though.
but once they are on desktop it wont let me delete it.

---

### Post by uk_sphinx on 2006-09-28
what a differance a little coffee can do to my attitude problem

---

### Post by kvonb on 2006-09-28
Quote:

```
right before i ask for an answer please dont bother telling me its dangerous coz im sick to my back teeth of not being able to do anything like delete files by right clicking.

can someone give me the code to make my account the super user please
i dont want the sudo -i command coz thats rubbish

i know the conciquences and i dont care if i have to install from scratch coz i cant even install a download thats on my desktop.
```

This is the original post, if you read it uk_sphinx asks for instructions, not advice or lectures Kilz - with respect. 

If you go into a hardware shop to buy nails, would you be happy if the salesperson refused to sell you nails but instead proceeds to tell you that you should be using screws instead?

I've seen another person ask for root on this forum, and they said that they could handle it.  The same person later posted that they damaged their setup and had to re-install it!  However they were "man" enough to admit that they were wrong, but learnt from the experience.

---

### Post by Kilz on 2006-09-28
> **orb9220 said:**
> To get over my frustation of sudo was learn how to use it.

I did this by dragging home to a panel to create shortcut there. And then I changed command to gksudo -g nautilus so I could copy,delete,rename,etc... But you have to be careful of not deleting anything in the filesystem area.
Note: the -g option tells it not to darken the screen on password prompt.

For the terminal I just use sudo or gksudo for graphic apps. The only annoying thing I had to get use to is entering my password everytime I  need sudo but I got use to it.

The reason for this way instead of running an account is you open your whole system up to attacks,corruption of files,and unrecoverable errors that could cause you to have to do a reinstall.

Take my suggestion for creating a shortcut to nautilus that has sudo automatically everytime you click on it and will save you gobs of frustration. This will leave your system in a safer state than having a wide open system.

Hope this helps and others don't consider my suggestion to drastic. But I really did get frustrated with the standard nautilus trying to get things done.
A very good suggestion, and one I have done myself. The gksudo nautilus shortcut should be standerd on Ubuntu installs.

---

### Post by wieman01 on 2006-09-28
> **orb9220 said:**
> Hope this helps and others don't consider my suggestion to drastic. But I really did get frustrated with the standard nautilus trying to get things done.
Nope, man. That's a good suggestion indeed. I am doing the same thing and I have to admit that's the best option there is. Wish Gnome/KDE simply furnished they file-browser with "sudo" button as has been suggested by other forum members. Good call!

---

### Post by wieman01 on 2006-09-28
> **wieman01 said:**
> Nope, man. That's a good suggestion indeed. I am doing the same thing and I have to admit that's the best option there is. Wish Gnome/KDE simply furnished they file-browser with "sudo" button as has been suggested by other forum members. Good call!
;-) You kill me, mate. Had a good laugh just now. Reckon we're on the same page.

---

### Post by xpod on 2006-09-28
> xpod, you've got a point, ok? But don't forget it's mutual. I can understand both sides (having been on both side at some point) and that tells me that beginners are very often given the impression that they are looked down up - if you know what I mean. I am not an expert either (althout I used to be a software developer), perhaps because of this I understand that being lectured is a painful experience.


I know more than most THAT sense of exasperation one can sometimes feel comming from the opposite end mate.
Im afraid to even post a new thread now because it`s assumed that i SHOULD by now how to do all the basics and at least figure it out myself....(yeah i make up for it with the "post" count but never just fro stupid beans)

Im still comming to terms with a "computer" never mind the OS that`s now on it.
I used to be afraid to reply with a "what" when some pro or psuedo-pro handed out some list of commands and i did`nt even know wether to hit "enter" after each.Telliing the pro my "sfc \scannow kept asking for "lol`s and an xp cd rom to get them from was my best one mate...(dll`s!!)

Sometimes you just need to step back a bit and rethink your approach...
Getting angry with those who are helping you aint going to work eh:D 
 And if and when you KNOW the pro is being a bit uppity with his superior knowlage then you just need to make allowances for THEIR  failings and look to other posts.....plenty of them:D 

Sorry again for my rant(if anyone see`s it as such??)
Just chill out mate and take on board what the "good guy`s" are trying to help you with.....And IF you still want to be "sudoless" then im sure it will be easy enough...

Good luck and again i apoligise for even butting in:mrgreen:

---

### Post by Kilz on 2006-09-28
> **kvonb said:**
> Quote:

```
right before i ask for an answer please dont bother telling me its dangerous coz im sick to my back teeth of not being able to do anything like delete files by right clicking.

can someone give me the code to make my account the super user please
i dont want the sudo -i command coz thats rubbish

i know the conciquences and i dont care if i have to install from scratch coz i cant even install a download thats on my desktop.
```

This is the original post, if you read it uk_sphinx asks for instructions, not advice or lectures Kilz - with respect. 

If you go into a hardware shop to buy nails, would you be happy if the salesperson refused to sell you nails but instead proceeds to tell you that you should be using screws instead?

I've seen another person ask for root on this forum, and they said that they could handle it.  The same person later posted that they damaged their setup and had to re-install it!  However they were "man" enough to admit that they were wrong, but learnt from the experience.


No I wouldn't , if the clerk says, " what job are you using the nails on? I say " to nail down the decking on my new front porch" The clerk then says " Use these screws they wont come up and will make the surface safer."
Safety should be a concern when answering questions in the beginners section IMHO. Because the person asking may not know the end results of the actions they want to do. I always try to  suggest the safest way first.

---

### Post by yaye on 2006-09-28
To learn how to enable the root account and use it in Graphics mode, see this post:

[http://www.ubuntuforums.org/showpost.php?p=154845&postcount=1](http://www.ubuntuforums.org/showpost.php?p=154845&postcount=1)

Use it responsibly. Login as root, do your administrative work, then log off.

---

### Post by uk_sphinx on 2006-09-28
cheers everyone

***its been emotional***

---

### Post by steve.horsley on 2006-09-28
> Im afraid to even post a new thread now because it`s assumed that i SHOULD by now how to do all the basics and at least figure it out myself
Hell, if you knew how long I've been tinkering with Linux you would be utterly disgusted at some of the questions I still ask!

**uk_sphinx**:
Can I suggest that if you ever login to the GUI as root, you set the desktop bright red as a reminder? Mandrake used to do that - good idea, I thought. I set the background of root's nautilus red too, as a reminder for when I use gksudo nautilus.

---

### Post by Angry on 2006-09-28
> **uk_sphinx said:**
> what i shouldnt be allowed to delete a file I downloaded to the desktop?
sounds peculiur to me!

I don't think the "log in as root" is the real issue here.  Correct me if I'm wrong, but it sounds like, for whatever reason, he cannot rename, delete, etc files that are on his own desktop, which he should have full permissions to do so.

I know for myself, if I put something in my home folder, its mine to do with as I please.  For uk_sphinx, it sounds like this is not the case, its not like he wants to delete the X11 folder or something, just a file that he, by rights, has full access to.

My 2 cents.

---

### Post by shriphani on 2006-09-28
you cant delete something on your desktop? elaborate more on your intentions.

---

### Post by uk_sphinx on 2006-09-28
thank you angry!

got it in one!

thats my exact problem.
i think after a little tinkering that i cant modify the file due to my perrmission on the actual filesystem.
i am only allowed to read, not write or remove.
thats according to what it says in the permissions tab when i right click the file system folder and go to properties.
but if this is the case, then how did i manage to download the file in question and "write" it to the desktop?
desktop is located in the file system in home user right?
anyway to the point, i "dont have permission" to change the read write remove permission in propertys.
after all that was said in this about me wanting root, i am now against it.
since reading an article about how if your logged in as root a hacker has complete access to your system. !! im paranoid about security!!
so its back to square one for me.

p.s after everyone stateing there well thought out opinions on the subject i just wanted someone like angry to say, "yes , i think i know what your problem is , here let me explain what code to use and what the code actually does in detail, because i know your a compleate noob end!"

its all good saying here use "gksudo -g -i - whatever but i need more explanation to get that code understood and stuck in my mind.

---

### Post by uk_sphinx on 2006-09-28
>    you cant delete something on your desktop? elaborate more on your intentions.  


how much more do i have to elaborate to explain that i have downloaded a file and i dont want it anymore?
the dammn things padlocked and i cant remove it.
from the tutorials i have read i got the impression that a user that created a file had full permission to delete it.

dont worry about the download its not inportant in the matter.
the sooner you lot understand this the better!

---

### Post by uk_sphinx on 2006-09-28
also,
i think we have enough people involved in this thread now.
please can no-one else place there opinions down as its gonna get complicated.

---

### Post by xpod on 2006-09-28
> Hell, if you knew how long I've been tinkering with Linux you would be utterly disgusted at some of the questions I still ask!

I could never be disgusted at any stupid question anyone asks mate....Just a bit bemused with "how" some end up asking when it might be getting the better of them....."your os ruined my hd"..rant rant rant...LOL
(not you sphinx...;) )

I get annoyed at myself quite often  but when you got 3 or 4 wee girls laughing at your frustrations you can but laugh too](*,) :D 

Im still totally confused about all the file permissions and stuff too so thats why im hanging around:mrgreen:

---

### Post by Brunellus on 2006-09-28
> **uk_sphinx said:**
> also,
i think we have enough people involved in this thread now.
please can no-one else place there opinions down as its gonna get complicated.
I'll be the judge of that.  

[RootSudo](http://wiki.ubuntu.com/RootSudo) tells you all you need to know about permissions.  Ignore good user/permissions practice at your peril.  Once you are root, everything is trivially easy, up to and including totally hosing your install and even rendering the whole machine unbootable.  If you don't know what you're doing...you should think twice about root.

For general installation help, please consult [InstallingSoftware](http://wiki.ubuntu.com/InstallingSoftware)

Please keep conversations civil, technical, and on-topic.

---

### Post by uk_sphinx on 2006-09-28
look brunnelus

did you think that post was going to help.
did you pay any attention to the argument that started because of people stating unwanted opinions?
go and have a look at what i put in my first post and the argument that ensued.

your suppsed to be a furum staff and your not helping my problem by posting points that have already been iliterated by other members.
go and have a read of what has been posted.

dont you think i understand the risks involved by the large debate on the subject?

why dont you try and help the problem and not specify risks to me that im already aware of.

i only put that comment about people not joining for the simple fact that people keep joining the thread and convering up my answer by getting involved in in other issues.

i think you just dont like me trying to put a little control on this thread  which i think has gotten out of hand in places.do you want to be the sole enforcer of the rulez?
go ahead, but dont complicate this matter further.

---

### Post by charles.g.moore on 2006-09-28
Dude what is your problem???

Go take a valium and come back later...

---

### Post by uk_sphinx on 2006-09-28
look i know it sounds harsh and all that but,
people should read the posts more.
re-entering allready stated answers buggs me

---

### Post by uk_sphinx on 2006-09-28
plus theres the fact that youve come to this thread that your not involved in and put down a statement of topic and insulting.
go to yahoo chat

---

### Post by Brunellus on 2006-09-28
> **uk_sphinx said:**
> look i know it sounds harsh and all that but,
people should read the posts more.
re-entering allready stated answers buggs me
If all the technical issues raised in this thread have been answered in previous posts, then I think this thread has served its purpose.  

This thread has degenerated into unwarranted abuse.  uk_sphinx:  please understand that you are posting in a public forum.  If you want to exclude users, please use the 'ignore this user' function.  Attempts to bully people are not welcome.

Thread closed.

---

### Post by charles.g.moore on 2006-09-28
If you want only what you ask for and no helpful suggestions then you should go to microsoft.com and purchase a long-term tech support plan, if you want free help then ask, listen (no matter how many times), and be nice...

---

