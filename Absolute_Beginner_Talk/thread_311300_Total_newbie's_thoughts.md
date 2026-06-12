---
title: "Total newbie's thoughts"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by sdmtnbiker on 2006-12-02
Ok, never played w/anything other than Windows my entire life (all 54 years of it) threw Ubuntu on my laptop and everything worked right out of the box except the WiFi. Went to the forums and found the fix. I have no idea how I got it to work, copied some code into the terminal window and there it was after a reboot.
The biggest thing for a newbie is installing programs and the language that is used "sudo"???   I miss my .EXE programs. Is there anywhere I can find a definitive web site or book that has all this stuff with complete walk through for the totally inept? It seems learning how to install programs is the biggest hurdle you have.
keep up the good work, you have an awesome product here.
Thanks.
(ps who makes up all these weird names and why does everything have a g in front of it)

---

### Post by smile_sunshine on 2006-12-02
using synaptic is probably the easiest way to install programs without having to type anything :)

---

### Post by ron999 on 2006-12-02
g stands for gnome, it's the gnome desktop used in Ubuntu.
Some programs start with k, that's for the KDE desktop used in Kubuntu.
:)

---

### Post by Bachstelze on 2006-12-02
Hi and welcome to Ubuntu !

[Here](http://psychocats.net/ubuntu/index.php) you wil find all you need to get you started :)

---

### Post by sdmtnbiker on 2006-12-02
> **smile_sunshine said:**
> using synaptic is probably the easiest way to install programs without having to type anything :)

ahhh   yes synaptic   um what is it and how can I download? I love the help and the fast response, but this is what I am talking about, I have no idea what synaptic is.

---

### Post by Doug11 on 2006-12-02
> **sdmtnbiker said:**
> Ok, never played w/anything other than Windows my entire life (all 54 years of it) threw Ubuntu on my laptop and everything worked right out of the box except the WiFi. Went to the forums and found the fix. I have no idea how I got it to work, copied some code into the terminal window and there it was after a reboot.
The biggest thing for a newbie is installing programs and the language that is used "sudo"???   I miss my .EXE programs. Is there anywhere I can find a definitive web site or book that has all this stuff with complete walk through for the totally inept? It seems learning how to install programs is the biggest hurdle you have.
keep up the good work, you have an awesome product here.
Thanks.
(ps who makes up all these weird names and why does everything have a g in front of it)

I'm with you. Was getting sick and bored with M$. Tried many differrent Linux Distros, but in my opinion, nothing comes close to Ubuntu as for the ease. The only problem I had as well was with Wifi, but found a great how-to and off I went. Synaptic package Manager is a great accessory but I also find Automatix is a great tool as well. Im  now learning how to convert and burn movies among other things and soon will be able to scratch M$ from my HD altogether. Good Luck.

PS,,System>Administration>synaptic Package Manager,,,you can find many gret tools in there that will install automaitcally.  Also, if you google Automatix,,you can find it where it will self install. It too has great progies.

---

### Post by Oki on 2006-12-02
Hi

Its hard coming from Windows – I agree. But I am so tired of all MS crap that I have decided to do my best to learn Ubuntu Linux, and there is so much great in this world. But those names... 

