---
title: "Security!"
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by Zingomoos135 on 2006-07-15
i was reading this month's PC world and it had a large section of PC security and i got to thinking that my ubuntu machine has no antivirus software or anything on it. is there anything that i can put on here that will keep my computer safe from crackers and other things without having to go into terminal and type a bunch of stuff?

if not, i'll be willing to put stuff in terminal if someone's willing to help me do it. i'm kinda new to the terminal commands.

thanks!

---

### Post by Jagot on 2006-07-15
You don't need anti-virus.  The most you really need is a firewall configuration app like firestarter which is available in the repos.

[http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_Firewall_.28Firestarter.29](http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_Firewall_.28Firestarter.29)

---

### Post by gezz on 2006-07-15
Doesn't ubuntu come with its own firewall installed anyway? I've read somewhere that it's there, but not activated because not really necessary for most stations.

I also read somewhere that ubuntu is quite secure because, unlike windows, we are not running in root mode anyway, so the OS is protected.

Anyway, look around, there is more geeky stuff about security in the help pages. Cheers!

---

### Post by T700 on 2006-07-15
By its nature, Linux is not susceptible to viruses and spyware, like Windows is.  So long as you don't routinely run as root, don't willy nilly download strange software from sketchy sources, and either have a firewall or exist behind a NAT enabled router, you will be fine.

If you would like to activate the already present firewall in Ubuntu, open a terminal and type just these two words:

```
gksudo firestarter
```

A very simple wizard will leap to life and in 3 minutes, your firewall is configured and you need never think of it again.  Pretty simple, eh?  :-)

Paul

---

### Post by catlett on 2006-07-15
If you are talking internet based attacks then a firewall and just using sudo to become root is enough. But if you are talking about keeping someone physicaly out of your computer and to make sure someone who has physical access to your compouter can't access inportant data etc., here is the dapper guides recommended actions.[http://doc.gwos.org/index.php/DapperGuide#Security](http://doc.gwos.org/index.php/DapperGuide#Security)

---

### Post by wildseven on 2006-07-15
I enjoy Firestarter. Everything works well default and the policies are really neat to use. But are there terminal commands i can use to secure my laptop? Just wondering ( why makes things harder lol ) I want to learn linux to its full extent. Also, lets say I SSH to my laptop, i would like to know how to configure my firewall etc..

thanks for reading if you did ^^

---

### Post by forumposters on 2006-07-16
If you have a linksys router then the software firewall would be redundant and unnecessary, is that right?

---

### Post by Zingomoos135 on 2006-07-16
i'm glad i don't have to worry about anti-virus stuff then

thanks everyone!

---

### Post by wildseven on 2006-07-16
depends. if you configure your router to protect you then i guess, but hey extra protection is good. ( except double wrapping condoms lol, its bad! )

any-who away from my sick jokes lol. If you dont setup your router 
ex/ leave default name Linksys most people will know the password is admin/admin, ex2/ not using WEP. Those to me i think are very important to setup.

but i havent taken my security classes yet ( 2 more semesters!!! ) so wth do i know lol. Just saying what i have played with and read on the internet

my 2 cents, hope it helped...somewhow lol.

---

### Post by MaximB on 2006-07-16
if somone happen to have a pishical access to your computer
there is nothing you can do !
1.he will reset your bios (there is a chip in your computer that resets it)
2.he will load from "crack cd" and he will reset your ubuntu password
3.say goodbye to your data

but if you are talking about access from the net - you are safe !
but if you are a paranoid about it - you can still download an antivirus in the add/remove programs
and offcourse set a firewall.

---

### Post by [S|G] on 2006-07-16
Well, I must say that I disagree with people that say that you don't need an antivirus for linux. I know it might be a bit of paranoia, but here are my reasons:


1. New viruses appear every day. As linux becomes more popular, the chances that new unix viruses appear also increase.
2. They exploit security breaches whenever possible, to gain root access. That means that if you don't run an updated system or if you are hit with a 0-day virus it *might* be able to gain root privileges. Anti-virus software  is often able to detect yet-unknown virus using heuristcs analysis.
3. Even if a virus cannot compromise your system, it might be able to wreck your home folder. And you don't want that.
4. We deal with windows files often (word documents, etc), and even if we won't get infected ourselves, we may help to stop other users from being infected.

I use f-prot on my system, but there is clam-av that is on ubuntu's repos and is also a nice way to protect yourself. Extra protection doesn't hurt, and even though chances that you will come across a unix virus today are VERY, VERY LOW, being protected can save you lots of headaches in the future.

And you should definitely use a firewall.

---

### Post by lunamystry on 2007-07-21
I have read a bit on the linux firewall that firestarter and them use but i have this friend who likes visiting illegal sites and i am kinda afraid to tell him to stop, I have firestarter installed  but I read somewhere that I can get these two things to detect rootkits (whatever they are, if they bad for my pardus i dont want them) so i was wondering, for my peace of mind, will installing both harm my PC in anyway? or make them less efficient, like installig two anti-virus software on mswin thingy. Just for my peace of mind, I want something I can see and firestarter is kinda not enough. 

If i sound paranoid its just that the friend of mine using MSwin got a really bad virud that prevented him access to somethings in his file or made his harddrive appear as a disc or something like that, and he claims to have got it from me. I remember he brought his USB saying there were some files that he could not delete that he downloaded from Pardus and i just sent them to the bin and they were gone. 

Thank you for your time.

---

### Post by por100pre1 on 2007-07-21
It's not a bad idea to have some antirootkits installed. I use chkrootkit and rkhunter.

To install them:
```


sudo aptitude install chkrootkit rkhunter


```

To use them:

```


sudo chkrootkit

sudo rkhunter --update && sudo rkhunter -c -sk


```

---

