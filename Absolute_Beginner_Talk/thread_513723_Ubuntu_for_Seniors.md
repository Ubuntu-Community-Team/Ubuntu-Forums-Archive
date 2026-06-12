---
title: "Ubuntu for Seniors"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by Niklas Schröder on 2007-07-30
My grandma just moved to a new house and I'm heading out there in a few weeks to help her finish moving in.  One of my jobs is to get her computer back up and running.  But, I want to install Ubuntu instead of Windows to make life easier.  But, I want to make the user interface as SIMPLE as possible.

------------------------------------

*Need To Do:*

* NON-admin account (I don't want her to know the admin password.  that way, she can't screw up the system.)
* No Ubuntu splash/loading bar (When the system boots, I would like to either change that to a Windows logon or get rid of it.)
* Windows XP GDM login manager

*Want To Do:*

* Create a custom live CD to automate the install process (To get rid of the extra programs she won't need and save myself some time if I ever have to re-install.)

------------------------------------

I may add things as the next few weeks progress, but for now, those are the only issues.

------------------------------------

*Accomplished:*

* Found a dial-up how-to...  [https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)
* Auto login
* No Grub

---

### Post by ~~Tito~~ on 2007-07-30
Thats so cool, can you send me the cd too, I need one of those for my mom if you can try to get ie6 with full active x that would be so awesome I'll donate to you (after its done ;) ).

---

### Post by Niklas Schröder on 2007-07-30
lol.  i really meant for this to be more of an "ask for help" thread.  but i'll be happy to upload an iso once it's done!  :)  (that is, IF i get the live cd working.  :p )

---

### Post by dpar on 2007-07-30
Autologin is easy.
System>Administration>Login Window
Click on the Security tab, it's all in there.:)

As far as Grub screen goes, you can shorten the timer to 2 seconds or so.
It's in /boot/grub/menu.lst
Change timeout from 10 to whatever you want.

---

### Post by Niklas Schröder on 2007-07-30
thanks.  i actually just found that.  :p  now my problem is making it so she WON'T be the admin account...  and thanks for the tip on the grub loader.  :)

---

### Post by oilchangeguy on 2007-07-30
> **Niklas Schröder said:**
> thanks.  i actually just found that.  :p  now my problem is making it so she WON'T be the admin account...  and thanks for the tip on the grub loader.  :)

as long as she doesn't have the password, it doesn't matter if the one user is the admin account.

---

### Post by Niklas Schröder on 2007-07-30
i know.  but i'd rather not risk having her find out the password.  plus, i'd like to set up the admin account with compiz fusion and some other bells and whistles to make myself feel more at home when i'm over at her house.  ;)

---

### Post by oilchangeguy on 2007-07-30
> **Niklas Schröder said:**
> i know.  but i'd rather not risk having her find out the password.  plus, i'd like to set up the admin account with compiz fusion and some other bells and whistles to make myself feel more at home when i'm over at her house.  ;)

just set up another user account. and have that account auto start. then if you want to use the computer, select the switch user option from the shut down menu.

---

### Post by dpar on 2007-07-30
How about System>Administration>Users and Groups
Click on the user
Click properties
User priviliges tab

---

### Post by Niklas Schröder on 2007-07-30
ok.  cool.  thanks.  :)  -bangs head with heel of hand-  why didn't i think of that?  :p

---

