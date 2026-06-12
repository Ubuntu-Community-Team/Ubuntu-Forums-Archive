---
title: "Basic installation questions"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by John E on 2006-11-21
Does Ubuntu have any restrictions with regard to the swap partition??

I've spent 4 days trying to install Linux - alternating between Ubuntu & Fedora (neither of which will install & run successfully). Ubuntu will run from my CD, where (presumably) it doesn't need a swap partition. Fedora, on the other hand, doesn't insist on a swap partition at all. But when I try to install Ubuntu on my hard drive, it insists that I set up a swap partition.

The only space I've got free is in an extended (i.e. logical) partition - but Ubuntu won't accept this. Does the swap partition need to be a primary partition? If so, could I install Ubunto itself onto the logical partition?

Secondly, Ubuntu won't accept that I have a hi-res graphics card. It insists on offering only 640 x 480 resolution. This is a pain in the butt during installation - because the various screens are all 800 x 600, so I have to keep moving them in order to read the contents.

Oh - one other point.... it's **very **frustrating that Ubuntu doesn't seem to be able to create the partitions it needs during installation. At the moment, I'm having to create suitable partitions externally (either using Fedora or Partition Magic) and then select them in Ubuntu. Shouldn't Ubuntu be able to do this for itself??

---

### Post by Bachstelze on 2006-11-21
Get an Alternate CD :)

I really hope the idea of an installable Live CD will be dropped, it creates far more problems that it solves...

---

### Post by John E on 2006-11-21
I appreciate the quick response but it doesn't really answer my question. If I got a (non-live) install CD, would that allow me to:-

a) Install without needing a swap partitioon, or
b) Use my logical partition as the swap partition?

---

### Post by anaconda on 2006-11-21
Hmm. 
I dont have a swap partition in my main computer. and atleast in 6.06 you didn't have to make swap partition when installing from liveCD. It did complain that swap partition wasn't made, but it asked if I want to continue or go back to partition editor or not..

When I installed 6.10 to my laptop I had also problems with the installer, and I had to make the partitions before starting the installer. But I did make a swap -partition, so now I dont know if you actually HAVE TO make it. Hope not, because swap-files are more flexible. Any too rigid rules are stupid. If you for example have 2-4GB of RAM I cant understand why would you need swap.. and requiring that you have to make it is just stupid. 

You can use logical partitions as swap partition, or you can install ubuntu to a logical partition.

And the alternate CD definitely allows you to install without needing a swap-partition.

---

### Post by Bachstelze on 2006-11-21
1) Yes, though it's not advisable to do so unless you have 2 gigs of RAM.

2) Yes, and also install Ubuntu on the logical if you wish.

---

### Post by John E on 2006-11-21
Thanks guys.

> **anaconda said:**
> in 6.06 you didn't have to make swap partition when installing from liveCD. It did complain that swap partition wasn't made, but it asked if I want to continue
So it does. I'm sure I tried this yesterday and it didn't work. Mind you, I was having a lot of problems with Fedora at the time - especially so with GRUB which took me nearly half a day to remove from my system. So you can imagine that I was less than pleased to find Ubuntu merrily re-installing it for me :( 

One problem so far is that at no stage have I been asked to provide a password for 'root'. Therefore, at the moment, I'm unable to do some of the things I'll soon need to do (like editing xorg.conf). Is it possible to overcome this problem?

---

### Post by Jimmey on 2006-11-21
Regarding the swap partition, if there's already a swap partition on one of the drives in your computer, during the alternate CD's setup, you can select that partition, and under the "Use as" menu, select "Swap partition".

It's better to use "sudo" that it is to log into root...Blahblah, there's lots of explainations on this. To do command-line administrative tasks, use "sudo", or to run a graphical application as root (like a text editor), try "gksudo application". So for xorg.conf, try "gksudo gedit /etc/X11/xorg.conf".

Hope I helped :-)

---

### Post by CatKiller on 2006-11-21
> **John E said:**
> One problem so far is that at no stage have I been asked to provide a password for 'root'. Therefore, at the moment, I'm unable to do some of the things I'll soon need to do (like editing xorg.conf). Is it possible to overcome this problem?

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by John E on 2006-11-21
I just tried following the instructions for setting up a 'root' account with password access. However, when I tried to log in (using the name **root** and my chosen password) I received a red message saying 'The system administrator is not allowed to log in from this screen". What have I done wrong...?

---

### Post by Bachstelze on 2006-11-21
Logging in as root graphically is a *very* bad idea. It is *possible* but I'm not going to tell you how, you're not on Windows.

