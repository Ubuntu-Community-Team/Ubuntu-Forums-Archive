---
title: "How To Disable A Wireless Card?"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by Rovdjur on 2007-07-28
Well I have a built-in wireless card that never worked too well, so I have an external wireless card (PCMCIA, not USB) that I purchased and I would like to use this one instead of the internal one. I have a hardware switch that turns off the internal wireless card when in Windows, but has no effect in linux. So how could I go about disabling an internal card?

---

### Post by MrHippocampus on 2007-07-28
You could try finding out what the driver is and the name of its kernel module, with this you can do:

```
sudo modprobe -r modulename
```
If that works you can blacklist the module so it wont get loaded on startup again.

---

### Post by Rovdjur on 2007-07-28
> **MrHippocampus said:**
> You could try finding out what the driver is and the name of its kernel module, with this you can do:

```
sudo modprobe -r modulename
```
If that works you can blacklist the module so it wont get loaded on startup again.

Hey thanks for the quick reply. I am new to linux, so I do not know much about it. How would I go about blacklisting it? I assume it is just a text file where I comment out a line?

---

### Post by MrHippocampus on 2007-07-28
actally its add a line, but yet thats pretty much the idea. Youll notice the file has some things blacklisted already due to e.g. bugs on a certain machine.

Im not on ubuntu at the moment so im not 100% sure where the blaclist file is located, but I think its /etc/modprobe.d/blacklist

For an example to blacklist my inbuilt wireless I would add
```

blacklist ipw3945

```
(I think thats the syntax, check the other entries and make yours look similar)

---

### Post by Rovdjur on 2007-07-28
> **MrHippocampus said:**
> actally its add a line, but yet thats pretty much the idea. Youll notice the file has some things blacklisted already due to e.g. bugs on a certain machine.

Im not on ubuntu at the moment so im not 100% sure where the blaclist file is located, but I think its /etc/modprobe.d/blacklist

For an example to blacklist my inbuilt wireless I would add
```

blacklist ipw3945

```
(I think thats the syntax, check the other entries and make yours look similar)

Ok, seems simple enough. However, just one more question for the newbie. I could not quite understand your instructions on how to modprobe. Could you explain it a little better please? Thank you so much :)

---

### Post by MrHippocampus on 2007-07-28
All you have to do is open a terminal "Accessories->Terminal (I think)" and then in that window type the command "sudo modprobe -r modulename" (modprobe is normally for loading modules, the -r tells it to unload a module), youll need to enter your password to get it to work :)

Have you found the name of the driver/module yet?

---

### Post by Rovdjur on 2007-07-28
> **MrHippocampus said:**
> All you have to do is open a terminal "Accessories->Terminal (I think)" and then in that window type the command "sudo modprobe -r modulename" (modprobe is normally for loading modules, the -r tells it to unload a module), youll need to enter your password to get it to work :)

Have you found the name of the driver/module yet?

Well when I type that I get this:

```
jonas@tux:~$ sudo modprobe -r modulename
Password:
FATAL: Module modulename not found.
jonas@tux:~$

```

Am I supposed to substitute "modulename" for the actual name of something? Sorry, I'm just really confused.

---

### Post by MrHippocampus on 2007-07-28
Sorry for not being more clear.

modulename should be replaced by the name of the module which controls your wireless card. What is the name of the wireless card you want to stop? from that we can figure out the driver and from that the module name :)

---

### Post by Rovdjur on 2007-07-28
> **MrHippocampus said:**
> Sorry for not being more clear.

modulename should be replaced by the name of the module which controls your wireless card. What is the name of the wireless card you want to stop? from that we can figure out the driver and from that the module name :)

Lol, I am so bad at linux that I do not even deserve to be running it on my machine.

How do I find out the name of the module that controls my wireless card? I took a random guess and did "iwconfig" then tried probing "ath0" but to no avail.

Haha, I suck.

---

### Post by MrHippocampus on 2007-07-28
heh heh, its not your fault that the steps needed to disable a wireless card involve using the command line, it really shouldnt.

anyway, try this one:

```

sudo modprobe -r ath_pci

```

---

### Post by Rovdjur on 2007-07-28
When I did "modprobe -r ath_pci" it said permission denied, so I sudo'd it, and then I got a blank line returned:

```
jonas@tux:~$ modprobe -r ath_pci
FATAL: Error removing ath_pci (/lib/modules/2.6.20-16-generic/net/ath_pci.ko): Operation not permitted
jonas@tux:~$ sudo modprobe -r ath_pci
jonas@tux:~$
```

From what you've said before it seems like this is supposed to happen!

So what now?

---

### Post by MrHippocampus on 2007-07-28
Strange I know, but the blank line is good :). Is the wireless card still there? (try an iwconfig or something)

---

### Post by Rovdjur on 2007-07-28
> **MrHippocampus said:**
> Strange I know, but the blank line is good :). Is the wireless card still there? (try an iwconfig or something)

Haha, nothing shows!

```
jonas@tux:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

jonas@tux:~$

```

Seems like it worked to me. Is that all there is too it, or do I now have to add a line or something?

---

### Post by MrHippocampus on 2007-07-28
Its strange to see that output you posted, so many people hate seeing that output from iwconfig because it means there wireless isnt working, but were happy about it :D.

Anyway, we now know that ath_pci is the module used by your wireless card and that unloading the module stops the wireless card working. So all that is left is making sure that this module is never loaded again.

All you should have to do is open the /etc/modprobe.d/blacklist file

```

sudo gedit /etc/modprobe.d/blacklist

```

and add the line:
```

blacklist ath_pci
```

Next time you restart you system the module wont be loaded automatically when the wirless card is detected and therefore the wireless card wont be working :)

---

### Post by Rovdjur on 2007-07-28
Yes!!! Thank you so much :)

iwconfig shows nothing when the pcmcia card is not in, but when I put it in it then shows the card, so it seems like the internal is now off and the pcmcia external works great!

Thank you for your help :)

I am forever in your debt.

---

### Post by MrHippocampus on 2007-07-28
heh heh heh, good to see its all working :)

Can you also please change your thread title to have [SOLVED]  at the front, just so other people know :)
(If you dont already know how, edit your first post with advanced edit -> edit title -> rename)

---

