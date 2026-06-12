---
title: "Linux Fast boot..free up disk space"
date: 2011-08-19
forum: Any Other OS
---

### Post by donut123 on 2011-08-19
I have this Linux fastboot in hyper terminal
The drives a re full..
I need to free up some space.
It runs off sd card..single board.
I have the reading

I know there is  a list there..
I looked at some..I didnt find anything
Here is the readout 		[>[IMG]http://www.ultimateeditionoz.com/forum/download/file.php?id=8346&t=1[/IMG]]("http://www.ultimateeditionoz.com/forum/download/file.php?id=8346&mode=view") 		



How do I free up space in the terminal commands?

---

### Post by Basher101 on 2011-08-19
why dont you try first removing unneeded packages from synaptics? or do it with a command ```
sudo apt-get autoremove
```

---

### Post by donut123 on 2011-08-19
> **Basher101 said:**
> why dont you try first removing unneeded packages from synaptics? or do it with a command ```
sudo apt-get autoremove
```

Well I would have did that..only there is no synaptic...there is only command line...I would have and not asked it..didnt you read my post?


and this is Debian based..ther is no sudo on here it dosent go by that. This is new to me..I have Linux..and this is all command line..there is no GUI


[B][URL="http://www.youtube.com/artist/Gregory_Isaacs?feature=watch_video_title"]
[/URL] [/B]

---

### Post by Basher101 on 2011-08-19
Ubuntu is debian based so it should work. Synaptic is your package manager so the command should also work. Just open a terminal, copy and paste the command there and enter your password if necessary.

---

### Post by donut123 on 2011-08-19
> **Basher101 said:**
> Ubuntu is debian based so it should work. Synaptic is your package manager so the command should also work. Just open a terminal, copy and paste the command there and enter your password if necessary.
yes I know cant you just tell me how to do it?
well sorry..I am working remotely...and its through the hyper terminal in windows..I m not familiar with this type of proceddure... I want my GUI back !
This is my new job..and Im stuck..sheeeeeesh
annd I thought Ubuntu is Debian based ?

---

### Post by donut123 on 2011-08-19
Sorry it dosent work the way you said..the problem is you dont kn ow whats going on here..its  a thumb drive..single board..runs from Debian fastboot..this is not  a usual thing..sudo does not work..i tried it time and time again.

this here is what Im working with
 [http://www.embeddedarm.com/products/board-detail.php?product=TS-7553](http://www.embeddedarm.com/products/board-detail.php?product=TS-7553)

---

### Post by kiyop on 2011-08-20
In debian, as defalut, usual user prepared at installation is not involved in group "sudo", thus as the usual user, "sudo" is not valid.
Use "su" or "sux" instead, or 
```
# vigr
```and add the usual user into sudo group to enable "sudo", which I do not prefer.

---

### Post by Duncan Williams on 2011-08-20
Also if you can work out and have enough room to install:
bleachbit
I ran it the other day and it deleted nearly 1-gig of not needed stuff.  I use it about twice a week.
It's in repositories and can be installed and ran from terminal.
more info:
[http://bleachbit.sourceforge.net/](http://bleachbit.sourceforge.net/)

---

### Post by donut123 on 2011-08-20
As I said  when I first started this
..this is not   a normal default Debian..its Linux fastboot with Debbian..
It dosent do anything anyone has shown me..I have alll kind
of codes that read things..but to fix some thing..it dosent work
There is no bleached there is no file manger. ther is no 
synaptic,
there is no autoclen,,
theres nothing, except fdisk..thats all
thank  witht the vgr..it did nothing..i dont know what that is..but on this Linux fastboot it means nothing
thank you

---

### Post by kiyop on 2011-08-20
> **donut123 said:**
> As I said  when I first started this
..this is not   a normal default Debian..its Linux fastboot with Debbian..
It dosent do anything anyone has shown me..I have alll kind
of codes that read things..but to fix some thing..it dosent work
There is no bleached there is no file manger. ther is no 
synaptic,
there is no autoclen,,
theres nothing, except fdisk..thats all
thank  witht the vgr..it did nothing..i dont know what that is..but on this Linux fastboot it means nothing
thank you
There are many typo.
For example, 
(typo) -> (correct)
vgr -> vigr
autoclen -> autoclean

Was there any typo when you executed the commands suggested?

---

### Post by donut123 on 2011-08-20
> **kiyop said:**
> There are many typo.
For example, 
(typo) -> (correct)
vgr -> vigr
autoclen -> autoclean

Was there any typo when you executed the commands suggested?

typos ..no I copy and paste..it goes the same way it is there

---

### Post by kiyop on 2011-08-21
Why are you doing "multipost"?
[http://forums.debian.net/viewtopic.php?f=17&t=68708&p=389656#p389656](http://forums.debian.net/viewtopic.php?f=17&t=68708&p=389656#p389656)

---

### Post by donut123 on 2011-08-21
> **kiyop said:**
> Why are you doing "multipost"?
[http://forums.debian.net/viewtopic.php?f=17&t=68708&p=389656#p389656](http://forums.debian.net/viewtopic.php?f=17&t=68708&p=389656#p389656)
Multi posts? because multi is better than one? LOL
and in  a situation I want as many answers as I can get. It is Debian the box is running.
Woudnt you do the same? And I have more posts than that.you just havent seen them.
 I cannot post where they are on here, its tweaked version sites.
But I can tell you I treid to register on the Debian Administrators site..It was enter your user
 name, email..and thats it, and then they didnt send  a password. I emailed and asked where 
is the password and why is it there is no reister form..the dude sent back an email saying they have 
banned my IP address..and when I sent  a reply they had blocked me.So dont ever go on there,
I dont think ists safe.

---

### Post by kiyop on 2011-08-22
I am not pleasant to read the following.
> **donut123 said:**
> Multi posts? because multi is better than one? LOL
and in  a situation I want as many answers as I can get. It is Debian the box is running.
Woudnt you do the same? And I have more posts than that.you just havent seen them.
 I cannot post where they are on here, its tweaked version sites.
But I can tell you I treid to register on the Debian Administrators site..It was enter your user
 name, email..and thats it, and then they didnt send  a password. I emailed and asked where 
is the password and why is it there is no reister form..the dude sent back an email saying they have 
banned my IP address..and when I sent  a reply they had blocked me.So dont ever go on there,
I dont think ists safe.

---

### Post by donut123 on 2011-08-23
> **kiyop said:**
> I am not pleasant to read the following.
you know I really Love you buddy.Why are you concerned about my posting and you dont help me out.?
Whats the problem? dont like me? you dont know me..but I still Love you son.:(

---

### Post by donut123 on 2011-08-23
> **kiyop said:**
> there are many typo.
For example, 
(typo) -> (correct)
vgr -> vigr
autoclen -> autoclean

was there any typo when you executed the commands suggested?Dont worry about it

---

### Post by donut123 on 2011-08-23
> **kiyop said:**
> i am not pleasant to read the following.
**[size=4][color=red]off topic[/color][/size]**

---

### Post by donut123 on 2011-08-23
[SIZE=4][COLOR=Red]**OFF TOPIC**[/COLOR][/SIZE][SIZE=4] :
I need help with some things, why I post where I post when I post and what I post about according to the rules..is irrelevant ![/SIZE] Thank you
[COLOR=Red][SIZE=4]Donut has left the building[/SIZE][/COLOR]
                                                                                                    Love
                                                                                           Love   :wink:
                                                                                                     Love

---

### Post by donaldsmith on 2011-08-23
I am often amazed at how often I get calls from family and friends because they are short of disk space. When it does, I wanted to share some tips to free some space. NOTE: Before attempting to use some of these techniques, you must perform a full system backup.

---

### Post by donut123 on 2011-08-23
> **donaldsmith said:**
> I am often amazed at how often I get calls from family and friends because they are short of disk space. When it does, I wanted to share some tips to free some space. NOTE: Before attempting to use some of these techniques, you must perform a full system backup.
The problem here is..no one is taking the time to look at what I am dealing with.Its not an OS..its a program running  a system foe Air conditioners. Its not an OS... Its a program run in a small single board machine it has no screen and all is done in command line into hyoper text box on a windows xp computer remotely.  
  Thats what iit is. It just happens to be Linux..Debian fastboot. No one uses fastboot in an OS.
Lets revist the page with the board...
 [http://www.embeddedarm.com/products/board-detail.php?product=TS-7553](http://www.embeddedarm.com/products/board-detail.php?product=TS-7553)
if you look to see ..also look at fastboot
 [http://www.embeddedarm.com/software/arm-linux-fastboot-ts7300.php](http://www.embeddedarm.com/software/arm-linux-fastboot-ts7300.php)

---

### Post by kiyop on 2011-08-24
To persons reading this thread;

Opening poster (donut123)'s problem was solved.

To donut123; 

If you posted the same question in many forums or in many threads, you should report that the problem is solved to all the threads (in all the forums) you posted, when it is solved.
[http://forums.debian.net/viewtopic.php?f=17&t=68708&p=390192#p390192](http://forums.debian.net/viewtopic.php?f=17&t=68708&p=390192#p390192)
> **donut123]the problem is solved  with some one from the company,[/quote]
Congratulations!

But...
I was irritated by your lack of manners, etiquette, and sincerity.
I was irritated by your laughing attitude (LOL) for my caution of multipost.
Crying loudly "LOVE" again and again is useless and seems to be mad.

Edit: At 2011/8/28 9:30 in JAPAN
[QUOTE=donut123 said:**
> [QUOTE=kiyop;11177797]I am not pleasant to read the following.you know I really Love you buddy.Why are you concerned about my posting and you dont help me out.?
Whats the problem? dont like me? you dont know me..but I still Love you son.:sad:[/QUOTE]
> **donut123 said:**
> [QUOTE=kiyop;11177797]i am not pleasant to read the following.**[SIZE=4][COLOR=red]off topic[/COLOR][/SIZE]**[/QUOTE]
Do not concoct. I do not type "i" for "I".
> **donut123 said:**
> [SIZE=4][COLOR=Red]**OFF TOPIC**[/COLOR][/SIZE][SIZE=4] :
I need help with some things, why I post where I post when I post and what I post about according to the rules..is irrelevant ![/SIZE] Thank you
[COLOR=Red][SIZE=4]Donut has left the building[/SIZE][/COLOR]
                                                                                                    Love
                                                                                           Love   :wink:
                                                                                                     Love

---

### Post by donut123 on 2011-08-26
> **kiyop said:**
> To persons reading this thread;

Opening poster (donut123)'s problem was solved.

To donut123; 

If you posted the same question in many forums or in many threads, you should report that the problem is solved to all the threads (in all the forums) you posted, when it is solved.
[http://forums.debian.net/viewtopic.php?f=17&t=68708&p=390192#p390192](http://forums.debian.net/viewtopic.php?f=17&t=68708&p=390192#p390192)

Congratulations!

But...
I was irritated by your lack of manners, etiquette, and sincerity.
I was irritated by your laughing attitude (LOL) for my caution of multi-post.
Crying loudly "LOVE" again and again is useless and seems to be mad.

If one chooses to be miserable., then it is up to the person to be happy , it is  a choice,
and you chose to be annoyed, why dont you choose to be  happy? Its all we have left.

---

### Post by kiyop on 2011-08-26
> **donut123 said:**
> If one chooses to be miserable., then it is up to the person to be happy , it is  a choice,
and you chose to be annoyed, why dont you choose to be  happy? Its all we have left.
I had been very happy until I read the above post of yours.
I am a little irritated by you again.
What I want to do is **telling you that crosspost is bad, and stopping your crosspost.**

Please read:
[http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)
> [B][SIZE=4]Section II - Posting Tips:
[/SIZE][/B][B]When asking for technical support:
[/B]12. Do not cross post, or post the same thing in multiple locations.

---

### Post by kiyop on 2011-08-26
> **wannabegeek said:**
> snip
Thank you, wannabegeek. I will ignore him.

---

### Post by Duncan Williams on 2011-08-27
he might be like 9 years old or something, it sorta sounds that way.

---

### Post by donut123 on 2011-08-30
> **Duncan Williams said:**
> he might be like 9 years old or something, it sorta sounds that 

way.


Im sorry you feel that way
I have no reason to lie and the program is 
not the same as  a n OS.
It is run all on command line.
  Werther you think I am  a liar or not 
is not an answer. I have been bashed more 
than I had any answers. 
I haven't bashed or was not rude to anyone on here. 
Its all how you look at it.
You don't know me and you do not like me because 
I am an or I live in the US. To hate me is not good for your soul
and to outsiders it looks bad. If I am wrong on multi posting
you can have an Admin to speak to me. You guys seem like you 
want to bash people and act like you are the boss. You are not my boss.
and I aint your N boy!
Have  a nice day and I Love you too:lolflag:

---

### Post by donut123 on 2011-08-30
I have contacted the Admin..to solve this problem of bashing and bullying members. Its not to set you in some trouble, its to settle this issue of you are upset because you do not understand the issues with Linus fastboot. It is not an OS..it is  a program..with  a Debian based Linux fastboot. and   a Long version of debian side by side. Th-computer.it is all run on command line..there is no GUI, We will see if I can post on Forums outside of Ubuntu..and I did not post the same ot  a different heading in different categories on Ubuntu Forums..that is the rules you set for me. That is what the rules are. to not post multi posts on here..Ubuntu forums..with Multi posts. What I do on the outside such as Debian..it is  a separate forum and  a separate OS. Debian, Mint,  iFedora, etc are all separate forums.. So if I am  a member of these forums..you say I cannot post on them because I am  a member on Ubuntu? that does not make sense..it is called  a thread because it thrads on all forums..otherwise the name thread should be removed, and all the rules should be posted to not  be allowed to be a member of several different forums.If members are upset with me, becaue the members think I am  a liar, stupid, rude, white. American.Black or other wise..then the members can bring it up to the board, and decide what I am and how to ban me from the forum. This  brings me to say , I would not like to have legal and Civil Rights assistance over a post that has gotten out of hand with discrimination..it would look bad for Ubuntu..
now I think we can settle this in a Humanly fashion..
  Thank you

---

### Post by uRock on 2011-08-30
Moved to *Other OS/Distro Talk* since it is a Debian problem, not ubuntu.

---

### Post by donut123 on 2011-08-30
Moved to..this is not  a Debian problem. This is an issue about bashing, this is not about where I post or what i post..on a Linux based Forum. Its about the bashing of members. This is an issue for ones who cannot get "free" help without paying some type of suffering for it. Not about Debian, Mint Ubuntu Fedora, OZ Unity..Israel Remix,etc, Its about simple respect. nd no the issue with this Box ..TS 7553 is not solved. Some of it was, not all, it became a cat and dog fight of why the commands wont work. did not work, or canot work at a normal Linux basis.

---

### Post by uRock on 2011-08-30
> **donut123 said:**
> Moved to..this is not  a Debian problem. This is an issue about bashing, this is not about where I post or what i post..on a Linux based Forum. Its about the bashing of members. This is an issue for ones who cannot get "free" help without paying some type of suffering for it. Not about Debian, Mint Ubuntu Fedora, OZ Unity..Israel Remix,etc, Its about simple respect. nd no the issue with this Box ..TS 7553 is not solved. Some of it was, not all, it became a cat and dog fight of why the commands wont work. did not work, or canot work at a normal Linux basis.
This thread is your help support thread, not your Resolution Center thread.

If you no longer need help with the issues with which you started the thread for, then please mark the thread as solved.

---

### Post by bodhi.zazen on 2011-08-30
I am closing this thread now as it has run it's course.

In the future, please use the Debian Forums if you require technical assistance with Debian.

---

