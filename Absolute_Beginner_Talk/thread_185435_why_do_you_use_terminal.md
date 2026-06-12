---
title: "why do you use terminal?"
date: 2006-05-31
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2006-05-31
i'm very new to the linux world, but am very excited to get deep into learning the ins and outs of using the os.

my question for you is...

with the graphical progression of ubuntu, what are the advantages of using the terminal for everything? i know there are things you can only do in the terminal, but i'm talking about overall use.

this may sound like a dumb question, but i guess that's how i learn.

---

### Post by meng on 2006-05-31
Well one reason is, when your GUI launcher isn't starting the program as it should do, you can try launching the same program from the terminal and see what error comes up.

Another reason is, when you need to do a command just once or twice that isn't worth writing a script for.

Some programs are terminal-only. For example, I found a nice scrabble program last night, but it's terminal-only. Another example - compiling my java files is easier from the command line.

Yet another is, you learn more about Linux that way, as opposed to just learning how to navigate the GUI.

---

### Post by johnc4510 on 2006-05-31
The terminal is a much faster way of doing things in most cases.

---

### Post by 23meg on 2006-05-31
Some tasks are more suited to command line operation than GUI; mostly redundant ones that require some level of automation. Also, with the shell's I/O redirection it's very easy to pull neat tricks that you can't even come close to with a GUI.

