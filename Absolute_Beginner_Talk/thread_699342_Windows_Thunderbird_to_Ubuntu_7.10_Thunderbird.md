---
title: "Windows Thunderbird to Ubuntu 7.10 Thunderbird"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by copperco2 on 2008-02-17
I need to open the windows thunderbird profile in thunderbird ubuntu. To follow the advice in various threads i have copied and pasted the thunderbird folder contents into the thunderbird ubuntu folder.. but still it is difficult to start .... 
i have only one profile to use...

pl. help

---

### Post by lncoll on 2008-02-17
Hi:
Usually I have not problems doing this is very easy:
[LIST=1]
[*]Locate your windows profile usually "c:/Documents and Settings/username/program data/Thunderbird/Profiles/somegarbage.default/
[*]copy all files inside to a know place to be located in Linux
[*]Boot in Linux and copy that files in /home/username/.mozilla-thunderbird/somescratch.default
[*]Start Thunderbird
[/LIST]
Also you can mount your XP drive in /media/sdx and copy from there

---

### Post by kellemes on 2008-02-17
Yes, or simply start TB from the terminal like so..
```
thunderbird -profilemanager
```
In the dialogbox point to the profilefolder on your windowsbox (first mount).. or create a shared disk between Win and Linux so you can share the profilefolder..

---

### Post by Victormd on 2008-02-17
If you use Thunderbird, the best thing is to create a profile, don't let TB manage the profile folder location. If you don't already have this setup and don't know where your profile folder is, you'll have to find it. It's usually located in your "documents and settings" somewhere. Once you find it, copy the folder to where ever you'd like (doing this makes it easier to backup your profile and e-mails). Then, in windows, click run and type "thunderbird -profilemanager" You can then "Create Profile," name it and "Choose Folder," and point it to the folder where your new profile files are. Click FINISH, select the new profile, mark "Don't ask at startup" and click Start Thunderbird. Presto, TB will now open the new profile everytime you start it.

Now, in ubuntu, open the terminal and type "thunderbird -profilemanager" and do the same thing: create a profile with the same name as you did in Windows and choose the same folder as you did for the Windows TB. Click FINISH, select the new profile, mark "Don't ask at startup" and click Start Thunderbird.

Now, any time you open Thunderbird (under windows or ubuntu) you'll have the same profile and e-mails (always updated whether in windows or ubuntu)

Hope this helps...

---

### Post by Victormd on 2008-02-17
> **copperco2 said:**
> I need to open the windows thunderbird profile in thunderbird ubuntu. To follow the advice in various threads i have copied and pasted the thunderbird folder contents into the thunderbird ubuntu folder.. but still it is difficult to start .... 
i have only one profile to use...

pl. help

DON'T copy the thunderbird folder, you need to copy the thunderbird profile folder, these are two different things... Per my previous post, don't copy the folder, simply point both profiles to the same folder...

---

### Post by copperco2 on 2008-02-17
I tried copying the profile but the following message 'error shows' up-
Error "I/O error" while copying "/media/Ma...com/Inbox".

Yes... i do not have XP anymore.. but only ubuntu 7.10.. the back was taken before i installed ubuntu..
pl. help.

---

### Post by copperco2 on 2008-02-17
> **copperco2 said:**
> I tried copying the profile but the following message 'error shows' up-
Error "I/O error" while copying "/media/Ma...com/Inbox".

Yes... i do not have XP anymore.. but only ubuntu 7.10.. the back was taken before i installed ubuntu..
pl. help.

Now after checking all the inbox messages.. i realise that on of the inbox is completely empty.. i dont know how did this happen.

And the issue is serious enough as the mailbox contans about 3GB of data/ mails..

pl. help

---

### Post by skrap on 2008-03-28
I am trying to do this also and i type the thunderbird-profilemanager in the terminal and I get command not recognized.   Did I not install a profile manager?

---

### Post by kellemes on 2008-03-28
> **skrap said:**
> I am trying to do this also and i type the thunderbird-profilemanager in the terminal and I get command not recognized.   Did I not install a profile manager?

Don't forget the space..
```
thunderbird -profilemanager
```

---

