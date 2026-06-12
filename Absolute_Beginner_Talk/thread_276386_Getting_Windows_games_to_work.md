---
title: "Getting Windows games to work"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by Kulluminatii on 2006-10-12
Hi, I have had Ubuntu installed on my old pc for a while now and have updated it to the 6.06 LTS that came out a while back,  but it has been collecting dust ever since I quit trying to make dial up work on it. Soon I am going to get DSL, and I have heard that making DSL work on Ubuntu is MUCH easier than getting dial up to work on it.

Back to my question. I was wondering, how would I go about playing "Emperor: Rise of the Middle Kingdom" on my old pc. My little brother loves that game, and I want him to stop annoying me to play it, and making it work on my old pc would be fantastic. I have heard of Window emulators such as WINE or Cedega, but I do not know how I can get those on my old pc since it doesnt have an internet connection. 

Hopefully someone knows an answer to my question, thank you guys for taking your time to read through this.

---

### Post by podunk on 2006-10-12
You know, I'd bet this would be hard to do. You could download the source for wine and burn it to a CD then copy it to your Ubuntu computer and compile it there – but if you have just a plain install with no updates run – I'd be willing to bet you wouldn't be able to resolve the dependices..

For instance – you wouldn't have build essential for one thing. 

did you ever think of buying a  Linux compatible modem? I'd bet it would be a lot easier than trying to  download,transfer then compile a bunch of stuff. You'd likely have a lot more hair left at the end of the day. :-)

---

### Post by Kulluminatii on 2006-10-12
Any suggesstions for a good and cheap linux compatible modem? Or should I wait until I get SBC(yahoo i think owns it) DSL and then try?

---

### Post by AndyCooll on 2006-10-12
Things get a bit tricky without an internet connection, for you need to install some software (and Wine is the one to start with).

