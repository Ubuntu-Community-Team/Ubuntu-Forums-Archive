---
title: "SU how do I"
date: 2006-09-15
forum: Absolute Beginner Talk
---

### Post by nmafzal on 2006-09-15
Hi,
    I just installed Ubuntu, when I su in the shell, it asks me for password, on entering the password it displays following:
su: Authentication failure
Sorry.
 what could be wrong? Am I using administrator account already? bevause when I type root at login it gives me same message.
Thanks,
Nomi

---

### Post by scochran on 2006-09-15
Me too...

I installed Ubuntu last night, created a user (steve) and a password(123).
When I tried to install a game just now, it tellse me to type "sudo" in a terminal.
When I do, it asks for a password.  I gave it my password, but it says its wrong.
But when I first start the computer, I have to give it my name and password, and it works then.
Did I do something wrong?

---

### Post by sethmahoney on 2006-09-15
Try sudo instead of su.  The password should be your normal login password.

---

### Post by Kateikyoushi on 2006-09-15
Read a bit, it is even included in the [FAQ]("https://help.ubuntu.com/community/CommonQuestions#head-a93fe09558d05b95a3b68200c629ec1cf3a70d7f").

---

### Post by Najand on 2006-09-15
Hmm, by default, the root user has been disabled in Ubuntu Linux, becasue of its dangerous abilities... You can activate it again, but it is recommended not to. See the following in Ubuntu Documentations about Root Privileges...
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Anonii on 2006-09-15
Short version: [I]sudo su 
[/I]
Larger version: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by scochran on 2006-09-15
Maybe I'm not explaining it right.

When I tried to install a game this morning, it tells me to type "sudo" in a terminal.
When I do, it asks me for a password. I gave it my password, but it says its wrong.

Does that explain it better?

---

### Post by NetworkGuy on 2006-09-15
You need to type the same password you type when you sign in.  The password is case-sensitive.

---

### Post by Najand on 2006-09-15
Can you login without any problem to your computer or it is always ON. Let us do a test.
Hit "ALT+Ctrl+F1" and you will see a black dark screen.
Login there and see if you can login there or not.
If you could, then type "exit" and hit "ALT+Ctrl+F7" to go back to the Graphical environment. Tell us if you could login there or not.

---

### Post by scochran on 2006-09-15
My password is 123
No caps.

I type ALT CTRL and F1 to get to the dark screen.
I give my name then password and it tells me a lot of things.
I wrote them down,
last login; fri sep 15 12:46:22 2006 on tity
linux steve-desktop 2.6.15-23-386 #1 PREMPT tue may 23 13:49:40 utc 2006 1686 nu/linux
the programs included with ubuntu system are free software, 
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.
ubuntu comes with ABSOLUTLY NO WARRANTY to the extent permitted by
applicable law.
steve@steve-desktop:^$

then i type exit and it says

ubuntu 6.o6 LTS steve-desktop tty1
steve-desktop login:
So do I have to try and login again?
Does that mean i can't login with my password?

So i rebooted and it asks for my name then password.
And then the brown screen.

do i have to change my password?

---

### Post by Najand on 2006-09-15
No... What exactly do you recieve as an error?

---

### Post by scochran on 2006-09-15
su: Authentication failure
Sorry.

---

### Post by Najand on 2006-09-15
Hmm, it sounds like a "su" command...
The "sudo" command doesn't have any error like that...
Did you make a "su" account before?

---

### Post by Anonii on 2006-09-15
I really dont understand the problem here. 
su is by default not enabled in Ubuntu, primary because there is _NO_ root account. If you want to have root access for a command you should use sudo. If you want to have root access for a console session "sudo su" or "sudo -s -H" would do that for you :/

---

### Post by Najand on 2006-09-15
Now I can understand what is the problem.
he wants to use "sudo" like "su" command.
Unfortunately, "sudo" alone means nothing. 
It should be followed by another command
which need Root Privileges. If you need to
start "root" session, use "sudo passwd"; 
enter your password, and a new password for
root account then use "su" to start using
"root"... But be careful and don't delete
anything you just thought unneccessory.

---

