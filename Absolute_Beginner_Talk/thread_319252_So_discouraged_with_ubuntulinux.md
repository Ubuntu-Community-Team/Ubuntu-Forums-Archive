---
title: "So discouraged with ubuntu/linux"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by danieltowsey on 2006-12-15
I am very new to this linux thing. I installed this program a few days ago. and I have spent the last three days trying to fix problems. I am very very discouraged with all the things that don't work. The list is endless. I don't think I will be using this program much more. I have duel boot XP...I think I will go back to only using XP....heres a few more of the problems I found. my printer prints blank pages, my Gaim messenger shows me a blank buddies list, when I download files (programs) I can't open any of them. It either tells me they are not supported, or they just can't be opened for a number of different reasons. also when I go to add remove and add things..all seems ok. then when it completes it installed nothing...So if you have some magical words of inspiration to tell me now why I should continue to use linux. Nows your chance..because I am soon about to give it up for ever.....

---

### Post by lance_klusener on 2006-12-15
Dont worry man , after all the problems are fixed u will fall in love with linux and will no longer use windows

---

### Post by Ben Sprinkle on 2006-12-15
Don't throw in the towel just yet, all of these things are fairly easy to fix.
What file types are you trying to open?

---

### Post by danieltowsey on 2006-12-15
I am now believing that I will never be able to fix all the problems..for example I downloaded an ISO for making a Grub backup disk. When I went to burn it, it came back that an error occured and I wasted a disk....there are many more things that don't work..

---

### Post by Ben Sprinkle on 2006-12-15
Try searching [the Ubuntu wiki](http://wiki.ubuntu.com) for some of your issues.

---

### Post by adewale on 2006-12-15
don't give up. i don't use a printer so i can't help u with that but check the hardware section. about gaim are ur contacts online and did u choose the option to display offline contacts? and the best way to install is through synaptic

---

### Post by Hendrixski on 2006-12-15
Sorry to hear that.  I have used many different operating systems, and I have to say Linux is the best.  I use it at work, and I have had no real problems with it.  Compared to installing and configuring windows XP, Ubuntu is easy and fast.

Setting up the printer is easy.  If you type in localhost:631 into your browser you are given a webpage through which you can add or remove printers.  If they are not working just try installing a different driver.  that said, printers are ALWAYS a problem regardless of which operating system you are on.  You have to tinker with it.

If you are behind a firewall Gaim may not work optimally.  I cannot use it at work for example.  But if you log in with your existing username and password it will download your buddylist from AOL's server.  :) easy

The install tool does install stuff trust me, it may just not show up on your menu automatically unless you select an option.  If you go to preferences --> menu options you will see what programs you have installed compared to which ones are showing on the menu, and can show them there.

:) It's really easy, just don't be afraid to ask for help.  that's what we're here for.  We're a community.   Welcome :)

---

### Post by danieltowsey on 2006-12-15
> **Goat Spirit said:**
> Don't throw in the towel just yet, all of these things are fairly easy to fix.
What file types are you trying to open?
I'll give you an example..I went Gaim messenger site to download some other files to try and fix the problem..then after I downloaded them..none could be opened..I tried many different ones.

---

### Post by igknighted on 2006-12-15
It sounds to me like you did not do a lot of research before you jumped in.  Linux is nothing like windows, so in order to learn it you must throw away your previous assumptions.

First, what type of printer do you have, and have you checked to see if it is supported by Ubuntu?

Second, thats a really weird Gaim error, I've never seen that before.  Double check your connection info, and if that doesn't work you can download AIM for linux or Kopete, both are fine IM clients.

