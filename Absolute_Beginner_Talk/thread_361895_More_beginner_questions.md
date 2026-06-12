---
title: "More beginner questions"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by tim1970 on 2007-02-14
I was able to get my hard drive partitioned, and ubuntu installed without any problems.  Now that I am up and running, I have a few questions and comments.

(Please bear with me over the next few weeks, because I am not one to just type something in and be glad it works.  I want to know more about what is actually going on, so I will be experimenting and asking questions as I go)


Coming from a Unix background, I am able to use the terminal window without being overwhelmed.  My questions has to do with the repository.  Does any software that I will ever need belong there?  Will I ever need to install software not in there?  Also why wouldn't I want to enable all of the repositories?  Is there a security concern or something?  Is there a listing somewhere online, that will describe the different packages?  And lastly, is there a way to control where my packages are installed?   Will they always be installed on my main partition?


Thanks in advance for all your help.  Even though I do not know much right now, I can definately see light at the end of the tunnel.

Tim

---

### Post by Maestro23 on 2007-02-14
.

---

### Post by Maestro23 on 2007-02-14
Welcome to the community. Some good links to introduce you to Ubuntu and how it does things:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

[http://www.cutlersoftware.com/ubuntuinstall/](http://www.cutlersoftware.com/ubuntuinstall/)

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Also the Ubuntu guide link is in my sig.

---

### Post by DerArzt on 2007-02-14
not all packages are in the repos. there are programs that you have to download and rub .debs for. As to enabling universe and multiverse, i have them enabled because i need them, and as far as i know theres no down side to this. That doesnt necessarily mean there isnt a down side, its just that if there is one i dont know of it. generally apps are installed to /usr/bin on your primary partition.

---

### Post by tonyr1988 on 2007-02-14
Unfortunately, I cannot answer all of your questions, but here's an answer to a few (until someone much smarter than me can chime in):

-Congratulations! I'm glad you've got everything up and running. With your background and your willingness to learn what's going on as you type something in, you'll get the hang of it in no time.

-Not all software is in the repository, but a lot of it is. Always check the repos first - that's the preferred way above all to install software. The great thing about repositories is that anytime a program in the repos gets updated, it's all integrated into one single "Update Manager" - if needed, you can update dozens of programs with the click of a button! :)

-If you need to install software not in the repositories, they will usually be a *.deb file (easy to install!), a source tarball (not too bad, depends on software), or another Linux distro file (like *.rpm - not hard to install at all, either). Someone's signature has a link on "How to install ANYTHING in Ubuntu" - definitely a good read.

-[This]("https://help.ubuntu.com/community/Repositories/Ubuntu") is a good wiki article that explains the differences between the default repositories. The security problems come in the third-party repositories. They would be able to add any bad software - again, if possible, get everything from the Ubuntu repos. It makes life easier. (fyi: the repo list is under Synaptic's Settings -> Repositories and also in /etc/apt/sources.list)

-Most of the packages should have a description - just click on it in Synaptic (System -> Administration). It's a pretty good graphical front-end that allows simple searching, browsing, and some other cool things.

Hope I answered at least a few questions. I'm sure someone will drop by to help a ton more than me. Feel free to ask as many questions as you need - the more you understand, the better your system will be (and the more you can help others! :D)

---

