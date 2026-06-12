---
title: "Just installed XUbuntu...what should I do first?"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by ArtF10 on 2007-08-21
Hello all:

I have just installed XUbuntu and would like to know what I should do next and in what order.  Here's what I can think of as being urgent:

1.  Download Adobe Flash, Java Runtime 6.0 and Opera Web browser

2.  Update my graphics card drivers using this guide (Multiverse and Universe seem to be enabled by default)
[http://www.albertomilone.com/latest_nvidia_udsf_feisty.html#METHOD_1](http://www.albertomilone.com/latest_nvidia_udsf_feisty.html#METHOD_1)

3.  Update the operating system....here I would need help..from where and how would I do this?

4.  Get all the keys on my keyboard to work since the ALT, internet short-cut and email short-cut keys do not work right now.  Can someone tell me why this is happening?

5.  I know this is a light distro but, are there some GNOME/KDE packages that I could remove to lighten it further?  All I need is AbiWord, calc, web, email(thunderbird, YES!!!!), instant messenger and a photo editor.  Everything under Applications would be needed, but are there any startup processes(GNOME or KDE) that I could do without?  Does this guide hold true for an XUbuntu install as well or would it not work for me?
LINK to GUIDE:  [http://www.psychocats.net/ubuntu/purexfcedapper](http://www.psychocats.net/ubuntu/purexfcedapper)

Thanks,
ArtF10

P.S. I'll get to printing later.

---

### Post by Gremlinzzz on 2007-08-21
I would start with the guide just copy and paste
[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

---

### Post by chrome307 on 2007-08-21
This is a general 'what to do next' for Feisty Fawn, but may be of some relevance to you with applications:

```


http://linuxondesktop.blogspot.com/2007/05/13-must-do-things-on-new-ubuntu-704.html


```

Goodluck :)

---

### Post by ArtF10 on 2007-08-21
1.  Ok, I have one specific question.  After installing the graphics drivers, I get a message saying something like that inorder for this system to run correctly, a *CAN'T REMEMBER NAME, but I think it was **restricted*** driver has been installed.  It seemed like the message was saying that the driver was not supported or something?

 Can I still proceed with updating the operating system or will I not be able to download updates as a result of this?

2.  Do I need to mount any partitions?  I selected Manual partitions and created / and /home ext3 partitions separate from a SWAP partition.  Would I have to mount some or all of these?

ArtF10

---

### Post by tommie74 on 2007-08-21
First learn to use google.

go to [www.google.com](www.google.com)

type: 'restricted driver ubuntu' in the search

see if there is any usable info


Second, see if you can access the /home partition in some way, if you don't have a clue about how to do this look for a introduction into ubuntu. I suppose you could use google to find a introduction into ubuntu.

---

### Post by Teamgeist on 2007-08-21
> **ArtF10 said:**
> 1.  Ok, I have one specific question.  After installing the graphics drivers, I get a message saying something like that inorder for this system to run correctly, a *CAN'T REMEMBER NAME, but I think it was **restricted*** driver has been installed.  It seemed like the message was saying that the driver was not supported or something?

 Can I still proceed with updating the operating system or will I not be able to download updates as a result of this?

2.  Do I need to mount any partitions?  I selected Manual partitions and created / and /home ext3 partitions separate from a SWAP partition.  Would I have to mount some or all of these?

ArtF10

1. You probably installed the NVIDIA or ATI proprietary driver for your graphics card.
Those drivers are closed source software, meaning that the Ubuntu team cannot fix them if they are broken or anything only NVIDIA and ATI can do that. So that message popped up and told you that you just installed a "restricted" driver and Ubuntu cannot do anything if the driver does not work properly.

Yes, you can update your system.

2. Your partiotions should be mounted. Have a look at Places--> Computer and see if everything is at its place.
If you're not sure that everything is alright post the content of /etc/fstab here and people will be able to help you.

---

### Post by misfitpierce on 2007-08-21
party and celebrate?

---

### Post by Kilz on 2007-08-21
Get a beer and use your Windows CD's as a coaster?

---

### Post by ArtF10 on 2007-08-21
> **Teamgeist said:**
> 1. You probably installed the NVIDIA or ATI proprietary driver for your graphics card.
Those drivers are closed source software, meaning that the Ubuntu team cannot fix them if they are broken or anything only NVIDIA and ATI can do that. So that message popped up and told you that you just installed a "restricted" driver and Ubuntu cannot do anything if the driver does not work properly.

Yes, you can update your system.

2. Your partiotions should be mounted. Have a look at Places--> Computer and see if everything is at its place.
If you're not sure that everything is alright post the content of /etc/fstab here and people will be able to help you.

Thanks you very much for help.  Well, I've got most of my questions answered. 1 was done with 2 and 3 being answered by you.  

As for 5, I read through the wiki article and can't find anything that I could remove right now.  In time I might consider some processes and will post then, so this is done for now.

That leaves me with only 4. the Wikipedia article discusses side mouse buttons but I just wanted to know about the middle(scroll wheel) button option to drag and drop...i.e. press it and scroll down fast.  That option does not work for my mouse.  Neither does the ALT button when using Firefox or Opera OR in AbiWord/Gnumeric.  So if I could help regarding material avaiable on this pair of issues, I would greatly appreciate it.

---