Third, what files are you downloading to install.  If they end in .exe, they are windows programs and are no good.  If they are .rpm they are for other forms of linux and you need to convert them.  If they are .deb they should install fairly painlessly, and if they are .tgz, .tar.gz, .tar.bz2 etc. they are archives (think .zip in windows) and must be extracted.  Inside there should be a text file with install instructions, or the instructions will be available on the website you downloaded from.  As a general rule, downloading programs from websites is a bad idea (in windows or linux, but in windows you don't have an alternative.  In linux, almost any program you could want is available in the Ubuntu repositories, so always check there first.  The other errors you are getting are likely permissions errors.  As a normal user you have no rights to edit the system files.  In order to do this you need to temporarily assume admin rights, via the 'sudo' command.  Any time you need to issue a terminal command as the sys-admin (known as root in linux) you need to put sudo before the command.

As for add/remove, have you searched the Applications menu for the program?  If this has not worked, try launching the program by typing its name in all lower case in the terminal.  This will let you know if its there or not.

I am not going to tell you to staywith linux if you dont want to.  I am going to warn you that it is a lot to learn, and tell you that once you learn what you are doing you will be a far more well rounded computer user and understand what you are doing on a computer better, in windows and linux.  If this is interesting to you, stick it out.  If it sounds loke a lot of work, it is at times, so be ready.  That said, I *do* hope you stay and join the community.  Good luck.

---

### Post by taurus on 2006-12-15
Again, the problem began when you created a user account by hand and removed oem by hand!!!  If you installed Ubuntu using oem option, then you needed to run this command after logging in for the first time with the oem account...

```
sudo oem-config-prepare
```
That would cure a lot of problems that you are experiencing right now!!!

Are you running Dapper or Edgy right now?

---

### Post by kapilg_it on 2006-12-15
when things go wrong dont' assume that you are going in wrong direction.
I thought of using my winter vaccations in studying about squid and squish ,got chance to use Ubuntu and now I m nearly seduced by it (by its straight forwardness and simplicity) . Never was this *NIX community so ready ,to give world a desktop edition.
You may probably using misconfigured system .

moreover u didn't even told what version are u using ?

---

### Post by danieltowsey on 2006-12-15
> **danieltowsey said:**
> I'll give you an example..I went Gaim messenger site to download some other files to try and fix the problem..then after I downloaded them..none could be opened..I tried many different ones.
I have spent the last three days doing nothing but searching for answers..I am an advanced windows user...I can fix just about anything on windows...but this ubuntu thing is just to screwed up...

---

### Post by danieltowsey on 2006-12-15
> **kapilg_it said:**
> when things go wrong dont' assume that you are going in wrong direction.
I thought of using my winter vaccations in studying about squid and squish ,got chance to use Ubuntu and now I m nearly seduced by it (by its straight forwardness and simplicity) . Never was this *NIX community so ready ,to give world a desktop edition.
You may probably using misconfigured system .

moreover u didn't even told what version are u using ?
I am using Ubuntu 6.06 LTS

---

### Post by igknighted on 2006-12-15
> **danieltowsey said:**
> I have spent the last three days doing nothing but searching for answers..I am an advanced windows user...I can fix just about anything on windows...but this ubuntu thing is just to screwed up...

Think about how well you could fix problems the first weeks you were on windows... assume the same thing here.  It takes time to learn the OS.

---

### Post by danieltowsey on 2006-12-15
> **adewale said:**
> don't give up. i don't use a printer so i can't help u with that but check the hardware section. about gaim are ur contacts online and did u choose the option to display offline contacts? and the best way to install is through synaptic
The gaim program is the one I installed when I was 'oem' user..and it displays nothing..

---

### Post by igknighted on 2006-12-15
> **danieltowsey said:**
> The gaim program is the one I installed when I was 'oem' user..and it displays nothing..

That might be the problem, you as a standard user might not have the permissions to use it.

---

### Post by danieltowsey on 2006-12-15
> **taurus said:**
> Again, the problem began when you created a user account by hand and removed oem by hand!!!  If you installed Ubuntu using oem option, then you needed to run this command after logging in for the first time with the oem account...

```
sudo oem-config-prepare
```
That would cure a lot of problems that you are experiencing right now!!!

Are you running Dapper or Edgy right now?
I am sure you are right..I did not do that..and at the time I was completely new to linux..I spent hours trying to find a command widow..no where was there any information on the net on such a simple thing...no one told me it was in the terminal..I did not know what a terminal was...so I just deletted the oem...now I am here..

---

### Post by danieltowsey on 2006-12-15
> **igknighted said:**
> That might be the problem, you as a standard user might not have the permissions to use it.
I think I screwd things up at the beginging when I just deletted the 'oem' user and created a new user..but when I did that I gave it admin privaledges..then I discovered I did not get any admin privaledges

---

### Post by deadgobby on 2006-12-15
I understand your getting upset with Linux. As some one said. "Linux is not windows." I was getting mad at Linux at first because I was trying to do windows things. Then I made it my goal to learn Linux. There are load of people here and there willing to help you. You'll get to know the Terminal, Synaptic which has loads of programs to install, Wine which can run some windows programs, and much more. If you want to start easy with Linux. There is Linspire to come off the to of my head.  Here are some links to help you understand Ubuntu
[http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
All so there is a little Life Saver ring on top of your monitor to help you out too.


Gobby

---

### Post by danieltowsey on 2006-12-15
> **Hendrixski said:**
> Sorry to hear that.  I have used many different operating systems, and I have to say Linux is the best.  I use it at work, and I have had no real problems with it.  Compared to installing and configuring windows XP, Ubuntu is easy and fast.

Setting up the printer is easy.  If you type in localhost:631 into your browser you are given a webpage through which you can add or remove printers.  If they are not working just try installing a different driver.  that said, printers are ALWAYS a problem regardless of which operating system you are on.  You have to tinker with it.

If you are behind a firewall Gaim may not work optimally.  I cannot use it at work for example.  But if you log in with your existing username and password it will download your buddylist from AOL's server.  :) easy

The install tool does install stuff trust me, it may just not show up on your menu automatically unless you select an option.  If you go to preferences --> menu options you will see what programs you have installed compared to which ones are showing on the menu, and can show them there.

:) It's really easy, just don't be afraid to ask for help.  that's what we're here for.  We're a community.   Welcome :)
Thanks for the help...I think taurus is on the right track..it all started by me just creatinfg a new user with adm and deletting 'oem' user..but I discovered I did not get any adm with my new user.

---

### Post by igknighted on 2006-12-15
> **danieltowsey said:**
> Thanks for the help...I think taurus is on the right track..it all started by me just creatinfg a new user with adm and deletting 'oem' user..but I discovered I did not get any adm with my new user.

If you want to get a fresh start try reinstalling to your current partition, then you wont make the same mistakes as before... I went through a phase where I reinstalled several times a week just because (a) I wanted to try different distros and (b) I would mess with it until I broke it then start over.  Sometimes trial and error is the best way to learn.  Then again, I was on summer break from college so I had the time to do that, but if you do have the time it's fun to try.

---

### Post by danieltowsey on 2006-12-15
> **igknighted said:**
> It sounds to me like you did not do a lot of research before you jumped in.  Linux is nothing like windows, so in order to learn it you must throw away your previous assumptions.

First, what type of printer do you have, and have you checked to see if it is supported by Ubuntu?

Second, thats a really weird Gaim error, I've never seen that before.  Double check your connection info, and if that doesn't work you can download AIM for linux or Kopete, both are fine IM clients.

Third, what files are you downloading to install.  If they end in .exe, they are windows programs and are no good.  If they are .rpm they are for other forms of linux and you need to convert them.  If they are .deb they should install fairly painlessly, and if they are .tgz, .tar.gz, .tar.bz2 etc. they are archives (think .zip in windows) and must be extracted.  Inside there should be a text file with install instructions, or the instructions will be available on the website you downloaded from.  As a general rule, downloading programs from websites is a bad idea (in windows or linux, but in windows you don't have an alternative.  In linux, almost any program you could want is available in the Ubuntu repositories, so always check there first.  The other errors you are getting are likely permissions errors.  As a normal user you have no rights to edit the system files.  In order to do this you need to temporarily assume admin rights, via the 'sudo' command.  Any time you need to issue a terminal command as the sys-admin (known as root in linux) you need to put sudo before the command.

As for add/remove, have you searched the Applications menu for the program?  If this has not worked, try launching the program by typing its name in all lower case in the terminal.  This will let you know if its there or not.

I am not going to tell you to staywith linux if you dont want to.  I am going to warn you that it is a lot to learn, and tell you that once you learn what you are doing you will be a far more well rounded computer user and understand what you are doing on a computer better, in windows and linux.  If this is interesting to you, stick it out.  If it sounds loke a lot of work, it is at times, so be ready.  That said, I *do* hope you stay and join the community.  Good luck.
Your message is great and I really appreciate your kind hearted effort...I have two printers and one is working...I am printing your message out for reference...what is and where is a Ubuntu repository...and I am a fast learner..I do want to learn to use linux..It has already shown me many things that I really like..my opinion of it is not all bad...plus it downloads really fast and it is not a cpu hog....I only have an 800megahertz processor..

---

### Post by danieltowsey on 2006-12-15
> **deadgobby said:**
> I understand your getting upset with Linux. As some one said. "Linux is not windows." I was getting mad at Linux at first because I was trying to do windows things. Then I made it my goal to learn Linux. There are load of people here and there willing to help you. You'll get to know the Terminal, Synaptic which has loads of programs to install, Wine which can run some windows programs, and much more. If you want to start easy with Linux. There is Linspire to come off the to of my head.  Here are some links to help you understand Ubuntu
[http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
All so there is a little Life Saver ring on top of your monitor to help you out too.


Gobby
Thanks I'll check the links...another thing that happened, when I installed I pick 1280x1024 screen resolution...and I ended up with a smaller diferent one..I tried to reset it and the size I need is not available

---

### Post by danieltowsey on 2006-12-15
thanks

---

### Post by danieltowsey on 2006-12-15
I have to say its a huge learning curve and mine I have been sliding down fast..It will hurt when I hit the ground...

---

### Post by danieltowsey on 2006-12-15
Well I have lots of time I am older now and unemployed on disability...I have a duel boot with XP..so how can I reinstall ubuntu without messing up my grub or duel boot?

---

### Post by igknighted on 2006-12-15
> **danieltowsey said:**
> Your message is great and I really appreciate your kind hearted effort...I have two printers and one is working...I am printing your message out for reference...what is and where is a Ubuntu repository...and I am a fast learner..I do want to learn to use linux..It has already shown me many things that I really like..my opinion of it is not all bad...plus it downloads really fast and it is not a cpu hog....I only have an 800megahertz processor..

Repositories are servers that store programs for you online.  If you install from the official repo's (I think they have some 20,000 programs available or so) then you know you are not at risk of downloading any kind of malicious software.  If you open the synaptic package manager (system->administration->synaptic package manager) and then go to the 'settings tab'->repositories you can choose which repo's to search when you are looking to install software.  I usually enable them all.  Another thign to try is automatix2, which will help install a lot of the software new users want automatically.  Check it out a ww.getautomatix.com.  Everything it does you could do yourself, but if you want a little quick help to get going check it out.

As far as the other printer, if it is not a lexmark is should be able to work... lexmarks and linux do not get along.

---

### Post by danieltowsey on 2006-12-15
Thanks that is very helpful information..but i think I need to reinstall ubuntu properly..but can it be done without screwing up my XP duel boot?

---

### Post by igknighted on 2006-12-15
> **danieltowsey said:**
> Well I have lots of time I am older now and unemployed on disability...I have a duel boot with XP..so how can I reinstall ubuntu without messing up my grub or duel boot?

You would install over the old grub, but it should recognize XP so you shouldn't need to configure it each time.  Just put the live CD in, follow the instructions, use manual partitioning, edit the current Ubuntu partition and change the mount point to /.  It will want to reformat it, let it.  **Make sure that the NTFS drive is not on the list to be formatted**.  Then let it do its thing.  Should give you a fresh install, as well as let you set up your own user account.  You wont have admin powers unless you use 'sudo'.  Thats how Ubuntu works, its a security feature.

---

### Post by danieltowsey on 2006-12-15
I don't anything about Sudo

---

### Post by meng on 2006-12-15
Search the wiki (wiki.ubuntu.com), there's an article called RootSudo.

I think we should have a new rule in these forums. NO WHINING!

---

### Post by danieltowsey on 2006-12-15
Your help is appreciated but your comment wasn't..your comment actually sounds like your whinning...have a good day

---

### Post by gn2 on 2006-12-15
Try PCLinuxOS before you give up altogether on Linux.......

---

### Post by Ben Sprinkle on 2006-12-15
> **danieltowsey said:**
> I'll give you an example..I went Gaim messenger site to download some other files to try and fix the problem..then after I downloaded them..none could be opened..I tried many different ones.

WHAT ARE THE EXTENSIONS?!

---

### Post by danieltowsey on 2006-12-15
What is PCLinux ? and how do I get it?

---

### Post by meng on 2006-12-15
> **danieltowsey said:**
> Your help is appreciated but your comment wasn't..your comment actually sounds like your whinning...have a good day
Sorry you were offended, it wasn't intended that way but instead as a suggestion that you may be more likely to get help if you ask for it in the right spirit. Have a great day yourself.

---

### Post by Ben Sprinkle on 2006-12-15
Ugh I'm out, your pissing me off.

---

### Post by danieltowsey on 2006-12-15
I will try to resolve this problem with Gaim after I reinstall ubuntu..and another person gave some pretty good answers to this problem..that i will try later...thanks for your help!

---

### Post by gn2 on 2006-12-15
Here it is: [http://www.pclinuxos.com/page.php?7](http://www.pclinuxos.com/page.php?7)

Go for Big Daddy it's got plenty software.

It has configuration through the Control Center and is very straightforward and easy to use.

Almost everything is set up ready to go, no mucking about finding codecs etc.....

You can always come back to Ubuntu when you are more experienced in Linux.

---

### Post by TooRight on 2006-12-15
Not knowing about sudo is what's causing alot of problems for you I think... on windows when you're the admin user, you're the admin user, you have admin privileges from when you log on to when you log off... not so with Linux. With Linux you're only using your admin privileges when they are actually needed, like when you install programs etc... this is one of the reasons why Linux is so secure :D

Placing the word "sudo", (think "Super User DO"), before a terminal command tells the machine that you are the admin user and that you're giving permission for the command to be carried out. The system then prompts you for your root password and carries out your command.

---

### Post by danieltowsey on 2006-12-15
> **TooRight said:**
> Not knowing about sudo is what's causing alot of problems for you I think... on windows when you're the admin user, you're the admin user, you have admin privileges from when you log on to when you log off... not so with Linux. With Linux you're only using your admin privileges when they are actually needed, like when you install programs etc... this is one of the reasons why Linux is so secure :D

Placing the word "sudo", (think "Super User DO"), before a terminal command tells the machine that you are the admin user and that you're giving permission for the command to be carried out. The system then prompts you for your root password and carries out your command.

I fixed the major problem I had. I reinstalled ubuntu. I made a big mistake in the first install...thanks for explaining Sudo..now I need to learn how to make my other drives accesible..to mount them

---

### Post by d3v1ant_0n3 on 2006-12-15
Here ya go:

[Howto for mounting NTFS (Windows) Partitions](http://www.psychocats.net/ubuntu/mountwindows)

I *LOVE* how good search is on this forum:D 

Good to see you haven't given up! When I first installed, I had no idea where anything was, or how anything worked...but I'm getting there. Remember, if you've been a windows power user for x amount of years, thats x amount of years worth of different habits you'll need to shake. I find windows very odd to use now, and constantly find myself thinking 'why on earth did they make it so hard to use??'. It's not hard. It's just different. Works both ways.

---

### Post by Kazna on 2006-12-15
You should stick with it and play about with it first. I'm not a fan or devotee of something/;someone but if a product is good obviously I like that and would respect that, as well as its helpers. I'm new to Linux but already have 4 installations carried out today working well. I love it but obviously there a few issues to play around with. 
Install it, but on another HDD is my advice. Play about with it separately in spare time, do what you want and when happy and learnt through experience, trial and errors with no worries and limitations of messing the dual boot OS's up, then put it on your main HDD alongside Win. 
I've used many Mac and Win OS's but only my first Linux and its looking good.

Sudo will be just one of the many things but be patient and for that, you need to plan/backup well. :)

---

### Post by danieltowsey on 2006-12-15
Well I agree with you..thanks for the link and I am presently going through the advanced add remove programs....its going to take many hours to go through it.  but it sure has alot of great stuff..alot of it I have no clue about...But I feel now that I should of got into linux years ago..I am now seeing what i missed....I am thinking its very good..but I am still not ready to give up the problem riddled xp

---

### Post by gn2 on 2006-12-16
> **danieltowsey said:**
> but I am still not ready to give up the problem riddled xp



At least with Linux the problems are free and you aren't paying large amounts of cash to Mr Gates & Co for them  :)

---

### Post by xpod on 2006-12-16
> At least with Linux the problems are free and you aren't paying large amounts of cash to Mr Gates & Co for them

Hey gn2 ...i cant complain about any £££££ that M$ cost me during my few months with them as i picked my old machines up with XP already on them and every program i ever used or NEEDED i was  able to find quite decent free(££££) versions of........:rolleyes: 

AVG,Spybot,adaware,hyjackthis,ccleaner,ewido,scandefrag,cwshredder,registry repair pro,zonealarm,scan this,clean that,run this and check that ...etc etc etc etc etc etc etc etc](*,) ...LOL

XP.O.D`d...R.I.P:mrgreen:....and a happy new year

---

### Post by xyz on 2006-12-16
So you "have spent the last **three days** trying to fix problems."
Don't take me wrong but, tell me, what **valuable** stuff have you ever learned in 3 days?

Hang in there! My humble advice is that you set Ubuntu aside for a while and go back to it when *you feel better*...so to speak. And next time you may not spend 3 entire days on it; dig into it one step at a time.
Good luck!

---

### Post by xpod on 2006-12-16
> So you "have spent the last three days trying to fix problems."
Don't take me wrong but, tell me, what valuable stuff have you ever learned in 3 days?

+1
"Taking a step back" when it`s mabey all getting too much at once is one of the best bits of advice i`ve been given these last  9 months or so on a pc.

Sometimes we can be trying far too hard to focus on some particular issue that we just cant see
whats right in front of us.......it`s my speciality:D 
Especially if we`re trying to figure numerous things at once;)

---

### Post by _simon_ on 2006-12-16
Printer printing blank pages = wrong print driver. What printer is it?

Gaim blank buddies list - you sure you haven't got offline buddies hidden and no-one is online?

To display offline buddies -> Buddies -> Show Offline Buddies

---

### Post by TooRight on 2006-12-16
Ahhh, but after days of messing with it is where the magic comes in!! Those moments when lil things are all of a sudden crystal clear to you... those moments are pricelessssssss!! I get suchh a natural high from my Ubuntu:D:D

If ya really want to have some fun after you get your basics set up (hardware, audio, video, java, flash etc), then head on over to [http://kde-look.org](http://kde-look.org) and think about adding the Kubuntu desktop... it rocksssssssss!!!

---

### Post by xpod on 2006-12-16
> Ahhh, but after days of messing with it is where the magic comes in!! Those moments when lil things are all of a sudden crystal clear to you... those moments are pricelessssssss!! I get suchh a natural high from my Ubuntu

TOO RIGHT TooRight:D

---

