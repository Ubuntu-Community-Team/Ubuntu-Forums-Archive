---
title: "Problem with the &quot;gksudo gedit 'file' &quot; command"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by mahasmb on 2007-08-29
I was trying to open a file so I can edit it.

I type the following
```
gksudo gedit /etc/network/interfaces
```

and I get this screen for five whole minutes before the file actually opens up  (see thumbnail)

However, with the following command
```
gedit
```

the file opens instantly. What's the problem here?

---

### Post by julian67 on 2007-08-29
I'm not sure why it's like this but it was the same for me. There are a couple of easy solutions. You could install a different text editor such as leafpad, or you could use vim which is already installed and is a terminal based app so it's always available even if X fails and it doesn't depend on any particular desktop environment or window manager etc. It's rather different from using a notepad type editor but [The Vim commands cheat sheet]("http://www.tuxfiles.org/linuxhelp/vimcheat.html") will get you up and running. And being a terminal app it will match your ubuntustudio theme.....

---

### Post by mahasmb on 2007-08-29
Thanks, but I wanna see if I can actually fix this because gedit is not the only program acting this way. I'm having the same problem with Network Manager.

---

### Post by rsambuca on 2007-08-29
Are you running compiz or beryl?

---

### Post by mahasmb on 2007-08-29
Neither

---

### Post by rsambuca on 2007-08-29
Does it prompt you for a password at all?

---

### Post by mahasmb on 2007-08-29
Yes. Remember, like I said it takes at least 5 minutes if not more for the programs to actually show up right.

---

### Post by rsambuca on 2007-08-29
OK, do you mean it takes 5 min for the password prompt window to open, and then another 5 min for the gedit program to open?, or does the password prompt window open right away?  You haven't been very specific with your descriptions.

---

### Post by diatribe on 2007-08-29
you could use sudo instead and see if it works

---

### Post by rsambuca on 2007-08-29
> **diatribe said:**
> you could use sudo instead and see if it works

No, you don't want to use sudo with graphical programs.

---

### Post by HermanAB on 2007-08-29
$ gksudo "gedit filename"

Cheers,

Herman

---

### Post by Harpoon on 2007-08-29
Try running "gksu gedit" rather than "gksudo gedit" and see if that helps.  I am trying to resolve a minor bug on my setup that returns an "authorization failed" error when using gksudo, hangs for a bit, then proceeds to load and run gedit properly anyway.  Sounds similar, if not exactly the same, to me.

---

### Post by mahasmb on 2007-08-29
I have been specific...

> **mahasmb said:**
> I was trying to open a file so I can edit it.

I type the following
```
gksudo gedit /etc/network/interfaces
```

and I get this screen for five whole minutes before the file actually opens up  (see thumbnail)

However, with the following command
```
gedit
```

the file opens instantly. What's the problem here?

There's no problem with the password prompt.

I type the above gksudo command. It prompts me in a sec, I enter my password in a second.

Then I get the above picture (in my thumnails of my initial post) for like 5 minutes, with the mouse showing that it's still loading or something. Then 5 or 10 minutes later I can finally see the contents of the file.

It's the same for NetworkManager. It just shows a window with no text, hangs there for minutes and minutes and then finally decides it's ready to work.


**EDIT:** Neither HermanAB's or Harpoons methods work. Thanks though.

---

### Post by Harpoon on 2007-08-29
Sorry that didn't get around your problem, but at least it was an easy try.  I am fussing with my setup trying to duplicate the problem, but without success so far.  If anything turns up I will get back to you.

---

### Post by Harpoon on 2007-08-29
If my understanding of what you have been saying is correct, then just about everything you try to do with "gksudo" is somehow fouled, and running without is OK.  This makes me wonder if gksudo, itself, may have been couled up in some way along the line.  

A relatively safe option is to go into the synaptic package manager, search  for gksudo, and reinstall it.

God, that sounds like either a really fudgy solution, or one from a die hard windows user.  Sorry. (but it just might work)

---

### Post by asmoore82 on 2007-08-29
are you sure you don't have some form of "Desktop Effects" enabled? :confused:

---

