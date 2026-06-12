---
title: "Ubuntu won't install any more."
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by Teddy_P on 2007-04-29
I have had edgy on this computer for a long time and it has been working great.
I wanted to play with Kubuntu (edgy) and it also worked good . I made a lot of changes and decided that I was going to try 7.04 and I did not want to down load a disk the first weekend because I figured that's what everyone else was doing. So I reinstalled (edgy) with the hopes to upgrade to 7.04.
Well that's where all the troubles started. I found my CD with ubuntu Edgy on it and started to install. Every thing was going good; I answered all the questions and chose a full erase of hard drive. It was working and stalled at 6%. I tried it a couple more times and still nothing.
Then I put it onto one of the kids computers and it worked, so the CD is fine.(I also checked the CD from the menu but I wanted to make sure.

I installed a command line system and it works (but I don't know anything about that stuff).
Then I tried to install a couple more times and I keep leaning to the Nvidia Vanta-16 Card because sometimes I can here the ubuntu starting. I typed the password and I got blue and black lines across the screen going up and down. If I push Ctrl + Alt + F1 I get back to the command line.  
Then I down loaded a 7.04 CD and it stalls at 46% but I am on line and writing this form the 7.04 live CD and every thing seems to be working fine.

I am at a loss of what to try next.
What should I do?
Why can I see a command line but not the desktop?
And why can I use the live CD for Fiesty but not install?
And the big one:
is there any meaning to Edgy stalling at 6% and fiesty stalling at 46%?


Computer is:
Compaq Evo
1.8 with 256 ram


Thanks
Teddy

---

### Post by aberry5555 on 2007-04-29
Although you've managed to install on that system before it's more than likely that you havnt got enough RAM (256MB is quite a small amount to both run and install an operating system at the same time). Do you happen to have any more RAM you could put in your PC?

---

### Post by Teddy_P on 2007-04-29
I am going to try this next I don't know why I didn't find it in my searches.
[http://ubuntuforums.org/showthread.php?t=427585](http://ubuntuforums.org/showthread.php?t=427585)



Teddy

---

### Post by Teddy_P on 2007-04-29
> **aberry5555 said:**
> Although you've managed to install on that system before it's more than likely that you havnt got enough RAM (256MB is quite a small amount to both run and install an operating system at the same time). Do you happen to have any more RAM you could put in your PC?

The edgy install was and alternative I was going to wipe any thing that was on there and just install.
What do you think of what I was going to try next?



Teddy

---

### Post by Teddy_P on 2007-04-29
I found an edubuntu edgy CD and installed a comand line system.

I first 
 ```
sudo aptitude update
```

Then 
```
sudo aptitude upgrade
```

And it updated and upgraded.

Can I install the gnome desktop to this?

And then upgrade to fiesty?


Teddy

---

### Post by Teddy_P on 2007-04-29
> **aberry5555 said:**
> Although you've managed to install on that system before it's more than likely that you havnt got enough RAM (256MB is quite a small amount to both run and install an operating system at the same time). Do you happen to have any more RAM you could put in your PC?

I do not have any more memory around now I will call around and see if I can find anyone that does.

Thanks
Teddy

---

### Post by wgscott on 2007-04-29
Hi Teddy:

You should be ok with that as memory.

If you want to upgrade to feisty, you will have to edit the file /etc/apt/sources.list, and substitute feisty for edgy.

Here is a one-line command that will do that and make a backup:

```
perl -pi.bak -e 's|edgy|feisty|g'   /etc/apt/sources.list
```

Then issue the following:

```


sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install xubuntu-desktop

```

or kubuntu-desktop
or ubuntu-desktop

If you are worried about memory, use xubuntu.  You can still run any kde or gnome application that suits you .  It is my personal favorite.

---

### Post by wgscott on 2007-04-29
If you are root, (the # prompt) you won't need to use sudo.

---

### Post by Teddy_P on 2007-04-30
After the update and upgrade:
 I did

```
sudo aptitude install ubuntu-desktop
```

Then System > Administration > update manager

I did not have any updates to do because I had just did them earlier.

Then I clicked the upgrade to Fiesty 7.04 

Now every thing is working and I am off to automatix to get the rest of the stuff I need.

Thanks for all you help

Teddy

---

