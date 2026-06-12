---
title: "[SOLVED] changed GDM theme - from GnomeLook, now I can't log in!!!"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by MozartlovesUbun2 on 2007-09-25
Hi, I just installed the **"GDM Gartoon theme"** from gnomelook for a friend

did it the proper way: System> Administration> Login Window > Local > Add

link below:

[http://www.gnome-look.org/content/show.php/GDM+Gartoon+theme?content=13510](http://www.gnome-look.org/content/show.php/GDM+Gartoon+theme?content=13510)

now I can't log in anymore, it's just totally a black blank screen with the little small white circle spinning around which I guess shows it's doing something, but nothing happens...

plesae help, how can I go back to my normal GDM theme, this is ridiculous.

I can't believe it :mad:

I urgently need help on this as I've screwed up someone else's system

](*,) :( :mad:

---

### Post by Dr Small on 2007-09-25
Lemme see how I would go about doing it...
Hmm..

1.) CTRL + ALT + F2
2.) Login
3.) xinit -- :1 vt12
4.) gksudo gdmsetup

That's how I would get back in to change it.

Dr Small

---

### Post by MozartlovesUbun2 on 2007-09-25
> **Dr Small said:**
> Lemme see how I would go about doing it...
Hmm..

1.) CTRL + ALT + F2
2.) Login
3.) xinit -- :1 vt12
4.) gksudo gdmsetup

That's how I would get back in to change it.

Dr Small

thank you for the instructions, will that take me back to my default login page???

(sorry just to ask you did you try that GDM theme yourself, is it working for you?)

**step number 3 is a bit confusing to read, are there spaces inbetween?**

---

### Post by Dr Small on 2007-09-25
I have not tried that GDM, but here is step three, written out.

3.) xinit space dash dash space :1 space vt12


[xinit -- :1 vt12]

When you start gdmsetup, you can then change it back to default in there.

Dr Small

---

### Post by Dr Small on 2007-09-25
Make step 4 "sudo gdmsetup" as gksudo doesn't work.

Dr Small

---

### Post by MozartlovesUbun2 on 2007-09-25
> **Dr Small said:**
> I have not tried that GDM, but here is step three, written out.

3.) xinit space dash dash space :1 space vt12


[xinit -- :1 vt12]

When you start gdmsetup, you can then change it back to default in there.

Dr Small

H E L P, I'm totally desperate here

ok tried your instructions, on 3rd step it goes to a grey screen with the little white terminal window top left, ok

**now on the 4th step it says: "Failed to run gdmsetup as user root" - "unable to copy the user's Xauthorization file"**
========================================

oooooooops, sorry just saw the "sudo bit" thanks :)

---

### Post by Dr Small on 2007-09-25
Lol. I got that too, so then tried sudo. :p
Hope that helps

Dr Small

---

### Post by MozartlovesUbun2 on 2007-09-25
> **Dr Small said:**
> Make step 4 "sudo gdmsetup" as gksudo doesn't work.

Dr Small

[B]ok I did

and the little configuration window popped up for about just  one tenth of a second, then poofff, disappeared and it's back to the black screen!!![/B]

if i go step one after that

1.) CTRL + ALT + F2

it throws up a lotta text, ......

---

### Post by Dr Small on 2007-09-25
Hmm. It works perfectly for me.... :|
I'll look around on the forums.

Dr Small

---

### Post by MozartlovesUbun2 on 2007-09-25
> **Dr Small said:**
> I have not tried that GDM, but here is step three, written out.

3.) xinit space dash dash space :1 space vt12


[xinit -- :1 vt12]

When you start gdmsetup, you can then change it back to default in there.

Dr Small
[B]
ok, there's no humanly way possible for me to change anything, that little "gdmsetup" window pops up and vanishes so quickly I can hardly even click on it![/B]

almost like in the cartoons, sob, sob...

ok I tried it now several times over and over, no way to catch that window, impossible

---

### Post by Dr Small on 2007-09-25
What happens if you try "gnome-session", and then access "Login Window" from the menu ?

**EDIT: Make that "sudo gnome-session" ... lol**

---

### Post by MozartlovesUbun2 on 2007-09-25
> **Dr Small said:**
> What happens if you try "gnome-session", and then access "Login Window" from the menu ?

**EDIT: Make that "sudo gnome-session" ... lol**

Ok I'm gonna try that now, I'll post again in a minute, thx

---

### Post by MozartlovesUbun2 on 2007-09-25
**OMG**

you won't believe it!!!!

ok that was much better, ah i heard the login tune, then desktop, then i went to where one changes the gdm theme, as soon as i clicked to open it, BANG

from my desktop: System> Administration> Login Window ***BLACK SCREEN!*** can't get to (> Local > Add)

