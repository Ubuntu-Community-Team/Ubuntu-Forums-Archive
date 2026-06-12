---
title: "Trying to get started on Ubuntustudio"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by campero on 2007-10-24
I'm completely new in the Linux world and to Ubuntu...I just heard Ubuntustudio is a really good option for videos, etc...so this is my very first time touching Linux/Ubuntu.
So, I donwloaded the image file from ubuntustudio.org and tried to burn the image but the file size is 800MB and the CD capacity is 700MB...am I missing something here? Is that OK?

Any help will be highly appreciated.

Thanks

---

### Post by ofb on 2007-10-24
Not OK - sorry. That's a DVD image. It won't fit on CD.

If you can't burn DVD and you want to try that sort of distro, then maybe check out pure:dyne? (I haven't yet - on my todo list.)
[http://en.wikipedia.org/wiki/Pure:dyne](http://en.wikipedia.org/wiki/Pure:dyne)

You could also install Ubuntu and then add whatever applications you like. At any rate you can burn the Ubuntu LiveCD and do a test drive to get a feel for it & Linux while you research distros targeted at multimedia creators.

---

### Post by nynoah on 2007-10-24
just  do what I did.  Download Ubuntu, go the synaptic and download the Ubuntu studio desktop.  It does the same thing as burning the ubuntu studio DVD install.

---

### Post by ofb on 2007-10-24
Yeah, what he said. Much better idea. Skip my stuff.

---

### Post by campero on 2007-10-25
Thanks guys, I apprecciate it

---

### Post by Drunky on 2007-10-25
From a fresh install of Ubuntu 7.10 Gusty you can upgrade to Ubuntu Studio 7.10.

```
sudo apt-get update && sudo apt-get install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-rt
```

From this[ Ubuntu Help Wiki.]("https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromGutsy?highlight=%28studio%29")

I did this last night and it worked wonderfully.

---

### Post by campero on 2007-10-25
Thanks for the advice Drunky, like I said earlier these are my very first attempts with Linux/Ubuntu so I have no idea about anything.
I just downloaded the CD for Ubuntu but I don't even know what to do with it. Do I just click on it and it will take care of itself? Do I have to burn it on a cd and run it?
After reading the Wiki for Ubuntustudio seems like I won't need all the applications it comes with, so I think it will work just fine installing Ubuntu and then downloading the specific application I'm looking for.
I have Winblows XP on my computer, can I share the same machine for Ubuntu and Winblows or does it have to be Ubuntu only?
At the end of your post you wrote a code, What is that code for? and how do I use it?
I know most of my questions might have been answered many times before and I could problaly find the answers my self with a little research. 
Again, thanks for putting up with my Ubuntu-ignorance and thanks for all the inputs.

---

### Post by jaybombalous on 2007-10-25
```
sudo apt-get update && sudo apt-get install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-rt
```

you type this in a terminal window, then it will automatically do the rest for you.

As for windows and ubuntu, yes u can use the same machine and same HD. But u should take the time to learn how to do that properly or u risk ruining your windows partition.

---

### Post by campero on 2007-10-25
Thanks jaybombalous, Yes...that's what I want...I want to learn it first and get used to it before switching...so what would be the best way to do that?

---

### Post by indytim on 2007-10-25
One of many good sources for getting started in the Ubuntu-Kubuntu world:

[http://www.psychocats.net/ubuntu/]("http://www.psychocats.net/ubuntu/")

IndyTim

---

### Post by bartt on 2007-10-26
campero-
I am in the same boat as you just a bit farther downstream..
Yes, You need to burn the iso image that you downloaded to a CD. Nero works great for this in XP if you have it. There are other iso burners out there, so you might have to look around a bit. In Nero look for the "burn image" option, that should let you point it at the iso file. Once that is done you can boot from the CD and bring up Ubuntu. 
HTH..

---

