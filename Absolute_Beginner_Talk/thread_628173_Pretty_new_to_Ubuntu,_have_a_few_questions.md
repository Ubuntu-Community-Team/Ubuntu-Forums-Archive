---
title: "Pretty new to Ubuntu, have a few questions"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by Aseld on 2007-11-30
I just started using Linux as my primary desktop operating system, and I have a few questions:

1. How can I change my sound device in KDE? I've figured out how to change it for certain individual programs, such as Audacity, but I'd like to be able to change it globally as well. I have an onboard sound device as well as a USB headset.

2. Is there any way to list hard drives and available disk space from the command line?

3. I've seen varying opinions on this - which is better to use, in general - aptitude or apt-get? Why?

4. I know it's not really an Ubuntu question, but I thought seeing as I was posting this anyway I may as well put it here - feel free to ignore it. Is there a way to receive a sound alert when a message is received in Kopete? I'm on the verge of switching to Pidgin at the moment if I can't find a way. 

Thanks a lot :)

---

### Post by Inxsible on 2007-12-01
2) ```
 df -h
```

3) doesn't matter at all. Initially apt-get didn't take into account the dependencies whereas aptitude did. But this was long ago...Since the last 4 versions of Ubuntu i think, apt-get and aptitude do exactly the same thing.

---

### Post by High Camp on 2007-12-01
Howdy

I can't answer all your questions but I can answer some.

1. No idea, I run Xubuntu were you don't have to worry about such things.

2.  You can see all the drives attached to you system by typing the command “ls /dev/hd*” or “ls /dev/sd*” depending on which type (IDE, SATA, etc.) the drives are. On the example system the result of this command looks like “/dev/hda /dev/hda1 /dev/hda2 /dev/hdb /dev/hdb1” The operating system is installed on hda, which has two partitions (hda1 and hda2), and there is one partition on hdb and hdb 
(copied from [http://www.ehow.com/how_1000631_hard-drive-linux.html](http://www.ehow.com/how_1000631_hard-drive-linux.html))
If you're looking for information about your hard drives consider Conky
If you're looking to partition your drives consider Gparted

3. I personally use apt-get because I can't spell aptitude. I have never seen an opinion either way on what's better.

4. I would imagine you could set up Kopete to run a program when a chat message is recieved (you can in Skype) and then you would set up a shell script that plays a system sound. It would be simple but I can't remember the name of the program that plays system sounds so I will look into it.

Hope that helps,

---

### Post by Aseld on 2007-12-01
Okay, thanks people.

---

### Post by SunnyRabbiera on 2007-12-01
both apt get and aptitude are pretty much the same, the difference is that aptitude is a little more like a gui then a command line app.
its still something you do in a terminal but its relitivly simular to synaptic the default gui package manager in ubuntu.
really there is no difference though

---

### Post by monte48lowes on 2007-12-01
kopete > Settings > Configure Notifications...

You can set sounds for almost anything.

Mike

I use adept to browse for new packages. It's easier for me to look for new things or since some packages have different names than their commands (ie kmymoney is listed as kmymoney2 in adept), Also it is useful to see what is going to be removed when you uninstall a package. I have accidentally removed kde by using apt-get. In adept I can use the filter to see what is going to be removed if I Apply Changes.

---

### Post by Aseld on 2007-12-01
Okay, thanks. Sorry about Kopete, I was certain that I'd tried that, but I guess not. Works perfectly now.

---

### Post by monte48lowes on 2007-12-01
Awesome! :guitar:

Check out the kubuntu forums as well. [http://www.kubuntuforums.net/forums/index.php]("http://www.kubuntuforums.net/forums/index.php")

Mike

---

