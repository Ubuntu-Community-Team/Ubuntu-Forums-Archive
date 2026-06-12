---
title: "I'm Very very new to Ubuntu"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by U2XS on 2006-11-16
Hi, I just installed Ubuntu on my Hard drive for the first time and I came across something that has me stuck.  The installation was quick and easy (under 30 minutes) but when I restart it asks me to put in the name and password (in the dos screen).  So I do.

But after that it runs something, lets me know that a few disclaimers and that I cant' use root but can use sudo (or something like that :confused:) and then I am expected to type in a command or soemthing.  I was expecting this to be more like Windows.

Did I do something wrong in the install or am I just missing a step or two?  Any/all help would be appreciated.  Thanks

---

### Post by amgeex on 2006-11-16
Wierd... Try typing "startx" (without the quotes) at the command promt (dos screen). Post back if you still have problems.

---

### Post by PriceChild on 2006-11-16
> **U2XS said:**
> Hi, I just installed Ubuntu on my Hard drive for the first time and I came across something that has me stuck.  The installation was quick and easy (under 30 minutes) but when I restart it asks me to put in the name and password (in the dos screen).  So I do.Did you do a server install?

Ubuntu doesn't normally crash to cli without an error.> But after that it runs something, lets me know that a few disclaimers and that I cant' use root but can use sudo (or something like that :confused:) and then I am expected to type in a command or soemthing.This is a standard message displayed first time you run a terminal.

```
I was expecting this to be more like Windows.
```Are you sure you're using Ubuntu for the right reasons? Linux is an "alternative" to windows... not a replacement.

---

### Post by emarkay on 2006-11-16
I have fallen into the same trap, and I knew much more about Ubuntu/Linux.  Ubuntu and Windows are parallel universes with the commonality being that they run on PC's, and do similar things, I have found.  :(

From what I recall, that's just the opening screen from a fresh install.

Can you run from the CD and get a 'window" that seems like it's runninng OK (look at the clock, try some menus).  That confirms that teh Ubuntu is OK and your PC is OK.

Can you post a screen shot - do you have a digital camera?

Let us know more details.

---

### Post by rlozano on 2006-11-16
> **U2XS said:**
> Hi, I just installed Ubuntu on my Hard drive for the first time and I came across something that has me stuck.  The installation was quick and easy (under 30 minutes) but when I restart it asks me to put in the name and password (in the dos screen).  So I do.

But after that it runs something, lets me know that a few disclaimers and that I cant' use root but can use sudo (or something like that :confused:) and then I am expected to type in a command or soemthing.  I was expecting this to be more like Windows.

Did I do something wrong in the install or am I just missing a step or two?  Any/all help would be appreciated.  Thanks

or your xorg.conf may have something to say as well. try posting it here. it can found in /etc/X11/xorg.conf

---

### Post by adamkane on 2006-11-16
I think u2xs means that Ubuntu is always asking for the root password when running applications. As we Ubuntu users all know, we are entering our password constantly.

Many are sad to learn that Ubuntu requires more typing than with Windows. If extra typing and security get you down, then Ubuntu may not be for you.

---

### Post by Shuja on 2006-11-16
> **adamkane said:**
> I think u2xs means that Ubuntu is always for the root password when running applications. As we Ubuntu users all know, we are entering our password constantly.

Many sad to learn that Ubuntu requires more typing than with Windows. If extra typing and security get you down, then Ubuntu may not be for you.

Vista is going to be the same way, lots of nagging windows when you try to change a configuration.  OS X asks for your password as well.

It sounds like he did a server install btw

---

### Post by mush on 2006-11-16
Yea this sounds like a server install. Sounds like you just installed it, and immediately started having problems with it. Your best bet is probaly just to put the Ubuntu CD back in and do a reinstall, except this time make sure you go a different route with the install.

---

### Post by U2XS on 2006-11-17
Hey guys, thanks for all of the help.  I don't mind typing when I know what I'm supposed to type. I Tried startx but it didn't work out.

I got through the entire install perfectly as well.  It was very easy and intuitive.  The language, clock, time zone, partition, etc...

I am aware that it is not like windows in every sense, but I just wasn't expecting it to be dos.  I only know a limited list of commands in dos and none of those helped me.  The screen shots I saw feature images and mouse-work; which is what I was expecting.

I will take pictures with my camera and post them if it helps.  As for my xorg.comf file - even if I could access it, I wouldnt' knwo how to transfer it out using dos.  I have installed Ubutu on an old 4.3 GB hard drive that is not related to my windows HD.

