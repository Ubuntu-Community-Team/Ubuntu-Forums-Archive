---
title: "Real absolute beginner...help please."
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by CoreDefence on 2007-07-17
Hi, here's my story, hope I gan get some guidance.

I'm a mature individual whose only experience of computing is 10 years of MS Windows. Rightly or wrongly,I have always valued the way Windows did everything for me. When MS XP came out I actually bought a full price version, and upgraded successfully but the 20gb WD hard drive died in April this year (lots of clicking and scratching on boot, I've tried popping it in the freezer, dropping it etc. to no avail). 

So I buy a new WD 80GB drive, install and try to load my XP OS. Not allowed, won't register 'cos it's already been installed on another computer, gotta buy again. 

Sod that, thinks I and being aware by now of Linux, I decide to give it a go and hopefully divorce myself from MS forever. I sorted myself with an Ubuntu boot disk and thats where I realised immediately that I've bitten off considerably more than I can chew. On the system I have designated to Ubuntu I cannot get connected the internet on my wireless network suggesting the network card is not configured, I've had problems with the graphics card (my earlier post here) and the sound card is not working.

Fundamentally, I seem to be in irretrievable 'Windows mode', my mindset is Windows, and the prospect of writing in some kinda code for every command is completely daunting. It's an 'old dogs & new tricks' scenario. 

Are there tutorials I can study from the very very basics of Ubuntu?  Has anyone any suggestions as to my best course to get my head around this whole new discipline? 

I'd be grateful for any feedback. 
Thanks in advance,
Core

---

### Post by jvc26 on 2007-07-17
Hi there, basically it does have a learning curve, as most people (including myself) come from a windows background, where even touching CLI is a foreign and weird idea. Don't panic, things become easier very quickly, and you become so familiar that you may well find windows becoming the odd way of doing things. CLI isnt necessary for everything, just to make clear, as things such as add/remove and synaptic package manager offer GUI methods for installation. There is loads of information out there on the internet to look at. Things such as the psychocats ubuntu guide (see my sig) the forums, the community documentation and ubuntu guide (also in my sig) are all there to assist. The forums are one of the best things in ubuntu's support - I have never before seen so many users out on here to assist people in how to solve problems. After all, if you can't find something the odds are it will have been answered before on here.
Il

---

### Post by oilchangeguy on 2007-07-17
it's great that you want to use linux. but who told you you'll have to buy windows again? this is not true. if you followed the activation sequence correctly you were probably prompted to call microsoft. CALL them, you can reactivate windows.

---

### Post by bobbocanfly on 2007-07-17
The easiest way to learn ubuntu is just to mess about in it for a while. Doing basic stuff like checking your email and surfing the net, or if the wrong client/browser is installed removing that and installing a new one will help you grasp the real basics. Once you know how to install and remove software (sudo apt-get install <packageName>)(sudo apt-get remove <packageName>) you can start having real fun.

Another thing i did to learn linux was set up a lamp server. That taught me a lot about permissions and using the terminal. 

Have fun

---

### Post by takayuki on 2007-07-17
Core,

Welcome.  It's difficult at the beginning, as with anything new, but if you are persistent and patient you'll be glad you made the switch.

To get you going, I'd suggest just running a hard line from the router to your computer instead of tackling wireless.  It should "just work".  This at least will get you on your feet.

If you have an extra slot you can buy a sound card that should work with linux for cheap on ebay.  It may be worth the $8 to pop in a card that you know is going to work.

here's a post from the skype forums on sound cards:
"One way to fix all your sound card related problems is simply search ebay for those VERY cheap sound cards from Hong Kong.. Any card with __8738 Chip-set__ will fix all these problems out of the box..
you can buy these cards for less than $12 or £5.. just type in the search for "PCI 5.1 Sound Card" and you will list about 1000 of these.."

hope that helps a little.  these forums are a great resource.

---

### Post by wolfen69 on 2007-07-17
> **oilchangeguy said:**
> it's great that you want to use linux. but who told you you'll have to buy windows again? this is not true. if you followed the activation sequence correctly you were probably prompted to call microsoft. CALL them, you can reactivate windows.

this is true. if you called them and explained the situation, they would allow you to reinstall. ive done it many times. im not trying to push you away from linux. just a heads up.

---

### Post by dptxp on 2007-07-17
Ubuntu is neither hard to install nor tough to learn.
It also does not take much time to get used to it.

You may have to to do a bit of work in case of some hardware. If you get cheap and compatible
hardware, it is the easiest way.

The forums here should get you through.

---