You have a number of options:
1. You could dual-boot that pc with it's original OS plus Ubuntu.
2. You can download a copy of the Wine software on to another pc and then transfer it using a USB key or something like that.
3. You can download a Ubuntu DVD (which contains all the software in the standard Ubuntu repository, burn it, and use that with your old pc.

:cool:

---

### Post by AndyCooll on 2006-10-12
Most bog standard modems will work.

:cool:

---

### Post by blendmaster on 2006-10-12
> 

Things get a bit tricky without an internet connection, for you need to install some software (and Wine is the one to start with).

You have a number of options:
1. You could dual-boot that pc with it's original OS plus Ubuntu.
2. You can download a copy of the Wine software on to another pc and then transfer it using a USB key or something like that.
3. You can download a Ubuntu DVD (which contains all the software in the standard Ubuntu repository, burn it, and use that with your old pc.



#3 is a good idea, but you have to watch out because of the fact that this is an old pc, it probably won't have a dvd player. Though if it does, then this idea is perfectly acceptable!:)

---

### Post by Kulluminatii on 2006-10-12
> **AndyCooll said:**
> Things get a bit tricky without an internet connection, for you need to install some software (and Wine is the one to start with).


2. You can download a copy of the Wine software on to another pc and then transfer it using a USB key or something like that.

3. You can download a Ubuntu DVD (which contains all the software in the standard Ubuntu repository, burn it, and use that with your old pc.

:cool:For #2, would a blank CD-R work?Once I get WINE, do I just install it and pop in the game and it will work. (im thinking that installing it would mean just clicking on it to open up an easy-to-use interface, but im not soo sure about that.)

and for #3, where can I download the Ubuntu DVD? Is it fairly small? Because on dial-up, imma end up ](*,)

---

### Post by Crashmaxx on 2006-10-12
Honestly, I'd just use windows if you just want to play this game on it. It will be a lot less work. A dual boot is a great idea so you can keep messing with ubuntu on it. Ubuntu isn't a great distro for no internet. Get a new modem or wait for DSL.

---

### Post by Kulluminatii on 2006-10-12
Ok, Im at the WINE download section.
Link: [http://www.winehq.com/site/download](http://www.winehq.com/site/download)

Listed is Ubuntu and Windows. Which one do I download? Do I download both? Keep in mind that I want to transfer WINE to Ubuntu from my pc which runs Windows. I am going to us a CD-R to do this, so do I download the Ubuntu version or Windows version?

---

### Post by blendmaster on 2006-10-12
Download the linux one.

you'll put that on the disk, and then put that on the other computer to unpack.

---

### Post by Kulluminatii on 2006-10-12
The only reason I want to try to get this game to work on Ubuntu is because my lil bro loves this game. I need my computer to do my homework and my own personal things on, after I get DSL, he will be on that computer fully, but I want to get this game working so he can wait a month for my dial-up subscription to run out.

---

### Post by Kulluminatii on 2006-10-12
Err...one problem....I clicked on the Ubuntu link, thinking it was going to download the program..but it opened up a new page where it talks about getting it through some sort of repository.

---

### Post by blendmaster on 2006-10-12
It's [here]("http://wine.budgetdedicated.com/archive/ubuntu/dapper/wine_0.9.22~winehq0~ubuntu~6.06-1_i386.deb").

---

### Post by Kulluminatii on 2006-10-12
> **Crashmaxx said:**
> Honestly, I'd just use windows if you just want to play this game on it. It will be a lot less work. A dual boot is a great idea so you can keep messing with ubuntu on it. Ubuntu isn't a great distro for no internet. Get a new modem or wait for DSL.

I Love You :biggrin:

---

### Post by Kulluminatii on 2006-10-13
Another quick question. Now that I got the flies burned to the cd, how do I go about installing WINE? Do I should click on the file in the cd and open it up?:-k

---

### Post by Kulluminatii on 2006-10-13
"Error: Dependincy is not satisfiable: libartsc0"

This is what it gives me when I try to open the file using Package Installer. What am I doing wrong?

---

### Post by podunk on 2006-10-17
In Linux you have these things called dependencies. They are library files a program needs to figure out what to do with what instruction.

In windows these are things like .dll and ocx files – all those weird file extensions you see when browsing your hard drive.

In windows – each program comes with all the files it needs to run – which makes it very easy to install. However – this is the primary reason windows gets so big so fast, the same files are in multiple directories. It's also one of the reason windows becomes slow and unreliable over time – you have multiple versions of the same file and some programs need older versions and some need newer versions (that is a grossly oversimplified view)

In Linux only the library files you need are installed – and all programs you install after use the same libraries – which keeps your hard drive from becoming bloated and you avoid version conflicts (mostly).

When you download a file to compile and install – only the file is downloaded – you will also have to download and install it's dependencies first.  If your program is a very advanced beta version (like wine!) you will likely find that you need dependencies for the  dependencies and it gets very complex very quickly.

Having an internet connection enables you to use repositories. Package managers are programs which resolve the  dependencies and install them in the proper order.  Things like aptitude and apt-get or the Package manager make life very simple *if you have an internet connection.*

Most of the programs you want to run are on the Live DVD which is here:
[http://www.mirrorservice.org/sites/cdimage.ubuntu.com/cdimage/releases/dapper/release.1/](http://www.mirrorservice.org/sites/cdimage.ubuntu.com/cdimage/releases/dapper/release.1/)

I'd advise reading this page:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by deadgobby on 2006-10-17
Does your box have a eithernet card all ready for DSL connection? You may need to ask about if your need if you do not have one all ready. You can goto ubies wiki site to see what either net card will work right out of the box.
Here is some docs to get your bros game to work using wine
[http://appdb.winehq.org/appview.php?iVersionId=3989&iTestingId=1639](http://appdb.winehq.org/appview.php?iVersionId=3989&iTestingId=1639)
[http://appdb.winehq.org/appview.php?iVersionId=4166](http://appdb.winehq.org/appview.php?iVersionId=4166)

---

### Post by caravel on 2006-10-17
> **Kulluminatii said:**
> Any suggesstions for a good and cheap linux compatible modem? Or should I wait until I get SBC(yahoo i think owns it) DSL and then try?

Regarding modems, I would wait for DSL to be honest.  Even a cheap external serial 56k modem will still cost you about £20.00+ and once you've got DSL you'll probably never use it again.  You may get a cheaper one off ebay but I wouldn't count on it functioning.  Don't bother with any more internal pci modems (winmodems) as you'll probably have the same problems you've got now.

There was/is a project called 'linmodems' [http://linmodems.org/](http://linmodems.org/) but I'm not sure if that is still being updated, nor how easy it is to get softmodems running.  The problem is that the modem itself is effectively nothing more than soundcard that emits the 'beeps' that are transmitted by the phone line, the real modem is a piece of windows software (the drivers).

-Edit: Another thought.  If that PC has ISA slots, then you may be able to pick up an old, but *real*, ISA bus modem for next to nothing.  I'm not 100% sure about the support for these however.

---

