---
title: "vim how is it different compared to other distributions?"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by vicky.irobot on 2007-11-23
I have been using opensuse 10.3 and recently moved to Ubuntu 7.1

I find the vim to be different compared to the one I have on 10.3.

For example the vim in ubuntu doesn't recognize 'color' in .vimrc file and also when I have opened multiple files using one vim and when I do 'ls' from command mode I should be able to see the list of files that are currently opened by vim but it can't find the command!!!!

The vim version that has come with Ubuntu is the latest one but when these restrictions?

Anyone know a fix for this or how to enable the full featured vim?

---

### Post by LaRoza on 2007-11-23
```

sudo aptitude install vim-full

```

I don't know why Ubuntu doesn't have this by default.

---

### Post by vicky.irobot on 2007-11-23
Cool. thnxs a lot.

It was quite a fast response, never experienced this fast response till now.

---

### Post by LaRoza on 2007-11-23
> **vicky.irobot said:**
> Cool. thnxs a lot.

It was quite a fast response, never experienced this fast response till now.

You only have four posts...

It is four in the morning here, Thanksgiving has really get me awake. Mountain Dew, no doubt.

Any particular reason you left openSUSE?

---

### Post by vicky.irobot on 2007-11-27
reason for moving from opensuse
> yes the major reason was for my wireless card. I needed to configure this thing manually and at times I find that after a while the wireless connection is down. It took me quite some time to get my wireless up
> next I had installed compiz on my machine and the effects were good but every time I see that after a while my bottom task bar is hung, I can't access anything there.
> after I finish installing suse I need to do a few manual interventions to get my system set up like for 10.3 I had to do the below changes
   1. grub needed some changes to load vista from dual boot
   2. fstab needed changes to write permission on NTFS
   3. had to download the win98 driver and setup that up for my netgear wireless using ndiswrapper
   4. after installing nvidia graphics i found my graphics session to not working and I found that some of the files needed to be edited to make these the graphical login back up.

It is frustrating that you spend so much time on these settings. I am more interested in having a desktop which will run smoothly after install and I need something rugged and which will help me migrate to Linux completely.

SuSE also has a lot of plus points which I like a lot.

My first taste for Ubuntu was when I had crashed my machine and nothing was coming up I booted from Ubuntu live cd and accessed the internet and got solutions to my problem. That was something really cool I like about Ubuntu. You actually don't waste the time when the installation is happening. After that I got these latest Ubuntu cds sent across to me and I thought I give it a try and found it to be excellent. The interface was quite smooth and found a few things very intelligent.

One thing I didn't like about Ubuntu was the grub loader compared to the SuSE one. Surprisingly the loader that come during Ubuntu installation in amazing. Wondering that wasnt brought in here. have to look at options where I can see the SuSE grub loader and bring the similar changes here.

---

