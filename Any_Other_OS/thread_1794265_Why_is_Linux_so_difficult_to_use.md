---
title: "Why is Linux so difficult to use ?"
date: 2011-06-30
forum: Any Other OS
---

### Post by coppullcaveman on 2011-06-30
this is my first attempt using linux , I have been playing for 2 days using samsung N130  Netbook.

Wired connection is ok but wireless simply does not function, I even removed secuity on my router to try but still nothing, I have tried terminal commands but it wants a password??? can I turn off keyring or whatever is doing this. I have never used anything but windows because it is easy to use and I an capable of sorting most win probs myself.ay
I have my windows disk at standby lol, Hope you guys are able to help me. linux mint by the w ay

---

### Post by zenfarm on 2011-06-30
try the mint forums.

---

### Post by haqking on 2011-06-30
> **coppullcaveman said:**
> this is my first attempt using linux , I have been playing for 2 days using samsung N130  Netbook.

Wired connection is ok but wireless simply does not function, I even removed secuity on my router to try but still nothing, I have tried terminal commands but it wants a password??? can I turn off keyring or whatever is doing this. I have never used anything but windows because it is easy to use and I an capable of sorting most win probs myself.ay
I have my windows disk at standby lol, Hope you guys are able to help me. linux mint by the w ay


This forum is for Ubuntu not mint.

password it asks for at terminal is your own password or root if it is enabled (in ubuntu root is disabled by default)

wireless (what is the error) if asking for a key, enter the wirelss key, you can turn keyring off by entering a blank password for it.

and as for Why is linux so difficult to use, what you should be asking yourself is "why is Windows so easy" ;-)
The only difficult question is the one you dont know the answer too ;-)

---

