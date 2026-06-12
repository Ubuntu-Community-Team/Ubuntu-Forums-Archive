---
title: "[SOLVED] Internet not working"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by Valthinos on 2008-02-20
I turned on my Ubuntu computer and my Internet suddenly didn't work. However, it works when I boot into Windows. All the help would be appreciated!

---

### Post by Bliepo32 on 2008-02-20
We need more information than this. First question which comes to my mind is: Is it a wireless?

---

### Post by Valthinos on 2008-02-20
No, I use a cable.

---

### Post by S15_88 on 2008-02-20
unplug it and plug it in again...

how do u connect? do u go throw terminal and do pon dsl-provider?
give more details about your problem and it's easier to help you.

thanks, Alain

---

### Post by teamkiller87 on 2008-02-20
Can you post the result of:

```
ifconfig eth0
```

---

### Post by Valthinos on 2008-02-20
I tried unplugging it and plugging it back in but that did nothing. I'm not sure what I do to connect, it just worked out of the box when I first installed Ubuntu.

---

### Post by Valthinos on 2008-02-20
Okay, there is the ifconfig eth0 report. Sorry it's a screenshot, it's just my other copmuter doesn't have internet so I didn't bother writing it all down.

---

### Post by S15_88 on 2008-02-20
what type of internet do you have? for me i had to configure mine by typing pppoe config in the terminal typing my username and password and now whenever i i want internet i do pon dsl-provier...if you were on a windows machine how would you connect?

---

### Post by Valthinos on 2008-02-20
Um.. in Windows, I just go to Network Connections if there's something wrong with the connection. Normally, in Ubuntu and Windows, they automatically connect though.

---

### Post by teamkiller87 on 2008-02-20
Try running:

```
sudo ifconfig eth0 down
sudo ifconfig eth0 up
```

Then log off and in again. This is just like a manual reset of your Ethernet interface.

---

### Post by Valthinos on 2008-02-20
Nothing happened.. internet still not working..

---

### Post by teamkiller87 on 2008-02-20
Well from what I can tell, judging on the output of your ifconfig, you are connected to the internet... What exactly isn't working? Browsing? If you haven't already, try connecting to your instant messaging client... See if that works. Also, do you need to put in some user name or password for your connection?

---

### Post by S15_88 on 2008-02-20
judging from the screenshot you ARE NOT connected! your mask is Mask:255.255.255.0
internet is 255.255.255.255.

could you post just ifconfig    no eth0, that way i can see all your devices.

Thanks, Alain

---

### Post by Valthinos on 2008-02-20
Browsing doesn't work. In amsn, it says host is unreachable. Can you make anything of that? And I don't need a password to connect to the internet.

---

### Post by Valthinos on 2008-02-20
Here's ifconfig without eth0.

---

### Post by S15_88 on 2008-02-20
can you check something for me...go to system>administration>network and check what the details of wired connection is.....enable roaming mode and restart

---

### Post by Valthinos on 2008-02-20
Roaming mode is enabled and I restarted, still can't browse and can't connect to Pidgin or amsn.:(

---

### Post by S15_88 on 2008-02-20
man that's a bummer, have you done anything recently that would have affected your internet connection?  

I know this must be frustrating but i'm sure we can figure it out, i had a painful experience with setting up my wireless but once it was fixed up it was well worth the struggle.

---

### Post by Valthinos on 2008-02-20
Hm.. yeah, it's a bit frustrating, I really don't know what could of caused this.. I'm not even too sure when was the last time I booted into Ubuntu, I got Counter Strike from a friend a few weeks back and I've been using Windows since to play it.:) I'll just keep using Windows for the time being, if you know anyone that can help or know anything that could help me, I'd really appreciate it.

---

### Post by sallen7711 on 2008-02-20
Are you using a cable modem? with router attached?

---

### Post by Valthinos on 2008-02-20
Yes. However, I'm pretty sure it's not the router's problem because when I boot into Windows it works and all the other computers in my house are also able to connect to the internet.

---

### Post by sallen7711 on 2008-02-20
you can try to ping other comp's on your local lan to see if you can reach them. This will let you know if your working locally. If successful then Check the gateway and DNS address in your router that was given by your ISP. once you have that boot into Ubuntu and try to ping that gateway address. If you cant hit it you may want to setup a static connection whereby you can enter the correct DNS settings. Hope that helps a little.

---

### Post by mrsteveman1 on 2008-02-20
Post the output of these:

```
sudo route
sudo cat /etc/resolv.conf
```

first one will tell if your computer is configured to communicate with other networks correctly, second one will tell if your system is able to resolve domain names like yahoo.com to their ip addresses.

---

### Post by ayenack on 2008-02-20
Have you set up a static address for your Ubuntu box of 192.168.1.100 in Ubuntu?

If you have you may well need to config that on the router as well.

---

### Post by Valthinos on 2008-02-26
> **mrsteveman1 said:**
> Post the output of these:

```
sudo route
sudo cat /etc/resolv.conf
```

first one will tell if your computer is configured to communicate with other networks correctly, second one will tell if your system is able to resolve domain names like yahoo.com to their ip addresses.

Okay, after typing it in, here are the results.
P.S. sorry for long wait in replies.

---

### Post by Valthinos on 2008-02-26
Well.. thanks for everyone who tried to help! However, the problem was with firestarter, it was blocking something so that's why I couldn't connect to the internet, I just removed it. Problem fixed now!

---

