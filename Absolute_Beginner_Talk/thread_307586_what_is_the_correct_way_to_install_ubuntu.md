---
title: "what is the correct way to install ubuntu"
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by scutty on 2006-11-26
I think I have screwed up my fresh (and first) install of ubuntu, I am using 6.10. Is there a setup I need to do after I install the OS? Of course i want functionality, stability and security--then all the eye candy and kewl things. I am an ultra noob when it comes to this but I am trying to wrap my head around so any help would be appriciated.
Thanks
scutty

---

### Post by bruenig on 2006-11-26
Generally if you are using ubuntu as a desktop OS, you need to enable a bunch of multimedia stuff and other things. I would suggest looking at these two things:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by vtel57 on 2006-11-26
Here's another great source for [Ubuntu Links]("http://forums.scotsnewsletter.com/index.php?showtopic=17087").

---

### Post by turbojugend_gr on 2006-11-26
I believe that all new users need to spend some type reading these guides. They are **VERY** useful, and you don't need to read all through them, just the parts of 'em you wish to know more about. I suggest bookmarking them.

1. Official [Ubuntu Desktop Guide]("https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/index.html").
2. [Ubuntuguide.org's guide]("http://www.ubuntuguide.org")
3. [Ubuntu Document Storage Facility]("http://doc.gwos.org/index.php/Main_Page")
4. Some great how-to's/guides from asyiu, on [psychocats]("http://www.psychocats.net/ubuntu/index.php")

As I tend to say, they will answer most of your question, and then create some new ad then answer them too. It is the perfect way of learning your new Operating System and all it's wonderful capabilities. I hope you will take my advice and spent some time reading them (what you feel like learning today, kinda thing).

Best Regards, TJ.

---

### Post by 56phil on 2006-11-26
Welcome to Ubuntu, Scutty. :) I stubbed my toe a few times and recovered just to do it again. I'm sure you'll do fine. 

Be [SIZE="2"]**careful**[/SIZE] out there.

---

### Post by Bartender on 2006-11-26
What leads you to believe you screwed up your install?  What are the symptoms?

---

### Post by scutty on 2006-11-27
First, Thanks for the words of encouragement...I fully intend to get ubuntu working properly.
To answer why I believe I have fouled the install is based on the error messages I get after trying to install (for example) the clam antivirus or these errors when I run Synaptic:

W: GPG error: [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 18B52FE3521A9C7C
W: GPG error: [http://media.blutkind.org](http://media.blutkind.org) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 31A5F97FED8A569E

I realise I am probably overreacting as the OS is not crashing, but this is my new system. I bought a harddrive just for ubuntu so I can dual boot and really give ubuntu a thorough workout without interrupting the rest of my family's computing. I'm going to start reading now.
Thanks
scutty

---

### Post by bruenig on 2006-11-28
> **scutty said:**
> First, Thanks for the words of encouragement...I fully intend to get ubuntu working properly.
To answer why I believe I have fouled the install is based on the error messages I get after trying to install (for example) the clam antivirus or these errors when I run Synaptic:

W: GPG error: [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 18B52FE3521A9C7C
W: GPG error: [http://media.blutkind.org](http://media.blutkind.org) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 31A5F97FED8A569E

I realise I am probably overreacting as the OS is not crashing, but this is my new system. I bought a harddrive just for ubuntu so I can dual boot and really give ubuntu a thorough workout without interrupting the rest of my family's computing. I'm going to start reading now.
Thanks
scutty
Not sure on the second error but as for the automatix error, you just need to open a terminal, applications>accessories>terminal and copy and paste the following in order to fix it.
```
 wget http://www.getautomatix.com/apt/key.gpg.asc
 gpg --import key.gpg.asc
 gpg --export --armor 521A9C7C | sudo apt-key add -
```

---

### Post by PriceChild on 2006-11-28
Why are you using automatix?

If you want to learn more I strongly suggest you do everything yourself.

You will do it better, cleaner and safer than automatix.

---

### Post by xpod on 2006-11-28
> Why are you using automatix?

If you want to learn more I strongly suggest you do everything yourself.

You will do it better, cleaner and safer than automatix.


Plenty time for "learning" i reckon.
I`d recommend any newcommer to use automatix to get themselves up and running
at first.
I`ve seen people give up simply because of the extra "learning" involved during that initial period.

All the time in the world to learn how to do things the many other ways

EDIT...just mho of course

---

### Post by AndyCooll on 2006-11-28
Those "GPG error" messages do not mean a screwed up system in any way whatsoever. They refer to "security password keys" you need to obtain before you are allowed to access those repositories mentioned (getautomatix and blutkind). The message is basically saying you can't enter until you give me the correct password.

I agree with xpod's comments too, plenty of time for learning. I used to use Automatix when I first started out with Ubuntu. I now prefer to install everything myself, but of course I'm much more confident with my Linux system.

:cool:

---

### Post by Neobuntu on 2006-11-28
Short answer. Use Windows on an old computer and install Dapper Drake 6.06.1 on your newer one (I prefer and suggest Kubuntu but whatever.)

If you have one >256MB RAM computer, use qtparted or gparted from the live CD and simply resize the WIndows partition and make it half (50/50). The live installer will take care of the rest.

Then, yes. Go to [http://www.getautomatix.com](http://www.getautomatix.com) and simply tripple click, cut and paste in (to Terminal) the lines to install it (on your menu) for Dapper. This way extras are check box easy.

That's my "correct way". :)

---