### Post by Rex Bouwense on 2011-06-30
Hey Caveman, welcome to the Ubuntu forums.  If you don't get a respose from anyone on these forums you can always try
[http://www.linuxquestions.org/](http://www.linuxquestions.org/)
They talk about all kinds of Linux distros there.

---

### Post by haqking on 2011-06-30
> **Rex Bouwense said:**
> Hey Caveman, welcome to the Ubuntu forums.  If you don't get a respose from anyone on these forums you can always try
[http://www.linuxquestions.org/](http://www.linuxquestions.org/)
They talk about all kinds of Linux distros there.


best to use [http://forums.linuxmint.com/](http://forums.linuxmint.com/) as he is running mint

---

### Post by uRock on 2011-06-30
Moved to Other OS/Distro Talk, however you may find better help for your distro via the Mint forums.

---

### Post by TeoBigusGeekus on 2011-06-30
What's your wireless card?
```
lshw -C network
```

---

### Post by Rex Bouwense on 2011-06-30
That may be true but there are a whole lot more folks on Linux Questions and they seem to be up on many distros (even if he has a Mint question).  As a matter of courtesy we try to answer all sorts of questions here too if we are knowledgeable.  Unfortunately, I am not.

---

### Post by life in color on 2011-06-30
Windows isn't easy to use your just using hardware designed for Windows not Linux. You can get your wireless card and driver to work with Linux it just might be a little bit harder, again blame whoever made your computer hardware not Linux.

---

### Post by dFlyer on 2011-06-30
Hi, welcome to the forum. Linux is really not difficult. You must remember it's not windows and chances are windows came pre-installed. Don't know if you ever tried to install windows and had to spend several days searching for driver for things like video, wifi, prints and sometimes even hard drive, and than finding you have to update your hardware because the version of windows your running doesn't support your old stuff. 

Linux is only a slight learning curve. Once it's setup and running smoothly you can forget about it. I've been running Linux since the mid 90's. Should have tried it back than, that was when it was difficult. Things like winmodems wouldn't run on linux so dial up was out of the questions, video drivers had to find. About 5 years ago, dsl networking was a pain, and wifi was almost unheard of with linux. Today you have it all, sometime with a little tweaking but you should be able to get everything working. Remember Linux is not windows, just go slow and have fun. When you have problems just ask questions but be sure to provide as much information as possible about your hardware and error messages, and if you don't know what information to provide, just ask and someone will jump in.

---

### Post by haqking on 2011-06-30
> **Rex Bouwense said:**
> That may be true but there are a whole lot more folks on Linux Questions and they seem to be up on many distros (even if he has a Mint question).  As a matter of courtesy we try to answer all sorts of questions here too if we are knowledgeable.  Unfortunately, I am not.


yes of course, and out of courtesy i answered all his questions (well what i could given the information supplied)

---

### Post by el_koraco on 2011-06-30
We'll need a little more information. First of all, I suggest you hook up your wired cable, and do a system update with the Update Manager. Then, type in Additional Drivers into the main menu, and run the program, while still being connected via wired cable. 

If it doesn't work, open a terminal and issue the command that TheoBigusGeekus gave you and we'll take it from there.

---

### Post by oldos2er on 2011-06-30
Linuxquestions.org has a subforum for Mint: [http://www.linuxquestions.org/questions/linux-mint-84/](http://www.linuxquestions.org/questions/linux-mint-84/)

---

### Post by krapp on 2011-06-30
I'd suggest that you stick with Windows if you insist on expecting Linux to act like Windows. If you can troubleshoot Windows on your own you're more than capable of figuring out Linux with the far superior online aids available, but you have to assume a different attitude first seeing as its an entirely different OS.

---

### Post by nzjethro on 2011-06-30
@ OP, I'd say the number one reason Linux is "so difficult to use" isn't the command line, or the interface, or installing packages, or dealing with DEs - it's the unfamiliarity. I found Ubuntu pretty hard to use when I started using it, but that's just because I'd used only Windows for ~9 years or so before that. Windows was all I knew, so of course shifting away from it was difficult. I imagine 90% of the people who complain about difficulty are really complaining about the unfamiliarity.

Stick with it, the learning curve's not that steep. My advice to a learner is to keep an eye on these forums, check definitions for unknown words in posts (imagine troubleshooting Windows without knowing what a "control panel" was), answers other people's questions if you can, and it'll all become a lot more clear. :)

---

### Post by life in color on 2011-06-30
@ nzjethro I second that comment!

---

### Post by aykoola on 2011-07-01
i'm a newbie and not equiped with tech knowledge, but Ubuntu and these forums really put fun back in computing for me (even if it is on a begginers level). It took me just a while to get used to terminal thing, software center etc., but now everything seems waaaaay less complicated than in windows.

---

### Post by slooksterpsv on 2011-07-01
Now this is in response to the title of your question and part of your original post.

Linux, on the right computer, works quite well. Chrome OS uses Linux as it's base, I use Linux on my Gateway NV53. It all works great for me.

Now why doesn't it work well for others? A lot of hardware manufacturers only provide drivers for Windows and not Linux. So in turn we have dedicated, diligent, smart, faithful, developers that try to make a driver or drivers for Linux, either by reverse engineering the windows driver or some other method. So if you want to blame someone for something not working, generally I say blame the OEMs and Hardware Manufacturers for not supporting Linux.

Some, like Broadcom, have started to release source code for drivers, others, still don't give any drivers.

---

### Post by NormanFLinux on 2011-07-02
Underneath, its all Ubuntu. Its an Ubuntu based distro after all!

---

### Post by wolfen69 on 2011-07-02
> **nzjethro said:**
> @ OP, I'd say the number one reason Linux is "so difficult to use" isn't the command line, or the interface, or installing packages, or dealing with DEs - it's the unfamiliarity. I found Ubuntu pretty hard to use when I started using it, but that's just because I'd used only Windows for ~9 years or so before that. Windows was all I knew, so of course shifting away from it was difficult. I imagine 90% of the people who complain about difficulty are really complaining about the unfamiliarity.

Stick with it, the learning curve's not that steep. My advice to a learner is to keep an eye on these forums, check definitions for unknown words in posts (imagine troubleshooting Windows without knowing what a "control panel" was), answers other people's questions if you can, and it'll all become a lot more clear. :)

I nominate this for Post of the Week. Well said! Well, too bad bad there are no awards given. :confused: but nice anyway.

---

### Post by nzjethro on 2011-07-02
> **wolfen69 said:**
> I nominate this for Post of the Week. Well said! Well, too bad bad there are no awards given. :confused: but nice anyway.

Haha, cheers wolfen69! I hope it helped the OP out as well.

---