Thank you all for all of the help.

---

### Post by steve.horsley on 2006-11-17
Ubunti should normally give you a graphical username prompt, and when you log in it gives a desktop not so different to Windows. If you have been dumped into a white-on-black command prompt, one of two things has happened:

1) You chose to install the "server" version, which doesn't have a GUI by default because servers don't need them. If this is the case you can use this command to get the GUI installed:
**sudo apt-get install ubuntu-desktop**

2) The install went wrong somehow and the GUI cannot start properly. If this is the case, there are two things you can try:
a) use the command **startx** and post the output here so a guru can help, or
b) use the command:
**sudo dpkg-reconfigure xserver-xorg**
and answer a load of questions, taking the defaults wherever you are not sure, and see if this fixes your GUI (if it does, **startx** will give you a working desktop). Often, just acccepting the defaults all the way through will fix the problem.

---

### Post by U2XS on 2006-11-20
Ok, so I took a picture of my screen as it appears.  Then I tried the command that Steve provided and took another picture.   Any thoughts?

[http://www.u2xs.com/temp/img-001.jpg]("http://www.u2xs.com/temp/img-001.jpg")
[http://www.u2xs.com/temp/img-002.jpg]("http://www.u2xs.com/temp/img-002.jpg")

---

### Post by 56phil on 2006-11-20
-u2xs

Where did you get your CD from? That doesn't look like the Ubuntu I know - and am growing to love.

Try this link:
 [http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download](http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download)

---

### Post by U2XS on 2006-11-20
Hey, I got it from here.  I went to 

[Http://www.ubuntu.com](Http://www.ubuntu.com)
Clicked on "Download"
Clicked on "Ubuntu 6.06 LTS, Ubuntu with long-term support"
Clicked on the first "United States" link and I ran it.

I guess I should try 6.10 then.

---

### Post by 56phil on 2006-11-20
That shouldn't matter 6.06LTS should be fine. Just be sure you got the desktop version and not the server version. OK?:)

---

### Post by U2XS on 2006-11-20
Awww Jesus I can't apologize enough.  I can't believe I could make such a stupid mistake!!!!!!!!!!!!!!

I was searching to look for the new download and I saw that I had clicked on the right architecture of the right release (6.06) but I downloaded the server version.  Ugh. ](*,) 

Thanks for your help.  I will be much more careful before I post again.

---

### Post by 56phil on 2006-11-20
No problem all humans are fallible and Ubuntu is Linux for humans.

---

### Post by IYY on 2006-11-20
They really should name this version something other than `Server install'. After all, many people may want to run graphical applications on their server (like with Windows servers), and think of the server install as regular Ubuntu plus some server-oriented apps. A better name would be `Non-graphical ubuntu' or 'Text-based Ubuntu'. 

By the way, the terminal in Ubuntu is not DOS. It's Ubuntu itself which, being a GNU/Linux distribution, is Unix-like. The shell you are seeing is called 'Bash' and is far more powerful than DOS. You will have to learn some new commands if you are coming from a DOS background, but it is important to learn the basics of working with the command line. Unlike with DOS and Windows, the GNU/Linux command like often offers simpler solutions than the graphical approach and is seen as one of the system's greatest powers.

---

### Post by adamkane on 2006-11-20
Agreed.

Desktop version for the average user.
Server version for the administrator.

Needs to be clearer.

---

### Post by Paul133 on 2006-11-21
Yeah. No surprise. I'm glad the guys at the forums were able to resolve it for you. And, when you say you expected it to be like Windows, I'm assuming you just meant that it would have a GUI. I don't blame you. When I installed Ubuntu with the regular install, it wouldn't even load. Then I tried the alternate CD a few times and it hung during the installation, During this time, my drives were out of commsion, too. I finally tried the server install, and it worked. And of course, just ```
 sudo apt-get install ubuntu-desktop 
``` and then I have Gnome on top of the raw CLI you just saw. By the way did you know you can switch between CLI and GUI by hitting ctrl-alt-F1 and ctrl-alt-F7, respectively. And you can call up terminals, too. I have my Windows key maooed to starting terminals. So, you can definitely use the CLI and it's sometimes preferred (such as when you have a problem), but you also have a GUI on top (Gnome is with Ubuntu and KDE with Kubuntu).

IYY's right. Gnome, the GUI, is built upon the raw goodness of UNIX that is the heart of Ubuntu. Unfortunately, most web sites now are optimized for GUI's, unlike in the 1980's and thus lynx (a  CLI web browser) will only take you so far.

---

