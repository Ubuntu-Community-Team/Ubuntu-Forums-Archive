---
title: "Installing/Using a Wireless Network Card on Kubuntu"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by beastrace91 on 2007-08-15
Hello everyone,

I have gotta Kubuntu 7.04 up and running on my home system and its working great! Now my next task: get it working on my laptop. The main thing I am having trouble with is connecting to my wireless network. It detects my wireless card but it shows no net work....(Right now I have a lan cable plugged into it.)

What can I do to go about getting my wireless card working? Any help would be great.

~J3ff

---

### Post by overdrank on 2007-08-15
> **beastrace91 said:**
> Hello everyone,

I have gotta Kubuntu 7.04 up and running on my home system and its working great! Now my next task: get it working on my laptop. The main thing I am having trouble with is connecting to my wireless network. It detects my wireless card but it shows no net work....(Right now I have a lan cable plugged into it.)

What can I do to go about getting my wireless card working? Any help would be great.

~J3ff

Hi if you can give use some info on the card we may can help you search and find a solution. The command in the terminal works great

```
lspci
```

---

### Post by beastrace91 on 2007-08-15
[IMG]http://img455.imageshack.us/img455/6048/lspcireadoutkp0.png[/IMG]

Theres a print screen of the console read out when I put in "lspci"

Hope this helps you help me some, also thanks for the speedy respone :)

~J3ff

---

### Post by overdrank on 2007-08-15
HI and a simple copy and paste would have worked but that it ok LOL Ok it is the BCM4318 Airforce one card and this thread has helped many
[http://ubuntuforums.org/showthread.php?t=405990&highlight=bcm4318](http://ubuntuforums.org/showthread.php?t=405990&highlight=bcm4318)
Good luck! :)

---

### Post by ayenack on 2007-08-15
Just thought that I would butt in here take a look at this [guide]("http://techaspect1.wordpress.com/2007/05/26/how-to-set-up-wireless-internet-on-ubuntu-with-dell-inspiron-2200-broadcom-corporation-bcm4318-airforce-one-54g-cards/") it should do the trick. Make sure to unplug your wired network before doing the install, this is most important. Seem I could be wrong about unplugging your wired network according to overdranks link. Emm.

---

### Post by beastrace91 on 2007-08-15
Is there a way to copy and paste out of Konsole? I used crtl+c and it didn't work.

Also thanks for those links I'll try them out in a few mins.

~J3ff

---

### Post by ayenack on 2007-08-15
To copy and paste from console (terminal) just highlight the text to be copied then right click and select copy. To paste right click and select paste. Simple.

---

### Post by beastrace91 on 2007-08-15
lol now I feel kinda dumb that should have been apprent.

~J3ff

---

### Post by ayenack on 2007-08-16
LOL

It's funny how when you move to a new environment you sometimes forget the straight forward things that you've done a million times before.:rolleyes:

---

### Post by st33med on 2007-08-16
> **ayenack said:**
> LOL

It's funny how when you move to a new environment you sometimes forget the straight forward things that you've done a million times before.:rolleyes:

Yeah, when I wanted to paste in the terminal, sometimes I'd hit Ctrl+V, but it come up with '^V'. :lol:

---

### Post by beastrace91 on 2007-08-17
> **overdrank said:**
> HI and a simple copy and paste would have worked but that it ok LOL Ok it is the BCM4318 Airforce one card and this thread has helped many
[http://ubuntuforums.org/showthread.php?t=405990&highlight=bcm4318](http://ubuntuforums.org/showthread.php?t=405990&highlight=bcm4318)
Good luck! :)

I got my wireless card working using that link thank you very much! Now my next trouble I got the card working @ a friends house and it jumped right on his wireless here @ home I am unable to connect to my brother's setup it stops @ 58% (IP Configuration) Everytime.

Is this a driver issue or a configuration issue on the part of the router? I am looking @ the front of the Router Now and it says "Linksys WRT150N Wireless-N Home Router"

Any help once more would be great.

~J3ff

---

