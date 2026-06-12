---
title: "Data Recovery the PITS!"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by boardfoot on 2008-04-06
Sorry for the title, but I noticed a mild assumption of bashing the OS brings the experts in droves.

Here is my problem:

1) Relatively new to Linux and Ubuntu but LOVING it. (I dropped all Windows on my machines as a result of this OS)

2) It would seem that the HardDrive on my antique laptop is finally calling it quits. Bad Sectors have invaded in droves and I cannot boot to desktop or anywhere else for that matter as a result (fsck is burping and farting in between chokes of smoke)

3) I have my install CD handy so I figure "God bless Linux and Ubuntu for this disk!" I figure I can boot in with CD and access all of my data (that is recoverable) through nautilus and dump it to my external Hard Drive and recover it back when I bring home the new 17" Ferrari later today.

All was going wonderfully well up until the point where I started to investigate my bookmarks and email data.

WHAMO!

So I am booted from CD and thus logged in as ubuntu by default. I go to access (backup) my hidden folders in my home Dir and I get permission problems.

My problem is that I am recovering from CD mode where I cannot log in as anything else other than ubuntu... or can I? I guess that is the question.

Now before the experts start sending me to terminal and bashing out voodoo magic code (I know its coming and I will appreciate it to be sure) I left with a bit of a Hmmmmffff

At risk of sounding like I'm bashing the OS, I'm hoping we could also engage in a small discussion (to keep it fresh LOL).

It has occurred to me (and I understand why it is the way it is completely) that if we can sudo in the terminal, why can't we sudo in nautilus?

This is where y'all are going to think I'm bashing the OS. I'm a windows victim of MANY years. I can even boast the saying "I predate microsoft" in my computing experience. I understand the reason root is not allowed on the harddrive boot and on the cd (security.... duh) and thank goodness for that. However, the sudo is also a really nice work around for issues such as mine. So why can't we emulate root as sudo in a desktop environment instead of having to use the terminal.

In all honesty, I think this little morsel would solve a LOT of support posts, allow a LOT of former windows victims some intuitive GUI recourse and would almost single handedly remove the requirement for new users to even touch the terminal.

I'm sure there is a good reason why, I'm hoping someone can fill me in on it just after they post voodoo magic terminal code to solve my dilemma that is inches from the finish line.

Thanks in advance.

---

### Post by Moop on 2008-04-06
You can sudo in nautilus. ```
gksudo nautilus
```

---

### Post by Hospadar on 2008-04-06
there's actually a plugin for nautilus to right-click open something as root.  check out "nautilus-gksu" in synaptic I think it might require a restart of gnome to make it pick it up.

If you don't see it in a file's right-click menu right after you install it, do a ctrl-alt-backspace to restart gnome, and then it should work fine.

---

### Post by boardfoot on 2008-04-06
Thanks for the attempted reply... but neither will or did work.

1) gksudo nautilus doesn't allow me to browse outside of the OS. Meaning... because I am loading the OS from the CD I cannot see or get to the Hard Drive. I can see the filesystem no problem, but not the drives I need to access as root.

2) That extension does not work for me because I cannot install it. I am booting from CD remember. I have nowhere to install it to.

Does anyone else have any suggestions? I do appreciate the feedback and thanks for taking the time.

Big question here is how do I access my data in hidden folders on the HDD when I have to boot up the OS with the CD? I can get all the other data... just not my email (thunderbird) and my bookmarks (mozilla).

I really need those emails...

Thanks for any further help. I feel like I've painted into a corner with these permission issues.

---

### Post by boardfoot on 2008-04-06
OK... so I'm a noob and I figured out that I can browse to /media/disk/blah blah

I can browse to the hidden folders. I can copy those hidden folders (YIPPEEEEEE!)

I go to paste them onto my external HDD (which detects/etc just dandy...) WHAMO!

I can't access that external drive anymore...

What gives? I'm so close... yet so far...

Any ideas why I can browse the external HDD in vanilla nautilus, cut paste vanilla files/folders, etc. but can't paste as root in gksudo nautilus?

This permission thing (although I understand it and why it is)  is really reaping havoc right now.

Thanks for any help.

---

### Post by bsharp on 2008-04-06
check if the external is mounted
```
sudo mount
```

and post the results.

---

