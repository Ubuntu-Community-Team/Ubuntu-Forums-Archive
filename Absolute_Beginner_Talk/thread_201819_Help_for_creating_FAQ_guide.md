---
title: "Help for creating FAQ guide"
date: 2006-06-22
forum: Absolute Beginner Talk
---

### Post by overcast on 2006-06-22
Hi,after reading the questions list of lug fest submitted by arunpawar.I've decided to create FAQ for ubuntu/kubuntu.This FAQ will also be installed on computrers with kubuntu/ubuntu installed during our local LUG install fests.Although ubuntu/kubuntu have online FAQ but i think still there is need of this for those computers which are not connected to the internet.

I've created categaries like 
1.general: for FOSS/about k/ubuntu & shipit type questions.
2.Installation: Questions about dual boot installation guide, guides/docs,filesystem,directories,installation realted questions.
3.software: this will answer knaptic,adept and other software installtion related questions.
4.desktop: for kde desktop related related questions
5.help: questions on where to ask for help,where to go dirsectly in case of information etc.

At start i'm starting with these categaries only,after alpha beta versions i will improve the faq.currently i'm short on questions for FAQ,if you remember most frequently asked questions and hier answer,please post it here.This way i can create better faq,and you will be given credit on the acknowledgement page.Please post it in question-answer format.

Please help.Thanks in advance.

---

### Post by aysiu on 2006-06-22
I realize your FAQ may address different issues, but--just so you know--every Ubuntu installation already has some extensive documentation already included with it (without online access).

---

### Post by overcast on 2006-06-22
[QUOTE=aysiu]I realize your FAQ may address different issues, but--just so you know--every Ubuntu installation already has some extensive documentation already included with it (without online access).[/QUOTE]

Hey i'm doing this for perticular Lug maybe this will solve some problem,or reduce the load on the forums with same repeated questions.

---

### Post by aysiu on 2006-06-22
[QUOTE=overcast]Hey i'm doing this for perticular Lug maybe this will solve some problem,or reduce the load on the forums with same repeated questions.[/QUOTE]
I just wanted to make sure you were aware of what already exists, so you're not duplicating any efforts.

---

### Post by MaximB on 2006-06-22
the adsl connection problem is a major problem for new users  (I too conforted that problem at my first time). so :

q: I have an adsl modem , it works fine on windows but I don't know how to configuer it on linux/ubuntu
in order to connect I have to insert my username and password given to me by my ISP , I've cheacked the networking but I did not find the way to insert thouse parametars - what shell I do ?

a: in order to configure your adsl modem you need to go to the console/terminal and type the command :
"sudo pppoeconf" - hit return and enter your first ubuntu username password 
then you will be asked for your modem configuration your username and password to login
if you wish to connect to the internet when ubuntu starts you can configure it from there.
if you wish to turn the connection off type in the console/terminal
"poff dsl-provider-name"
if you wish to turn the connection back on type :
"pon dsl provider-name"

another very popular question is how to configure ATI graphic card
but all I didn't managed to get it fully working myself(I hope so , with that slow 3d graphic on ubuntu I very hope so...) 
as soon as I will configure it correctly I will pose a few answers to this question (as we know linux has a multiplay solutions to one problem).

you can pose my Q&A in your FAQ - but I advice you to correct my grammer first :)

---

### Post by catlett on 2006-06-22
I can't compile?

This is a big problem with Ubuntu. It comes in many forms (the questions that is) I'll get to the reason and you can take it from there. To compile on Ubuntu the package "build-essential" has to be installed. Everyone extracts a tar file and starts to run ./configure, make and before they get that far they have an error.
So I would advise a spot for..."Install "build-essential" with apt-get or through synaptic before you compile any tarballs.

That's the first one that comes to mind. If I think of others I'll post. 

P.S. ATI cards are a big issue, as already mentioned, people are aleays posting "xserver could not start errors"

---

### Post by aysiu on 2006-06-22
Don't forget that *build-essential* is on both the Alternate and Desktop CDs. You don't need an internet connection to install it.

---

### Post by catlett on 2006-06-22
Another issue is the confusion of linux users who come to Ubuntu and try to get a root terminal. "How do I become root?" "How do I get a root terminal" "I enter su and my password doesn't work. How do I set a rot password?"

The question are something like that. The fact that Ubuntu uses "sudo" instead of su and a password is an issue. People need to be educated on root access in Ubuntu. I just post the link to the documentation page  as a response. [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by catlett on 2006-06-22
[QUOTE=aysiu]Don't forget that *build-essential* is on both the Alternate and Desktop CDs. You don't need an internet connection to install it.[/QUOTE]
Would users without internet connection just put the install cd in and then run apt-get or synaptic as usual?

---

### Post by Drakkor on 2006-06-22
[http://www.ubuntuforums.org/showthread.php?t=201775](http://www.ubuntuforums.org/showthread.php?t=201775)
Some people are having trouble just following normal procedure,and can't even get Ubuntu installed at all !  Then the usual mounting windows partitons,synaptic,easyubuntu and so forth.

---

### Post by aysiu on 2006-06-22
[QUOTE=catlett]Would users without internet connection just put the install cd in and then run apt-get or synaptic as usual?[/QUOTE]
Well, from the command-line, you can add the CD as a repository with this command: ```
sudo apt-cdrom add
``` From Synaptic, you can go to Settings > Repositories > Add CD

---