---

### Post by steve.horsley on 2006-11-21
> a) Install without needing a swap partitioon, or
Yes. The installer doesn't need a swap partition while installing, and I believe you can create a system without a swap partition, though I would recomment you have one. 
> 
b) Use my logical partition as the swap partition?
Yes - my swap partition is on a logical partition (hda8), and I think that's the default configuration that the installer likes to suggest.

---

### Post by John E on 2006-11-21
HymnToLife....

I hear what you're saying but nevertheless, I trust myself - and I know it's possible with other versions of Linux because I did this only yesterday, when I was trying out Fedora.

Don't take this the wrong way - but I'm not going back to learning obscure, command-line parameters that the rest of the world gave up on, 20 years ago. This is the 21st century and we've all moved away from the old fashioned 'terminal entry' style that dates back to the 1800's.

I'm sensible enough to back up my data before messing with it so I'm not in any danger of losing anything.

---

### Post by adam.tropics on 2006-11-21
> **John E said:**
> HymnToLife....

Don't take this the wrong way - but I'm not going back to learning obscure, command-line parameters that the rest of the world gave up on, 20 years ago. This is the 21st century and we've all moved away from the old fashioned 'terminal entry' style that dates back to the 1800's.
  

Don't take this the wrong way, but your loss. The command line is an insanely powerful tool, that if you take a little time to get used to can vastly improve your Linux experience...anyway...

---

### Post by John E on 2006-11-21
Adam - I don't doubt what you're saying but command-line interfacing is arcane and antiquated. The rest of the world has moved on and realised that there's nothing you can do with a command line that can't be done better by some other method.

And it's really this kind of thinking that stops Linux and Unix from gaining wider acceptance.

---

### Post by adam.tropics on 2006-11-21
> **John E said:**
> Adam - I don't doubt what you're saying but command-line interfacing is arcane and antiquated. The rest of the world has moved on and realised that there's nothing you can do with a command line that can't be done better by some other method.

And it's really this kind of thinking that stops Linux and Unix from gaining wider acceptance.


Yeah whatever. I am not gonna argue this, as it's been done too many times already. I would say that Ubuntu/Linux makes no claim that it is just like windows. But just in case you thought only Linux used such arcane technology, well, so do [Microsoft, so take your pick!]("http://www.microsoft.com/downloads/details.aspx?FamilyID=14f411a5-04e2-4f1d-806d-2019baec1b51&DisplayLang=en")

---

### Post by John E on 2006-11-21
The difference being that Microsoft only expects IT professionals and other expert users to use such tools (and even then, it doesn't enforce their usage - they're generally offered as an alternative).

And it isn't me who'll lose out anyway. If I can't do what I need to do with Ubuntu, then I'll just switch to a distro that's more flexible.

---

### Post by hyper_ch on 2006-11-21
for what tasks that an average computer uses needs do you need command line on ubuntu? And don't forget, your are much more skilled than the average computer user.. I see this here at my university all the time... most students have even problems getting a simple program like Lotus Notes to be installed and run correctly...

---

### Post by anaconda on 2006-11-21
> **John E said:**
> And it isn't me who'll lose out anyway. If I can't do what I need to do with Ubuntu, then I'll just switch to a distro that's more flexible.

You are right. Moving from different flavour of linux where I was used to being root when needed (not often) this sounds silly. 
It is only annoying, when someone says that I know the solution you seek, but wont tell you. Kind of reminds me of microsofts helpline. "I know the solution to your problem, but wont tell you unless you pay $10.."  

The end of this page tells what you have to do to enable root to login craphically:  
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by John E on 2006-11-21
Let me say for the record that Ubuntu is the best Linux distro I've seen so far, by a long margin. I know I've been sounding a bit over-critical but I'm only criticising its bad points. It has many good points...!:-D

---

### Post by Jimmey on 2006-11-21
Basically, Ubuntu's got a "Doing stuff as root is okay. Logging in as root, not so good." kind of setup.

It becomes difficult to actually log in as root. Ubuntu have provided the appropriate tools, however, that enable the users to perform adminstrative tasks.

Two of these being sudo and gksudo (which allow you to run applications with root priviledges).

sudo has a number of command line options. One you might want to consider is "-i". The command "sudo -i" basically gives you a root shell.

Logging in as root graphically doesn't seem like such a smart idea to me. If there's a specific graphical application you'd like to run, like has been mentioned, use gksudo.

---

