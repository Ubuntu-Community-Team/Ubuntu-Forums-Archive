---
title: "Honest Question"
date: 2006-02-01
forum: Absolute Beginner Talk
---

### Post by thepocketdrummer on 2006-02-01
I do not intend to insult Linux or anger Linux users with this question:

Why is it that there isn't an easy way to install Drivers and Software on linux? I mean, Windows and OS X both have easy ways to get programs to work on your system. Is there a reason why this has never been implemented into Linux? I think it would attract much more users if it did.

---

### Post by bored2k on 2006-02-01
Before everyone else jumps on you, can you give specific examples? Most of the distributions I've used do a hell lot better job than other operating systems at recognizing and working with hardware, even when it does not even fully recognize it.

Software? try installing OOo on Windows. It takes you more than triple the time than it would take you to do so here. Heck, we don't even have to do anything here. Apt-get (and co.) arguably owns the scene.

Please, next time you are to post these type of messages, notice that you're on a linux forum and that you _will_ get jumped on, so be as verbose as you can without falling into trollism.

---

### Post by Perfect Storm on 2006-02-01
It's actual very easy when you learn how to do it, it's just a bit diffrent than windows.

When installing software(application), most of the times it can be done with one line in the terminal, like:

```

sudo apt-get install <name of the software>

```

It's about habits and it can take some time to change habits ;)

If you want gui for installing stuff use synaptic package manger. System ---> Adminstration ---> synaptic package manager

---

### Post by Gcool on 2006-02-01
I think linux has evolved very much on this issue, the last few years.

Let's take synaptic in ubuntu as an example. Programs like this have made it very easy to install software under linux. Also the hardware support is getting better with every release of a new kernel.

---

### Post by Lord Illidan on 2006-02-01
[quote=thepocketdrummer]I do not intend to insult Linux or anger Linux users with this question:

Why is it that there isn't an easy way to install Drivers and Software on linux? I mean, Windows and OS X both have easy ways to get programs to work on your system. Is there a reason why this has never been implemented into Linux? I think it would attract much more users if it did.[/quote]

I don't want to "jump" on you, but as the people above stated, yes, it is easy with apt-get and synaptic to install packages.

If you want to install .bin or .sh, all you have to do is type ```
sh *name of program*
```

And if you want to compile a program, it is still not so hard : ```
./configure; sudo make; sudo make install
```
./configure checks system for dependencies, make compiles the program, and make install installs the program in /usr/bin (I think..) so you can run the program from anywhere in the system.

What I think you mean is point and click installation of .deb s etc? I too wish that that can be implemented in Dapper Drake, but until then, I am quite happy.

Where installation really gets difficult is when you are in dependency hell...or when an application needs a library which is not in the repos...:(

---

### Post by earobinson on 2006-02-01
Simple answer:
1) because you are learning something new, first time you installed in windows it was hard
2) linux has less hw support because companies wont write drivers or help us write drivers.

---

### Post by cotcot on 2006-02-01
Depends on the applications you want.
For a standard desktop with mail, internet, office (OOo) a ubuntu install is at least as easy as windows. 

More specialized applications can be more difficult to install. However it is typically for linux that you have a good documentation and support (for free). The forums work excellent. Forums are very patient with people starting with ubuntu (and others). 

So do you allow me to invite you to do a ubuntu installation, experiment and come back with comments ? The proof is in eating the pudding.

---

### Post by TeeAhr1 on 2006-02-01
Well, here's a great example, and maybe it'll even illuminate the "why" a little.  I have spent the last three days trying to get gDesklets 0.35.3 installed and running on my system.  I never really knew what "dependency hell" was before, but baby, do I ever know now.

The provided documentation is pathetically inadequate, the dependency list in the README is about half complete, and several of the requisite libraries are not in the repositories, requiring a "by hand" installation.  Some of said dependencies have unmet dependencies themselves, compounding the issue further.  (Having said all that, someone from my local LUG helped me out, and I think once I get home I've got it.)

Now why is this neccessary, you ask?  Good question.  The people who build and maintain gDesklets (God bless 'em) don't just build it for Ubuntu, or Red Hat, or Solaris.  It's made to work any any Unix-like platform.

When you write a program for Windows, you're only writing to one OS, you know where everything is, how to find it, etc.  When you're writing for Linux, you're writing for an infinite number of present and future operating systems.  A library that I have installed by default in Ubuntu may not be there in Mandriva, or it may be in a different directory, or a million other subtly different things may be going on.

The point: Asking "Why doesn't Linux have an easy, unified installer?" is like asking "Why don't Windows 3.1, Windows XP, Apple IIc, PowerBook, and 1973 IBM mainframes have an easy, unified installer?"  The technical challenges are just enormous.  Not to say that it'll never be done, but we're not there yet.

(Please note that this is meant to be an illustrative story, not literal truth.  I am not a developer, and I don't know how most of this stuff works, and half of what I just said is probably glaringly inaccurate.  But I believe the gist of it to be true.)

---

### Post by mishranurag on 2006-02-01
To put few things in perspective!

When I reinstalled XP on my desktop, I had a hard time finding the codecs for my AV applications. I had to search for Nvidia drivers as my original graphics CD was lost. To make my other SATA hard drive be identified, it took me three days to find the driver (may be I was looking at worng place). I still don have software to play DVD on my XP. (I don want to buy it).

I had to download and install softwares I like, Firefox, thunderbird, antivirus, webdav, winamp, real

I installed UBUNTU about three months back. I didn't have any problems like that (AUTOMATIX helped in that too). I installed most of the softwares I liked using Synaptic ( I wish Yahoo Messenger was in repositories too). Didn't bother about AV yet ;)

Hey, I forgot one thing...

Why I reinstalled my XP? I had Symantec AV 10 version, and it interfered in XP somehow so bad that my XP would sometimes restart without warning and XP would shout that something serious happened to your comp, we don know why. It was after 2 months of consistent restarting that XP told me (their crash analysis report), it was due to AV.

Well, I think that's enough for me to compare :).


But couple of things, which are important for me, and I couldn't figure out yet are

1) VPN
2) I cannot play streaming Music from RAAGA yet.