### Post by Brunellus on 2006-09-15
> **Najand said:**
> Now I can understand what is the problem.
he wants to use "sudo" like "su" command.
Unfortunately, "sudo" alone means nothing. 
It should be followed by another command
which need Root Privileges. If you need to
start "root" session, use "sudo passwd"; 
enter your password, and a new password for
root account then use "su" to start using
"root"... But be careful and don't delete
anything you just thought unneccessory.
[http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo)

RECOMMENDATION:  if you want to be root for a while, use

sudo -s 

the password is your own user pass.  Do this as LITTLE AS NECESSARY, since running constantly as root invites trouble.

---

### Post by Najand on 2006-09-15
Well, that is the link I posted at the begining.

---

### Post by scochran on 2006-09-15
I tryed to install a game.
It says I have to be root to install.
I look online, and find that to get root, I have to go to a terminal and use sudo.
when I type sudo, it tells me usage: sudo -k 1 -L 1 -v 1 -h 1
and a lot more.  I dont understand any of that, and i don't want to do something wrong, so i close the terminal.
I go back on line and find that i should use su to get to root, not sudo.
so i do that and it asks for a password.
i give it my password and it's wrong.
so i ask the question here, and i get a lot of different answers.
and it still doesnt work.

i never used ubuntu before but i heard it is supposed to be really good and easy to use so i figure i'm doing something wrong cause this sure isnt easy!
maybe its not made for playing games?

---

### Post by Brunellus on 2006-09-15
the answer is 

sudo -s

and give it your USER PASSWORD

---

### Post by scochran on 2006-09-15
I used sudo -s and it never asks for a password.
i try sudo su and it doesn't do anything.
i try sudo -s -h and it doesn't do anything.

Did you make a "su" account before?
do I have to do that?  How do i do that?

---

### Post by Najand on 2006-09-15
Well, that is good you could find how to use root.
For me iit has been months, haven't seen:
```

root@iLinux:

```
in the bash.

---

### Post by Najand on 2006-09-15
It didn't ask you for a password becuase you already had entered yours.
Once you enter your password for sudo, it  won't ask you for password for 15 minutes on the same session.

---

### Post by bulldog on 2006-09-15
It's very simple in fact,watch what's before the @ in terminal.

normal is

steve@steve-desktop:~$

when you do sudo it ask your password and there changed nothing visiual but you have root permissions for a given time to do your job.

When you do sudo -s it asks your password and the terminal should look like this

root@steve-desktop:~ #

You're root now till you type exit.

Your password is accepted cause you could login in tty1 [ctrl-alt-f1] when it not's accepted in terminal for sudo I'm confused.

[when you get in tty1 you can go back to GUI hitting ctrl-alt-f7 instead of rebooting]

---

### Post by scochran on 2006-09-15
Well, that is good you could find how to use root.
  I dont want to sound silly, but I don't know how to use root.  I must of said something that sounded right, though... 

It didn't ask you for a password becuase you already had entered yours.
Once you enter your password for sudo, it won't ask you for password for 15 minutes on the same session.
I am confused by this statement.
The only time I entered my password is when i reboot the computer.
When I type sudo, it never ever asked for my password.
do I have to wait 15 minutes after i turn on the computer to use sudo?  That just sounds silly.  But I really don't understand what I'm doing wrong.
Is there some reason why the game just won't install without going through all of this?

---

### Post by Brunellus on 2006-09-15
sudo is meant to give you root permissions for one command only:

sudo ls -a 

for instance, will list the contents of one directory, including hidden files, as if root had asked to do it. it is NOT used as a command by itself.

---

### Post by scochran on 2006-09-15
when you do sudo it ask your password

no it doesnt.  i said that twice already.

Your password is accepted cause you could login in tty1 [ctrl-alt-f1] when it not's accepted in terminal for sudo I'm confused.

so do I have to do ctrl-alt-f1 to install the game?  it never said anything about that.

where do i find all of these instructions you are all telling me?

---

### Post by Brunellus on 2006-09-15
> **scochran said:**
> when you do sudo it ask your password

no it doesnt.  i said that twice already.

Your password is accepted cause you could login in tty1 [ctrl-alt-f1] when it not's accepted in terminal for sudo I'm confused.

so do I have to do ctrl-alt-f1 to install the game?  it never said anything about that.

