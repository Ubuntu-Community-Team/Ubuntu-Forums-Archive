---
title: "Restricted Drivers and Beryl Wont install because..."
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by phizikal on 2007-07-01
Because I am getting this error for both.

```

root@admin:/home/admin# sudo apt-get install beryl
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

root@admin:/home/admin# sudo aptitude install restricted-manager
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

Any help?

---

### Post by avik on 2007-07-01
Are you running something like synaptic or the Add/Remove Software program?  You can't run more than one of those alongside apt-get or aptitude.

---

### Post by phizikal on 2007-07-01
Beryl won't show up in synapatic.

And I need restricted drivers to get my drivers going for my sound. Because its sayingthat I need GStreamer or something, i tried installing it and it says its already there. =/

---

### Post by avik on 2007-07-01
But are you running something like Synaptic?  You can't run Synaptic and apt-get at the same time.

---

### Post by bigken on 2007-07-01
restart the pc and run this sudo reconfigure -a

then sudo aptitude install beryl

sudo aptitude install emerald

---

### Post by phizikal on 2007-07-01
Wait, lol. Yes... and it still can't find beryl. =/

I figured since my pc is pretty good performance and has direct rendering I try it. =/

---

### Post by avik on 2007-07-01
Did you enable the other repos?  Go to System->Administration->Software Sources and enable universe and multiverse.

---

### Post by phizikal on 2007-07-01
Okay, I had universe 6.06 LTS checked. But with multiverse, theres only LTS backports? Use that?

---

### Post by bigken on 2007-07-01
why dont you upgrade to feisty if its desktop affects your after take a look at fusion

---

### Post by phizikal on 2007-07-01
I have CD's coming in from my request. I don't have any blanks and sure don't know anybody from my small town that would. I currently live on my own and is low on spare money. 

Fiesty would be a great help, can't wait until I receive my cd's. :D

---

### Post by bigken on 2007-07-01
you could edit your source list change dapper to feisty and run apt-get update
then apt-get upgrade

---

### Post by phizikal on 2007-07-01
BTW, know anywhere I can look for info on fusion and maybe a link for download instructions if I am interested?

---

### Post by bigken on 2007-07-01
look [here:D]("http://ubuntuforums.org/showthread.php?t=481615")

---

### Post by phizikal on 2007-07-01
And I didn't know you can "upgrade" dapper to fiesty. Can you find an article on how to do that also. I hope it doesn't reset everything, because I have no backup options.

---

### Post by bigken on 2007-07-01
take look[ here ]("http://www.debianadmin.com/upgrade-ubuntu-dapper-to-ubuntu-edgy-eft.html")

sudo gedit /etc/apt/sources.list

change dapper to feisty 

sudo apt-get update

sudo apt-get dist-upgrade


sudo apt-get -f install
 

sudo dpkg --configure -a


then reboot

---

### Post by phizikal on 2007-07-01
Will I lose my saved data? Just to ask?

---

### Post by bigken on 2007-07-01
no but it is risky do you have a separate /home partition

---

### Post by phizikal on 2007-07-01
No, how would I do that?

---

### Post by bigken on 2007-07-01
when you created your ubuntu partitons you create three not two 

/ (root)
swap
/home

so if you ever need to reinstall the os you files stay safe on the seperate home partiton ;)

---

### Post by phizikal on 2007-07-01
Ok? I now know I need a seperate partition. But how do I make a seperate partition?

And the info above didn't help that much.

---

### Post by bigken on 2007-07-01
If I were you I would wait until the discs arrive then backup my data and do a clean install

---

### Post by phizikal on 2007-07-01
Sounds like a good plan, and also I noticed this [Compiz Tutorial]("http://ubuntuforums.org/showthread.php?t=481615") only shows for fiesty. Is it available for dapper also?

---

### Post by bigken on 2007-07-01
dont know you will have to search the forum

---

