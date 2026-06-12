---
title: "ubuntu (6.0.6) install ... failed"
date: 2006-06-11
forum: Absolute Beginner Talk
---

### Post by Imre Mehesz on 2006-06-11
hello everyone,

it looks like i am not the only one with this, however I couldn't find solution yet...

i really want to use ubuntu (and get rid of my ol MS finally!) and the LIVE CD is working fine, but when i try to install ub from the CD it goes 15% and stops saying:
**failed to create a file system**

and i can click OK, it finishes the installation (like nothing happened) but when I try to reboot... the GRUB fails with **errorcode 15** ...

is it my hardware? (can I try to install an older version of ubuntu?)

thanks
iM

---

### Post by Warlord88 on 2006-06-11
I have had problems with the live cd. The screen used to go blank just before the installation menu. So I used the alternate cd. It does not have a graphical installer but a good text installer. I installed successfully with that cd.

But before that, you can try testing the cd which you have for defects. I think there is an option during installation to test the cd image.

---

### Post by chainzz on 2006-06-11
Please post the specs of your system.

---

### Post by Imre Mehesz on 2006-06-11
This is a compaq armada M700 (laptop) 650Mhz PIII 256MB ... and i have a pci linksys WPC54G wireless ... the live CD was OK... i'm downloading an older one (5.10) right now, and we'll see if that works ... (i'd like 6.06 though ;) )

thanks
iM

---

### Post by patrick295767 on 2006-06-11
I had some problesm with installing with server & desktop Iso cds 
(fresh cd installation) 
  
now it's solved:   
The alternate cd install is really great !! 
I would advice you to try this one.
Then the dapper sources.list is here : [http://www.ubuntuforums.org/showthread.php?t=185758&highlight=sources.list](http://www.ubuntuforums.org/showthread.php?t=185758&highlight=sources.list)

---

### Post by slb33 on 2006-06-11
Seems like many people have had problems with the installation from the live cd.
I had it crash on me the first time I tried it but the second time it worked fine.
Not sure what the problem is but it sure looks like there are some bugs in the live cd installer.
For now it looks like it's better to use the alternate install disk. Sure it's in text mode but it is better to have an install that nobodys having problems with and it's not any harder to install it in text mode.
Just make sure you read what it's asking you before clicking ok.

---

### Post by Imre Mehesz on 2006-06-11
hello,

i'm sorry but I'm totally newbie to this ubuntu thing... where can I find this alternate CD??? i'd love to give it a try :D

i am sorry, I found it already... i'll give it a try.. thanks again

thanks

---

### Post by Imre Mehesz on 2006-06-12
hello ya'll,

so yesterday I installed 5.10 ... it did recognize my card, but I still couldn't go online. today i'm installing this 6.06 alternate version, but at the beginning it was saying that i do not have a network card :(

is there any way to make ubu to recognize my card later? (like new hardware or something.. (in redhat there was something called kudzu if i remember correctly...)

thanks anyway,
iM

---

### Post by ascherjim on 2006-06-12
[QUOTE=slb33]Seems like many people have had problems with the installation from the live cd.
I had it crash on me the first time I tried it but the second time it worked fine.
Not sure what the problem is but it sure looks like there are some bugs in the live cd installer.
For now it looks like it's better to use the alternate install disk. Sure it's in text mode but it is better to have an install that nobodys having problems with and it's not any harder to install it in text mode.
Just make sure you read what it's asking you before clicking ok.[/QUOTE]
In attempting to switch from Fedora, I've managed to successflly load Ubuntu with the alternate, direct-install disk.  However, after having done so, I can't boot it.  I can ultimately manage to get some favorable text resonse by inserting "acpi=off" in the optional boot instruction, but that only takes me to a double "$" command line and I don't know what command to enter from there.  Anyone encounter this same situation?  For now, I'm going back to Fedora (FC1).

---

### Post by patrick295767 on 2006-06-15
[QUOTE=slb33]Seems like many people have had problems with the installation from the live cd.
I had it crash on me the first time I tried it but the second time it worked fine.
Not sure what the problem is but it sure looks like there are some bugs in the live cd installer.
For now it looks like it's better to use the alternate install disk. Sure it's in text mode but it is better to have an install that nobodys having problems with and it's not any harder to install it in text mode.
Just make sure you read what it's asking you before clicking ok.[/QUOTE]
  
I have impression that text mode installation is the best alternative
(alternate cd iso install)
you are sure that'll be working
  
Man, I had to install a slackware distro, the last version, what a difference with the ubuntu text instalation cd !! 
Ubuntu text install is really good
  
the slack txt install looks still same as third slack 3.1 version !!
No changes ...

Greetz

---

### Post by nashife on 2006-06-15
Someone just asked, but no one replied above, but where is the "alternate" dapper install cd?

Edit: I just found a link here, so other people can find it too: [http://mirror.cs.umn.edu/ubuntu-releases/6.06/ubuntu-6.06-alternate-i386.iso](http://mirror.cs.umn.edu/ubuntu-releases/6.06/ubuntu-6.06-alternate-i386.iso)

---

### Post by xenblend on 2006-06-16
Unfortunately the one thing about linux is that if you want a perfect install, your not gonna get it.  

Boot to a console and run 'grub-install' on your boot partition.  Or dl and burn the alternate cd, that worked well for me after teh normal cd didnt work.

---

