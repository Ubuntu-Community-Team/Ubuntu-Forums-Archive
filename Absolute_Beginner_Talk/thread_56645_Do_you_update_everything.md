---
title: "Do you update everything"
date: 2005-08-13
forum: Absolute Beginner Talk
---

### Post by Irony on 2005-08-13
Now I've modified my /etc/apt/sources.list file to include backports and other repositories I've noticed that there is a whole bunch of new updates (41).

What is the common practice here, do people just update everything to get rid of the red symbol. How do they undo updates that might mess with their computer.

And what about unauthenticated updates - do people restrict themselves to authenticated updates unless they have a need for particular programs.

If they don't update doesn't the list just get bigger.

Unlike updates in windows these updates also include updates to things like gimp, so is updates a security thing just telling me that certain programs can be updated - can I just untick all updates by default.

---

### Post by sapo on 2005-08-13
NO!

I just update something that:

1 - the currenty version isnt working properly

2 - I want some feature that i can just use if i install the newest version

If my answer was YES to the 2 question i would install.. if not i would leave the current version :p

I have a bunch of updates here to install.. but i dont install any of them.. why update gimp if i just use it to cut and convert some images from png to jpg or something like it? Why do i need the lastest version? i dont need it.. the current fits my needs perfectly :p

---

### Post by aysiu on 2005-08-13
I took that red symbol off my panel long ago. Occasionally I'll "mark all upgrades," but usually I just upgrade my Firefox.

---

### Post by PeP on 2005-08-13
Yes I do update everything, sometimes it brokes something but it is very unusual for I use only official repositories for hoary.

The main advantages of this is to get the fixes from hoary-security.

---

### Post by Irony on 2005-08-13
So its not really like windows update. I think I'll install stuff if I need it, I prefer it that way because if something goes wrong I know why. Having said that when I updated Firefox it enabled me to install flash.

I assume these updates are visible in synaptic (the stars?). Couldn't see how to remove the red warning symbol from the panel.

---

### Post by GavinX on 2005-08-13
I use Breezy and I just update everything as they come. However, the trick it to only install the things that you really use. Therefore when it's update time, only the apps which you have installed from the very beginning are updated. As a result, only what I use is on my system and they're in the latest versions!

---

### Post by PeP on 2005-08-13
[QUOTE=Irony]So its not really like windows update. I think I'll install stuff if I need it, I prefer it that way because if something goes wrong I know why. Having said that when I updated Firefox it enabled me to install flash.

I assume these updates are visible in synaptic (the stars?). Couldn't see how to remove the red warning symbol from the panel.[/QUOTE]
it is far more powerfull than windows updates, as such it might shake a little bit your system or break it depending on what repositories you use.

---

### Post by GreyFox503 on 2005-08-14
You guys bring up a good point.  Coming from the Windows world, I know the importance of getting all the security patches.  So whenever any update icon pops up in the system tray, my cursor flies there like a hawk!

Maybe that was good practice in Windows, but perhaps not necessary with Ubuntu.

---

### Post by bjweeks on 2005-08-14
I always update everthing but I removed main and restricted from the backports.

---

### Post by Slugger on 2005-08-14
I havent got to update ubuntu yet because I havent got internet access to the computer. As soon as I get internet I will be updating asap

---

### Post by Irony on 2005-08-14
There seem to be types of updater, those who update everything and those who update what they feel they need.

Interestingly no one has mentioned that they update for security reasons.

---

### Post by manicka on 2005-08-14
Usually if the repo is stable then I'll update everything that comes along. I find backports very reliable and include it in all my upgrade routine. 

My main exception is backports-staging, which I turn on only when I want a specific package.

Other than that I install all updates

---

### Post by sophtpaw on 2005-08-14
[QUOTE=Irony]Now I've modified my /etc/apt/sources.list file to include backports and other repositories I've noticed that there is a whole bunch of new updates (41).

What is the common practice here, do people just update everything to get rid of the red symbol. How do they undo updates that might mess with their computer.

And what about unauthenticated updates - do people restrict themselves to authenticated updates unless they have a need for particular programs.

If they don't update doesn't the list just get bigger.

Unlike updates in windows these updates also include updates to things like gimp, so is updates a security thing just telling me that certain programs can be updated - can I just untick all updates by default.[/QUOTE]
 Its interesting that you brought this question up. I didn't realise everyone had a different style.
Personally, it is more peace of mind to update everything. I could remove the red tab but i like to know that there is a more recent version of something. Even if it is for simple tasks that a newer version is not necessary, as someone said, it doesn't hurt either to have the latest, plus should requirement dictate you can always operate knowing you have the latest. Useful for questions and answers.

The trick is like GavinX says to only have those apps installed that one wants and uses. Then wouldn't you want to have the latest version?

--
sophtpaw

---

### Post by ozzie123 on 2005-08-14
I always update everything when the red icon shows up. It does, however, consumes quite alot of time and because of that, I only update when the computer is off duty (e.g. late night).

I always includes the backport repo to update because I use alot of programs from there and it's convenient to know that your box is up-to-date :)

---

### Post by phen on 2005-08-14
because updating is soo easy and comfortable under linux, i update everything allways. never had problems thereafter. You do not need to close any apps, you do not need to reboot, you can put synaptic to a not used workspace. and it makes me feel productive :-)

---

### Post by TristanMike on 2005-08-14
This is a good thread as the questions posed have been in the back of my mind too.

In Windows I update as soon as they become available. Since installing Ubuntu, I have kept the same practices, that is updating pretty much anything they give me (critical updates and such). I was always curious on proper Linux/Ubuntu update etiquette. I figured that it would only update those things that I had installed and not everything in my repos. But, I seem to always have 1 update left, the python-xdg package that everytime I install freezes my Add/Remove menu and I have to go and force Original Version. This makes me question the proper use of the updates as well.

---

### Post by Trojan1313 on 2005-08-14
I update everything, I like having the latest version of everything. I see no reason why I SHOULDN'T update.

---

### Post by KageKeeper on 2005-08-14
Yes, I agree. 

I also update everything. I see no reason not too quite honestly. :)

---

### Post by xequence on 2005-08-14
Accidently I did. Took an hour and was 152 mb :P I was only going to update firefox.

Unlike windows, which has a new virus/spyware/etc update every week, linux (as far as I know) doesent need them.

It is ultra conveinent to do one command and let it do everything for you though :)

---

### Post by trash on 2005-08-14
I'm glad this came up, I actually think the updater should ONLY ever update from main and security, as it did happen once that i forgot that i enabled universe and multiverse and went ahead with an update... i was lucky nothing broke but i can easily see new users getting into trouble with this.

I think the updater installed with a system should read from a different file than the sources.list with ONLY the sources of the original install, but i guess this could be hard to do.

---

### Post by Trojan1313 on 2005-08-14
[QUOTE=trash]I'm glad this came up, I actually think the updater should ONLY ever update from main and security, as it did happen once that i forgot that i enabled universe and multiverse and went ahead with an update... i was lucky nothing broke but i can easily see new users getting into trouble with this.

I think the updater installed with a system should read from a different file than the sources.list with ONLY the sources of the original install, but i guess this could be hard to do.[/QUOTE]
 But some users, like me, want the latest of everything.
I could agree with an updater where you can choose wich things you want.

---

