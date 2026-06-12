---
title: "how to uninstall ubuntu and keep just kubuntu?"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by vandroiy.cl on 2007-08-19
Hi, I'm a newbie ^^
I want to uninstall Ubuntu and Keep just Kubuntu because it's works better in my laptop (Olidata), recognizing everything and with the "full screen" video with Kaffeine working great, thing that I couldn't do in Ubuntu whit Totem, VLC and Mplayer. So I guess that this is the exact distro for me.

Let me tell you what I've done 'till now
I format the hard drive with Gparted and say bye to windows 
then I installed Ubuntu 6.01 from CD and updated it to 7.04
then i use "aptitude install kubuntu" and then test the "full screen" stuff that wasn't working for me in gnome
and that's it, now i just want to uninstall Ubuntu and keep just Kubuntu working. 

Thanks =)

---

### Post by Hobo Joe on 2007-08-19
I'm a little confused, are you saying that you installed Ubuntu, and then updated it to install Kubuntu on top of Ubuntu?

I may be wrong, but the command should be:
```

sudo aptitude install kubuntu-desktop

```

---

### Post by wolfen69 on 2007-08-19
```
sudo aptitude remove ubuntu-desktop
```

---

### Post by vandroiy.cl on 2007-08-19
i installed Ubuntu 6 and updated it to 7
then, when i realize that it wasn't working well, i install Kubuntu (using the command that you say), and now i want to uninstall ubuntu =)

sorry if my English is not so good ^^

I got a question,
if I use that command > sudo aptitude remove ubuntu-desktop
it will remove everything i got in ubuntu, installed programs like VLC for example,  except for my personal folder, right?

---

### Post by TeaSwigger on 2007-08-19
Hello, 

This guide might be what you want:

Getting Back to a Pure KDE on Ubuntu
[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

But understand you don't have to choose. That's a nice thing about it. You can install and keep what you want to.

---

