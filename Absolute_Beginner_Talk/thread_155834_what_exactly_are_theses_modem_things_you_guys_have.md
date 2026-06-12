---
title: "what exactly are theses modem things you guys have been talking about lately?"
date: 2006-04-05
forum: Absolute Beginner Talk
---

### Post by TheRingmaster on 2006-04-05
I see other forum discussions that talk about the dial-up modems that are available on ubuntu linux and probably others. An example would be like gppp and kppp. How good of a connection do these bring. Would I be charged on my phone bill? I also see that there is a vote going on about winmodem. any information would be appreciated. currently I am using windows xp pro (not for long) and use dial-up internet provided by Juno internet service.

thanks

jp

---

### Post by encompass on 2006-04-05
Modems are not fast... they are the old technology that people used that used an ordinary phoneline to communicate with the internet.
the ppp software they speak of is the software that talks to the modem so that you can get on the internet.
wow, I never thought I would answer this kind of question, but I think it is getting to that point now, when they are ousting modem connections.
Hope that helps.
[http://en.wikipedia.org/wiki/Modem]("http://wiki_modems")

---

### Post by NeghVar on 2006-04-05
Ok, I'll assume you don't know what a modem is:

[http://en.wikipedia.org/wiki/Modem](http://en.wikipedia.org/wiki/Modem)

Its long and indepth and it goes back to the very early days but it explains what modems are. Basically its just a piece of hardware that is used to connect your computer to the internet via dialup. If you already have dialup then you have a modem, its what you plug the phone line into.

As for winmodems, they are covered in the article but go like this. Most modems use hardware to send and recieve, winmodems cut back on HW and use software built into windows to do this, this means that when going to another OS they can have mixed results, there are tutorials and such on how to get certain winmodems working in Linux.

Hope that helps.

---

### Post by kop316 on 2006-04-05
Hey

Well INstalling the modem is one thing different from getting the ISP to work with linux. If you use the modem connections and not a program for connecitong to the internet, it shoudl be easy, as you use the system, administration, netwokring feature. 

If you use a program to connect to the internet (I did in Windows), figure out your telephone number that you connect to. When it promptr for a user name, just use your E-mail, and the rest is pretty straight foward.

If you need to find out how to use your modemwokring with linux, I would say you shoudl look through the forums or the wiki.ubuntu.com. They give a lot of way to get your moedem working. 
However, if you do not have a modem, or do not wish to go through this, I woudl recommend buying an external modem. Make sure it is a serial modem (uses the serial port). I found a Best Data 56k modem for 60$, but it worked straight out of the box.

I hope I helped.

---

### Post by dermotti on 2006-04-05
Wow, I never thought ide see the day where someone would say "whats these modem things".

I am only 27, and now i offically feel like an old man.

---

### Post by skirkpatrick on 2006-04-06
You're not too old, remember that he already stated he's using dial-up Internet under XP.  However, you almost never see an external modem anymore, to most people they are just another jack in the back of the computer.

---

### Post by towsonu2003 on 2006-04-06
> **jpazindustries]How good of a connection do these bring. Would I be charged on my phone bill?[/QUOTE]
using dial up in windows and linux are almost the same things. Think of your modem as some guy using your phone to talk to your ISP[1] about some stuff :) 

A couple of differences:
1. hardware support sucks in linux for winmodems, so it's hard to configure them (winmodems, unlike real (serial/hard) modems, depend on your Operating System and software installed in there to function properly). 

2. tools to dial for the connections are different. the end result is the same if your driver in linux works... hmm, okay, may be not the same: my winmodem dialup connection is faster in linux than in windows. 

3. Related to both 1 and 2, you may experience dialing difficulties: your hardware may not be working due to crappy drivers (my sl-modem does this sometimes: disconnects when CPU usage goes too high while at the same time something is writing too much data to the disk), or your ISP won't accept your dialing bc you are not using their software (AOL best example?). There is really no way of knowing the difference between these two once you have dialing difficulties. Best would be to search around the forum to see if people with your ISP report problems, or post a new thread (with you ISP + question as the title).

The second link in my signature will explain how supported modems can be configured and what the common tools to dial are. I personally prefer wvdial especially because it gives some output about the connection. 

Dial up charges your phone bill because you dial and connect using your modem as a "phone". Unless you do not call some special number (provided by ISP), the telecom provider will not know the difference between <the time you are connected to your ISP> and <the time you spend talking with someone on the phone>. Some telecom providers though (Verizon for example) offer unlimited local calls so you don't get bankrupt  said:**
> ISP = Internet Service Provider (AOL, Comcast, Juno -yours- and whatnot)

> I also see that there is a vote going on about winmodem. any information would be appreciated.
A vote that's not working for Dapper... The main purpose of that post was to get Ubuntu devels working with linmodems.org to come up with a nice solution for our winmodem recognition problems... 

[quote]modems that are available on ubuntu linux
if you are thinking about switching to linux but still using your winmodem, you might wanna do one of the following:

1. Do not wipe out your Windows installation but instead dual boot Linux & Windows. Believe me, you're gonna need Windows to get your Linux driver working

2. Use the live cd to try to configure your winmodem. this is not practical. but I find it useful especially because if you somehow bork your linux during winmodem configuration, you just reboot and the installation is back for you to restart configuring the crap :) In my early days, because I didn't know what I was doing, I installed linux 4-5 times just to restart configuring the modem... The LiveCD will also enable you to know whether your modem is supported (see scanmodem in second link in my signature) in linux without having to install to hard drive.

---

### Post by natehatewindows on 2007-10-23
make me feel kinda old too.....:( :) dialup is not fast (just like said before) but it is better than no connection at all ;).

---