There are 4 books about Ubuntu (perhaps more):
The Official Ubuntu Book ([http://www.ubuntu.com/news/Official_Ubuntu_Book?highlight=%28book%29](http://www.ubuntu.com/news/Official_Ubuntu_Book?highlight=%28book%29))
Ubuntu Hacks Tips and Tools
Ubuntu Unleashed
Beginning Ubuntu Linux: From Novice to Professional 

If you are wondering about the terminal take a look here;
Good guide:
[http://www.ubuntuforums.org/showpost.php?p=398953&postcount=1](http://www.ubuntuforums.org/showpost.php?p=398953&postcount=1)
Others:
[http://ubuntuguide.org/wiki/Dapper#extrafonts](http://ubuntuguide.org/wiki/Dapper#extrafonts)
[http://www.linuxcommand.org/](http://www.linuxcommand.org/)
[http://www.ss64.com/bash/index.html](http://www.ss64.com/bash/index.html)

---

### Post by IYY on 2006-12-02
> ahhh yes synaptic um what is it and how can I download? I love the help and the fast response, but this is what I am talking about, I have no idea what synaptic is.

Synaptic is a graphical way of installing software from a huge online repository. You launch it by going to System > Administration > Synaptic Package Manager. It will present you with a huge list of ``packages'' (things to install; they can be programs, add-ons, or libraries required for programs to run.) You can install any of them by double clicking on the name and clicking ``Apply''. 

Note that you can enable a much larger amount of programs by adding the universe and multiverse repositories. This is done inside synaptic by going to Settings > Repositories and checking the appropriate checkboxes.

Of course, synaptic is only the graphical front end to apt-get, which you can also access from the command line. In the command line, you can simply type

```
sudo apt-get install banshee
```

You'll find all the major Linux programs in Synaptic, but if you need to download from elsewhere, always try to find a Deb file. This type of file can be installed with a simple double click, just like an EXE installer in Windows. Compiling the source code is a bit more difficult.

and the banshee music player will be installed on your system.

---

### Post by Shatrat on 2006-12-02
> g stands for gnome, it's the gnome desktop used in Ubuntu.
The ultimate origin of the G is from GNU.
GNU stands for GNU is Not Unix.  Geeks think recursion is funny.

You'll find that most of the problems you run into in linux come from 3rd party drivers and programs and data which is proprietary and undocumented which prevents people from easily writing programs to deal with these hardware, programs, documents, et cetera.

---

### Post by CaveRat on 2006-12-02
HA Ha! Those were my exact thoughts when I saw the names of Linux programs. You can look in the Synaptics Package Manager at all the programs and say "What the heck". Clicking on them will give you a brief explanation of what they are for in the bottom frame. It can be difficult for us ol' timers to convert, but it's actually rather fun. All these youngsters in this forum have taught me a thing or two for sure. Some of the code lines they can throw out there like a second native language can be mind boggling. Stick with it and you will toss Windows aside like a dirty rag before long, or at least rarely boot to it. Patients is definitely a virtue with LInux coming from Windows. Think of it like going back to school and the kids are our teachers. Bring it on. I've been brain dead with Windows for too long. 

CaveRat

---

### Post by cogvos on 2006-12-02
Hi there,

A little bit about programmes and stuff that might help you.
In windows you really only have one way to put a new programme, be it game, image editor, word processor, or whatever on your computer. 

You install it. 

That is you click on an icon which then starts an application called an installer. This copies all the information that the thing you're installing needs into the right places for it to work. At the end of this (oh the fun of watching that little bar). you end up with another icon, or an option in the start menu that lets you use the programme.

With Linux you have two ways.

The first is similar to windows and is via synamtic. This acts just like the windows installer, copying all the stuff needed by the programme into the right places. You also use it to remove the programme if you don't need it. Unlike windows Synamtic is the gateway to not just one but thousands of different programmes.

The second way (and something that is much harder for a beginner) is to build an application from the source code. This involves a number of steps, and although they are often laid out in the various text files that come with the source can seem daunting. 

A book will help a lot here as there are often a number of different options that require setting before you can start. 

The good thing is that many many applications only need you to build from the source if you want the very latest version. Generally you just use Synamptic.

Hope that helps.

John.

---

### Post by 56phil on 2006-12-02
> The biggest thing for a newbie is installing programs and the language that is used "sudo"??? I miss my .EXE programs. Is there anywhere I can find a definitive web site or book that has all this stuff with complete walk through for the totally inept? It

sudo stands for **s**uper **u**ser **do**

You can run most, err many, of your .EXE programs using wine. Which is installed most easily using the synaptic package manager. 

Good Luck and welcome to Ubuntu.

---

### Post by nalmeth on 2006-12-02
I believe this may be of some use to you:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

Also, installing .debs is even easier than installing .exe's. Double click, only extra step is to hit OK to install. 

Compiling from source gets more complicated, especially if you have to find some extra libraries and dependencies, but thankfully for newer users, the situation is rare where they actually are forced to compile. 

People do a good job of packaging

---

### Post by Epperly on 2006-12-02
> **Shatrat said:**
> GNU stands for GNU is Not Unix.  Geeks think recursion is funny.
"GNU is Not Unix is Not Unix is Not Unix is Not Unix is Not Unix is Not Unix." haha

---

### Post by IYY on 2006-12-02
> 
You can run most of your .EXE programs using wine. 

This is pretty optimistic. Wine is very cool, but has many problems and you should always try finding a native alternative first.

---

### Post by 56phil on 2006-12-02
> This is pretty optimistic. Wine is very cool, but has many problems and you should always try finding a native alternative first. 
True. I suppose I overcompensated for my depression. Sorry.](*,)

---

### Post by Geebird on 2006-12-02
I'm also new to ubuntu and I've spent the last couple of weeks, or so, playing with things. I thought about getting a book but once I got the internet connection working, there was no need. 
There is more information on this forum (and another couple of sites) than any book could hold.  I know that the sometimes conflicting answers to problems can be, at first, frustrating. However, I have not had this much fun in front of a PC since my first machine (an 8088 with 2* 720 floppy drives..no HD an a CGA monitor runing MS Dos 4.. eek!)
All the answers to all the questions are here...you just gotta search for them.

So.. a thanks to all.  Your postings have made me a happy chap.
I'm not sure my wife is so happy...but...I'm not sure there is a thread for upset wifes?? ;)

---

### Post by angkor on 2006-12-02
> **Geebird said:**
> So.. a thanks to all.  Your postings have made me a happy chap.
I'm not sure my wife is so happy...but...I'm not sure there is a thread for upset wifes?? ;)

I don't think there is, but she's free to create one in the Cafe section of the forums. :)

---

### Post by Geebird on 2006-12-02
> **angkor said:**
> I don't think there is, but she's free to create one in the Cafe section of the forums. :)

But then I would have no where to hide. ](*,)

---

### Post by sdmtnbiker on 2006-12-03
Just want to thank everybody who replied, I got a lot of good info and it will take me awhile to get it together, but all of you have been great, you made me feel as though I have a home here. I am going to stick w/it and maybe someday I can help or add to this awesome community.
Thanks again!
Steve

---

