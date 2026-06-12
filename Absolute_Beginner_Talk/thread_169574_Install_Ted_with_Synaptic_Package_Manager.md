---
title: "Install Ted with Synaptic Package Manager"
date: 2006-05-02
forum: Absolute Beginner Talk
---

### Post by mel_lamarre on 2006-05-02
Hello,

I'm completely new to Linux and Ubuntu.
I would like to install that light word processor which seems great, Ted, and in fact, I don't know at all where I should begin. I've found the Ted website ([http://www.nllgg.nl/Ted)](http://www.nllgg.nl/Ted)), but wasn't sure what I should download or not. I would like to install Ted with Synaptic, if it is possible, but don't know how to connect both software to get it done. I've searched for the last hour on Google and Ubuntu forum, but still feel pretty lost.
So, if someone could help me out with a step-by-step procedure, I would be really grateful.
Thanks a lot,

Mélodie

---

### Post by testube_babies on 2006-05-02
1) Make sure you have extra repositories enabled:
[http://wiki.ubuntu.com/AddingRepositoriesHowto](http://wiki.ubuntu.com/AddingRepositoriesHowto)

2) Open up a terminal and type:
```
sudo apt-get install ted
```

Alternatively, after the extra repositories are enabled, you could install ted through Synaptic.

---

### Post by mel_lamarre on 2006-05-02
[QUOTE=testube_babies]1) Make sure you have extra repositories enabled:
[http://wiki.ubuntu.com/AddingRepositoriesHowto](http://wiki.ubuntu.com/AddingRepositoriesHowto)[/QUOTE]

Step 1 done. Thanks a lot for the info.

[QUOTE=testube_babies]2) Open up a terminal and type:
```
sudo apt-get install ted
```[/QUOTE]

Now, when I go to step 2, I get this message in the terminal :

```
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ted
```

What do I miss?

---

### Post by linear on 2006-05-03
Are you sure you have Universe enabled?

---

### Post by Rinzwind on 2006-05-03
Otherwise do a 
**sudo apt-get update**

Maybe you need to refresh your database :)

---

### Post by mel_lamarre on 2006-05-05
I found the problem. I realized I had enabled the Universe repository for Hoary but not for Breezy. When I did it for Breezy, I found Ted and was able to install it after reloading.
Thanks a lot everybody for your help.
Mélodie

---