where do i find all of these instructions you are all telling me?
if you're in ubuntu now, please do the following:

open a terminal window.

now execute

sudo ls

hit enter.  Highlight everything in the terminal window.  hit reply to this thread, and click the middle mouse button in the "message" box.  that will let us see what you're seeing.

---

### Post by bulldog on 2006-09-15
Normally it should ask your password when you type sudo.
Only when you use sudo in a short time period,you have to give your password once every 15 min.

Why you're not asked for your password when you do sudo strikes me.
It should!!

Now every one kan mess with your Ubuntu because you need no password apparently.
I for myself would sort this out instead of installing a game.

---

### Post by Najand on 2006-09-15
You are not suppose to do anything.
Just click:
Application -> Accessories -> Terminal
Use:
```

sudo -s

```
and it will ask for your password... 
Enter your password and continue as your game guidence written.

---

### Post by RoyArne on 2006-09-15
> so do I have to do ctrl-alt-f1 to install the game?

What is the command you tried to install the game with?

---

### Post by scochran on 2006-09-15
My mouse is only 2 buttons, but here it is

steve@steve-desktop:~$ sudo ls
Desktop  Examples
steve@steve-desktop:~$

---

### Post by Brunellus on 2006-09-15
now post the result of

sudo -s

---

### Post by scochran on 2006-09-15
steve@steve-desktop:~$ sudo -s
root@steve-desktop:~$

is this right?

it says root now but it never asked for a password, but I rebooted the computer like an hour ago.

---

### Post by bulldog on 2006-09-15
This is not good!

When you open synaptic [application installer] is your password asked then?

---

### Post by Brunellus on 2006-09-15
> **scochran said:**
> steve@steve-desktop:~$ sudo -s
root@steve-desktop:~$

is this right?

it says root now but it never asked for a password, but I rebooted the computer like an hour ago.

That's what you're supposed to be seeing.  It should have prompted you for your user password though.

If you didn't set a password with this account, I would VERY STRONGLY urge you to do so.  The whole idea of unix permissions is premised on having proper user accounts with passwords.  Without a password, it's trivial for someone to find your machine, log on as you (the unprivileged user) and escalate his privileges to root. 

do you have a user password *at all*?

---

### Post by bulldog on 2006-09-15
What I understand,yes he has.

He uses it to login and that's it.

sudo and root are given to him without a password.

Sounds not right to me at all.

---

### Post by scochran on 2006-09-15
When you open synaptic [application installer] is your password asked then?
I don't even know what that means.

my password is 123.  I said that many times.

---

### Post by bulldog on 2006-09-15
You have an issue here.which we try to solve.
A little cooperative behavior is in place.

Go to System--administration--update-manager and click it and see if it asks you for a password.

[You shouldn't give your password on a forum or anywhere else for that matter]

---

### Post by Brunellus on 2006-09-15
> **scochran said:**
> When you open synaptic [application installer] is your password asked then?
I don't even know what that means.

my password is 123.  I said that many times.
OK.  I think I know what's going on.

the first time you used sudo -s, (or sudo ANYTHING), you would have needed to have been prompted for the password.

If you've been continuously sudoing, though--that is, 15 minutes did not elapse between two uses of 'sudo'--then you wouldn't have needed any passwords for anything.

Offtopic, I'd change your password.  it should be at least six characters (preferably more) long, and include lowercase and uppercase letters as well as numbers.

---

### Post by scochran on 2006-09-15
I think this is a mistake.
All I did was put in the ubuntu cd and follow directions.
then i try to play a game and it takes 5 hours and alot of typing and it still not installed.
all of the people here say that i should use root or not use root or root is disabled or i should use su or not use su or sudo or alt-ctl-f1 or f7 or i have to make a su account or alot of other things.
it sounds like ubuntu installed wrong and the game doesnt know how to install itself and everybody doesnt know how to log in.
isnt ubuntu supposed to be easy to use casue it isnt easy at all for everybody here. what happens if i want to try another game, will i have to go through all this again?

---

### Post by bulldog on 2006-09-15
That's why I asked to see if synaptic prompt for his password.

---

### Post by Brunellus on 2006-09-15
> **scochran said:**
> I think this is a mistake.
All I did was put in the ubuntu cd and follow directions.
then i try to play a game and it takes 5 hours and alot of typing and it still not installed.
all of the people here say that i should use root or not use root or root is disabled or i should use su or not use su or sudo or alt-ctl-f1 or f7 or i have to make a su account or alot of other things.
it sounds like ubuntu installed wrong and the game doesnt know how to install itself and everybody doesnt know how to log in.
isnt ubuntu supposed to be easy to use casue it isnt easy at all for everybody here. what happens if i want to try another game, will i have to go through all this again?
1) what game are you trying to install, and using what directions?

