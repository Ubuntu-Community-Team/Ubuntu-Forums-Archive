---
title: "Installing first download"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by phr0ze on 2006-08-29
I downloaded the DEB package for FreeCiv. I was pretty excited. Then I found out it requires Libasound2. So I download that package and ran it. Then I find out it needs lib6c... well that one has more dependencies too. 

What am I missing, or does it really take all of this to install one package? I realize this is not really Ubuntu's problem.

---

### Post by o_fortuna on 2006-08-29
> **phr0ze said:**
> I downloaded the DEB package for FreeCiv. I was pretty excited. Then I found out it requires Libasound2. So I download that package and ran it. Then I find out it needs lib6c... well that one has more dependencies too. 

What am I missing, or does it really take all of this to install one package? I realize this is not really Ubuntu's problem.
I think you can install Freeciv much more easily by either

a) click Applications->Add/Remove, then type Freeciv into the search box. Check it; install.

b) click Applications->Accessories->Terminal and enter this command:

```
sudo aptitude install freeciv
```

c) Open the .deb file with gdebi package installer (usually by double clicking, but you might need to right click and select "Open with..."). This usually takes care of dependencies automatically.

A) is the easiest, B) is the fastest, and C) isn't really necessary.

---

### Post by Toxicity999 on 2006-08-30
Atleast with debian based distros games for one are broken up into enviroment specific binarys (freeciv) and platform independant data (freeciv-data) Just for future reference. You'll be amazed what the repositories hold, always skim them first.

---

### Post by phr0ze on 2006-08-30
> **o_fortuna said:**
> a) click Applications->Add/Remove, then type Freeciv into the search box. Check it; install.

I browsed through all the games in add/remove and didn't see it. So there are more games in add/remove but they aren't listed, you just need to know what they are called?

> **o_fortuna said:**
> 
b) click Applications->Accessories->Terminal and enter this command:

```
sudo aptitude install freeciv
```
.

I'll try this at home tonight.

> **o_fortuna said:**
> 
c) Open the .deb file with gdebi package installer (usually by double clicking, but you might need to right click and select "Open with..."). This usually takes care of dependencies automatically.
.

I'm pretty sure I was opening it with gdebi. This is the program that kept telling me what part I was missing, and the install button was greyed out because of the missing dependency.

Thanks for all the help, I'll try the top two options. 

I am pro linux and anti-microsoft but I have been stuck in microsoft's world for many reasons. While looking at linux I see the most talked about issue is 'why more aren't switching,etc'. As a newbie to linux/ubuntu, I'm starting to see some of the reasons which long time linux fans may not see as well because they have been in it too long. I don't want to turn this into a debate, but I'd like to try to help remove some of the newbie frustrations.

Thanks,
John

---

### Post by PPAAUULL on 2006-08-30
You could use synaptic. That is what I use to install a lot of my programs.

---

### Post by PPAAUULL on 2006-08-30
Oh and it even takes care of the dependencies for you.

---

### Post by anaconda on 2006-08-30
> **phr0ze said:**
> 
'why more aren't switching,etc'. As a newbie to linux/ubuntu, I'm starting to see some of the reasons which long time linux fans may not see as well because they have been in it too long.


I have been trying to convert few people to ubuntu, and it is really frustrating, when they assume that they shouldn't have to learn anything.. because they already can do something in windows. I mean how can ANYTHING change with zero effort & zero motivation..  Having said this I think some things might be made a bit easier.. 


Oh. And I would also recommend the synaptic GUI installer.. or aptitude  (both work fine if you have updated your sources.list -file (repositories))

I think the add/remove applications is only for adding already installed aplications to menu.. might be wromg..?

---

### Post by mcduck on 2006-08-30
> **anaconda said:**
> 
I think the add/remove applications is only for adding already installed aplications to menu.. might be wromg..?

No, it can actally install all those apps that are listed there, as long as you have a working internet connection. It's a frontend to apt-get, just like Synaptic is.

The Alacarte Menu Editor is for adding apps to Gnome's menu :)

---

### Post by Tomosaur on 2006-08-30
Considering this is your first download, you may need to enable a few more repositories. To do this, open up a terminal (command line: Applications > Accessories > Terminal) and type:
```

sudo gedit /etc/apt/sources.list

```

Use the instructions in that file to uncomment the extra repositories (remove the # to uncomment), save, and exit.

Re-open the Add/Remove program, and try searching for FreeCiv again.

---

### Post by phr0ze on 2006-08-30
> **anaconda said:**
> I have been trying to convert few people to ubuntu, and it is really frustrating, when they assume that they shouldn't have to learn anything.. because they already can do something in windows. I mean how can ANYTHING change with zero effort & zero motivation..  Having said this I think some things might be made a bit easier....?

The whole reason I'm in linux/ubuntu is to learn it. I'm not saying I'm not willing, but your average computer user is not going to find a forum, register and search/post questions. I really think it is important to make this as easy and intuitive as possible. The whole point of me bringing up this difficulty with moving to linux is so it can be improved. I expected there to be a learning curve. With one of my earlier experieces with linux (Suse I think.) I had to modify and compile a network driver to get my network card to work. So things are much better.

---

### Post by Toxicity999 on 2006-08-30
you don't need to find it... the first thing any new user will do is survery the new gnome environment, then play with the application tabs. Eventuall open the system tab and see help... then 'community support' And they say that's what I need! then they find us. How about rephrasing that to any user intelligent enough to operate a mouse will find our forum. And be able to read enough to see a search button or the Beginner forum... there you go... If you can find one icon to click in the most simple of places then there's not much you could accomplish on a computer... I mean I know by chance someone might just not find that but in any case they found the OS on the site where the information is, or a knowledgable friend hooked them up. Even perhaps they picked it up with the Ubuntu book. My point being there's always a ready entry point in any recruitment case.

The 'Average' Computer user is referred here by someone who is above average.

---

### Post by phr0ze on 2006-08-30
Nevermind. I was just trying to help.

Thanks for the info all about using other sources for applications.

John

---

### Post by Tomosaur on 2006-08-30
> **Toxicity999 said:**
> 
The 'Average' Computer user is referred here by someone who is above average.
Way to be leet.

An average user is an average user. Above average is above average. There's absolutely no need to try and sound smarmy.

---

