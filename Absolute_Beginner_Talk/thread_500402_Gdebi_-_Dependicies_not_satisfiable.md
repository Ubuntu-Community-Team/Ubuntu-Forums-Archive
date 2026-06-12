---
title: "Gdebi - Dependicies not satisfiable"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by itruck4fun on 2007-07-13
I am new to linux (Fiesty Fawn 7.04) :) and getting frustrated :( not being able to do anything. I like linux having used u**x a few years years ago before xwindows was really popular and look forward to becoming a proficient user and hopefully contributor. I also thank everybody in advance for the help and patience in getting me there.

I found the driver I need for my wireless brother mfc665cw all in one (printer, scanner etc) but am having trouble installing it and need guided help. According to instructions at Brother's website it should be easy, except when I click on the .deb file I get an error code as follows: 

Error:Dependency is not satisfiable: mfc665cwlpr

this is not the first time I have seen this sort of error :confused::confused: and to date haven't been able to figure out where to go to make it work. Looked in synaptic manager but I don't know what I am looking for. 

thanks again for any help. I am even newer to user forums and not entirely sure on protocol so if I broke any rules beat me softly!!

I used to think I knew things about computers... then I installed linux!!

---

### Post by RomeReactor on 2007-07-13
Hi. Try [this thread]("http://ubuntuforums.org/showthread.php?t=301112").

---

### Post by itruck4fun on 2007-07-13
Thank you for the response however it is not so much the configuration as that is a battle I will need to tackle once I resolve the installation of the driver. Presently my problem is with gdebi and the whole DEPENDENCY NOT SATISFIABLE.

what dependencies do I need to resolve? And where do I go to resolve them? I am assuming I have to install a library to install the driver. 

I was at the Brother Site to get the driver files initially now I would like to make em work.


thanks again.

---

### Post by RomeReactor on 2007-07-13
> **itruck4fun said:**
> Error: Dependency is not satisfiable: mfc665cwlpr

Did you download both files and install them? First double click on **mfc665cwlpr-1.0.0-6.i386.deb** and when it finishes installing, double-click on the **mfc665cwcupswrapper-1.0.0-6.i386.deb**.

---

### Post by itruck4fun on 2007-07-13
after reading and reading... something I am actually accustomed to doing in learn mode. I installed the LPR driver first (which on first read seemed to mean that I did NOT have to install it) that resolved my dependency issue... then I installed the cupswrapper and lo and behold I can print.

Thank you so much today I learned something and that is a great feeling.

I will figure this out because I persevere. :)

so if I understand this correctly though.. .in the future with dependency issues I should look to synaptic for the lib (or appropriate dependency) and the a repository?

---

### Post by itruck4fun on 2007-07-13
now... to get that USB cam and sound card working...

---

### Post by RomeReactor on 2007-07-13
Glad you got your printer going!

As for dependencies, if Gdebi, Synaptic, Add/Remove, Apt-Get or Aptitude complain of not finding a dependency (as happened to you), then that dependency (a program or library) can't be found in the repositories you have currently enabled. That means you must enable other repositories or add unofficial repositories; or find the required dependency as a stand-alone package (as you just did) and install them. Also, in your case, the error message was:
> Error: Dependency is not satisfiable: **mfc665cwlpr**
It's always a good idea to search the forums for the missing dependency; hopefully you won't need to, but you never know ;)

Sorry I can't help with your USB camera, though.

---

### Post by itruck4fun on 2007-07-13
no worries on the USB or sound card. You helped a ton... amazing how often the smallest things that are overlooked hold the answer to the problem we have.

I used to use ( ages and ages ago ) FreeB*D with a bourne shell and got pretty good at it but I am tripping over myself trying to figure out the commands in the bash shell and the man pages are fighting me. Things have changed a LOT in the last 15 years and Linux is better than Un*x anyway. 

again thanks and I will turn to the forums more often.

---

### Post by RomeReactor on 2007-07-13
> **itruck4fun said:**
> Things have changed a LOT in the last 15 years and Linux is better than Un*x anyway.

Wow, you certainly have more mileage with *nix systems than me. I bet there's plenty of useful things you could teach others (myself included)! Personally I haven't used BSDs, but as I understand it, Linux and BSDs are not *that* different, are they?

---

### Post by itruck4fun on 2007-07-13
well besides the shell which is easily changed not really. I was using it at a time when xwindows was a new thing so the gui was rarely used. then I went to windows cause it was easier and I got lazy. Not sure that I could teach anyone here anything. But I DO hope to learn fast. 

The terminal messes me up because none of the commands I remember work... I'll get there though and looking forward to the experience

---

### Post by RomeReactor on 2007-07-14
Just thought that [LinuxCommand]("http://www.linuxcommand.org/") could help you get used to the differences on the command line; I don't know how Linux commands differ  from BSD commands, though. Hope it helps.

---

### Post by itruck4fun on 2007-07-14
you are very helpful and a wealth of information. My understanding would be that as the development is opensrc and there are a few different shells that the commands should be the same in whatever distro you would be using. So if you are familiar with bash in linux it wouldn't be much different in BSD or Slackware or whatever distro you are using as the commands remain consistent from one update to the next. I believe all these distros evolved from BSD way back when. 

Linus Thorvald had an idea to improve on the original development which has grown to be an excellent OS and I am preparing to ditch windows again as my main machine. Bill has gotten enough of my money.

Anyway, thanks again for you help now I can learn the bash shell commands and forget about bourne or tch.

---

