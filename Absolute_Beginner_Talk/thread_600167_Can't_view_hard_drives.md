---
title: "Can't view hard drives"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by Iamshiznaki on 2007-11-02
I'm new to linux, this is my first install. When I used the live CD I could see, but not access the drives. I thought nothing of it and went ahead with the install. It went without a hitch, I used the no-partition option, I didn't want windows anymore. Now I can't view either drive. I have a laptop with a 40 gig and a 20 gig hard drive in it. It appears to have lumped the two drives together maybe? I can't manipulate files at all, they are all locked. How do I view these files? I read about mounting, but I get all sorts of strange errors. I'm really frustrated here and this is kind of ruining linux for me.

Please help.

---

### Post by gsiliceo on 2007-11-02
sudo aptitude install ntfs-config
Then you can find a tool for that in the menu.

---

### Post by Hospadar on 2007-11-02
the hard drive you installed linux on is just going to be your "filesystem" It won't show up as a drive like you would expect it to in windows.

If your other drive is formatted ntfs, you could install ntfs-config, (and then run "sudo ntfs-config" from a command line), or you could use gparted (installable through synaptic) to just format it ext3.

---

### Post by ozylog on 2007-11-02
run terminal and enter command: sudo apt-get install ntfs-config

---

### Post by Iamshiznaki on 2007-11-02
I get this error
> E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

How do I use Synaptic to install GParted?

---

### Post by rudeboyskunk on 2007-11-02
You must have another program running using the package management system.

Go to System>Administration>Synaptic Package Manager.  Make sure no terminal is downloading/installing a program or that you are not doing the "system update" (little orange icon on your taskbar) when opening synaptic.

Once in Synaptic, just do a search for "gparted."  It'll come up.  Then, once it's installed, you'll find it in System>Preferences (or maybe Administration)>GParted (or maybe called Partition Hard Disks or something like that).

---

### Post by Iamshiznaki on 2007-11-02
When I run a search for it, gparted does not come up. I get no search results.

---

### Post by rudeboyskunk on 2007-11-02
Make sure all your repositories are enabled.  Close Synaptic and go to System>Administration>Software Sources and make sure universe, multiverse, etc etc are all checked off.  Then click Apply.  Then redo your search.

---

### Post by Iamshiznaki on 2007-11-02
Okay I got gparted to work. Now it shows three things, all of which are locked. I can't do anything from here.

What now?

---

### Post by rudeboyskunk on 2007-11-02
What are the three things called?  Can you provide a screenshot?  does GParted ask for your root password when you try to open it?

[This should help some too.]("http://www.howtoforge.com/partitioning_with_gparted")

---

### Post by Iamshiznaki on 2007-11-02
[IMG]http://img217.imageshack.us/img217/6210/screenshotdr5.png[/IMG]

It did not ask for the password upon running it.

---

### Post by rudeboyskunk on 2007-11-02
Ok, up at the very top on the right, where it says /dev/sda.  See that?  Click on that and there should be an option for /dev/sdb.  That's your other hard drive.  Then you can format that one and set it up however you want.  If it's locked, look for an option in one of the menus for "unlock" or "edit" or something along those lines.  If it does not let you do anything at all, go to a command line, type "sudo gparted" and then it should allow you to do whatever you desire.

---

### Post by Iamshiznaki on 2007-11-02
When I click /dev/sda no other options appear, as if I don't have another hard drive?
Maybe I can partition part of the first drive off for storage?

Thanks for all of this help by the way.

---

### Post by rudeboyskunk on 2007-11-02
Ok, I just reread your original post, and now it really does appear that your two hard drives are lumped together somehow.  ODD.  Unless you originally had only one and Windows tricked you into thinking you had two (unlikely, since you probably installed one yourself).

Well, if you ever want to install another OS you can just partition sda.  Looks like you have plenty of space.

I have no idea what's happened though.  Hopefully somebody more knowledgeable than I will come along.

---

### Post by Iamshiznaki on 2007-11-02
I did not install both hard drives to it's very likely that's what happened. So I should get a new hard drive if I want storage, right?

---

### Post by rudeboyskunk on 2007-11-02
If you want, you can just do what you suggested earlier and partition the one you have now.  Then use that.  Save some $$$.

---

### Post by Iamshiznaki on 2007-11-02
So I should reinstall and have it partition upon install, correct?

---

### Post by rudeboyskunk on 2007-11-02
You should be able to partition it now with no problem.  If I'm wrong, somebody please tell me.

EDIT:  But if you do a clean install, you could name the new partition /home, not only giving you a ton of storage, but making your computer run a tad more efficiently.

---

### Post by Iamshiznaki on 2007-11-02
Well gparted won't let me partition, so a fresh install it is.

See you in a half hour-ish.

---

### Post by Officer Dibble on 2007-11-02
What was on the other drives/partitions? Is there anything you DON'T want to lose there?

---

### Post by Iamshiznaki on 2007-11-02
Having more problems. I partitioned the disk to allow for 15g filesystem. Then I used Gparter to format the rest as ext3. It tells me that I don't have permission to access the drives now. 

Help?

---