I suggest you check out [http://www.linuxcommand.org](http://www.linuxcommand.org) which is an excellent site that takes you from zero knowledge of the command line to and advanced level where you'll be making sophisticated bash scripts.

---

### Post by gingermark on 2006-05-31
You get a lot of terminal commands here (on this forum) because it's easier than telling someone to "click this, then click that" and there is less chance for errors, as the person you are helping can just copy and paste the commands given.

---

### Post by s_h_a_d_o_w_s on 2006-05-31
It's more ''internal'. You have direct access to your computer. Many actions take place in the terminal. There are even some funny things in there! Just check out my signature! (below)

---

### Post by xXx 0wn3d xXx on 2006-05-31
I use the command line for everything because it's fast, easy to use, simple, it gives you the feeling that you have control over your system and you get to see what's going on behind the scenes.

---

### Post by IYY on 2006-05-31
It's faster, and less frustrating once you get used to it. I hate these "wizard" configurations and help screens that keep going in circles and treat the user like an idiot. 

With the terminal you can also automate things you do often by writing scripts.

And, you have much more power if you login to your machine remotely. I can do almost everything I need without even having access to my machine! So I can be in the other room, in the university, or even in another country and still be able to download files to my machine at home, configure things, upgrade the operating system... Anything I like. This is especially useful for servers.

---

### Post by catlett on 2006-05-31
[http://www.linuxcommand.org/learning_the_shell.php](http://www.linuxcommand.org/learning_the_shell.php)

Personally I was dumbfounded with it after migrating from xp. But once you learn it you realise how powerful and fast your computer is. I use to "drill down" through explorer to get to something or worse  trying to  get to a registry key. I would have a whole folder of shortcuts to get me somewhere on the computer. With a terminal it is  cd and a path. 
You don't have to see something to do it. If you want to copy something you just cp what it is to where you want it. That's it. No drilling through explorer to find the folders or files and then opening two windows and dragging it over and waiting for it to copy.
Once you learn it you can't believe you got stuff done without it.

---

### Post by Sef on 2006-05-31
I like the terminal because I like being able to do what I want and see it, instead of it being hidden by the gui.

> Some programs are terminal-only. For example, I found a nice scrabble program last night, but it's terminal-only. 

Thank you meng.  I love scrabble.

I like the terminal because I like being able to do what I want and see it, instead of it being hidden by the gui.

---

### Post by shanepardue on 2006-05-31
this is all very helpful and i am continuing to learn it..i have to admit, i'm very intimidated by the complex stuff...i've managed to learn moving, copying, etc..but when it comes to the complex stuff, i'm lost...

i appreciate the links..they'll definitely be used often!

---

### Post by shanepardue on 2006-05-31
also..what good does a new version of ubuntu do for hardcore terminal lovers?

---

### Post by nanotube on 2006-05-31
[QUOTE=s_h_a_d_o_w_s]apt-get moo[/QUOTE]
haha nice. those apt-get developers were having some fun eh :)

---

### Post by pjbgravely on 2006-05-31
Once you have used Linux for a while you will probably want to start using the command line more. It is not hard like it is in windows. You will get a lot of help in the form of command lines. Just open up a terminal, and paste the line in and push enter. Much easier than clicking with a mouse. 


Here is cool trick if you have an internet connection.

Open up a terminal, and paste in,

telnet towel.blinkenlights.nl

Paul

---

### Post by aysiu on 2006-05-31
[Why I think the command-line is user-friendly...](http://www.ubuntuforums.org/showthread.php?t=59334)

---

### Post by gingermark on 2006-05-31
[QUOTE=shanepardue]also..what good does a new version of ubuntu do for hardcore terminal lovers?[/QUOTE]
Well, with better and better hardware recognition with each release, it means they have to spend less time in the terminal setting their hardware up!
(so maybe that's a bad thing :) )

---

### Post by 23meg on 2006-05-31
[QUOTE=shanepardue]also..what good does a new version of ubuntu do for hardcore terminal lovers?[/QUOTE]
Just about the same it does for non-terminal-lovers: newer software, better performance and security. On the more superficial side, thanks to Dapper I have one side of my Compiz cube reserved to three transparent terminals that are constantly open.

---

### Post by az on 2006-05-31
[QUOTE=shanepardue]this is all very helpful and i am continuing to learn it..i have to admit, i'm very intimidated by the complex stuff...i've managed to learn moving, copying, etc..but when it comes to the complex stuff, i'm lost...

[/QUOTE]
Don't let anyone tell you that you need to learn the command line to use Ubuntu.  You can, but it is not a prerequisite.

The number of things that *require* you use the command line is getting smaller rapidly.

---

### Post by aysiu on 2006-05-31
[QUOTE=azz]Don't let anyone tell you that you need to learn the command line to use Ubuntu.  You can, but it is not a prerequisite.

The number of things that *require* you use the command line is getting smaller rapidly.[/QUOTE] To *use* Ubuntu, you don't need the command-line.

If you want to set it up, though, you may end up doing a ```
sudo dpkg-reconfigure xserver-xorg
``` to get your video set up or some other commands to get wireless set up.

Installation and use are two completely separate procedures.

---

### Post by catlett on 2006-05-31
[QUOTE=pjbgravely]Once you have used Linux for a while you will probably want to start using the command line more. It is not hard like it is in windows. You will get a lot of help in the form of command lines. Just open up a terminal, and paste the line in and push enter. Much easier than clicking with a mouse. 


Here is cool trick if you have an internet connection.

Open up a terminal, and paste in,

telnet towel.blinkenlights.nl

Paul[/QUOTE]
That was great. I don't even want to know how long that took them.:-D

---

### Post by az on 2006-05-31
[QUOTE=aysiu]To *use* Ubuntu, you don't need the command-line.

If you want to set it up, though, you may end up doing a ```
sudo dpkg-reconfigure xserver-xorg
``` to get your video set up or some other commands to get wireless set up.

Installation and use are two completely separate procedures.[/QUOTE]

On how many boxes have you installed Ubuntu?  I have never had to reconfigure X as part of the installation.  And many wireless cards just work - and not everybody uses wireless.

Most of the time, I can hand someone a cd and tell them roughly how to install and it goes fine.

---

### Post by aysiu on 2006-05-31
[QUOTE=azz]On how many boxes have you installed Ubuntu?[/quote] Two. Why does it matter? I've seen enough people on these forums have issues with wireless and X. Do you want to make the statement that only with rare exception do people ever need to configure wireless or video cards/monitors? > I have never had to reconfigure X as part of the installation. Good for you. Only your experiences matter, apparently. > And many wireless cards just work - and not everybody uses wireless. And many don't. So what?

> 
Most of the time, I can hand someone a cd and tell them roughly how to install and it goes fine. And the other times, people might need to use the command-line.

---

### Post by gingermark on 2006-05-31
I'm with aysiu on this one, although (as mentioned before) with each release the hardware recognition gets better and better.

I've had to reconfigure X when installing, as sometimes I don't make it into X or if I do I'm using vesa.

I'm not sure how useful speculating on what a user may or may not do when installing Ubuntu is. But I do know that the command line is useful if one does run into a problem! :)

---

### Post by az on 2006-05-31
[QUOTE=aysiu]Two. Why does it matter? I've seen enough people on these forums have issues with wireless and X. Do you want to make the statement that only with rare exception do people ever need to configure wireless or video cards/monitors? [/QUOTE]

Well, if it works out-of-the box, why would you ask for help on a forum?

[QUOTE=aysiu]
 Good for you. Only your experiences matter, apparently.  [/QUOTE]

Is that your way of saying you dissagree?  Dude, chill.

[QUOTE=aysiu]
And many don't. So what?

 And the other times, people might need to use the command-line.[/QUOTE]

Your conclusion that you need to use the command line to install ubuntu is false.  It's correct to say that you sometimes need to use the command line.  And those issues are being addressed aggressively.

I'm not saying that the command line is a bad thing.  I'm saying that you don't need to know/feel comfortable with/advocate the command line to use/install Ubuntu.

---

### Post by aysiu on 2006-05-31
Telling someone she does not need the command-line to install Ubuntu is false.

Yes, the people who ask for help are by definition people who have problems, but there are *a lot* of people who ask for help with configuring X. It's not like the number of people who ask for help installing the latest version of aMSN or the number of people asking for help setting up Cisco VPN. The numbers are much bigger for getting a simple monitor and video card set up.

I don't think it's *difficult* to get these things set up (usually you just need to add a line or two to the /etc/X11/xorg.conf file), but it does require command-line use.

Will *everyone* need to use the command-line to configure Ubuntu? Of course not. But to not at least warn people it might be necessary for getting everything working is misleading and careless.

[quote=azz]Your conclusion that you need to use the command line to install ubuntu is false.[/quote] When did I say "You need to use the command-line to install Ubuntu"? Please point that post # out to me. Thanks.

There are distributions that allow you to reinstall Grub with your mouse, configure X with your mouse. Until Ubuntu can do those things, I will at least warn people they may need to use the command-line to install and configure Ubuntu. You can mislead people all you want.

---

### Post by 2501 on 2006-05-31
I am old school but I have to admit that if you really want to have control of your OS, you must use the command line. I started back in 1983 and we had no choice but to use the command line until Amiga messed the whole thing. But at the same time it was a big step for computing because GUIs were created to make life easier.

If you want to run linux, you have to use the command line. It is fun!!!!!!!!!

-2501

ps: I love Amiga too.

---

### Post by ProjectGod on 2006-05-31
meeoowwwww!

why use the command line? well its got an aesthetic aspect to it... its esoteric and abstruse. its... nevermind. :D

i like the terminal cause if you know enough of it and start getting into bash scripting... you get paid quite a lot!!! which means more cat food for me :mrgreen:

---

### Post by az on 2006-05-31
[QUOTE=aysiu]

Will *everyone* need to use the command-line to configure Ubuntu? Of course not. But to not at least warn people it might be necessary for getting everything working is misleading and careless.[/QUOTE]

I wouldn't put it that way, myself, but I agree with what you are saying.

[QUOTE=aysiu]
 When did I say "You need to use the command-line to install Ubuntu"? Please point that post # out to me. Thanks.
[/QUOTE]
Number 19.

I don't wanna argue about this.  We dissagree.  I think pimping the command line to people who do not know about linux and are somewhat hesitant is doing them a disservice.  I think the default desktop will work fine for the majority of people and talking about the command line (warning) will probably scare them away from Ubuntu rather than make them want to actually install.

That's why the installer strives to be as simple as possible and ask as few questions as possible.

---

### Post by aysiu on 2006-05-31
[QUOTE=azz]
Number 19.[/quote] I never said you needed the terminal. Please re-read #19.

> 
I don't wanna argue about this.  We dissagree.  I think pimping the command line to people who do not know about linux and are somewhat hesitant is doing them a disservice.  I think the default desktop will work fine for the majority of people and talking about the command line (warning) will probably scare them away from Ubuntu rather than make them want to actually install.

That's why the installer strives to be as simple as possible and ask as few questions as possible. There's a difference between "pimping the command-line" and acknowledging that you may, in fact, need it to get Ubuntu working. If people are deathly afraid of the command-line, I wouldn't recommend installing Ubuntu unless I knew 100% that Ubuntu would detect all hardware on that person's computer.

I think you might have just misunderstood what I was implying.

We both agree that Ubuntu will in many situations not require the command-line for installation/configuration, and in other situations it will. We also both agree that pushing the command-line on people who don't want it is a bad idea, but false assurances that the command-line is definitely unnecessary is also a bad idea.

---

### Post by uzi09 on 2006-05-31
my reasons:

1) VERY VERY (did i mention VERY) fast :D (as mentioned numerous times before)
not only in processing, but also the fact that as soon as i think of it, i just type part of its name and hit [tab] [enter] and its running, with gui's u gotta think about it, then try to remember where u saw it last, go through the menus and when you find out where it is, finally initiate a click to start it up. not only that, you then have to wait for the system intensive graphics to load and be displayed ](*,) 

2) when you've mastered the terminal, you know how it all works. then when you're using a gui, u can tell exactly what places take long and a lot of the times figure out where the problem might exist. it's sometimes easier to troubleshoot through the terminal since everything is in front of and not all done behind the scenes with a pretty lil bar running across the screen :-D 

3) oh man, it -- along with yourself ;) -- looks damn cool! :twisted:

---

### Post by Marcelino on 2006-06-02
I use The Terminal, mainly because I can have root right for some operations.

---

### Post by robins_web on 2006-06-02
Well, you can (for example) use the command line to search all of your text files for a specific string of text, write the results to a new file (along with the total number of lines it found, as well as the file names and their locations), and load the new file for either viewing or editing.

As Stan Freberg once said (in another context) "Let's see you do ***that*** on TV!"

---

