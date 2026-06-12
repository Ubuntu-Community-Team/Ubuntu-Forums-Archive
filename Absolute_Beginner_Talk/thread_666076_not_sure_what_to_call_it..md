---
title: "not sure what to call it."
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by joemacnz on 2008-01-13
I have a problem, however, while I have searched the forums for something similar, I don't really know what the problem is. I am intimate with the symptoms though!!

To start with firefox freezes for a couple of minutes,and then disappears off the screen.
Next I try to get the terminal.(I have the windows button set to bring it up)
Nothing happens
Then I click on "accessories" and the whole top and bottom bar disappears.
This leaves me with no recourse to do anything really(as far as I can see)

I have tried all the 'F' buttons. I have tried all the buttons in fact.

Also, my screen saver has disappeared 

Can anyone help please?

---

### Post by kostkon on 2008-01-13
> **joemacnz said:**
> I have a problem, however, while I have searched the forums for something similar, I don't really know what the problem is. I am intimate with the symptoms though!!

To start with firefox freezes for a couple of minutes,and then disappears off the screen.
Next I try to get the terminal.(I have the windows button set to bring it up)
Nothing happens
Then I click on "accessories" and the whole top and bottom bar disappears.
This leaves me with no recourse to do anything really(as far as I can see)

I have tried all the 'F' buttons. I have tried all the buttons in fact.

Can anyone help please?

There is a possibility that the above are symptoms of a bad installation. Did you install your system very  recently or these problems appeared suddenly after a long time?

---

### Post by nikoPSK on 2008-01-13
> **joemacnz said:**
> I have a problem, however, while I have searched the forums for something similar, I don't really know what the problem is. I am intimate with the symptoms though!!

To start with firefox freezes for a couple of minutes,and then disappears off the screen.
Next I try to get the terminal.(I have the windows button set to bring it up)
Nothing happens
Then I click on "accessories" and the whole top and bottom bar disappears.
This leaves me with no recourse to do anything really(as far as I can see)

I have tried all the 'F' buttons. I have tried all the buttons in fact.

Also, my screen saver has disappeared 

Can anyone help please?

something went horribly wrong... corrupted something? Anything you did in particular before this happened?

---

### Post by joemacnz on 2008-01-13
I have had this install for about 18 months. It is fairly sudden, though I have been having a few firefox issues in the last couple of weeks

---

### Post by joemacnz on 2008-01-13
> **nikoPSK said:**
> something went horribly wrong... corrupted something? Anything you did in particular before this happened?


Not that I can think of, I am not very adventurous so other than trying to install various programs, nothing.

---

### Post by RomeReactor on 2008-01-13
Hi. Do you have desktop effects enabled, and if so, does the same happen when they're disabled?

---

### Post by joemacnz on 2008-01-13
this is what I was getting a few weeks ago:

> **joemacnz said:**
> While browsing the last few days, firefox has suddenly stopped working. when try to do a restart I get the following:

[849.188761] EXT-fs error(device hda1): ext3-find-entry:reading directory #4407743 offset0


Can anyone help please?

[http://ubuntuforums.org/showthread.php?t=655082](http://ubuntuforums.org/showthread.php?t=655082)

---

### Post by joemacnz on 2008-01-13
> **RomeReactor said:**
> Hi. Do you have desktop effects enabled, and if so, does the same happen when they're disabled?

I am not sure, I will resett it and find out

---

### Post by joemacnz on 2008-01-13
> **RomeReactor said:**
> Hi. Do you have desktop effects enabled, and if so, does the same happen when they're disabled?

Visual effect are off.

---

### Post by RomeReactor on 2008-01-13
In [this thread]("http://ubuntuforums.org/showthread.php?t=106260") someone also had an EXT-fs error (although a different one); It seems that doing a **fsck** (File System Check) might help; however, I've never done that manually, so I wouldn't know if it **is** necessary. Someone more knowledgeable will be able to tell you if it's necessary and how to go about it. Otherwise, try going to the **#ubuntu** IRC channel and ask there.

---

### Post by joemacnz on 2008-01-13
I typed  "fsck" and it told me that it could do serious damage. Do I want to do it?

---

### Post by RomeReactor on 2008-01-13
> **joemacnz said:**
> I typed  "fsck" and it told me that it could do serious damage. Do I want to do it?

**Don't** do it unless someone more knowledgeable tells you why and how; try asking in the#ubuntu channel in  IRC.

---

### Post by kostkon on 2008-01-13
> **joemacnz said:**
> I typed  "fsck" and it told me that it could do serious damage. Do I want to do it?

I believe your file system got corrupted somehow. You can force the system to do a *fsck* and check your file system at the next boot. This is the safest way to do a *fsck*.

Open a terminal, and give this
```
sudo touch /forcefsck
```

the above command will force your system to do the check. You will then need to reboot your system, like this
```
sudo reboot
```

Although this is a safe way to check your file system I cannot take any responsibility if any bad thing will happen. **Do it at your own risk**.

---

### Post by joemacnz on 2008-01-13
> **kostkon said:**
> I believe your file system got corrupted somehow. You can force the system to do a *fsck* and check your file system at the next boot. This is the safest way to do a *fsck*.

Open a terminal, and give this
```
sudo touch /forcefsck
```

the above command will force your system to do the check. You will then need to reboot your system, like this
```
sudo reboot
```

Although this is a safe way to check your file system I cannot take any responsibility if any bad thing will happen. **Do it at your own risk**.

I tried this and it all came up roses. Everything seemss to be working but I don't think anything has been fixed. I think this is an intermittent problem. How do I get onto the #ubuntu IRC channel. Especially if I have to use a windoze box to do it?

---

### Post by RomeReactor on 2008-01-13
> **joemacnz said:**
> How do I get onto the #ubuntu IRC channel. Especially if I have to use a windoze box to do it?

There are many [IRC clients available for windows]("http://en.wikipedia.org/wiki/Comparison_of_IRC_clients#Operating_system_support"), but I [recommend Pidgin]("http://www.pidgin.im/"); it's very good, it incorporates many protocols such as IRC, MSN, AIM, Yahoo, ICQ, and many others in one program. It's also the default messaging program in Ubuntu. You can download [the windows client here]("http://www.pidgin.im/download/windows/").

To create an IRC account, launch it, right click on its taskbar icon and select "Accounts" and press the "Add" button; then fill it out like this:

* Protocol: IRC
* Screen Name: (Choose what you want here)
* Server: irc.ubuntu.com
* Password: (Only if you [registered your nickname]("http://freenode.net/faq.shtml#nicksetup"); otherwise leave it blank)
* Local Alias (Leave blank if you want)
* Remember Password: (Only if you set up a password; otherwise leave unchecked).

---

### Post by tact on 2008-01-13
> **joemacnz said:**
> I typed  "fsck" and it told me that it could do serious damage. Do I want to do it?

Glad its all rosy now.  In case you are interested you got the message "this can do serious damage" when you tried to run fsck - because you were running it in a terminal while booted into ubuntu and so the partitions/file system you wanted to check were mounted.

You should only ever run fsck on unmounted file systems and kostkon gave you the right advice how to do that...  the commands he gave you creates a file on / (root) that tells your system to do a fsck on the next boot before file systems are mounted.

evidently this fixed the corruption that was causing the symptoms you were noticing.  everything being rosy now.

What you need to ask yourself now is...  what could have caused the corruption?  How do I rectify this.

It could be just a messy shutdown.  Was the power pulled unexpectedly some time before the bad stuff started to happen?  

It could be a HDD that is on the way out.

You need to do some checking.  And back up anything essential to some place other than that HDD.  :)

---