### Post by Steven_B on 2007-07-17
> Are there tutorials I can study from the very very basics of Ubuntu? Has anyone any suggestions as to my best course to get my head around this whole new discipline?  You might want to start here: [https://help.ubuntu.com/]("https://help.ubuntu.com/")  As you get more comfortable with how things work in Ubuntu, you can take on some of hardware problems you're having.
> On the system I have designated to Ubuntu I cannot get connected the internet on my wireless network suggesting the network card is not configured, I've had problems with the graphics card (my earlier post here) and the sound card is not working.
Those are all pretty common problems, so there's probably several threads here about how to fix them.
It's great you realize Ubuntu is different, and want to learn.  All too often, people come here expecting to find a free Windows clone - and come away disappointed.  If you're patient and willing to try things, I think you'll find Ubuntu is a great OS.

---

### Post by davidjmayo on 2007-07-17
Hi fellow forum members,

Have you read the other post ? [http://ubuntuforums.org/showthread.php?t=502955](http://ubuntuforums.org/showthread.php?t=502955)

The initial problem here is a graphics card ( the wireless and sound are other issues that need to be sorted) and a simple way for a newcomer to fix this issue which is not where my experience lies.

Core: what happened when you did this (from your other post reply #2 or #3 as it may help others)
> sudo dpkg-reconfigure xserver-xorg


I dont know this graphics card. What would be the best way to get OP up and running?

1 install from safe graphics mode?
2 Alternate CD?
3 fix another way?

---

### Post by tsmiller on 2007-07-17
Just a note about what (k)ubuntu does. 

If losing windows completely is scary !!!  I am running a **complete unmodified version of windows xp** that runs in a window on my linux box -->   [http://www.virtualbox.org]("http://www.virtualbox.org")

I am running feisty.

I installed the windows xp from the restore disk that came with a windows machine that I had bought.

Anyway, I thought something like this would help the transition from windows to linux.

Tom

---

### Post by bruce2000 on 2007-07-17
Another alternative option you may want to consider is trying another version of Linux. You may find one that detects your hardware better than Ubuntu has. Certain distributions provide a Live CD enabling you to check out if your hardware works before you actually install it (in the same way Ubuntu does.)

---

### Post by CoreDefence on 2007-07-17
WOW!

Many thanks for the many positive and encouraging responses to my post.

To update, I called MS about my XP problem and that is now sorted, thanks go to OilChange and others.

Notwithstanding, I am even more determined to go into Linux and persevere with Ubuntu by following some if not all of the guidance offered here.

I think I can guarantee.....I'll be back.

Many, many thanks to all 

Core

---

### Post by crimesaucer on 2007-07-17
Now that you got your Windows back, and have become interested in Ubuntu, you should try a dual boot of your computer so you can use both your Windows Xp and Ubuntu Feisty. That way you can have an OS that you know how to use when you need to do something, and also your partition of ubuntu to learn on.


This is a good guide for a text install dual boot of Ubuntu, Xp, and a FAT32 file, using the Alternative ISO: [http://users.bigpond.net.au/hermanzone/p2.htm](http://users.bigpond.net.au/hermanzone/p2.htm)

....this is the home page of that site: [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)



This is also a good guide for a regular install: [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)  




I found that the first link had easy "step by step" directions, with pictures for every important step.

---

### Post by CoreDefence on 2007-07-17
> **davidjmayo said:**
> Hi fellow forum members,

Have you read the other post ? [http://ubuntuforums.org/showthread.php?t=502955](http://ubuntuforums.org/showthread.php?t=502955)

The initial problem here is a graphics card ( the wireless and sound are other issues that need to be sorted) and a simple way for a newcomer to fix this issue which is not where my experience lies.

Core: what happened when you did this (from your other post reply #2 or #3 as it may help others)



I dont know this graphics card. What would be the best way to get OP up and running?

1 install from safe graphics mode?
2 Alternate CD?
3 fix another way?
Sorry, I shoulda answered this individually. When I did 'sudo dpkg-reconfigure xserver-xorg' I got the questions asking me for details of my graphics card. I got as far as it asking me to input the card's BUS???
I could not be sure whether I would need to dismantle the system and remove the card to determine this and so just left it.

In the last hour I have however loaded the Ubuntu disk onto another PC I have which had no OS on it (it's like PC junkyard here, I tinker). No graphics problems with that, though sound and networking are still not up & running. 

Thanks for the response,
Core

---

### Post by CoreDefence on 2007-07-17
Thanks for that. As mentioned, I have another system to run ubuntu exclusively so I wonder about whether I need to run a dual OS system. I note that in #10 TSMiller advises running a dual or do I misunderstand him? For the time being I'll work with the single system until I know more.
Thanks again,
Core

---

### Post by deadlikeoscar on 2007-07-17
CoreDefence,

I sent you a private message. Thought it might help you out.:)

---

### Post by CoreDefence on 2007-07-17
> **deadlikeoscar said:**
> CoreDefence,

I sent you a private message. Thought it might help you out.:)
You did? Well thanks but I'm also an absolute beginner in this forum so how would I pick that up please?

Core

---

### Post by CoreDefence on 2007-07-17
Found the PMs and have replied, thanks.

Core

---

### Post by deadlikeoscar on 2007-07-17
No problem...:)

---

