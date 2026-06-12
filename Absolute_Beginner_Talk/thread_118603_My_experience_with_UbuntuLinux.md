---
title: "My experience with Ubuntu/Linux"
date: 2006-01-17
forum: Absolute Beginner Talk
---

### Post by apette on 2006-01-17
I made my self a new year resolution for 2006: I was going to give linux a fair chance and since I was going to format and reinstall my computer anyway I have now made reality out of it. I ended up using Ubuntu because I thought that would be the best and most convenient distribution.

I have been using only Ubuntu for a week or so now, and here is my experience so far:
I have to admit I am not impressed. Not at all.

First of all, it takes ages to start up my computer. At least 3 times longer than with Windows XP. 
Second, the system freezes often. Much more often then Windows.

I have spent a lot of time getting the correct drivers for my system and to get software which can do the same operations as I used to do before. When I finally find some useful software it's either for another linux distribution or I do not have the correct packages installed, so I have to spend time finding them. I have never seen as many error messages as I have since I installed ubuntu.

In totally I have spend so much time doing extra work now, that I should rather spent on licenses in a windows system.

Maybe I am doing something totally wrong, but if I am, I guess most other people are doing it too. :mad:

---

### Post by 23meg on 2006-01-17
> First of all, it takes ages to start up my computer. At least 3 times longer than with Windows XP. 
Mine starts faster than XP. See [this]("http://www.ubuntuforums.org/showthread.php?t=89491"), and [this]("http://www.ubuntuforums.org/showthread.php?t=80423").
> Second, the system freezes often. Much more often then Windows.
That just shouldn't happen; does it happen at particular times, when using particular apps for example? Do you see any errors in your logs (Applications / System Tools / System Log)?
> 
I have spent a lot of time getting the correct drivers for my system and to get software which can do the same operations as I used to do before. When I finally find some useful software it's either for another linux distribution or I do not have the correct packages installed, so I have to spend time finding them.What's your hardware? What devices are you trying to configure? > Maybe I am doing something totally wrong, but if I am, I guess most other people are doing it too. I see this is your first post so it seems you haven't asked for help; that's what you're doing wrong. If you do, chances are your problems will be fixed. So if you want help, start by giving us details about your hardware.

---

### Post by djheadley on 2006-01-17
What are the spec of your computer?  Exactly what have you been having trouble with?  What programs are you trying to install?

---

### Post by earobinson on 2006-01-17
Are you looking for help or is this just a post about this distro?

---

### Post by apette on 2006-01-17
Ok. I have got rid of my desperation now, so lets try being constructive now.

My major problem - which I also think is what causes the systems long startup time - is the network connections. I got a laptop, and hence I am using different networks often, also changing between wired and wireless networks. Therefore I would like to have them both active at the same time and make the computer find out whats more suitable for the loaction I am on at the moment. But when both the wireless and ethernet are set active in the System > Administration > Networking windows, none of them work. I have to deactivate one of the to get on of them working. Is it supposed to be like this or is there anything I can do?

I am using a Compal CL56 computer, Pentium Mobile 1.6MHz processor, 512 mb RAM, 60 GB harddrive, Ethernet card: Realtek 8139; Wirelss: Intel Pro/wireless 2200BG.

---

### Post by tekwarren on 2006-01-17
I think the frustration of alot new people is that they *expect* it to be as "easy" as what they are used to. When really trying out something and giving it an honest chance you really have to be open and accept that it simply is NOT going to be like windows. Another thing I have learned through personal experience is that if you know nothing about linux then trying to learn it without any help is only going to frustrate you. It takes patience and alot of questions...questions that usually easily answered by those who have overcome the situation themselves.

I'm a beginner myself having only toyed with Linux over the years and currently experiencing Ubuntu...and it is exactly that...an EXPERIENCE. It seems every couple days there is another "not impressed" post or someone frustrated and having a negative experience with Ubuntu...I dare say the underlying reason is usually just because of the lack of knowledge. Just in reading and searching these forums I have been able to do alot and the few posts I have that where questions help was usually only mintues away.