### Post by rsambuca on 2007-08-29
> **asmoore82 said:**
> are you sure you don't have some form of "Desktop Effects" enabled? :confused:

Yeah, that's why I asked about compiz or beryl.  I honestly think that is the problem.

---

### Post by mahasmb on 2007-08-29
I have Ubuntu Ultimate Edition 1.4 installed.

I definitely don't have any "Desktop Effects" enabled. In fact, I just tried to enable desktop effects 10 seconds ago and it wouldn't let me. I get the error "Desktop Effects could not be enabled"

I haven't touched Beryl or Compiz since installation.

Harpoon's right. Pretty much anything that requires gksudo takes forever. But there's no  package for "gksudo" in Synaptic Package manager. There is a "sudo" package though.

I also notice that the following programs are also taking 5-10 minutes to open even though I never open them with a "gksudo" or "sudo" command. 

- Wireless Assistant 0.5.7
- Azureus

For Wireless Assistant and Azureus though, nothing shows up for 5-10 minutes. But when it does, I can use either program right away. I don't know if this last bit is also connected to the gksudo problem.

All other programs seem to be working fine.

---

### Post by rsambuca on 2007-08-29
Wow, this is very strange.  If you have another program open prior to starting the gksudo... command, can you still use the other program during those 5 minutes, or is the computer basically dead except for the cursor?

Could it be related to the ultimate edition?  I know nothing of it.

---

### Post by asmoore82 on 2007-08-29
open a terminal and ...
```
~ $ ps -A | grep be
```
... post the output.

---

### Post by mahasmb on 2007-08-29
The computer is never dead. Just those programs I mentioned. Everything else works fine


```
maha@maha-dlu:~$ ~ $ ps -A | grep be
bash: /home/maha: is a directory
maha@maha-dlu:~$ 
 
```

---

### Post by rsambuca on 2007-08-29
You didn't answer my question.  If you have a program open (eg. firefox), and then you open a terminal and try to use gksudo gedit filename, can you still use firefox while you are waiting for gedit?

Also, in a terminal please enter this command```
ps -A | grep be
```

---

### Post by mahasmb on 2007-08-29
Yes. I said. "Everything else works fine"

While I'm waiting for any of those programs to open/load up I can do whatever else I want. (ie open firefox, use opera, check my system process, use nautilus, play chess etc. )

```
 maha@maha-dlu:~$ ps -A | grep be
 5749 ?        00:00:03 beagled
 5752 ?        00:00:01 beagle-search
 8274 ?        00:00:17 beagled-helper
maha@maha-dlu:~$ 

```

---

### Post by julian67 on 2007-08-30
I assume you're using alt+f2 to issue the command? Try it from the terminal and see what feedback you get. And while it's launching (or not) have a look at what the system is doing by using the top command ```
top
``` in another terminal tab and you might see where it's choking.

---

### Post by mahasmb on 2007-08-30
No, I don't use alt+f2. I use the terminal.

With the **top** command, what should I be paying more attention to? Memory? Because under "%MEM" it never goes over 20 (percent??) while trying to open the file.

Thank you everyone for your help so far.

---

