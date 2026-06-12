---
title: "[SOLVED] Running an application as ROOT"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by kdchapman1776 on 2007-08-29
I am a little perplexed by something.  I am trying to enable a Cisco Aironet 350 card in Feisty Fawn and the drivers are apparently in Feisty.  One of the steps I need to follow requires me to execute some lines with root access.  I tried sudo and su but had no luck.  Here is what the website is telling me to do.  

[COLOR="Blue"]The following two commands need to be executed as root:

 echo "exit" > /etc/default/NetworkManager
 echo "exit" > /etc/default/NetworkManagerDispatcher[/COLOR]

Could someone please tell me how to do this?  Thanks.

---

### Post by viciouslime on 2007-08-29
It should be a case of running:

```
sudo echo "exit" > /etc/default/NetworkManager
sudo echo "exit" > /etc/default/NetworkManagerDispatcher
```


Is this how you did it?

Failing that, try typing:

```
sudo su
echo "exit" > /etc/default/NetworkManager
echo "exit" > /etc/default/NetworkManagerDispatcher
```

That should work :)

---

### Post by tszanon on 2007-08-29
> **kdchapman1776 said:**
> I am a little perplexed by something.  I am trying to enable a Cisco Aironet 350 card in Feisty Fawn and the drivers are apparently in Feisty.  One of the steps I need to follow requires me to execute some lines with root access.  I tried sudo and su but had no luck.  Here is what the website is telling me to do.  

[COLOR="Blue"]The following two commands need to be executed as root:

 echo "exit" > /etc/default/NetworkManager
 echo "exit" > /etc/default/NetworkManagerDispatcher[/COLOR]

Could someone please tell me how to do this?  Thanks.
It should be:
```
sudo echo "exit" > /etc/default/NetworkManager
sudo echo "exit" > /etc/default/NetworkManagerDispatcher
```
or you could:
```
sudo su
echo "exit" > /etc/default/NetworkManager
echo "exit" > /etc/default/NetworkManagerDispatcher
exit
```

Is this what you have tried?

---

### Post by Seisen on 2007-08-29
You can also do 

```
sudo -s -H
```

---

### Post by Mornedhel on 2007-08-29
[COLOR=Black]sudo or su should both work.

With sudo :
sudo [/COLOR][COLOR=Black]  echo "exit" > /etc/default/NetworkManager
sudo [/COLOR][COLOR=Black]  echo "exit" > /etc/default/NetworkManagerDispatcher
(will prompt you for the root password each time)

With su : (I have an actual root user enabled on my box)
su
(type password)
[/COLOR][COLOR=Black]echo "exit" > /etc/default/NetworkManager[/COLOR]
[COLOR=Black]  echo "exit" > /etc/default/NetworkManagerDispatcher

OK, so four people have said this while I was posting. meh.
[/COLOR]

---

### Post by kdchapman1776 on 2007-08-29
I am not near the machine at this time and I thought this is how I used the sudo command.  I will post my results when I can try this.

---