2) most of this back and forth is due to a number of misunderstandings.  did you read the RootSudo page people linked you to?

3)  The password/login issue is something that I'm quite interested in, because I personally have not experienced it.  If there is a problem there, it needs to be fixed and soon.

4) Never give your password out on the internets.

---

### Post by scochran on 2006-09-15
after i turned on my computer it asked me for my password.
then it asked me and it said it was wrong.
then i asked here and everbody is confusing about it and has me try alot of different things.
and now my password is wrong but i already asked if i had to change it and somebody said no.
i think maybe i made a mistake.

---

### Post by Brunellus on 2006-09-15
> **scochran said:**
> after i turned on my computer it asked me for my password.
then it asked me and it said it was wrong.
then i asked here and everbody is confusing about it and has me try alot of different things.
and now my password is wrong but i already asked if i had to change it and somebody said no.
i think maybe i made a mistake.
too many "it"s, not enough nouns. 

When did it ask you for the password, when was it 'wrong,' and what did it do?

---

### Post by bulldog on 2006-09-15
> **scochran said:**
> steve@steve-desktop:~$ sudo -s
root@steve-desktop:~$

is this right?

it says root now but it never asked for a password, but I rebooted the computer like an hour ago.

When I read this I'm confused.
He stated that he uses his password only by login and never more.
To use sudo he should be prompted for his password.
When given he can be root.
But when Ubuntu never asks for a password [exeption login] there should be something wrong.

@scochran
On a forum you get many answers that's a fact and not always a good thing though,it maybe confusing you.
You're thinking at your game and you wanna play and not be botherd by password issues.

But in fact, if I undestand everything correctly,you have a major safety issue on your hands,which first must be solved.
It's not funny when you want to login and someone else is the root [owner] of your computer.
Just be patient and let us try to solve this problem.

---

### Post by Brunellus on 2006-09-15
> **bulldog said:**
> When I read this I'm confused.
He stated that he uses his password only by login and never more.
To use sudo he should be prompted for his password.
When given he can be root.
But when Ubuntu never asks for a password [exeption login] there should be something wrong.
sudo should have asked for password at the first instance.  User must have been constantly invoking sudo before the 15-minute timeout.

---

### Post by scochran on 2006-09-15
i do not understand ubuntu.  
but i go back and read this forum and i type in everything like you tell me to, and i tell you what it says exactly.
but its not working right and i still don't know how to change my password like i asked a long time ago.
i was trying to play armagetron but it was bad instructions i thought cause everyone said there is no root or something. so now i deleted the game cuase all this didn't work at all and now my password needs changed and i still dont know how any of this works at all.
it is all too confusing for me to understand this.

---

### Post by Brunellus on 2006-09-15
> **scochran said:**
> i do not understand ubuntu.  
but i go back and read this forum and i type in everything like you tell me to, and i tell you what it says exactly.
but its not working right and i still don't know how to change my password like i asked a long time ago.
i was trying to play armagetron but it was bad instructions i thought cause everyone said there is no root or something. so now i deleted the game cuase all this didn't work at all and now my password needs changed and i still dont know how any of this works at all.
it is all too confusing for me to understand this.
OK, we will begin at the beginning.

USERS AND PERMISSIONS

Linux, UNLIKE Windows, has "users" and "permissions."  There are two kinds of users, broadly speaking:  "regular" users and the "superuser" (also known as "root").

"root" can do anything on the computer, without restriction--up to and including actions that break the computer.  If you're "root," Linux won't care that you've just instructed it to delete itself.  It will dutifully do whatever "root" asks it to do.

