---
title: "A few problems that bug me"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by Majorix on 2007-07-10
Ok I have been using Ubuntu for around 6 months for now, but it causes me some problems. These are:

1. I have set the computer to hibernate if the lid is closed. But sometimes when I open the lid after some time, I get to see that the comp wasn't put to hibernate at all. The battery is nearly empty. I can't find an explanation for this :confused:

2. After the computer comes out of the hibernation, it can't for some reason connect to the wireless internet at all. But when I completely reboot the pc, it works fine with the connection. Again, I can't find an explanation.

3. A few days ago, I discovered that the problem with the desktop not "auto-cleaning itself" was one from the past, yet noone has even bothered fixing it.

4. For some reason, the downloads from the servers are very very slow. I am downloading at the 1/4th speed of the max download speed. I tried the "find the best server" option 2 or 3 times... It is really annoying and again, I got no explanation.

I REALLY love Ubuntu but these simple points make me think I can't even trust it with the simplest of all problems. Imagine yourself having to face the first problem...

What are your thoughts? Can I get to fix these problems somehow? Or should I just give up and use a different OS?

---

### Post by Pragmatist on 2007-07-10
> **Majorix said:**
> ...should I just give up and use a different OS? 

There are three main categories of ubuntu users:

1.) Users who have no serious problems.

2.) Users who have problems that can be fixed.
 (a) Users who spend their time trying to make it work.   
 (b) Users who get frustrated and ask if they should give it all up.
     
3.) Users who have problems that cannot be fixed (i.e. there is incompatible hardware)

Personally, I think you should just give up, since you are either in situation 3. or you are a 2.b. type of user.

---

### Post by tak1150 on 2007-07-10
> **Majorix said:**
> 
1. I have set the computer to hibernate if the lid is closed. But sometimes when I open the lid after some time, I get to see that the comp wasn't put to hibernate at all. The battery is nearly empty. I can't find an explanation for this :confused:

2. After the computer comes out of the hibernation, it can't for some reason connect to the wireless internet at all. But when I completely reboot the pc, it works fine with the connection. Again, I can't find an explanation.


I have the same problems as well. I have Dell Inspiron 1150. What laptop do you have? I'll also try to look for solutions and will post if I find any.

---

### Post by Majorix on 2007-07-10
I have a Toshiba M70-215.

---

### Post by Majorix on 2007-07-11
Anybody? Any ideas?

---

### Post by Pragmatist on 2007-07-11
Have you tried "toshutils"?  It is a package in the repositories and you can find it by doing a search in synaptic using the keyword: toshiba

---

### Post by tgalati4 on 2007-07-11
For your wireless networking, you may have to modify the "wake-up" script to reinitialize your wireless card (or restart DHCP to get a dynamic IP address).  An alternative is to set up a static IP address which I find more reliable for wireless use.

I think all of your problems have solutions, but it will take some time.  Work them one at a time and let's see how far you get.

---

### Post by Majorix on 2007-07-11
OK I have installed it now but how does it work? I tried typing toshutils in the terminal but that didn't work. Or isn't it supposed to be "started"?

BTW my wireless doesn't work at all now. I don't know if it has anything to do with previous problems or with Ubuntu at all. I don't have any other OS installed on this machine and I don't have any other PCs to test with. But I will try to find a way.

---

### Post by Majorix on 2007-07-11
@tgalati4:

How do I change the wakeup script? I am a newbie at these kind of things :)

---

### Post by Pragmatist on 2007-07-11
> **Majorix said:**
> OK I have installed it now but how does it work? I tried typing toshutils in the terminal but that didn't work. Or isn't it supposed to be "started"?
What happens if you try:
```
man toshutils
```

---

### Post by moredhel on 2007-07-11
3. Feel free to fix it if you want to.

4. I live in the UK and get 250 kbps - the max i can basically go, so i dunno.

---

### Post by Majorix on 2007-07-11
@Pragmatist:
It says "no manual entry for toshutils" if I try that.

@moredhel:
I will probably try a few other mirrors to see if anything changes.

And wireless works again for some reason I don't know. :lolflag:

---

### Post by Pragmatist on 2007-07-11
I just installed toshutils, and it doesn't look like it will solve your problem.  If you want to read about what it can do, read the README file at:  **/usr/share/doc/toshutils/README**

Another program, which is installed by default--I have it installed and I don't have a laptop--is **toshset**  toshset does have a man page:
```
man toshset
```

---

### Post by Majorix on 2007-07-11
I used toshset now to disable a feature, but I got this message in the process:
> required kernel toshiba support not enabled

Can this be the cause of other problems? I am just taking an educated guess.

BTW, I managed to find a faster server. Shame on my country's server for being so slow.

So the only problems left now are problems one and two: Computer randomly not being put into hibernation and computer not coming out of hibernation with wireless support.

Any help is much appreciated..

---

### Post by tgalati4 on 2007-07-11
I'm running Dapper so your configuration may be different under Feisty.  For wake-up scripts try the following:

>cd /etc/acpi/resume.d

>ls -la


There are a bunch of scripts that get run when you resume from standby.  Look through each one.  Print them out if you have to.  Somewhere in one of these scripts we need to reload a wireless module to properly wake-up the wireless connection.

I have an old Dell Inspiron 7500 and I find that it takes as long to come out of hibernation as it does to cold boot.  So I don't use hibernate.  I use standby and leave it plugged in.

The advantage is that the machine comes out of standby reliably and much quicker than hibernate.  Hibernate is a special state that saves the memory to disk.  When waking, this disk file gets read back into memory, but sometimes the BIOS doesn't wake up all of the hardware.

