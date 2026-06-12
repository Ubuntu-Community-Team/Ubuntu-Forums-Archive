---
title: "Help with ClamTK"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by nike007 on 2007-07-02
Hi there i am newbie and just recently installed Kubuntu 7.04 I found it really cool just wanted some help with clamTK well when i open clamtk to scan it says [I]Unable to view ClamAV's information file.
This will affect
how ClamTk views the number of viruses and version information[/I].it says then You do not appear to have virus definitions!

Running "freshclam -v" as root may fix the problem i dnt know anything about how to login to root and how to fix this problem 
regards

---

### Post by Outrunner on 2007-07-02
You do not login as root in Ubuntu. You use 'sudo' before a command to get temporary root permissions
```

sudo freshclam -v
```

Also note that you have to use 'gksudo' if you want to run a graphical app as root

---

### Post by nike007 on 2007-07-02
where do i enter this code

---

### Post by Outrunner on 2007-07-02
Applications -> Accessories -> Terminal

---

### Post by nike007 on 2007-07-03
hey there with your help i was able to update thanks a  lot
any idea on how to fix this problem " Unable to view ClamAv's information file"
regards 
nike007

---

### Post by RomeReactor on 2007-07-03
Hi. It seems that's a [bug]("https://bugs.launchpad.net/ubuntu/+source/clamtk/+bug/90790") with ClamTK; for now, you can launch it from Konsole like this:
```
kdesu clamtk
```
Or you could install **Klamav**, which is a frontend for ClamAV that will better integrate with your KDE desktop. It's available through Adept, or from the command line:
```
sudo apt-get install klamav
```

---

### Post by nike007 on 2007-07-06
thanks a lot 
i installed KlamAv you were it gels better with KDE

---

### Post by nike007 on 2007-07-06
i mean right

---

### Post by RomeReactor on 2007-07-06
Glad you got it working!;)

---

### Post by nike007 on 2007-07-06
and is apt get available for kubuntu if so could you give me the code for installing it
---------------------------------------------------------------------------------------------------------------------------------------
ubuntu has got my interest back in computers....

---

### Post by RomeReactor on 2007-07-06
Sure, apt-get is available in all Ubuntu versions (Ubuntu, Kubuntu, Xubuntu) and is already installed (it's part of the default programs that come with the system); to install programs with it, open a Konsole and enter:
```
sudo apt-get install PACKAGE_NAME
```
It might be a little difficult to use at first, since you need to know the name of the program or library you want to install before actually installing it. If you use Adept (I think it's in **K-menu->System->Adept Package Manager**), you can search for key words which will make finding the program you want easier.

---

### Post by nike007 on 2007-07-06
ok now i understand that adept manager and apt get are the same btw i know about adept manager thanks

---

### Post by kitterma on 2007-07-12
sudo apt-get klamav

Don't bother with the current clamtk in Feisty.  It doesn't work with the current clamav.  I've requested a backport from Gutsy, but it's basically useless for now.

---