As you can see, "root" is pretty dangerous.  Most of the time, you spend your time as a "normal" user.  You can do anything you want in your home directory, which is the only bit of the computer you're really allowed free reign on.  

If you want to make major system changes--like, say, install software that will be usable by all users on a computer--you need to be root. 

Ubuntu is so concerned about the danger of a separate "root" user that that account simply doesn't exist--he isn't there.

So how to be root in ubuntu?

Sudo.

Sudo stands for "SUPERUSER DO."  It gives a regular user 'super' powers to do whatever he wants...only for one command at a time. 

It works like this.  Say user 'brunellus' wants to do something that can only be done by root--copy a file called 'file' to the special /usr directory--he does this

brunellus@examplebox $ sudo cp file /usr

Which means, in English: 

"Computer, Brunellus wants superuser permission to move a file into /usr"

to which the kernel responds with a prompt:

Password:

brunellus then types his user password--the one he logged in with.  The command executes, file is copied to /usr, and the action is logged.

What if brunellus wants to do more things as root?  well, he can keep using 'sudo' before the commands. So long as 15 minutes have not passed since the last time he used 'sudo' he won't be bothered for his password again.

What if brunellus gets sick of typing 'sudo' all the time?

well, he can always make himself root temporarily by executing

brunellus@examplebox $ sudo -s

Which, after a password prompt, turns his commandline to 

root@examplebox #

there, see?  Now he's "root."

---

### Post by bulldog on 2006-09-15
You have a brand new OS installed on your computer and you have to take the time to get to know it.

It's not Windows.
It works completely different and so is installing and playing games.

A safety build in is that you use Ubuntu as a user with restricted privileges.
When you want to alter anything  which could affect your Ubuntu,like installing games or any application and much more,you need root privileges.

This can be obtained on different manners.
One is sudo for one command and your password is stored for a limited amount of time for your convinience.
When you want to be root for a longer period you use sudo -s so you become root without time limit.

But the most important thing is that Ubuntu asks for your password when you login and when you use sudo or sudo -s.

That's where things go wrong on your computer,Ubuntu does not ask for your password!!!
This is not good as you would understand and MUST be solved for your safety.

That's the only thing that matters for now,your game has to wait.

When this is solved we can help you to install your game :grin:

You type faster Brunellus :lol:

---

### Post by scochran on 2006-09-15
i'll never be able to figure all that out.
there's just no way at all.
i dont know enough about computers for this.  it's way over my head.
i think i'll get windows.  we use it at work and its pretty easy to use.
i just thought ubuntu was going to be easy to use.
i'll just leave it for the experts.

thanks for all your help, sorry i wasted your time.

---

### Post by bulldog on 2006-09-15
And we lost another Ubuntu user who thinks it's easier to use.

Not taking the time to get to know it.

I'm not happy:frown:

---

### Post by Brunellus on 2006-09-15
> **bulldog said:**
> And we lost another Ubuntu user who thinks it's easier to use.

Not taking the time to get to know it.

I'm not happy:frown:
User was never going to stay.

---

### Post by mikewright on 2006-09-15
I must say, I give the guy credit for trying...

I've been using Mandriva for the past 6-7 months, and my first experience with Ubuntu about a week ago was HORRIBLE.  I was ready to throw in the towel right away!

Fortunately, I've learned enough BASH commands and other Linux-specific methods that I was able to get around a bit in Ubuntu, but my GOD!

I'm sure it's a fine OS, and every time I see a reference to Linux, it always involves never-ending praise for Ubuntu (Linux for the masses, no?)

But I honestly don't see the draw... I was expecting it to be a plug-it-in-and-start-going-to-town-NOW sort of shock-and-awe distro.

It has a VERY steep learning curve, and not just because it's "not windows", but seemingly because it's also "not Linux".  To be honest, the "no root by default" thing seems a little... microsofty. ("we're going to make it idiot proof by taking away intuitive functionality")

Every time I have a question with Mandriva, I can readily find a LOT of online support in several forums, and I have rarely run into the situation where there are multiple contradictory answers to one question.

Granted, the user sounds a little confused when it comes to all things computerish, but I think he could have started with something a little less like Ubuntu, and something that would have a more standardized approach to Linux...  And keep in mind, with a hundred different distros to choose from, finding a good 'starter distro' is enough of a challenge without having to learn a new approach to Linux with each one!

