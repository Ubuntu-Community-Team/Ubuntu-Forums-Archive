---
title: "upgrading to ubuntu 7.04"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by lsprague on 2007-07-29
I am a ubuntu newbe, I have ubuntu 6.06 installed in a dual boot with windows xp, on my dell 6400/1505 laptop. I can't seem to make  the wireless card work in ubuntu, I have a wired connection that works fine.
Is there an upgrade to ubuntu 7.04 ?
thanks

---

### Post by lmlypfan on 2007-07-29
I would do a fresh install of 7.04
From what I can gather it is easier to get some wireless networking cards up and running.

---

### Post by lunamystry on 2007-07-29
I there a way to Upgrade say from Feisty to Gusty ( when it comes out of course) without making a clean install? I heard that ubuntu has something to help keep my files during an installation or too import files that i have into an installation but that has not worked for me yet. It tells me there is nothing to import even though a few thing in my hard drive.

On the upgrade issue is there maybe a way to repair my Kubuntu installation? I am having problems that come from the first install ( i think) which i did using sudo apt-get install kubuntu-desktop while I was using gnome then i used some instructions that I got to remove gnome. I cant remember where I got the instructions but it think i can find them again if they're needed. 

Thank you for your valuable time

---

### Post by Daveth on 2007-07-29
if you make yourself a separate /home partition with something like Gparted, then you won't mind upgrading and over-writing, as all you precious data is separate.

Returning to the original thread owners question, I upgraded from dapper to feisty but went on the path of making a separate /home, then install feisty from cd, only formatting the dapper partition. It picks up home nicely when you tell it where to mount /home, and off you go. Wireless support does seem better in feisty- I prefer nice solid cables myself though!

I would stay away from an internet upgrade through edgy- too perilous, not to mention slow!

---

### Post by laidback on 2007-07-29
I went from 6.06 to 7.04 with a fresh install as I was also moving to a new machine. I understand that you can upgrade through software but I've not done it. I've copied over all my old files and settings including Evolution mail and Forefox browser bookmarks etc. The area you will be concerned with is /home and /home/myarea with all the hidden files as well. I copied over the complete directory for Firefox (~/.Mozilla) plus others as needed. I renamed the 7.04 versions in order to keep them just in case anything went wrong, it didn't. I've been runing 7.04 for several months now and I'm very pleased with it, a definite improvement on 6.06.

---

### Post by lunamystry on 2007-07-29
I found Kparted and it sems a bit dodge, Should i use it? but then I couldnt access the tutorial section of the site that i downloaded from.

Okay me is  just find this:

 [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) 

which me thinks me is gonna use to make home partition but I'd like to know one thing before I do, can i use Gparted and the ubuntu live CD to edit the Kubuntu partition? I think can but i need confirmation 

Thank you for your patience

---

### Post by laidback on 2007-07-30
I see no reason why you couldn't use Gparted from the live CD, it's often recommended. Just back up important files first. I use gnome and the Live CD for Gparted rather than the version that comes with the live Ubuntu CD, it's slightly more up to date and formats memory sticks too. Google for Gparted to find the ISO, very easy to download and burn your own copy...I even managed it.

---

