---
title: "Internet connection - need all the help i can get"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by rbless on 2007-06-29
i tried following the instructions but it is just confusing the hell out of me i did the pppoeconfig but it still wasent connecting 

i using bell sympatico high speed dsl with a speedstream modem , is there any type of program i could download or a procedure i could follow to get it working??? please help

---

### Post by rbless on 2007-06-29
anyone

---

### Post by juxtaposed on 2007-07-04
That modem usually works fine for me, maybe its your network card?

I always just let it auto config with DHCP or something like that.

---

### Post by blastus on 2007-07-04
If your modem is connected to an Ethernet (network) card in your computer then you shouldn't have any issues with it. Some providers require you to run pppoeconfig, some don't. The better ISPs do not require pppoeconfig and their modems work right out-of-the-box with no configuration and will work with any operating system.

If your modem is a USB or wireless modem, I'd go to the manufacturer's website and find out if the modem is supported on non-Windows machines like Mac OX for example. This may give you a clue as to whether you have what's called a full-blown winmodem--that is a modem that is exclusively designed to work with Windows only and nothing else. winmodems are a class of modems that lack the basic hardware and cannot function without proprietary Window's drivers--because they lack the necessary hardware to function without those Windows drivers..

That's said, if you do have a USB or wireless modem, I wouldn't give up. There's lots of people on these forums that have USB or wireless modems and have got them working. These modems may require special drivers. I'm sorry I couldn't be more help on this one.

---

### Post by RedSquirrel on 2007-07-04
Just a thought:

If your networking hardware is functioning properly, here's something else to be aware of: when you provide your login information in the pppoeconfig program, you may have to provide a full username like this:

```
 [EMAIL="username@yourisp.com"]username@yourisp.com[/EMAIL]
```

and _not_ just 

```
 username
```

It's just a simple thing, but that has stopped a lot of people from connecting with pppoe. ;)

---