I actually came upon this thread after trying to install Opera... right out of the gate, I was told to "become root with su".  And that just doesn't happen with Ubuntu!

Seeing as this is the "absolute beginner" forum, I was kind of looking for a "1.Click this.  2.Type this.  3.Copy and paste this..."  I think scochran was looking for that, too.

Personally, after a week, I'm not up to learning a new Linux; I'm sticking with Mandriva.

And scochran, I suggest the same for you...  It's a little more intuitive, a little less intimidating, and a little more windowy.

---

### Post by bulldog on 2006-09-15
If you're glad with Mandriva I'm happy for you,you should stick to it.

---

### Post by Najand on 2006-09-15
Well, selecting a distribution is just a matter of taste, if you prefer mandrake and you find it more comfortable, you should stick to it...

---

### Post by Brunellus on 2006-09-16
I'm of the opinion that Ubuntu is a great *second* distro.

out of the box, ubuntu will give you sane defaults, but it doesn't do too much handholding.

---

### Post by scochran on 2006-09-16
I went to the store this morning and they say it will cost 600$ to buy windows and word and email and then I tell them how hard ubuntu is to figure out and then i show them the question i asked and all the different answers and that i do something wrong when i install it and can they install windows instead but thats to much!
so they give me a new disk called an f disk and they tell me it's all clean and will install ubuntu just fine.  then i tell them to install it for me so i dont mess up again, and then they give me a bad password cause its not like what brunellus said it should be, but they say its fine like it is. but i told them to be sure since it caused problems last time so they make a new user for me to log into, so now i have scochran and cochrans on the same computer!
and now its all set back up again and i have to make sure its ok now but i dont know how to check it.  can you help me make sure the root is not a problem again cause i can't afford 600 dollars for windows and i guess i'll have to figure out ubuntu.
and is mandriva something that will make ubuntu run better?
and what is synaptic? will it help me too?
and will the f disk help like they say it will?

---

### Post by Brunellus on 2006-09-16
> **scochran said:**
> I went to the store this morning and they say it will cost 600$ to buy windows and word and email and then I tell them how hard ubuntu is to figure out and then i show them the question i asked and all the different answers and that i do something wrong when i install it and can they install windows instead but thats to much!
so they give me a new disk called an f disk and they tell me it's all clean and will install ubuntu just fine.  then i tell them to install it for me so i dont mess up again, and then they give me a bad password cause its not like what brunellus said it should be, but they say its fine like it is. but i told them to be sure since it caused problems last time so they make a new user for me to log into, so now i have scochran and cochrans on the same computer!
and now its all set back up again and i have to make sure its ok now but i dont know how to check it.  can you help me make sure the root is not a problem again cause i can't afford 600 dollars for windows and i guess i'll have to figure out ubuntu.
and is mandriva something that will make ubuntu run better?
and what is synaptic? will it help me too?
and will the f disk help like they say it will?
the computer guys don't have the first idea what they're talking about.

fdisk is just the MS-DOS disk partitioner.  in linux, it has a corresponding program also called fdisk.  All that disk they're giving you will do is wipe whatever you have on your hard drive to start fresh.

you could, if you really wanted to go this way, simply reinstall ubuntu and enable a root account following the drections on 

[http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo)

again, not recommended.  

Once again:  sudo should prompt you for a password when you invoke it for the first time.  when you sudo -s to become root for a long session it will look something like this:

brunellus@examplebox$ sudo -s
Password:
root@examplebox /home/brunellus#

question:  did the COMPUTER SHOP GUYS install ubuntu for you?!  Because that might explain the lack of password prompt for sudo.  If so, I'd have had a very sharp word with them for setting it up like that.

---

### Post by xpod on 2006-09-16
> i was trying to play armagetron 

```
sudo aptitude update
```

Then

```
sudo aptitude install armagetron
```

I have that game and thats what i did but obviously it is also in the "add\remove" or in "synaptic"

