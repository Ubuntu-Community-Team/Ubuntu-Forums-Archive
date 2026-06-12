---
title: "Bizzare Behavior on Booting Breezy..."
date: 2006-05-08
forum: Absolute Beginner Talk
---

### Post by Omicron Machine on 2006-05-08
I was hoping all those B's would attract your attention. ;)  heh. 

Anyways, so after some issues, I got it loaded. There were some issues: I had to install it a second time because it wouldn't recognise my login and password, which I was absolutly sure were right. I use this password/username combination for tons of stuff. But I couldn't log in at all. Not knowing what else to do, I reintall it (which seems dumb in retospect) and I have some problems partitioning and with hanging, but I overcame those myself. Got it loaded. Got to the part where it tells me to remove the CD and press any key to reboot. So out comes the CD and I press the space bar (because, you see, I'd some time ago taken a marker and written "any" on it).

It reboots alright and I see the Ubuntu logo with the little tan-coloured progress bar. That does its thing. Then it shows that last blue screen with a grey box and red progress bar. That hangs or just gives a huge, unmanageable error message. I try a few times to get this to work. Finally, I get this message on two consecutive attempts:

> 
There was a problem with the selected software

One or more packages failed to install. This may be due to bugs in the packages or you may be out of disk space or experiencing some other problem. 

Simply trying to install those packages (or a slightly different set of packages) again may work around the problem, or at least move the installation process along a little further. If you want, if you want, you can go back to the package selection step, and try again.

If you decide not to try again, bear in mind that some packages on your system will be in a broken state untill you manually resolve the problem.


The two times I got this message, I tried to do what it said. I wasn't able to. I couldn't figure out how to get to any package selection step.

Now when I try to turn the system on, I can't even get back to the blue screen with the red progress bar. I can't quite remember whether or not I see the tan progress bar with the Ubuntu logo, but I do get the following:

> 
Ubuntu 5.10 "Breezy Badger" Antithesis tty1

Antithesis login:


Antithesis is the name I gave to the computer, obviously. I'll be the only one using it, and it's not actually on a network, so I just chose a word I liked. Since all the other computers in the house run Windows, and this one is going to eventually have Linux, in comparison to the others....well, Antithesis seemed both a logical name and a cool word, know what I mean? 

Anyways, this bit appears just as text. I'm not sure what this is, but since it seems similar in appeance and function to the Windows "cmd" bit, I assume this is the Linux commandline. I can log in just fine. I just dont know what to do once I'm in to get this computer running.

Help?

---

### Post by user1397 on 2006-05-08
So when you login it's still in black-and-white, command-line form? If it is try 
```
sudo apt-get update
``` 
and then 
```
sudo apt-get install ubuntu-desktop
```

---

### Post by catlett on 2006-05-08
It seems you have the server install of Ubuntu. First off try ```
startx
``` This will launch the gnome desktop if it is installed. But if it doesn't because you only have a server install try ```
sudo apt-get install ubuntu-desktop
```
Try those and hopefully one works and things are easy. Post if not.


edit: erik your too quick for me

---

### Post by user1397 on 2006-05-08
[quote=catlett]edit: erik your too quick for me[/quote] well...what can I say? :cool:
Your advice on "startx" is very necessary, however, and so my post was not perfect. :(

---

### Post by Omicron Machine on 2006-05-08
<a very newbie question>
Will the install bits require the computer to be connected to the internet?
</a very newbie question>

---

### Post by catlett on 2006-05-08
Yes. Sorry to not be more informative. The apt-get is a package management system that connects to online repositories where the various packages that are compatable with Ubuntu are kept. So when you  sudo apt-get install ubuntu-desktop, you're telling your system to use apt to go online to the repositories and get the package ubuntu-desktop and install it on your system.
If this doesn't work there is a bigger error in your install. But first run the command and post what happens.

---

### Post by Omicron Machine on 2006-05-08
The computer I'm trying to set up isn't connected to the internet. Can I get the files on one computer and burn them to a CD to put them on the Linux-computer-to-be?

---

### Post by user1397 on 2006-05-08
[quote=Omicron Machine]The computer I'm trying to set up isn't connected to the internet. Can I get the files on one computer and burn them to a CD to put them on the Linux-computer-to-be?[/quote]
I don't know about that...but can you at least temporarily connect to the internet? (broadband would be painless, dialup would be painful...)

---

### Post by Omicron Machine on 2006-05-08
No, I can't, for a couple reasons. I'm updating a kind old computer and it can't yet connect to the internet. Second, I'm not the person at my house who decides. My parents are. (The whole arrangment is a bit silly, really: I know about computers and they don't but they get to decide what I'm allowed to do, despite the fact before they can make their descision, I have to try to explain what's going on :confused: )

---

### Post by catlett on 2006-05-08
Ubuntu is very internet orientated. I've seen alot of posts where people ask that same question and don't seem to get a solid answer. I never looked into it because I've always had a connection when using Ubuntu.
I'll try and check for you in the wiki or other posts.
In the meantime, what means of install are you using? Is it a cd  someone downloaded off the Ubuntu internet site? Is it one of the free Ubuntu cds from [Ship IT]("https://shipit.ubuntu.com/")?  I'm Just trying to get a feel of what your cd has on it for packages.
 If everything is on it for a full install then there is something else wrong. Your cd might be a server install only or if it is a type of cd that finishes the install over the internet.
Again no internet and Ubuntu is tough because the package management system and the software update functions are all internet based.I won't say any more because I am not qualified to really answer this question. If I find out something solid about Ubuntu and packages without the internet I'll post here.

---

### Post by Omicron Machine on 2006-05-08
I had it almost running before, and the CD should work. This is the file I downloaded for it: ubuntu-5.10-install-i386.iso

---

### Post by catlett on 2006-05-08
Everything you need to get a full install will be in that iso.

---

