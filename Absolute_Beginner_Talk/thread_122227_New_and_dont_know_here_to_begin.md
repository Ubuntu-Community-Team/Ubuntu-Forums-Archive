---
title: "New and dont know here to begin"
date: 2006-01-27
forum: Absolute Beginner Talk
---

### Post by cmarlow on 2006-01-27
Hello All,
I am very new to linux just installed it I dont know where to start on setting up if I have to configure things that I have to do bc this isnt like my win xp that i just got rid of well it tells you what you need to set up and do whatever at the very first book up

idk... im very worried bc i dont konw what im doing i can get online right now but i dont know whats what

when i was on windows i used stuff like YAHOO MSGR, MSN, AIM, ICQ, LIMEWIRE, WINDOWS MEDIA, stuff like that

i dont even know how to install stuff...... how do you do that? 

wow...... im so lost...... where do i begin

help me end my nervousness


thanks ,
Christopher

---

### Post by aysiu on 2006-01-27
I'd start with [this PDF](http://ubuntu.xgn.com.br/ubuntu_user_guide.pdf) to give you some basic explanations about Ubuntu--think of it as an orientation.

The links in my signature also cover the most frequently asked questions from newbies.

---

### Post by Jucato on 2006-01-27
Listen to aysiu! The guides he/she (sorry, I haven't asked...) made are great! They helped me a lot. And her essays (linux and non-linux) are also nice. :D

Maybe you could also add this:

[https://wiki.ubuntu.com/UserDocumentation]("https://wiki.ubuntu.com/UserDocumentation")

Then after you get a hang of some of those things, you could follow the stickied thread above about Automatix, w/c will let you easily install some basic stuff (like Firefox, multimedia codecs to play mp3, avi, etc).

Welcome to the wonderful world of Linux and Ubuntu!

---

### Post by cmarlow on 2006-01-27
[QUOTE=Fenyx]Listen to aysiu! The guides he/she (sorry, I haven't asked...) made are great! They helped me a lot. And her essays (linux and non-linux) are also nice. :D

Maybe you could also add this:

[https://wiki.ubuntu.com/UserDocumentation]("https://wiki.ubuntu.com/UserDocumentation")

Then after you get a hang of some of those things, you could follow the stickied thread above about Automatix, w/c will let you easily install some basic stuff (like Firefox, multimedia codecs to play mp3, avi, etc).

Welcome to the wonderful world of Linux and Ubuntu![/QUOTE]



thanx!

i am so nervous....lol...... I am so use to installing windows then doin all the stupid live updates then installing the program

yeah, this is gonna be a long journey

now if I could get my flipping printer to work it be great lol

---

### Post by cmarlow on 2006-01-27
[QUOTE=aysiu]I'd start with [this PDF](http://ubuntu.xgn.com.br/ubuntu_user_guide.pdf) to give you some basic explanations about Ubuntu--think of it as an orientation.

The links in my signature also cover the most frequently asked questions from newbies.[/QUOTE]


yeah hi.... I was practicing in Terminal just getting comfortable with it becuase im scared of it....

and i did the SUDO APT-GET UPDATE

and like it downloaded 14 things

now i got this red icon up by the clock what is that??????


lol dont tell me its the equiv. of WINDOWS UPDATE lol

---

### Post by aysiu on 2006-01-27
[QUOTE=cmarlow]yeah hi.... I was practicing in Terminal just getting comfortable with it becuase im scared of it....

and i did the SUDO APT-GET UPDATE

and like it downloaded 14 things[/quote] Actually, it didn't really download anything. When you do *sudo apt-get update*, apt-get checks the list of packages available in the online software repositories and also what you have installed. After you get that list, then you can install packages by doing an install command. For example, to install Thunderbird: ```
sudo apt-get update
sudo apt-get install mozilla-thunderbird
```

> 
now i got this red icon up by the clock what is that??????


lol dont tell me its the equiv. of WINDOWS UPDATE lol Actually, it is. I turn that off right after a fresh Ubuntu installation.

---

### Post by cmarlow on 2006-01-27
[QUOTE=aysiu]Actually, it didn't really download anything. When you do *sudo apt-get update*, apt-get checks the list of packages available in the online software repositories and also what you have installed. After you get that list, then you can install packages by doing an install command. For example, to install Thunderbird: ```
sudo apt-get update
sudo apt-get install mozilla-thunderbird
```

 Actually, it is. I turn that off right after a fresh Ubuntu installation.[/QUOTE]



so what does that do????? ( the red light )

---

### Post by cmarlow on 2006-01-27
[QUOTE=aysiu]Actually, it didn't really download anything. When you do *sudo apt-get update*, apt-get checks the list of packages available in the online software repositories and also what you have installed. After you get that list, then you can install packages by doing an install command. For example, to install Thunderbird: ```
sudo apt-get update
sudo apt-get install mozilla-thunderbird
```

 Actually, it is. I turn that off right after a fresh Ubuntu installation.[/QUOTE]


see when i did the SUDO APT-get update

it says 

GET1: SECURITY.UBUNTU.COM/

GET 2: ARCHIVE.UBUNTU.COM

and theres like 9 of those



now that red thing poped up says NEW UPDATES AVAILIBLE?

---

### Post by cmarlow on 2006-01-27
[QUOTE=aysiu]Actually, it didn't really download anything. When you do *sudo apt-get update*, apt-get checks the list of packages available in the online software repositories and also what you have installed. After you get that list, then you can install packages by doing an install command. For example, to install Thunderbird: ```
sudo apt-get update
sudo apt-get install mozilla-thunderbird
```

 Actually, it is. I turn that off right after a fresh Ubuntu installation.[/QUOTE]


hahaha to funny.. its like windows update... neato

---

### Post by cmarlow on 2006-01-27
so just wondering do i need to install the 13 updatesd that is up there with the red light?

---

### Post by tekwarren on 2006-01-27
i was wondering something similiar myself. For now I don't mind being notified that updates are available. My question is what to install, I can read what the things are get somewhat of an idea what they are. If its not something I use can I just not install it? Or are the things I'm seeing things that are installed and should be updated if i use it or not? I know things like kernal updates are important but alot of other things I'm not sure I want to clutter up my install with. I like to keep things clean and not add anything I don't need or won't actually use.


Thanks.

---

### Post by aysiu on 2006-01-27
There's a built-in system for installing software in Ubuntu called dpkg/apt-get.
There are several ways to access it.

One is via the command-line terminal. For that, you use the *apt-get* command. apt-get update updates the list of what's available from online. apt-get install installs whatever application you want to install.

Another is the red light updates. It basically lets you know if security updates are available for the applications you already have installed. You click on that red dot and a little dialogue pops up saying "There are updates for all these applications. Do you want to install them?"

Another is "Add Applications" in the Gnome menu. It's a more complex version of the red light because the red light will let you know only if there are updates to programs you have installed. Add applications lets you add and remove applications.

Synaptic Package Manager (in System > Administration) is even more complex than Add Applications. You can search by description or category. The "Reload" button does essentially the same thing as the apt-get update command--one's point-and-click; the other is a typed command.

They *all* do the same thing: red dot, apt-get command, Add Applications, Synaptic Package Manager.

---

### Post by aysiu on 2006-01-27
[QUOTE=tekwarren]i was wondering something similiar myself. For now I don't mind being notified that updates are available. My question is what to install, I can read what the things are get somewhat of an idea what they are. If its not something I use can I just not install it? Or are the things I'm seeing things that are installed and should be updated if i use it or not? I know things like kernal updates are important but alot of other things I'm not sure I want to clutter up my install with. I like to keep things clean and not add anything I don't need or won't actually use.[/QUOTE] In that case, I'd remove the red dot and just use Synaptic Package Manager. You can "mark all upgrades" and see what's going to be updated and look at descriptions.

---

### Post by cmarlow on 2006-01-27
I think i just made some progress

I downloaded the tar for thunderbird to the desktop 


then did the SUDO APT-GET INSTALL THUNDERBIRD

through terminal

and it said at the very end

after it dled the files and all that

" PRE INST SUCCESSFUL"


does that mean it installed thunderbird

i was just using thunderbird as practice in installing files

---

### Post by aysiu on 2006-01-27
Yes, it installed Thunderbird but not from the .tar ball you downloaded.

When you do *sudo apt-get install mozilla-thunderbird*, it looks at the online repositories, downloads all the packages it needs (hence--no need for the .tar ball separately) and then installs Thunderbird for you. That one command does *everything*.

I repeat--as long as you're apt-getting, you don't need to download anything separately.

Read the second link of my signature for more details.

---

### Post by cmarlow on 2006-01-27
[QUOTE=aysiu]Yes, it installed Thunderbird but not from the .tar ball you downloaded.

When you do *sudo apt-get install mozilla-thunderbird*, it looks at the online repositories, downloads all the packages it needs (hence--no need for the .tar ball separately) and then installs Thunderbird for you. That one command does *everything*.

I repeat--as long as you're apt-getting, you don't need to download anything separately.

Read the second link of my signature for more details.[/QUOTE]

[COLOR="Red"]
ALL RIGHT! GO ME!

i did my first linux installation

wow im not so scared of command line now
its not as confusing as i thought it was !!!!!![/COLOR]

---

### Post by aysiu on 2006-01-27
[QUOTE=cmarlow][COLOR="Red"]
ALL RIGHT! GO ME!

i did my first linux installation

wow im not so scared of command line now
its not as confusing as i thought it was !!!!!![/COLOR][/QUOTE] Congratulations. If you really think about it, the command-line isn't really that scary--it's just typing. As long as you know what to type, it's just like writing English... except it's not English.

Keep in mind, though, that what you just did can be done entirely through point-and-click. System > Administration > Synaptic Package Manager. It comes  in extra handy when you don't know the exact name of the application you're looking for or want to search by description or browse by category.

---

### Post by Puptentacle on 2006-01-27
cmarlow, your two absolute best friends are the "Search" function here and good old Google. I set up a separate folder in my bookmarks called "Ubuntu/Linux" and have stuck quite a few sites in there that are helpful. 

The search function on this forum, however, should be stop number one with any questions. I've used it a ton in the last few weeks and it's only let me down a couple of times. Those times I've posted a question and gotten a reply in nearly no time at all. 

Have fun learning Linux. I know I am!

---

### Post by tekwarren on 2006-01-27
ok so just to clarify the "red light" updates are only showing me updates for things that I DO have already installed. And if there are things it wants to update that I don't think I want or need...I could just not update that item and look into removing it?

---

### Post by cmarlow on 2006-01-27
[QUOTE=Puptentacle]cmarlow, your two absolute best friends are the "Search" function here and good old Google. I set up a separate folder in my bookmarks called "Ubuntu/Linux" and have stuck quite a few sites in there that are helpful. 

The search function on this forum, however, should be stop number one with any questions. I've used it a ton in the last few weeks and it's only let me down a couple of times. Those times I've posted a question and gotten a reply in nearly no time at all. 

Have fun learning Linux. I know I am![/QUOTE]


[SIZE="7"]
Thanx :)[/SIZE]

so how long have you been using linux?

---