Unless you are talking about having used "aptitude" or indeed "apt-get" to install the game you would`nt even need to use "sudo"  to play the game.#
It would be in your games menu which you only need to click to open.

Great game though.....Hope you get on one of those lightcycles sooon.

Finding out whats wrong is waaaayyyyy out of my league but i cant see how you need "sudo" to play the game.....IF indeed it`s installed?

EDIT:of course i understand these guy`s need to fix it IF theres a problem

---

### Post by spur on 2006-09-16
This guy requires a step by step approach. One thing at a time. No confusion.
First is it ubuntu or kubuntu? I have kubuntu and it responds bettter to kdesu than sudo. It refused sudo a number of times.
To check that the permissions are right attempt to open your packagemanager. Thats adept on kubuntu or synaptic on ubuntu. You get to it via the icon in the corner where the start button is on windows. The go up to system settings. It should be there. If you click on it it should ask for your password. Use the one for your user account. Report back on what happens. It may be that only one of your accounts has administrator priviledges. So you may have to log off and on again as the other one if it does not work at first.

---

### Post by xpod on 2006-09-16
> i'll never be able to figure all that out.
there's just no way at all.
i dont know enough about computers for this. it's way over my head.
i think i'll get windows. we use it at work and its pretty easy to use.
i just thought ubuntu was going to be easy to use.
i'll just leave it for the experts.

thanks for all your help, sorry i wasted your time.

OH dear...i just realised he was mabey gone
Surely if he did`nt have any real experience of windows either like he aludes  to this should have been all the easier?
 I still know jack s**t but i too did`nt have much experience of windows and that is supposed to be the best way is it not?

---

### Post by scochran on 2006-09-17
the computer guys don't have the first idea what they're talking about.
Now i don't know whos right and whos wrong.
I went back to the store and told them they did sudo wrong but he got a little upset and showed me the terminal and when he went sudo s it ask him for the password and he says thats the way it should be.
Then i ask him about the f disk and he told me they already done that and I don't need it anymore.
and when i tell him if i don't need it then why did i pay him for it and he told me that he cant help me any more so now i think im really screwed.
but i get it home and hook it back up again and then my monitor didnt work so i went to a different store and got a new monitor and now the picture is all skinny like a movie with black on top but i cant see the bottom cause i try to adjust it with the buttons on the monitor and it only goes up this high.
but he told me at the computer store that its called ubuntu and thats what is on the cd.
but i can log on and use the internet and the word processer and i try to set up my email and i think thats all i want to do now cause everybody uses to many computer words and I dont know how to do all that.

---

### Post by xpod on 2006-09-17
> when i tell him if i don't need it then why did i pay him 

OMG...You got "charged" for "fdisk".....I reckon you should stay as far AWAY from that place as you possibly can.

They are probably just making it impossible for you so you concede and ask them to put bloody windows on it which of course will cost a hell of a lot more than "fdisk"......

EDIT:> uses to many computer words and I dont know how to do all that.

Get the "dictionary tooltip" extension for firefox then ANY weird looking words you dont understand can be quickly learned by merely double clicking on the word in question.
I still dont know what 99% of it means BUT i`d start learning even quicker than i do just now IF i was left with the choice of going to YOUR local shop!!

---

### Post by bulldog on 2006-09-17
@Scochran,

Well if you want to use a computer you will have to learn the basic skills to work with it.
You also did learn to use a bycicle and you surely did fall of sometimes I gues.

So it is with computers.
But if you're willing to learn and be a little patient it is not that hard to do.

You must understand that the members on the forum assume that the user of a computer who comes here for help,have the basic skills yo use it.
We can't see that it's not so.

A computer is more than a basic box with a screen and a mouse atach.
It's a sofisticated peace of electronica with several parts in it,which when it all went right can give you much pleasure,but on the other hand,it could be a pain in the *** as well when things won't work out of the box.

I suggest you first try to understand a little what a computer is and what it can do.
Then find an OS [operating system] what is suitable for your needs.

I personally would advice you an OS like Mepis or Suse which is somewhat easyer to install and use.

When I read you have bought another monitor because the old one didn't work right,but the new one isn't also,I think you're srewed up, but that's my opinion.

Basicly we all will help you with your problems but you need to understand what we try to tell you to do.
And if we're counter another problem, beside your game where you came for ,we'll try to solve that too,even if you don't understand sh*t were telling you.

