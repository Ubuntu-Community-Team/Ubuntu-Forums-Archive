---
title: "Synaptic vs line coding?"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by paker on 2007-02-12
Synaptic takes care of adding softwares nicely. Why then all the line code instructions? When I first switched over to Ubuntu from Windows 2000 a month ago, I thought Ubuntu was all about line coding. I thought I was going back to stone ages. But that's not entirely true. I bet many newbies like me will go through the same experience. Is it because experienced users were showing off their line coding skills? Or are there things that ave to be line coded?

---

### Post by MrKlean on 2007-02-12
Somethings can only be done thru "line coding" ...plus, you sure learn a bunch of stuff ; ))

---

### Post by nickoli_02 on 2007-02-12
Many things can be done much faster when you know the exact commands of what you want to do. For instance, if you know you need to install package wxyz from the repositories, why go through synaptic where you have to type a search and click a bunch of checkboxes when you can just open a command line and type 
```
sudo aptitude install wxyz
```

To the best of my knowledge, for everything you can do through a gui interface in linux, there is a terminal command that does the same thing. When you're offering advice to someone it's often just easier to say "open a terminal and type this:" than saying "go here, then click this, open this tab, click this button" etc.

---

### Post by jordanmthomas on 2007-02-12
To add to what kickoli_02 said, some people may not have Synaptic installed.
Say they use Kubuntu...the instructions for Synaptic wouldn't work correctly for them.  Command line programs are more universal and will work on any *buntu (and with the exception of a few distro-centric tools and file layout differences, any Linux distribution).

---

### Post by g3k0 on 2007-02-13
Directions with gui tend to become more complicated and ambiguous.  It has nothing to do with showing "line coding skills."  Its just difficult to say things like "ok press the little blue doohickie next the the red thing."  Also one command takes much less time then looking for buttons.

You will see the beauty of it as you become more experienced

---

### Post by atihimself on 2007-02-13
If you lear how to use terminal then (un)installing, searching, and configuring will be much easier than through GUI, oh gosh, well, maybe I just love terminal too much

---

### Post by v8YKxgHe on 2007-02-13
Most guides use command line tools because it is far far easier for us to explain to someone to do :

```
sudo apt-get install my-program-here
```

Than to say:

> Ok, go to System->Administration->Synaptic Package Manager. Now, wait for that to load ... yeah you may need to type your password in when it asks for it. Ok, now go to Search and enter in the textbox "My Program Here" then press the Search button. Right click on the package and select "Mark for Installation" once you've done that, go to Apply (top-left).

Which is shorter and easier for us to say =)

---

### Post by paker on 2007-02-13
I see the point now. I have always been on the advice-receiving side, and never understood your position. By the way, does "sudo apt-get install PROGRAM NAME" do everything, including configuration file updating? Thanks.

---

### Post by xpod on 2007-02-13
"sudo apt-get(or aptitude) install <program name>" will install any program as long as you have the relevant repo in your sources list.

You`ll need to use a text editor for altering configuration files though.
Mabey this site will help you out with some of the basics.

[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

---

### Post by jvc26 on 2007-02-13
I use the 'sudo apt-get' line as I find it far faster and easier - esp if I'm running a new install and I want to install some 20+ packages. To go through and install all of them by hand would be painful to say the least so instead I use the CLI - clean, efficient and easy.
Il

---

### Post by bodhi.zazen on 2007-02-13
> **paker said:**
> Synaptic takes care of adding softwares nicely.

yea, synaptic is great :)

> Why then all the line code instructions?

What AlexC_ said :)

> When I first switched over to Ubuntu from Windows 2000 a month ago, I thought Ubuntu was all about line coding. I thought I was going back to stone ages. But that's not entirely true. I bet many newbies like me will go through the same experience. Is it because experienced users were showing off their line coding skills? Or are there things that ave to be line coded?

LOL parker.

You are talking about the CLI or terminal. I agree 100 % a new OS is intimidating to say the least. And the CLI seems at first to be mysterious, intimidating, and a throw back to the stone age all at the same time :)

As you become more familiar with Linux the CLI will seem better and better, it is very powerful.

Here is a link that may help a little :

[http://doc.gwos.org/index.php/CommandLineBeginners](http://doc.gwos.org/index.php/CommandLineBeginners)

Oh, and one thing about Ubuntu, there are very few "show off's" here and you will find a lot of good advice.

---

### Post by bodhi.zazen on 2007-02-13
> **paker said:**
> I see the point now. I have always been on the advice-receiving side, and never understood your position. By the way, does "sudo apt-get install PROGRAM NAME" do everything, including configuration file updating? Thanks.

Missed that one.

Yes, it does :)

---

### Post by xpod on 2007-02-13
Trust you to spot my error bondi:) 

I mis-read and didn`t realise parker meant actual program installation files.
Of course you dont need a text editor for THOSE configuration updates...sorry m8

I`ll awa an boil ma heid:lolflag:

---

