---
title: "cannot access second hd"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by blackshadow05 on 2007-02-05
Hi all. I just did an install of ubuntu. I have 2 hard drives but I can only seem to access one of them. I may have messed up on the install. As i have many files on the second drive I would like to find a way to access the drive. I am new to linux and I am somewhat confused by the terminology, So if there is any help, please be gentle..lol  thanks Mike. I will be glad to answer any questions I can to help.  

oh by the way, When i shut down ubuntu, I hear the hard drives spin down, the fans remain running and the splash screen remains, and it never shuts off. Is this normal??In this state nothing works and the only way to make things work is a hard boot at the power switch. Any help??

---

### Post by taurus on 2007-02-05
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by marx2k on 2007-02-05
What sort of filesystem is your second hard drive? 

you can look through [http://www.ubuntuforums.org/showthread.php?t=353494&highlight=mounting](http://www.ubuntuforums.org/showthread.php?t=353494&highlight=mounting)

(from an Ubuntu search thats the first good link I found in the list that describes something like what youre going through)

As far as the second issue of not shutting down correctly, I am having the same behavior on my girlfriend's laptop. Usually not an issue since she can just hit the power switch.... buuut on the other hand I know a lot of the time I select 'Shut Down' and then close the laptop lid, put the laptop in my bookbag... a few times I get to another location and found out it never shut down and the battery is either mostly or totally depleted (*BOGUS*) - So I would like to hear an answer as to this second issue also.  I'm betting it's a pretty simple fix but the key is how do you find out what process is hanging on?

---

### Post by blackshadow05 on 2007-02-06
Thanks guys, The info you pointed me to is over my head.  The old system was 98se so i guess it is fat 32. I will read somemore....

---

### Post by taurus on 2007-02-06
What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

