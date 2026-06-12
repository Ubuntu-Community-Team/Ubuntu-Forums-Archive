---
title: "wireless card and secured network identification"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by newdummy on 2007-08-10
hello everybody

let me tell you about my linux experiences. two moths ago i decided to give linux a try as i totally hated my windows vista. my first distribution was linux mint. this is a great choice for a complete beginner. however, i couldn't figure out how to get my wireless card working. therefore, i tried pclinuxos. this is an almost perfect distribution in my limited opinion. it detected the wireless card of my dell inspiron 6000 without any problems during the installation process. it even asked for the security key of the network that i could choose! unfortunately, it uses the kde-desktop which is a complete pain in the neck. this is why i decided to give another distribution a try. this is where ubuntu enters my story. unfortunately, it doesn't come with that completely awesome installation feature of pclinuxos that performs the wireless setup in a matter of a few seconds or minutes (depending on how fast you can hit your security key in). this brings me to my question: is there a software, a package for ubuntu that i can download and that'll do the job for me? how difficult is it to set everything up "by brute force"? it seems to me that this is very difficult for a beginner like me ... :(

i would be very thankful for an answer and i'm looking forward to hearing from you.

have fun,
cheers,

newdummy.

---

### Post by wirelessmonkey on 2007-08-11
Well, depending on which type of security, i.e. wep, wpa, you can probably just apt-get network-manager

---

### Post by jimrz on 2007-08-11
please post which wifi card (make/model/chipset) you are using, so that others with the same may be able to offer advice based on how they got it working

---

### Post by campgirl on 2007-08-11
Hello, I'm really new at this, so please bare with me if I'm not asking in the right way.

I also have an issue with my wireless card. It's a D-link AirPlus G, wifi and I believe I'm using wpa encryption. Someone has set it up for me so that it is now recognized (I honestly couldn't remember how he did though, and I'll reply when I find out), but I am still having some issues.

 When I first turn my computer up and it's running, a place for my wireless network key comes up so that I can use the internet. I have a long encryption key with numbers and letters which I have saved in a text document, so that all I have to do is copy and paste it into the text field and click okay. Then, a thing saying "Keyring manager" comes up and asked for a password for that. Currently, I've been hitting deny and my internet works with out filing it out. It's a good workaround for now, but I think I should be doing something with the keyring manager thing, but I don't want to mess things up. Initially I had used it, but my internet didn't work in the end and I ended up reinstalling Ubuntu.

Does anyone have any information, or websites I could check out for help?

Thanks

---

### Post by ugm6hr on 2007-08-11
@newdummy:
Have you already installed Ubuntu? If not, what Linux are you currently using?

The reason I ask, is that you could fairly easily find out what the PCLinuxOS wifi solution was, and then ask for directions on how to get it working in Ubuntu.

So - if you still have PCLinuxOS - do the following in a Terminal window (after configuring wifi):
```
lshw -C network
```

Then tell us the results.

Other info that will be useful (particularly if you no longer have PCLinuxOS):
```
lspci -nn | grep Network
lspci -nn | grep Ethernet
```

@campgirl:
Out of courtesy for newdummy, perhaps best if you start a new thread, since your issue is not really related to the original problem.  Just click on "Forum Tools" to start a new thread from Absolute Beginners.

---

### Post by laidback on 2007-08-11
I have made a couple of observations re wireless cards here:-

[http://ubuntuforums.org/search.php?searchid=25222132](http://ubuntuforums.org/search.php?searchid=25222132)

might be of interest.

I recently took my laptop to a friends house where I connected OK once I had chosen the correct encryption system (ascii or hex). I used the DHCP system.

I just use the Network Administration tool, System>Network then password. Feisty Fawn seems to configure things correctly by default.

---

### Post by campgirl on 2007-08-11
> **ugm6hr said:**
> 
@campgirl:
Out of courtesy for newdummy, perhaps best if you start a new thread, since your issue is not really related to the original problem.  Just click on "Forum Tools" to start a new thread from Absolute Beginners.

Oh, okay. I'm sorry about that newdummy. (Still really new, thanks for the advice ugm6hr :))

---

### Post by bwtranch on 2007-08-11
Hi guys,

I'm not trying to be obtuse and I probably should know this. But isn't keyring manager the place to keep your GNG keys? Or does it have another use :confused: Thanks!

---