### Post by julian67 on 2007-08-30
this might interest you [https://launchpad.net/ubuntu/+source/nautilus/+bug/71248]("https://launchpad.net/ubuntu/+source/nautilus/+bug/71248")

different application (nautilus) but same behaviour and an explanation of why it happens.

---

### Post by rsambuca on 2007-08-31
I have been looking for possible explanations.  Can you post your /etc/hosts file?  Some people have had success with similar type problems by defining the localhost name.

---

### Post by mahasmb on 2007-08-31
```
127.0.0.1	localhost
127.0.1.1	maha-dlu

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

I may not be able to reply readily for the rest of the weekend. I'll be away on a short trip. Thank you for all your help so far.

Also: 

```
maha@maha-dlu:~$ gksudo gedit /boot/grub/menu.lst
(gedit:14233): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

```

---

### Post by Harpoon on 2007-09-02
I have been chasing around for information on this for a while now.  What I have seen says that the "Authenication failed" error is common, and not attached to any single process/application other than gksudo.  For the most part it seems it can be ignored, for now.  The slow-down probably has its own source, and the error message is dovertong attention from finding out what that is (I could be wrong, of course,  I usually am - - ask my ex).

But:  looking at what you posted, you might want to take a look at this: [http://ubuntuforums.org/showthread.php?t=87798](http://ubuntuforums.org/showthread.php?t=87798)

I deals with ipv6 and internet performance, but I would be curious to see if it has any side effects (like mitigating your particular problem).

---

### Post by julian67 on 2007-09-04
It's hard to see how a problem with gksudo and gedit has anything to do with ipv6 or hosts file or localhost name.  The original query relates to opening a plain text file located on /

Again I suggest looking at [this bug]("https://launchpad.net/ubuntu/+source/nautilus/+bug/71248")  which is apparently now fixed.

---

### Post by louieb on 2007-09-04
Weird problem. **gksudo** is a link to **gksu**. and is in /usr/bin. Just on a lark that gksu has some twisted bits why don't you reinstall gksu. That is in Synaptic.

---

### Post by irish_flu on 2007-09-04
> **julian67 said:**
> It's hard to see how a problem with gksudo and gedit has anything to do with ipv6 or hosts file or localhost name.  The original query relates to opening a plain text file located on /


Not saying this *is* the problem, but hostname issues can cause all kinds of stuff to go badly; if gksudo looks for who is in the "sudoers" file, but doesn't know the hostname of the user (user@machine)\, it can cause issues doing anything with root privs.

I haven't seen that cause exactly this behavior, but have seen similar due to hostname issues.

---

### Post by rsambuca on 2007-09-05
> **irish_flu said:**
> Not saying this *is* the problem, but hostname issues can cause all kinds of stuff to go badly; if gksudo looks for who is in the "sudoers" file, but doesn't know the hostname of the user (user@machine)\, it can cause issues doing anything with root privs.

I haven't seen that cause exactly this behavior, but have seen similar due to hostname issues.

This was precisely what I was thinking, and why I suggested he post his /etc/hosts info.  Seems very strange, but others have reported very similar problems due to a hostname mismatch.

---

### Post by julian67 on 2007-09-05
which is all fine but there is a known, identified and apparently solved bug of this behaviour with gksudo on launchpad. I would study it and try the fix.

---

### Post by rsambuca on 2007-09-05
> **julian67 said:**
> which is all fine but there is a known, identified and apparently solved bug of this behaviour with gksudo on launchpad. I would study it and try the fix.

Fine.  I was throwing out a suggestion that takes 10 seconds to check and POSSIBLY could have solved his problem.  I will go elsewhere.

---

### Post by julian67 on 2007-09-05
> **rsambuca said:**
> Fine.  I was throwing out a suggestion that takes 10 seconds to check and POSSIBLY could have solved his problem.  I will go elsewhere.

All I'm saying is do the obvious first and check for known bugs before looking for answers elsewhere, no personal attack or suggestion that other answers are invalid.

---

### Post by Gone fishing on 2007-09-05
Sorry but can I ask why you shouldn't sudo with gedit. I use gksu rather than gksudo does it make any difference?

---

### Post by julian67 on 2007-09-05
> **Gone fishing said:**
> Sorry but can I ask why you shouldn't sudo with gedit. I use gksu rather than gksudo does it make any difference?

[http://psychocats.net/ubuntu/graphicalsudo]("http://psychocats.net/ubuntu/graphicalsudo")

edit: I believe that in Ubuntu with a gui program it makes no difference if you start it with gksu or gksudo

---

### Post by mahasmb on 2007-09-06
[https://launchpad.net/ubuntu/+source/nautilus/+bug/71248](https://launchpad.net/ubuntu/+source/nautilus/+bug/71248)

I've looked the above site over. Yet I still feel like I'm missing something.

Basically, it's saying the following would work? Whereas "myprog" is whatever program I want to launch?
```
sudo dbus-launch myprog 
```

This isn't working.

---

### Post by mahasmb on 2007-09-09
Anything?

Anyone?

Please?

It's really annoying waiting for 10+ minutes just for some programs to load.

---

### Post by julian67 on 2007-09-09
There's another bug on Launchpad [https://launchpad.net/ubuntu/+source/gksu/+bug/23917]("https://launchpad.net/ubuntu/+source/gksu/+bug/23917")

> Running from terminal an application that requires authentication (i.e. gksudo
network-admin) always returns this message:

(network-admin:10511): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified
are supported and host-based authentication failed.



> I am running dapper. From a terminal, just type (i.e.)

gksudo gedit

and I am getting this (in the terminal):

(gedit:10047): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols
specified are supported and host-based authentication failed.

Look familiar? I noticed that several of the people reporting experiencing this bug have used automatix and that you are using Ubuntu Ultimate which includes automatix.

> I first noticed it today while installing programs through automatix.

Ultimate is a non supported unofficial project and having looked at the list of superfluous buggy crap...er, excuse me I meant to say exciting alpha software...that it includes it's surprising it works at all. 

I'd strongly suggest using an official version of Ubuntu and adding the extra features/software you want as required by using the official tools and repositories as far as possible. Ubuntu (and any other distro) is so customisable that a modded version from an unknown 3rd party is an even worse idea than it first seems.

---

### Post by mahasmb on 2007-09-09
Yes, that's exactly my situation.

How bad an idea is it really to use Ubuntu Ultimate?

I'm using Ultimate not only because it'll save me hours and hours of installing various programs and configurations, but also because I've only been using Ubuntu for a few months partially and really wanted to get a broader and faster look at all the features and programs for Linux out there that just happen to come with Ubuntu Ultimate. This way I get to try out different programs and find out which are the best for me without bothering with installing and configuring them all myself (because of the time issue,  the chance I might mess something up, and the fact that I barely know most of the good LInux programs out there). I'm really fed up with computer problems and having to spend so much time just to make sure my laptop and desktop computers are working fine. It's the reason I'm switching from Windows XP.

Seriously, it took me way too long to configure and get all my programs set up when I did an official install with Dapper and Feisty on my laptop, so I figured that I'd use a faster *easier* route when I wiped Windows from desktop to install Ubuntu Ultimate.

I'm not complaining, just trying to explain my situation and circumstances so that you can better understand where I'm coming from.

Even with everything I've said above, you as a more experienced Ubuntu user, do you still think Ultimate is really that bad an idea? I ask because I am still learning and would really like to learn why Ubuntu Ultimate may be a bad idea.

---

### Post by Paul133 on 2007-09-09
Julian is worried that Ubuntu Ultimate may have unstable 'alpha' sotware that could contribute to problems. If you install regular Ubuntu and then ad programs, you'll start with a clean system and be able to tell what's screwing your system if you have problems. Of course, I'm not sure a program in UU is causing this, but it might be.

By the way, you don't have to use vim. If you want an easy (vi and vim are infamous for their learning terrible curves) terminal editor, just use nano. If you need to open a document, ```
sudo nano FILE
```
Then just type. Ctrl-O will save it, you can change the name, enter confirms the name change, and Crtl-X will exit.

---

### Post by julian67 on 2007-09-10
> **mahasmb said:**
> 

Even with everything I've said above, you as a more experienced Ubuntu user, do you still think Ultimate is really that bad an idea? I ask because I am still learning and would really like to learn why Ubuntu Ultimate may be a bad idea.

I think it's a really bad idea for several reasons.

It includes utilities that can break your OS

It's not officially supported. So if you get hit with a bug like this there is no comeback, it's your problem.  The OS cannot considered to be secure in the same way as the official distributions. There could be anything in there. It ships with a huge amount of stuff you almost certainly don't need or want, each of these can have security holes, bugs etc. It has it's own repository that has nothing to do with Canonical/official Ubuntu. So how can you be sure that the code in there is properly tested, stable and security checked and subsequently bugfixed as needed? You can't. You have to trust an unknown 3rd party with no obligation of any kind to you. 

It is mostly redundant. If you do a regular install of Feisty and spend a little time using it, trying stuff out,  and reading the official and community docs and howtos you'll find you can probably do everything you need to do, maybe even better than someone else does. 

It's worth it to spend a little time learning how to set up your PC but if you want a desktop with added features right out of the box you might be better off looking at Mepis.

---

