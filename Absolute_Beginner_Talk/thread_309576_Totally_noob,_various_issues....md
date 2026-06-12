---
title: "Totally noob, various issues..."
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by mrSlush50 on 2006-11-29
Hello,

just finished installing ubuntu yesterday.  So far, I'm unimpressed as I'm having some issues.  If these can be resolved, I think I would really like the system, but it is getting pretty frustrating.

If anyone can help me out that would be great.

I am running 6.10 on an AMD laptop.

1. gmail crashes firefox.

gmail isn't the only site, but it's the most consistent.  I'm not the only one with this problem.  there are at least a dozen other threads on this topic, none of which have a solution that has worked for me. this lead to my next problem.

2. command prompt issues.

This one is most likely simply due to my unfamilliarity with the system.  In trying to fix the first problem I ran across a solution that involved changing the color depth on my monitor.  I open the terminal, and type sudo /etc/X11/xorg.conf

it asks for my password, which I type (It took me a couple of seconds to realize that my keyboard was not broken, as nothing shows up when you type) 

then I get this message:  sudo: /etc/X11/xorg.cong: command not found

huh?

also, I've been trying install java using the instructions on their site. [http://www.java.com/en/download/help/5000010500.xml#selfextracting](http://www.java.com/en/download/help/5000010500.xml#selfextracting)

this is what I get:

keith@LAPPY-5000:~$ su
Password: 
su: Authentication failure
Sorry.


clearly I'm doing something wrong here, the problem is determining what.

3.  ipod issues.

I could spend hours searching around trying to find out how to; play mp4 m4a and m4v files, transfer music too and from my Ipod, etc...  or someone with an Ipod video who has already figured this out might be able to help me out.  :) 

4. wireless network problems

my wireless card has a switch.  the switch is off.  i cannot turn it on.  ???

I don't even know what information to provide in order for someone to be able to help me.


Thank you for your help.

---

### Post by d3v1ant_0n3 on 2006-11-29
For #2:

The command you need is:

sudo gedit /etc/X11/xorg.conf

and remember, the X in X11 is case-sensitive:D 

For your ipod, you might want to try GKPod (or is it GTKPod?) I don't own an Ipod myself, but have heard good things about it.

For Java installation, maybe consider giving [ AUTOMATIX](http://getautomatix.com/wiki/index.php?title=Installation) a try. It's a program that automates the installation of lots of handy programs, media codecs etc for you. It's not the purist's way of installing this stuff, but it is quick and dirty, and gets the job done.

Hope this is of some help:D

---

### Post by ReaderRat on 2006-11-29
> I open the terminal, and type sudo /etc/X11/xorg.conf
Should be:
```
sudo **gedit** /etc/X11/xorg.conf
```

[How **sudo** Works](http://www.ubuntuforums.org/showthread.php?t=275605)

---

### Post by crazedgremlin on 2006-11-29
you are trying to log in to root by use of su

in Ubuntu by default you can't log in to root, you can only give your account temporary root privileges by use of sudo

to make root log-in-able, type:
     sudo passwd root

now you can type su to log into root.
------------------

I'm not sure about your wifi card... what type is it?

---

### Post by Peepsalot on 2006-11-29
I wouldn't bother with the instructions from the Java site...
Have you been to this site?
[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

You should be able to Java from the repositories, there are instructions here:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox)

---

### Post by lumpki on 2006-11-29
Any time that it calls for 'su' and then do something, prefix those command(s) with 'sudo' instead. Or you can activate the root account like crazedgremlin suggests, but only use it when you need to.

Ok, I see that some people fixed their Firefox problem by setting their colordepth. That's wierd. Anyway, to reconfigure X, instead of editing the file by hand, you can do
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by mrSlush50 on 2006-11-30
I reconfigured the color depth, with no luck.  I downloaded epiphany and set up thunderbird so that I can check my email, but it's still really annoying not having firefox.  

would I have better luck with 6.06?  what would switching over entail?  Is that a fresh install?  what features would I be missing?

also, resources for getting a wireless card working?  I've checked the forums, but since I don't even know what my specific problem is, they haven't been very helpful.

---

### Post by Peepsalot on 2006-11-30
Your wireless problems are incredibly vague.  You never said what card you have.  What do you mean you have a switch that you can't turn on?

---

### Post by mrSlush50 on 2006-11-30
well... there's a button at the top of my keyboard.  it's the wireless button.  in windows, when I press the button, it lights up and the wireless card turns on and windows automatically detects then connects to an available wireless network.

when i press the button in ubuntu, nothing happens.  ubuntu knows the card is there, but beyond that I can't get it to do anything at all.

its a Broadcom Corporation BCM4306 802.1b/g Wireless LAN.

---

### Post by RMorris78 on 2006-11-30
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Ndiswrapper_for_Broadcom_43xx_wireless_chipset](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Ndiswrapper_for_Broadcom_43xx_wireless_chipset)

that should be good for installing the wireless card

---

### Post by fatneck on 2006-11-30
[http://www.ubuntuforums.org/showthread.php?t=185174](http://www.ubuntuforums.org/showthread.php?t=185174)

this worked for me with the wireless - my laptop sounds similar to yours...

---

### Post by riven0 on 2006-11-30
You may have already done this, but have you tried the ndiswrapper? 

Also [this howto?]("http://www.ubuntuforums.org/showthread.php?t=185174&highlight=Broadcom") may help. I don't use wireless, but apparently it worked for the majority of people.

EDIT: Ah, fatneck got it before me! :D BTW, gtkpod works like a dream. I tried iTunes under Windows. Got massive slowdowns.

---

### Post by mrSlush50 on 2006-11-30
alright, wireless now functions.  it will load pages for a couple of seconds, then quit.  don't know what that's about as it still says I'm connected to the network.  but at least there is some improvement.

Thank you.

still no luck with flash and firefox.

---

### Post by seshomaru samma on 2006-12-01
> **mrSlush50 said:**
> I reconfigured the color depth, with no luck.  I downloaded epiphany and set up thunderbird so that I can check my email, but it's still really annoying not having firefox.  

would I have better luck with 6.06?  what would switching over entail?  Is that a fresh install?  what features would I be missing?

also, resources for getting a wireless card working?  I've checked the forums, but since I don't even know what my specific problem is, they haven't been very helpful.

I noticed that since Edgy came out there are many threads about Firefox problems. In Dapper these problems do not exists. To get Dapper you need to reinstall but you wont lose any features as far as I know.

---

### Post by mrSlush50 on 2006-12-01
dapper is 6.06?  I'm starting to think that that's what I should have used to begin with.

---

### Post by Energizor on 2006-12-02
I had a problem with Firefox 2.0 crashing when I went to Yahoo all the time after a fresh install of Edge. I found a link to a script  /usr/bin/firefox . I ran it as an application and Firefox hasn't crashed when going to Yahoo since. Was hoping someone else could try it out and let me know if it fixes their problem.

---