**black screen**

---

### Post by aktiwers on 2007-09-25
When you are in full consol, and login, it doesnt take you straight to desktop after typing 
```
startx
```??

If not...
Im not a 100 % sure on this, but its worth a try. Just remember to chage it back if it didnt work:

```
 sudo nano /etc/X11/gdm/gdm.conf
```Then after all the commends (text with # infront) one of the very first lines are:
```
AutomaticLoginEnable=false
AutomaticLogin=
```Or something very simulair.

Change it to:

```
 AutomaticLoginEnable=true
AutomaticLogin=<your username>
```And replace <your username> with your own username.

Now save and exit. and reboot.
Remember to remove your edits after you have restarted.

---

### Post by Dr Small on 2007-09-25
> **MozartlovesUbun2 said:**
> **OMG**

you won't believe it!!!!

ok that was much better, ah i heard the login tune, then desktop, then i went to where one changes the gdm theme, as soon as i clicked to open it, BANG

from my desktop: System> Administration> Login Window BLACK SCREEN! can't get to (> Local > Add)

**black screen**
Something is utterly wrong with that pc...

---

### Post by MozartlovesUbun2 on 2007-09-25
> **Dr Small said:**
> Something is utterly wrong with that pc...

**I'm crying here**

everything was perfect, till I showed my mate where to get cool stuff from for his new ubuntu (since 3 weeks)

never had any problems,PC is rock solid

it was my stupid idea now to change the GDM theme, and i'm screwed

---

### Post by MozartlovesUbun2 on 2007-09-25
> **aktiwers said:**
> When you are in full consol, and login, it doesnt take you straight to desktop after typing 
```
startx
```??



ok i'm gonna try that now, thx

---

### Post by Dr Small on 2007-09-25
The reason I never suggested startx, is because that never works properly for me :p

---

### Post by MozartlovesUbun2 on 2007-09-25
Yes true can I disable the login name and password totally

that should work!!!

---

### Post by MozartlovesUbun2 on 2007-09-25
> **Dr Small said:**
> The reason I never suggested startx, is because that never works properly for me :p

sorry am a little confused, where and when am i supposed to type in "startx"

?

---

### Post by Dr Small on 2007-09-25
Just enable automatic login, as i don't know of a way to disable a username and password.

---

### Post by aktiwers on 2007-09-25
Yes!

System-->Administration-->Login Window
Security-->Enable Automatic Login

---

### Post by Dr Small on 2007-09-25
> **MozartlovesUbun2 said:**
> sorry am a little confused, where and when am i supposed to type in "startx"

?
1.) CTRL + ALT + F2
2.) startx

---

### Post by aktiwers on 2007-09-25
1.) CTRL + ALT + F2
2.) Login
3.)type: startx

---

### Post by MozartlovesUbun2 on 2007-09-25
> **aktiwers said:**
> 1.) CTRL + ALT + F2
2.) Login
3.)type: startx

ok thank you, both of you, gonna try that now hope it works, fingers crossed.

---

### Post by MozartlovesUbun2 on 2007-09-25
> **aktiwers said:**
> 1.) CTRL + ALT + F2
2.) Login
3.)type: startx

**Fatal server error:**

server is already active for display 0

if this server is no longer running, remove /tmp/ .X0-lock
and start again


???

is there another way

can i just go in live a liveCD and change what ever I need to, how would i do that please?

---

### Post by aktiwers on 2007-09-25
Try remove that file:
```
sudo rm /tmp/.X0-lock
```and type startx again..

---

### Post by MozartlovesUbun2 on 2007-09-25
> **aktiwers said:**
> Try remove that file:
```
sudo rm /tmp/.X0-lock
```and type startx again..

ok gnna try that now, thx

====================

ok tried it, it says no such file or directory!!!

what do i do

---

### Post by Dr Small on 2007-09-25
[quote=MozartlovesUbun2]is there another way

can i just go in live a liveCD and change what ever I need to, how would i do that please?[/quote]

The terminal can do everything and more than the live cd can do, so just stick with the terminal.

Dr Small

---

### Post by MozartlovesUbun2 on 2007-09-25
oooo, where can I find that config file, i just wanna go change it manually

---

### Post by MozartlovesUbun2 on 2007-09-25
> **Dr Small said:**
> The terminal can do everything and more than the live cd can do, so just stick with the terminal.

Dr Small

ok one second...

ok got the terminal running, but how do i change that file now?

---

### Post by aktiwers on 2007-09-25
My first post here was how to get auto login manually. After the startx part :)

---

### Post by Dr Small on 2007-09-25
[http://ubuntuforums.org/showpost.php?p=3427184&postcount=14](http://ubuntuforums.org/showpost.php?p=3427184&postcount=14)

---

### Post by MozartlovesUbun2 on 2007-09-25
> **aktiwers said:**
> My first post here was how to get auto login manually. After the startx part :)

