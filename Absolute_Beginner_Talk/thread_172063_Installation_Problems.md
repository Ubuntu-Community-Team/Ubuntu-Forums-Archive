---
title: "Installation Problems"
date: 2006-05-07
forum: Absolute Beginner Talk
---

### Post by jonno112 on 2006-05-07
Hi 

This is like im starting to walk again.

I have recieved my linux disk Ubuntu 5.10 all five of them and i just installed it as per these instructions [http://www.pcmech.com/show/os/903/](http://www.pcmech.com/show/os/903/)

I know this must sound lame, I have googled, checked Ubuntu site and reinstalled 3 times i cannot get a graphical interface I login with my username and password all i am getting is jw@Mrlinux. I know there has got to be more.

first time user maybe the last.

---

### Post by nalmeth on 2006-05-07
Don't get hasty now.
we are not moved by threat's :p
It sounds like you did a basic "server" install rather than the default.
You could try again, and just hit enter rather than type server, but while you're installed already, you can get your Graphical Interface.
Do you have an active internet connection?
From the command prompt, type:
sudo apt-get update (enter your user-password)
sudo apt-get install ubuntu-desktop
reboot the computer

---

### Post by Omnios on 2006-05-07
One quick question did you do the base install or just hit enter to get things going. Base insall is just the server which will give you jw@Mrlinux. Another thing you can try is log in and type startx which will try to start xserver, if there is no xserver found you probably have the base server isntall.

 edit: oops you beat me to it lol.

---

### Post by uzi09 on 2006-05-07
hi,

i had a similar problem with 5.10 (breezy). the issue was actually with my hardware, breezy didn't have the support built for it because it was such a new computer. when i switched over to the latest (still unstable) version "dapper drake" (v. 6.06) it worked perfectly fine.

if you don't mind, can you please provide us with some specs. that way we'll know what you seem to be working with. also if you happened to get any errors/warnings, please copy them down and let us know.

thanks so much

---

### Post by jonno112 on 2006-05-07
First of all thanks for the quick reply to my issue.

I did what you told me to do nalmeth and it appears to be working, i did type in server at the start up. I guess i didn't read it properly :-( 

An error i noticed while installing
Frontconfig error: Cannot load default config file  - Comes up a few times

Finished installing and restarted the post loads then the screen goes blank i hit enter and i hear drums bit no screen..



Specs
IBM Vectra
10gb Hd
256mb ram
Intel Pro 10/100
Intel 845G chipset

---

### Post by uzi09 on 2006-05-07
well, usually when the drums go off, you see the log-in screen. it sounds like your lacking some support for your video card. is your video card integrated into the cpu? unfortunately, beyond this point, i'm probably not going to be able to help you much more since it's beyond my scope of knowledge (in linux anyway :lol:).

it's a good thing you chose ubuntu to try out first. it's known for it's support. trust me , you're in good hands, you may just have to give it a bit of time for someone who knows the answer to come across your thread.

wish u the best of luck,
uzi

---

### Post by nalmeth on 2006-05-08
in the command line again, type:
sudo apt-get update
sudo apt-get dist-upgrade
and try to login again.

---

### Post by jonno112 on 2006-05-08
I turn the system on and after post is finished it goes blank so i cannot type what you have asked.

Is there another way of doing it?

I also got this error

Error temp fail in name resolution > I didn't have the network cable in

---

### Post by nalmeth on 2006-05-08
If you hit CNTL-ALT-F2 can you get to the command prompt?
What do you mean by post?
to restart your internet connection, type:
sudo /etc/init.d/networking restart

I know, this all looks messy and discouraging, by whilst in this state, it is what we have to do to get started. Be patient, and I hope we can get this to pay off.

Did you reinstall by the way?

---

### Post by jonno112 on 2006-05-08
I am actually reinstalling right now.
POST - Power on self test -  i think.

Ok iI now have an interface nice.

Thanks nalmeth for the help i can put the rope away now.:razz:

---

