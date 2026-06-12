---
title: "what is the easist way to communicate through skype"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by mozkaynak on 2007-12-19
Hi all,
I havent used Skype before and I am supposed to use it for an international voice communication this weekend. 
Can I use Pidgin? or should I install the messanger from skype.com?

What is the easiest and most reliable way?

Thanks...

---

### Post by wormser on 2007-12-20
Pidgin will not work.  You will have to install Skype.  There are 2 ways to install.  Download the .deb from [skype.com]("http://www.skype.com") or add the Medibuntu repository.  I prefer the repositories for installing.

Ubuntu 7.10 "Gutsy Gibbon" command, other Ubuntu versions [here]("https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f").
```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```

Then, add the GPG Key: 
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

Now install:
```
sudo apt-get install skype
```

I would make some test conference calls.  Skype in the past has been a bit buggy with Linux but is improving fast.

---

### Post by Severun on 2007-12-20
sudo apt-get install skype should get you the skype client.

You can use Synaptics package manger to install it too

System->Administration->Synaptic Package manager

click search, then type skype

I don't remember if it's in restricted so you may have to check the box in Synaptic that adds the "multiverse" or Restricted packages, then click on "Reload", then do a search for skype.

It worked out of the box for me on Gutsy (7.10).

hehe.... Oh see above ^^^^^^

---