I guess I'm just trying to say to others in this situation take it in stride...none of us where born knowing how to use windows. Learning takes time give it a chance.

---

### Post by 23meg on 2006-01-17
What's your video chip?
> 
But when both the wireless and ethernet are set active in the System > Administration > Networking windows, none of them work. I have to deactivate one of the to get on of them working. Is it supposed to be like this or is there anything I can do?Try using GTKWifi or Wifi Radar. I'd also suggest Network Manager but I haven't tried under Breezy. 

You can also skip the network activation and time sync steps (actually any step) with Ctrl+C.

---

### Post by apette on 2006-01-17
[QUOTE=23meg]What's your video chip?[/QUOTE]

ATI mobility radeon 9700

---

### Post by 23meg on 2006-01-17
Have you installed the ATI fglrx drivers? I'm not familiar with ATI hardware but you should be able to find the appropriate instructions if you do a forum search.

---

### Post by apette on 2006-01-17
And another thing. Why does Ubuntu install so much software which I can't choose not to install. I don't need all these silly games, chatting software, bad media players  . I would like to install the software I need and contain a clean system, instead of filling it with thing I don't use.

---

### Post by apette on 2006-01-17
[QUOTE=23meg]Have you installed the ATI fglrx drivers?[/QUOTE]

I tried to but I never suceeded.

---

### Post by 23meg on 2006-01-17
[QUOTE=apette]I tried to but I never suceeded.[/QUOTE]
There it is; I bet we've pinned down your main problem :cool: As I said, I don't know how to install fglrx but if you state the errors you're getting I'm sure you'll find help.

---

### Post by newuser111 on 2006-01-17
you can use easy ubuntu to install the ati drivers, thats what i did when i first installed ubuntu, it seemed to work fine

[https://launchpad.net/products/easyubuntu/](https://launchpad.net/products/easyubuntu/)

---

### Post by apette on 2006-01-17
Hopefulle. But when I tried to the last time I fucked up everything and couldn't access the GUI anymore, only a command line. And I got so scared I didn't dare to try again.

I didn't know you people here where that helpful. I have found some answers here before, but I didn't think anyone would care helping me out, so thanx. My most frustrating day was yesterday, and then I couldn't access ubuntuforums.org at all.

---

### Post by kostkon on 2006-01-17
Apette you have confused me! Can you explain how do you try to install apps?!! Do you know that you can easily install apps with Synaptic and, furthermore, you can uninstall from there anything you don't like. It's so simple, hundred times simpler than in Windows!!

How can you say that you had problems to find apps, problems installing them (dependencies). This only happens when you try to install from sources outside the Ubuntu repositories. You only do this in exceptional circumstances and depends mostly of your needs. But for normal situations, the Ubuntu repositories and Synaptic is more that enough; is perfect.

I would recommend you to give Ubuntu another try. Ask here the community to help you, first of all, how to install the ATI drivers. Don't say I tried and failed and that's the end; and ask the community to explain to you anything that you don't understand fully.

Think positive

---

### Post by Mustard on 2006-01-17
[QUOTE=apette]Hopefulle. But when I tried to the last time I fucked up everything and couldn't access the GUI anymore, only a command line. And I got so scared I didn't dare to try again.

I didn't know you people here where that helpful. I have found some answers here before, but I didn't think anyone would care helping me out, so thanx. My most frustrating day was yesterday, and then I couldn't access ubuntuforums.org at all.[/QUOTE]

When you lose your display like that you can do this command in terminal (which normally fixes it)..

```
sudo dpkg-reconfigure xserver-xorg
```

That command will reconfigure your xorg.conf file which controls your keyboard, mouse and display settings.  It would ask you lots of questions, to which you would just choose the default answer each time, until you get to the display drivers part.  You can change the display drivers back to the 'vesa' drivers and that should allow you to get back into your gui.

---

