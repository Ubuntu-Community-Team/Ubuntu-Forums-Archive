---
title: "What the... Gutsy install security issue"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by phr0ze on 2007-10-18
I have just installed Gusty, and because my computer is not connected to the internet, I got a Security warning that Security Updates on security.ubuntu.com couldn't be accessed.

This is fine. But then the error goes on to say that it is commenting out security.ubuntu.com from /etc/apt/sources.list.

Am I to understand that if any Noob installs Gutsy and apt can't connect, they will never get security updates?

---

### Post by Paul820 on 2007-10-18
It's ok, you just need to take off the '#' at the beginning of the line in the sources.list file.
In the terminal type

> sudo gedit /etc/apt/sources.list

The lines will look like this:

> #deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
Take out the #. Don't uncomment everything, just the security updates it said it had commented out.

---

### Post by LowSky on 2007-10-18
Ubuntu is an OS that really needs an internet connection but why would you need security updates if your not connected to the internet?


It most likely is commenting them out because it assumes the computer will not be used on the internet therfore it doesn't want you to see an error message everyday. Kinda odd but It wouldn't suprise me.

---

### Post by phr0ze on 2007-10-18
But this is the problem. I can do it fine. I'm worried about the NOOBs or someone who bought a preconfigured computer. What is going to remind them to go uncomment these lines?

Why are we making a user's first experience with linux a forced command line?

And does everyone assume that users will even pay attention. Users will go on without these updates and never know it.

---

### Post by juantovarm on 2007-10-18
Ubuntu depends a lot on the web, it will get all the necessary updates from it, thus, how can you get an update if you cannot connect, regardless what kind of upgrade it is? If you want to to include your security updates, all you have to do is to eliminate the comment (#) symbol before the line, which is extremely easy: in the terminal type:

sudo pico /etc/apt/sources.list

and then read where the security update is and just deletete the #. Save it and exit.

But, those changes won't take effect until you run

sudo apt-get upgrade

and in order for that process to run smoothly, you need internet access.

So don't worry, if you do not have internet access, you do not need to do any of those steps

I hope i cleared your questions

juan

---

### Post by phr0ze on 2007-10-18
> **LowSky said:**
> Ubuntu is an OS that really needs an internet connection but why would you need security updates if your not connected to the internet?


It most likely is commenting them out because it assumes the computer will not be used on the internet therfore it doesn't want you to see an error message everyday. Kinda odd but It wouldn't suprise me.

I'm installing on a laptop which will be on the internet all the time. I just don't happen to have any Wifi near by. Who's to say at the moment someone is installing ubuntu that their ISP isn't down, or DNS isn't returning an address, or some other type of hiccup?

None of the other repositories have to show me an error message every day. Why does this one? Is this really the best way to handle this?

---

### Post by loganm10 on 2007-10-18
Also the "noob" friendly solution would be going into synaptic and going into the repositories and checking all the boxes, not very hard but they might not know where to look

---

### Post by phr0ze on 2007-10-18
> **juantovarm said:**
> Ubuntu depends a lot on the web, it will get all the necessary updates from it, thus, how can you get an update if you cannot connect, regardless what kind of upgrade it is? If you want to to include your security updates, all you have to do is to eliminate the comment (#) symbol before the line, which is extremely easy: in the terminal type:

sudo pico /etc/apt/sources.list

and then read where the security update is and just deletete the #. Save it and exit.

But, those changes won't take effect until you run

sudo apt-get upgrade

and in order for that process to run smoothly, you need internet access.

So don't worry, if you do not have internet access, you do not need to do any of those steps

I hope i cleared your questions

juan


I'm not worried about me. I know how to edit sources.list, but thanks any ways. 

I've worked on so many computers for others that I know a warning like this will get ignored by the new user, and this new user will then no longer get updates. I'm worried about these new users.

---

### Post by kingpoiuy on 2007-10-18
Should at least come up with a second warning after the OS is installed totally.  Sometimes during an install or early after complete install the NIC does not work yet.  It is very common.  You  could always just have another popup come up even 10 days after installation is complete.

---

### Post by krlill on 2007-10-18
"I've worked on so many computers for others that I know a warning like this will get ignored by the new user, and this new user will then no longer get updates. I'm worried about these new users"

I'm one of those noobs. Thanks for the warning.  I'll make sure I'm online when I install.

---

### Post by Sunflower1970 on 2007-10-18
This surprised be a bit when I was doing a fresh install at one point. Live CD wasn't able to connect to my wireless and while installing I had gotten up to do something for a bit. Came back after a half hour or so, and I thought I had originally done something wrong, or was worried my install was going to be screwed up. 

It wasn't that big a deal to go into the sources.list to uncomment everything (everything for me was commented out, not just the security updates), but I can see a first time user who may not have access to the internet be a bit worried they've done something wrong. Most won't be affected by it, but there's that small percentage that will wonder what that is.

If this needs to be there, that's fine, but it should, maybe, be a bit friendlier. Instead of the red circle with line through it, maybe a light bulb or some other little symbol to let people know this isn't anything much to worry about while installing. And maybe after installed, a box could pop up explaining how to change this.

---

### Post by Paul820 on 2007-10-18
Sorry about that i didn't think you knew how to do uncomment them :-? Anyway, i do agree with you, there should be a pop-up warning explaining that the security updates need reactivating in the apt sources list. Most users don't even know what a source.list is never mind a terminal.

---

### Post by phr0ze on 2007-10-18
I'm going to submit this to the bug tracker too. I don't think this is the right answer. So what if the address is not accessable at one point in time. Disabling this 'permanently' is the wrong thing to do.  

By permanently I mean that the system will not re-enable this for you. You must take action to do it.

---

### Post by lespaul_rentals on 2007-10-18
Yeah, maybe after a couple of days a window should pop up describing the situation and ask if the user has an Internet connection and wants to recieve security updates.  If so, it would un-comment that line.

---

### Post by Lord_Dicranius on 2007-10-18
> **lespaul_rentals said:**
> Yeah, maybe after a couple of days a window should pop up describing the situation and ask if the user has an Internet connection and wants to recieve security updates.  If so, it would un-comment that line.
But what about those who will never be connecting to the net?  I think there's needs to be a different way of going about the situation as a whole.  Something else instead commenting out the entire file.

---

### Post by Frak on 2007-10-18
> **phr0ze said:**
> But this is the problem. I can do it fine. I'm worried about the NOOBs or someone who bought a preconfigured computer. What is going to remind them to go uncomment these lines?

Why are we making a user's first experience with linux a forced command line?

And does everyone assume that users will even pay attention. Users will go on without these updates and never know it.
Goto software sources and uncheck updates. Not a big deal, its stated in the help documentation on a fresh Ubuntu installation.

---

### Post by ebichete on 2007-10-18
File a bug report in launchpad. It is an important issue, though possibly low impact issue. But file the bug.

---

### Post by Lord_Dicranius on 2007-10-18
> **Frak said:**
> Goto software sources and uncheck updates. Not a big deal, its stated in the help documentation on a fresh Ubuntu installation.
Ah, nice.  I'll check that out when I get home.  Thanks Frak :)

---

