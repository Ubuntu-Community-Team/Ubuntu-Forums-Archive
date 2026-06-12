---
title: "AIGLX on Dapper"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by ctrlcctrlv on 2006-11-16
Hello. I am trying to install Beryl. I have successfully installed my ati drivers. 

I previously ran Beryl on XGL and was informed that I should not use XGL;rather I should be using AIGLX.

I read about it and I followed the directions listed very clearly here:
[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/AiGLX](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/AiGLX)

after running this command:

sudo apt-get install xserver-xorg-air-core linux-dri-modules-common linux-dri-modules-`uname -r`

I recieved a message telling me that some libraries had noot be found. THe next step in the instructions talk about a "a small glitch with xserver-xorg-air-core:"

I tried to follow the fix that follows the notice of the "glitch".

Thats fine but i get a message that says that the directories it trys to reference do not exist. 


What is unclear about this set of instructions is what the glitch is and how i can identify that I have experienced the glitch.


I have a fresh install adn id really like to get beryl running on AIGLX?

Is there a better tutorial than this one? 


thanks 

ctrl

---

### Post by frikadunse on 2006-11-16
I just finished two noob days (me beeing the noob) fiddeling with xgl, aixgl compiz and beryl.
The final solution for me was installing Ubuntu Edgy eft, and then just typing $sudo apt-get install beryl

That did the trick in a matter of minutes.
To start beryl you just type $beryl -manager (or $sudo beryl -manager) cant remember if you have to be root?

I have to mention though, there is a problem with some of the gfx drivers, for my part I have ATI and I get a warning when swithcing to beryl, but it works anyways.

Hope it helps!

/Niels

---

### Post by DRAGONPOWER on 2006-11-30
Heya,im a noob too. OK: im using kubuntu 6.06.1 dapper , and successfully installed ati 8.31.5 drivers, fglrxinfo output was 9600XT card. So far so good.

Now i cant really find any good/working aiglx or beryl manuala/howtos/guides...its a bit frustrating, i know a lot of people are using dapper drake instead of edgy, but i cant seem to find any aiglx + dapper + ati guides...

I started off with ubuntu dapper, and then reinstalled using kubuntu dapper drake. I found Kubuntu was more responsive to errors/fixes/updates than ubuntu, thanks to the great adept package manager!

Anyway, post your thoughts man, we need feedback, have you used aiglx on ati dapper? how did you get it working? and where could i find some beryl repos that are working?!

PEACE OUT!

(oh yeah, did i mention im a bit of a noob with linux?) :)

Here's what i found:

[http://wiki.beryl-project.org/index.php?title=Install/Ubuntu/Dapper/AiGLX#Add_repositories](http://wiki.beryl-project.org/index.php?title=Install/Ubuntu/Dapper/AiGLX#Add_repositories)

this looks really good, although theres a repo that doesn't quite work. im stuck on the third line of code

```
wget [http://ubuntu.beryl-project.org/quinn.key.asc](http://ubuntu.beryl-project.org/quinn.key.asc) -O - | sudo apt-key add -
```

this doesn't work, it outputs **Error 404** to me, i think the server is not working! damn!

---

