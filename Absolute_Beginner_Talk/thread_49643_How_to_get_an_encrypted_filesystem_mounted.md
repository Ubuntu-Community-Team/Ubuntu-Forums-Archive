---
title: "How to get an encrypted filesystem mounted?"
date: 2005-07-17
forum: Absolute Beginner Talk
---

### Post by Candid Dauth on 2005-07-17
I've just changed from SuSE to kubuntu. I'm really confused with all this stuff, I tried to mount my encrypted home partition.

I've noted these two keywords about the kind of encryption my home partition uses:
twofish256, loop_fish2

Some Howto told me to modprobe loop_fish2, but I get an error that there is no loop_fish2. It also told me to install cryptsetup by using apt-get, but I can't find any information about using apt-get. apt-get seems not to be able to find any package, and I don't have any idea where to find installation sources to configure. Not very newbie-friendly.

So how to define installation sources and how to mount my encrypted filesystem?

---

### Post by Strangerdave on 2005-07-17
Greetings,

I too have just made the switch from SUSE to Ubuntu and am having a good time with it.  i have learned quite a bit and will probably stick with it.

At any rate, I can not help in in total with your question, but I do understand somethings that might make things easier for you.  

First off, apt-get is the way in which one downloads and installs programs.  There is no Yast here to do that for you, like in SUSE.  Apt-get is a command line interface that you use when you open a terminal.  There is a graphical interfcae called Synaptic which is more like Yast.  Go -> SYSTEM ->ADMINISTRATION -> SYNAPTIC PACKAGE MANAGER.  

For the command line interface you just pen up a regualr terminal and type apt-get install program, and it is done.  APPLICATIONS->SYSTEM TOOLS->TERMINAL

Now as for installation sources, they are out there my firend, but once again, there is no Yast to help you along.  For Ubuntu they are called Repositories and you can add some.

I suggest taking a look at [this](http://ubuntuguide.org/#extrarepositories) page for help in installing programs and repositories.  It is out of date, as I have found that some programs and isntallatins don't work, but it got me started.  There you will find info on mounting partitions and drives etc.

I think Ubuntu is a great "next step" from SUSE.  Yast did a lot of work, more than I knew, but now with Ubuntu, you can get a better sense of what is going on and why.

Good luck though, and don't give up!!! ;-) 

SD

---

### Post by Candid Dauth on 2005-07-18
Thanks for your help.

I was sitting the whole after-noon on it, now it works very fine and I think I&#8217;ve learned quite a bit about ubuntu and linux.

I didn&#8217;t get my crypto filesystem working, the kernel module which supports the twofish256 encryption seemed to be SuSE specific, as I learned in some IRC channel. So someone gave me the tip to move all my data to otherwhere and then reformat the partition. I did so and it works quite well.

I&#8217;m really happy about having changed to ubuntu, everything goes faster and doesn&#8217;t take too much space. And I think I will learn using those apt-get and kynaptic things soon.

---

### Post by Strangerdave on 2005-07-19
That is great!!  If you want practise on apt-get make sure you visit [this](http://ubuntuguide.org/) site for tons of info.  In a way I like it better than SUSE in that I feel more involved in what is going on.

SD

---

