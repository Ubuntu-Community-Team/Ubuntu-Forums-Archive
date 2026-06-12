---
title: "VBox guest additions install problem"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by Stingray23 on 2007-07-24
I am having a problem getting guest additions to install. I am new to linux and cannot figure out how to solve this problem

I am running WinXp as the host and Ubuntu Feisty is the guest. When I mount Guest Additions I get an icon on the desktop. I double click VBoxLinux Additions.run, I get a message that says 

"Could not open the file /cdrom/VBoxLinuxAdditions. run using the unicode (UTF-8) character coding

Any help is greatly appreciated

Stingray

---

### Post by gaylapdancer on 2007-07-24
Is it opening the file in gedit or something similar?

---

### Post by Stingray23 on 2007-07-24
Yes it is.

---

### Post by starcraft.man on 2007-07-24
> **Stingray23 said:**
> Yes it is.

Easy fix. Copy it to the home folder (the home folder is the first entry in the places menu) and then open up any terminal (Applications > Accessories > Terminal), and type this in:

```
sudo ./VBoxLinuxAdditions.run
```

Then it will run the script answer with the default answers. For more information on the terminal, read the far left link in my sig, blue one will explain installing in Ubuntu. Good reads.

Hope I got that right, haven't done vbox in a week or so...

---

### Post by Stingray23 on 2007-07-24
I tried that and received the following message:  command not found

---

### Post by starcraft.man on 2007-07-24
> **Stingray23 said:**
> I tried that and received the following message:  command not found

Whuups, sorry. Remember to copy all the files (should be 6 I think) from the CD to the home folder, the run file is just a script that installs the drivers on any linux distro. If you did copy all the files from the CD to the same place, you must be in wrong directory. To understand directories and how to navigate in the terminal please read [this page]("http://www.linuxcommand.org/learning_the_shell.php") (lessons 1 2 and 3 in particular) then use the ls command to make sure all the files you copied are in the directory your working in. If they aren't (or your in the wrong directory) use the cd command to move to the right one. Once you get that sorted, run the command again.

The site explains the basics very well. I know it seems a bit of a pain, there are easier ways to install things in Linux in general but VBox uses the .run file because it can be universally installed on all distros from the terminal (where as if it was packaged it would only run on those compatible with the package type).

---

### Post by Stingray23 on 2007-07-24
I understand navigation in Linux, but I read the links posted to make sure.

I am in the /home/user_name folder. I still get the message that the command can not be found.
All 6 files are my home folder. 

In the terminal I have also navigated to the home folder...Still no luck

---

### Post by starcraft.man on 2007-07-24
> **Stingray23 said:**
> I understand navigation in Linux, but I read the links posted to make sure.

I am in the /home/user_name folder. I still get the message that the command can not be found.
All 6 files are my home folder. 

In the terminal I have also navigated to the home folder...Still no luck

Ok two seconds, I must be giving you wrong command. I'll go pop it open and give ya the right one in a minute... been a while.

---

### Post by starcraft.man on 2007-07-24
LOL! Silly me, I just popped open the manual and realized I forgot the sh bit. Here is the command you want to issue in the home directory:

```
sudo sh ./VBoxLinuxAdditions.run
```

That should do it, oh and the manual with all the common questions answers is [here]("http://www.virtualbox.org/wiki/Downloads") on the downloads page at the top.

Have fun with VBox. :)

---

### Post by Stingray23 on 2007-07-24
That worked!

Thanks for your help

Stingray

---

### Post by starcraft.man on 2007-07-24
> **Stingray23 said:**
> That worked!

Thanks for your help

Stingray

Your welcome. I just feel silly forgetting the command as I've used it a hundred times. Have a great time with the VM and feel free to visit the VBox forums ( Community tab of the main page) for any other questions or specific problems/bugs.

---