Enjoi
Anurag

---

### Post by Lord Illidan on 2006-02-01
[quote=mishranurag]To put few things in perspective!

When I reinstalled XP on my desktop, I had a hard time finding the codecs for my AV applications. I had to search for Nvidia drivers as my original graphics CD was lost. To make my other SATA hard drive be identified, it took me three days to find the driver (may be I was looking at worng place). I still don have software to play DVD on my XP. (I don want to buy it).

I had to download and install softwares I like, Firefox, thunderbird, antivirus, webdav, winamp, real

I installed UBUNTU about three months back. I didn't have any problems like that (AUTOMATIX helped in that too). I installed most of the softwares I liked using Synaptic ( I wish Yahoo Messenger was in repositories too). Didn't bother about AV yet ;)

Hey, I forgot one thing...

Why I reinstalled my XP? I had Symantec AV 10 version, and it interfered in XP somehow so bad that my XP would sometimes restart without warning and XP would shout that something serious happened to your comp, we don know why. It was after 2 months of consistent restarting that XP told me (their crash analysis report), it was due to AV.

Well, I think that's enough for me to compare :).

But couple of things, which are important for me, and I couldn't figure out yet are

1) VPN
2) I cannot play streaming Music from RAAGA yet.


Enjoi
Anurag[/quote] 
I used VLC to play DVDs on XP, worked like a charm.

---

### Post by mishranurag on 2006-02-01
Ohhh Thanks, Edited :)
Since I rarely use XP now, I do not bother for DVD to play on that, but thanks for the suggestion.
Anurag

---

### Post by Lord Illidan on 2006-02-01
When you talk of VPN, what exactly do you mean by it?

---

### Post by mishranurag on 2006-02-01
Virtual Private Network. My university website does give detailed instruction on how to set it up on XP, but nothing on linux. I have installed pptpconfig and get it connected to the university website. The connection sends lots of packets from it, but recieve none. I didn't have time to study pptp.sourceforge.net either.

I am hoping to find time to read details, or waiting for someone to comeup with exactly same issue and solution ;)

Anurag

[quote=Lord Illidan]When you talk of VPN, what exactly do you mean by it?[/quote]

---

### Post by thepocketdrummer on 2006-02-01
I actually retyped this post 3 times before actually submitting it. It's a bit hard to get the "tone of voice" across through text. I didn't mean for it to sound like a complaint, I'm more interested in what is holding development for this sort of thing back. The driver part makes sense. I found that Logitech offers no drivers what-so-ever for linux. Thats not Ubuntu's problem at all, Logitech doesn't offer the the drivers. However, getting nVidia drivers to work was a HUGE problem for me because of the process that required two days with support from people on the forums.

I've heard that it is very hard to change ways linux does certain things because of how many different distros there are. I've also heard that the different GUIs cause problems. What is the *real* conflict in the progression of Linux?

Tone of voice: Inquisitive/confused

---

### Post by earobinson on 2006-02-01
Everyone will have a diferent answer to that, some may even say its fine right now like me.

nVidia drivers can be installed with one click using [Automatix]("http://ubuntuforums.org/showthread.php?t=66563")

---

### Post by thepocketdrummer on 2006-02-01
It says no support for AMD64 :cry:

---

### Post by earobinson on 2006-02-01
That sucks, support for 64 in general is a bit lagging both windows and linux as I understand.

---

### Post by thepocketdrummer on 2006-02-01
Yeah... XP 64-bit edition is a nightmare from what I hear.

---

### Post by mishranurag on 2006-02-01
Your tone of voice was perfectly fine, and I guess what me and others were trying to say that there are better things about using linux too compared to other OS. I think linux is progressing towards getting better and better. But big chunk of a problem is people don know about many things. 

Anybody can argue that Firefox is better than IE, but I have seen some people leaving firefox to go back to IE. They don know how this tab browing things work, how easily they can get support for extra languages, they can get beautiful themes and stuff like that, and then they think firefox is just another browser and go back to familiar blue 'e'.

Well at my Univ they are doing some *nix crash course to help people proceed with it and learn about it. They do many official courses for people to get acquainted with MS applications but *nix course is given by volunteers. So, you can see how bad the balance is.
[http://ubuntuforums.org/showpost.php?p=698652&postcount=2](http://ubuntuforums.org/showpost.php?p=698652&postcount=2)

Enjoi
Anurag

[quote=thepocketdrummer] voice: Inquisitive/confused[/quote]

---

### Post by Lord Illidan on 2006-02-01
Nothing wrong about volunteers. But in a uni course, they should bring someone professional, I think..

I am getting my grandfather to use Firefox... He seems ok with it so far, primarily because of the bookmarks in toolbar.... I love that feature myself.

---

### Post by mishranurag on 2006-02-01
As far as I know all of them are professionals, but the course they are doing is voluntary i.e. they are not being paid by the university.


[quote=Lord Illidan]Nothing wrong about volunteers. But in a uni course, they should bring someone professional, I think..

I am getting my grandfather to use Firefox... He seems ok with it so far, primarily because of the bookmarks in toolbar.... I love that feature myself.[/quote]

---