### Post by yorkie on 2007-07-30
First of all its good to hear you say that you are going to set up your  Grandmothers computer up for her.Then you told us what you want to do to make it easier for her.We did not get any info what your Grandmother wants it is after all her computer so I take it that she knows how to use a PC.
I hope you are not assuming persons of a certain age are not capable to use computers productively.
If your Grandmother is comfortable with windows she may want to stick with what she knows best if on the other hand she would like to try Ubuntu, put the live cd in she can then see the differrence . If your Grandmother decides to have Ubuntu installed I don`t think the normal boot screen will be a problem and when it comes to the login & password the only problem is remembering the login/password so just write them down.
I have used windows off and on since 1984 I recently installed ubuntu dual booting with XP
I hardly ever boot into windows despite some of the problems I have with ubuntu so even at the young age of 57 we can still keep up with the latest o/s. Just think  your Grandmother gave birth to one of your parents so using a PC is a peice of cake for her .Best wishes to and you and your Grandmother'

---

### Post by Niklas Schröder on 2007-07-30
i'm sorry if my thread came across as saying that seniors can't use linux.  that's not at all what i meant!  sorry if i've offended anyone.  but my grandma's VERY technologically "impared" and i just want to make it as simple as possible for her.  one of the reasons i don't want the boot screen is because i don't want her to freak out every time she sees it.  cause she'd just end up calling me like she always does.  :p  and the other reason i'm putting ubuntu on her computer is because i'm sick of doing virus scans every time i come over just so her computer is workable again. (she doesn't care what she opens/looks at.  as long as it's sent to her by a friend, she thinks it's ok.)  so i'm really installing just to make my life simpler.  plus, all she needs to do is be able to get on the internet and check e-mail.  ;)  so i think she'll be fine with ubuntu.  i just want to make it as simple as possible so she's fully confident with it (she never was very confident with windows either).

---

### Post by the.phantom on 2007-07-30
i agree with yorkie !!!
and yep i am a senior citizen
if you just want a basic web browser and e-mail
i would say take a look at xubuntu
as it is a light weight version
but i think she should be the one that decides what she can learn ;-DD
my mother thought if she clicked the mouse wrong she would kill the computer ;-D

she was online surfing and e-mailing untill she passed away
i had a few basic "cheat sheets" for her to follow 
and it worked fine !!!!!


there are windows people that think Ubuntu is too hard so i would do a live cd and let her decide!

note ubuntu is a bit hard to get online with a dialup and even harder if a winmodem !!!

---

### Post by flatwombat on 2007-07-30
You may be selling Grandma a bit short.  I'm 62 and booting 7 distros at the moment.  I picked up linux when I retired and can comfortably handle anything that comes along in CLI or gui versions.  Frankly, I'd have been a bit ticked if someone wanted to deny me access because they thought my abilities might have been a bit limited, so talk it over with your Grandmother before you take such a step.

---

### Post by Niklas Schröder on 2007-07-30
no.  you guys don't know my grandma.  she calls me for EVERYTHING.  :p  and i'm sure about the ubuntu thing.  i'm going to install it and that's that.  i respect your opinions, but i'd rather just have help with my task.

and i'm up to the challenge of getting the modem working.  it means no more virus troubles for me!  yay!

---

### Post by dpar on 2007-07-30
Your probably doing the right thing.I'm 60 and have no problem with the ins and outs of computers, but my mother would freak if I tried to get her to do anything more than check email. Some people just don't want anything to do with anything complicated.:biggrin:

---

### Post by flatwombat on 2007-07-30
So, you've already got the basics down then; auto-login and shorten the boot through /boot/grub/menu.lst and change 'timeout'.   Why not keep her away from the menu by using desktop links to the packages she's likely to use almost continuously?  Firefox, Thunderbird or Evolution, perhaps Pidgin, maybe a Word Processor and Google Earth or Picasa. Got to add a few card games or whatever she likes there.   

Then, how about limiting the number of desktops to one, so that she suddenly doesn't find a blank desktop when she's browsing?

---

### Post by yeastpuppet on 2007-07-30
Your grandmother sounds just like my mother!

---

### Post by Niklas Schröder on 2007-07-31
lol.  yes.  the single desktop idea is a good one.

---

### Post by ugm6hr on 2007-07-31
> **flatwombat said:**
> Why not keep her away from the menu by using desktop links to the packages she's likely to use almost continuously?  Firefox, Thunderbird or Evolution, perhaps Pidgin, maybe a Word Processor and Google Earth or Picasa. Got to add a few card games or whatever she likes there.   


If you set desktop or panel launchers for all her apps, you could potentially remove the menu completely.  A lot simpler - and it would mean no ready access for her to modify the desktop (which might generate calls to repair to prior state), and no access to the Terminal to launch things without prior knowledge of Alt+F2.

You could even let her choose what to call the launchers (e.g. Internet rather than Firefox, Email rather than Thunderbird etc), and what icons to use ([http://www.iconarchive.com/](http://www.iconarchive.com/) has plenty of free ones to chose from if the included ones are not good enough).

Of course - this is all rather limiting - but if minimum service calls are what you are hoping for...

---

### Post by Niklas Schröder on 2007-07-31
yep.  that's what i'm planning on doing.  i'm gonna try to emulate the windows start menu and make it as simple as possible.  maybe add some shortcuts.

---

### Post by ugm6hr on 2007-07-31
Couple of links to XP-style login / splash themes (if you haven't seen them):
[http://www.gnome-look.org/content/show.php/XP+Ubuntu+?content=63163](http://www.gnome-look.org/content/show.php/XP+Ubuntu+?content=63163)
[http://www.gnome-look.org/content/show.php/XP+Ubuntu+GDM?content=63383](http://www.gnome-look.org/content/show.php/XP+Ubuntu+GDM?content=63383)

---

### Post by Niklas Schröder on 2007-07-31
cool!  thanks!  :)  EXACTLY what i was looking for!  :D

---

### Post by steevols on 2007-07-31
[http://gnome-look.org/content/show.php/Windoze+Professional?content=53906](http://gnome-look.org/content/show.php/Windoze+Professional?content=53906)

A great copy of XP Pro/Home's login screen.

EDIT: Oops, didn't see that last post :P

---

### Post by sailor2001 on 2007-07-31
well, I'm 80 and have to go on call for a lot of the "youngsters" (in the 60's) to fix their windows. Point is some ppl cannot grasp the workings of a computer no matter how long they bang on one.........and then there are others :)

---

### Post by bluenova on 2007-07-31
For making your own cd with splash screens etc, check out:
[http://reconstructor.aperantis.com/](http://reconstructor.aperantis.com/)

---

### Post by st33med on 2007-07-31
You could also try Freespire...


LOLz! No, rather, don't. I don't really trust the MS-Linspire relationship.

---

