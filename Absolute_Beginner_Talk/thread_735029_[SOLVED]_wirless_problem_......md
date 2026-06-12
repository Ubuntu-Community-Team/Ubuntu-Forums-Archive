---
title: "[SOLVED] wirless problem ....."
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by trigsenior on 2008-03-25
hello,

I Hope this question has not been asked somwhere on the forum but im not sure what to search for.

I installed ubuntu a couple days ago and i could connect to the internet via wirless unsercured network but arfter about an hour the connection dies and i have to reboot. It can t even pick up the connection arfter it dies. I tried the network connection and the wirless option is not their any more. This is probaly my fault but could any one give me any tips 
many, many thanxs  :)

---

### Post by LowSky on 2008-03-25
What kind of wirless card do you have?

what version of Ubuntu are you using?

---

### Post by northern lights on 2008-03-25
Could you please post the output of ```
lspci -v | grep -network
```

---

### Post by trigsenior on 2008-03-25
hello thanxs for your help,

I tryed the code in terminal and i got nothing =( ,
 Im using ubuntu 7.10 gusty  .
How can i find out my wirless card ?

---

### Post by northern lights on 2008-03-25
Should ```
lspci | grep -network
```
return nothing, simply post the output of ```
lspci
```

---

### Post by leroyc on 2008-03-25
I have already posted this reply in several threads, but here it goes again:

The Ubuntu default Network Manager is pretty unstable when dealing with several types of encryption for wireless keys.

It is also VERY unfriendly and has NO options.

That is why I recommend the wicd application. It totally ownz, has an option to select key type, to enter the key, to set manual configuration for ip/gateway/dns... everything needed.

I have explained how to install and configure it completely here:
[URL="http://top-web-solutions.com/ubuntu-wireless-application/"]
Ubuntu Wireless Application[/URL]

---

### Post by which_chick on 2008-03-25
LeroyC:  When I edited my /etc/network/interfaces file so that it only contained the loopback stuff, as per the instructions that you wrote, the internet disappeared.

After that part, the instructions suggested that I ",,, click Reload. After the packages are updated, select wicd and right click on it - Install. Then click Apply and you are ready."  I did not have any luck getting the packages to update or getting wicd without any internet on my computer.

I restored my /etc/network/interfaces file to its previously-working state of affairs and I tried again.  I've only had Ubuntu installed on my machine since 3-16-08 and there is a lot I don't know, so if something doesn't work like I think it should, I try again before complaining.

So, I gave it another whirl.  I edited /etc/network/interfaces so that it just had the loopback stuff in it.  I saved the file.  The internet disappeared.  Again.

Maybe this would work better if you had folks go and get the file FIRST but on the synaptic doo-dad, check the box for "Download files only" so that it would cache them for local install later.

Then, folks can get the files FIRST.  After they get the files, then they can go fix /etc/network/interfaces and *then* return to synaptic and have it install.  That might work better.  I'm going to give it a try.

Update:  Yes, that worked perfectly.

---

### Post by trigsenior on 2008-03-26
thanxs so much ,

Your tutorial you linked was very help full , i completed it and it work great . It seems a lot better than the default ubuntu 7.10 one . 

thanxs for everyone who helped me !   :)


:KS

---