I have had random problems with my Dell with hibernate and wireless and USB.  It seems the BIOS doesn't always supply power to these components coming out of hibernation.  The only way to recover is to hold down the power button for a hard turn off.  It's frustrating, so I don't use hibernate.  I use standby instead.

---

### Post by sugarland2k on 2007-07-11
You might try sudo apt-get install toshutils 

For laptop specific problems, try 
[http://ubuntuforums.org/](http://ubuntuforums.org/)

and see Ubuntu Forums > The Ubuntu Forum Community > Main Support Categories, 
Hardware & Laptops  

I had some similar problems with my Pansonic Toughbook but most of them are worked out.

---

### Post by Majorix on 2007-07-11
Thanks for pointing out the Laptops forum. Yes, I know it exists, but as the newbie I am, I thought maybe this beginner forum would suit my needs more :)

@tgalati4:
I >'ed the results of the ls to a file, which can be found attached to this post. I personally looked at a few of them, and couldn't necessarily figure out which one might be the correct script and what I have to place in that script. It would be great if someone could help me out with this one.

---

### Post by Majorix on 2007-07-12
Anyone want to help? Thanks.

---

### Post by Nussbaum on 2007-07-12
Not sure if this can help you but it might be worth checking out. 

[https://bugs.launchpad.net/ubuntu/+bug/69426](https://bugs.launchpad.net/ubuntu/+bug/69426)

---

### Post by Seine on 2007-07-12
> 2. After the computer comes out of the hibernation, it can't for some reason connect to the wireless internet at all. But when I completely reboot the pc, it works fine with the connection. Again, I can't find an explanation.Sometimes in my house, as far as I can tell, the machine coming out of hibernation will not negotiate a new IP address from the DHCP server, despite the old IP being released to another machine. Are other machines involved?

---

### Post by Majorix on 2007-07-12
Ok apparently number 2 was a bug or something similar. I fixed it by following Nussbaum's link, and then by following the advice there to change the /etc/default/acpi-support. Thanks to anyone who tried to help with this problem.

Now ONLY ONE PROBLEM is left and thats number 1: Computer randomly not deciding to be put into hibernation. Could anyone find a solution to this?

Thanks a lot beforehand.

---

### Post by Pragmatist on 2007-07-12
Does the problem occur with suspend?

---

### Post by Majorix on 2007-07-13
I have never tried suspending.. Should I?

---

### Post by Pragmatist on 2007-07-13
I would try it.  It could help diagnose the hibernate problem.

---

### Post by Pragmatist on 2007-07-13
Check out this alternative: [http://www.tuxonice.net/](http://www.tuxonice.net/)
You can find it in the repositories under the name: **suspend2-user**

---

### Post by Pragmatist on 2007-07-13
What happens if you manually go into hibernate mode?  In other words, you don't trigger hibernation by closing the lid of the laptop, you just put it in hibernate mode.

---

### Post by Majorix on 2007-07-13
When I manually hibernate everything is fine.

Suspend mode is also ok manually.

---

### Post by Pragmatist on 2007-07-13
> **Majorix said:**
> When I manually hibernate everything is fine.
Great!  So you have a solution for the time being.  Is it that critical that you trigger the hibernation by closing the laptop?

---

### Post by Majorix on 2007-07-13
I just want to be able to hibernate without clicking any buttons or pressing any keys. Of course, it is not crucial though.

Can the problem be because of hardware problems? Probably the comp doesn't recognize that the lid has been closed? If this is the case, can there be a solution?

Thanks.

---

### Post by Pragmatist on 2007-07-13
If you want to solve the problem, be methodical:

1.) Define the problem:  
(a) Is it persistent or intermittent?  
(b) Can you consistently replicate the problem?  
(c) Does the computer *ever* go into hibernation when you close the lid?

2.) Is it a hardware or a software problem?
(a) The "lid" is part of your laptop's hardware.  What make and model laptop are you using?
(b) What program are you using for hibernation? 
(c) Does your BIOS have a "suspend-to-RAM" option?  If so, is it selected?

3.) Search for others with the same problem using:
(a) The Ubuntu Forums
(b) Google
(c) bug trackers like Bugzilla.

4.) If nobody has the same problem, post a thread and get some help.

5.) Perform tests to isolate the problem. (you could do this anytime after steps 1 and 2).

We already know that hibernation works for you, now we need to figure out why you can't trigger the hibernation by closing the lid of your laptop.  

Post answers to the above questions even if they seem obvious or irrelevant.  If you need clarification on a question, just ask.

---

### Post by Majorix on 2007-07-14
Ok I will try to answer the questions:
1.
a. Persistent.
b. No.
c. It sometimes does, sometimes not.

2.
a. The make is toshiba, model is m70-215.
b. I am using the default one. didn't install anything besides that.
c. I have no idea. How can I check.

3. It seems a few other people on the Ubuntu forums also have the same problem.
I googled but didn't get relevant results.
I will be looking at bugzilla and launchpad but don't know what to search for? I mean searching using a parameter like "closing the lid doesn't trigger hibernate" would be too dumb.

4. N/A

5. I am constantly trying to hibernate by closing the lid so I believe I am testing enough?

---

### Post by Nussbaum on 2007-07-14
Not sure if this helps but it does deal with this problem. (post #6) Might be worth a try. 

[http://ubuntuforums.org/showthread.php?t=121720](http://ubuntuforums.org/showthread.php?t=121720)

EDIT:
If it doesn't work you could also try appending it with 'force' (/etc/acpi/hibernate.sh force). Also maybe for diagnostics you run  this command first
```
 cat /proc/acpi/button/lid/*/state 
```

in a terminal and see if it says open or closed. If it says closed its probably not a good idea to make those changes.

---