yes sorry, i went back looked at it and changed it

good, i am back in again

phew, it's tough to do some repair when u break someone elses PC and the guys over your shoulder watching every move, my palms are sweaty

ok i'm not gonna do anything more for tonight

am back in /home, logged in

now i just hope it lets me change the darn GDM theme, and doesnt freakin go back to black screen!

===================

ok it lets me open the window to change themes now, and i really wanna get rid of that one theme, but the (REMOVE) button is greyed out?

how do i remove a theme?

---

### Post by aktiwers on 2007-09-25
Good to hear.. let us know if it lets you do that :)

---

### Post by MozartlovesUbun2 on 2007-09-25
> **aktiwers said:**
> Good to hear.. let us know if it lets you do that :)

yup it's ok i go get to the change GDM theme window now
[B]
B I G thanks[/B] to you both :)

just wanna remove that theme now so no one accidently chooses it and has a bad surprise

the the REMOVE button is greyed out

---

### Post by Dr Small on 2007-09-25
Click on another GDM login window theme, make another one default, go back up and click on the offending theme, and then click remove.

Dr Small

---

### Post by MozartlovesUbun2 on 2007-09-25
> **Dr Small said:**
> Click on another GDM login window theme, make another one default, go back up and click on the offending theme, and then click remove.

Dr Small

LOL

pretty simple, eh

ok i better go chill out now, enough excitment already

---

### Post by Dr Small on 2007-09-25
Tell the fellow over your shoulder, that if he would not have been breathing down your neck for the last hour, you would have solved it sooner :p

It really does make one nervous when another is continually watching over your shoulder.
Glad you got it all sorted out.
You can mark the thread as solved now ;)

Dr Small

---

### Post by MozartlovesUbun2 on 2007-09-25
> **Dr Small said:**
> Tell the fellow over your shoulder, that if he would not have been breathing down your neck for the last hour, you would have solved it sooner :p

It really does make one nervous when another is continually watching over your shoulder.
Glad you got it all sorted out.
You can mark the thread as solved now ;)

Dr Small

LOL, I did, he just kicked my ****
--------------------------------------

yup thread is marked as solved

thanks to you two

I went to my first post and put a solved in front of it, is that ok, is that how one does mark a thread solved (lol, sounds like another job)

:)

---

### Post by kostkon on 2007-09-25
I am not pretty sure, but I believe another way to solve this would have been to start in safe mode, open the *gdm.conf-custom* file
```
sudo nano /etc/gdm/gdm.conf-custom
```

find this line and edit it
```
GraphicalTheme=*name_of_your_theme*
```

by replacing the name of the theme you had installed with *Human* (*Human* is the name of the default theme in *Ubuntu*)
```
GraphicalTheme=*Human*
```
and then restart X.

Anyway, I am amazed that the people here kept helping you in every step you made to solve your problem. Congratulations to the forum members that participated in this thread; the community here is amazing!

---

### Post by aktiwers on 2007-09-25
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Its late here too..  good night :)

---

### Post by Dr Small on 2007-09-25
Well, it most likely would have saved us alot of posts, frustration, and nervousness on our partner's end, if you would have showed up a little sooner :D

We'll have to use this thread as a complete guide to solving this problem :p

Dr Small

---

### Post by crjackson on 2007-09-25
> **MozartlovesUbun2 said:**
> LOL, I did, he just kicked my ****
--------------------------------------

yup thread is marked as solved

thanks to you two

I went to my first post and put a solved in front of it, is that ok, is that how one does mark a thread solved (lol, sounds like another job)

:)

That doesn't mark it as solved.  You need to look up at the top right of the post and click on thread tool>Mark Thread Solved.

Then your done...

---

### Post by SabrinalovesUbun2 on 2007-09-25
> **Dr Small said:**
> Well, it most likely would have saved us alot of posts, frustration, and nervousness on our partner's end, if you would have showed up a little sooner :D

We'll have to use this thread as a complete guide to solving this problem :p

Dr Small

LOL

it was our PC which was been fixed, ok we were a little bit tough on him (Mozart)

oh well, thx guys my brother and I are happy again

(maybe sometime later we wanna try having cartoon icons for the desktop and a nice GDM theme)

---

### Post by Dr Small on 2007-09-25
> **SabrinalovesUbun2 said:**
> LOL

it was our PC which was been fixed, ok we were a little bit tough on him (Mozart)

oh well, thx guys my brother and I are happy again
Your brother ?!
Aww.. shucks.. If we would have known that, why we would have never helped him!
Just kidding :p

Dr Small

---