That's the Ubuntu forum like,and to confuse you even more,there are several people speaking over your problem,and they have all an opinion how to get it solved.
But it will get solved in the end,and that's what's matters.
We all [at least I do] learn from eachother and from our misstakes.

That's why I love this place,it,s full of knowledge and you only have to ask for it.

That's what I wanted to tell you,you have to make your own mind what to do.

---

### Post by xpod on 2006-09-17
> When I read you have bought another monitor because the old one didn't work right,but the new one isn't also,I think you're srewed up, but that's my opinion.

A bit like my daft mother in law....a new box whenever she messes the present one up with all her free offers and dodgy bingo sites..clicky clicky:mad: 
NOT anymore mind you8-) .

Good luck anyway....stay away from dodgy shops

---

### Post by Brunellus on 2006-09-17
> **scochran said:**
> the computer guys don't have the first idea what they're talking about.
Now i don't know whos right and whos wrong.
I went back to the store and told them they did sudo wrong but he got a little upset and showed me the terminal and when he went sudo s it ask him for the password and he says thats the way it should be.

OK, look.

when you sudo -s, does it ask you for a password?  sudo will ALWAYS ask for a password the FIRST TIME YOU USE IT.  If this is what happened at the shop, then you are fine.

> Then i ask him about the f disk and he told me they already done that and I don't need it anymore.
and when i tell him if i don't need it then why did i pay him for it and he told me that he cant help me any more so now i think im really screwed.

This guy is no good.  Charging you for fdisk was ridiculous.  Don't spend any more cash at this place.

> but i get it home and hook it back up again and then my monitor didnt work so i went to a different store and got a new monitor and now the picture is all skinny like a movie with black on top but i cant see the bottom cause i try to adjust it with the buttons on the monitor and it only goes up this high.

You have to adjust display setttings when you connect new monitors (same as windows, incidentally).  Define "didn't work" with your old monitor?  This sort of thing doesn't just happen.

If you simply weren't getting *any* picture at all, I would have done the obvious and checked for loose connections.  Getting a NEW monitor without eliminating the possibility of installation error is unwise.

> but he told me at the computer store that its called ubuntu and thats what is on the cd.

I don't understand this sentence.

> but i can log on and use the internet and the word processer and i try to set up my email and i think thats all i want to do now cause everybody uses to many computer words and I dont know how to do all that.

To review the original issue:

Sudo apparently works the way that it's supposed to.  It prompted for a password THE FIRST TIME you used it, and since you kept hammering away using 'sudo' all the time, it didn't bother asking for a password, since 15 minutes had not expired between each time you used 'sudo'.

The MONITOR issue:

You would have had to have damaged your old monitor *physically* for it not to work any more.  This is highly unlikely.  Try hooking it up again, and DOUBLE-CHECK all the connections.  Make sure they are tight, not loose.  Don't force any connectors--they only go in one way.   Make sure the monitor has power.  Then run it again:  your old settings should work.

Off-topic:

There is a "quote" option when you hit "reply"--it makes things MUCH easier for us to follow when we know what you're responding to.

---

### Post by scochran on 2006-09-17
I checked my moniter before i bought a new one.
it was just black.
the power light was green then yellow and it said no signal.
so i bought a new one and it works ok.

i hit reply and i dont see any quote button, just yellow and blue smiley faces and Valid file extensions: bmp bz2 doc gif gpl gz jpe jpeg jpg pdf png psd svg txt zip and some other things.

---

### Post by Brunellus on 2006-09-17
> **scochran said:**
> I checked my moniter before i bought a new one.
it was just black.
the power light was green then yellow and it said no signal.
so i bought a new one and it works ok.

i hit reply and i dont see any quote button, just yellow and blue smiley faces and Valid file extensions: bmp bz2 doc gif gpl gz jpe jpeg jpg pdf png psd svg txt zip and some other things.
I still suspect something was wrong with your connections.  

Each post has a number of icons in the bottom-right corner:    one of them (looks like a letter with a sunburst in the top-right) is "REPLY WITH QUOTE")

---

### Post by xpod on 2006-09-17
> he power light was green then yellow and it said no signal.

Exactly what any of my monitors say ...only if they aint connected yet!

---

