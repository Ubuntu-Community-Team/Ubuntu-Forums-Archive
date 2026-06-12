---
title: "Upgrading To Dapper In The Future"
date: 2006-03-18
forum: Absolute Beginner Talk
---

### Post by wdbreen on 2006-03-18
Gday mates
I know it's a bit premature, but when Dapper is released as a stable OS, does Breezy need to be killed or written over by another CD or is there a smooth update process for those using Breezy 5.10?

Breeny

---

### Post by tkiesel on 2006-03-18
I installed Ubuntu 4.10 "Warty" in Feb. 2005.  When Hoary was released, I modified one file, ran two commands and upgraded to Hoary.

Recently I did the same to get to Breezy.  I'll do the same for Dapper.

:)  It's easy and works remarkably well!

Just replace every occurrance of your current version's name with the new name in the /etc/apt/sources.list  file.  

```
sudo gedit /etc/apt/sources.list
```

Alternately, you can do that from within Synaptic too. Just change the names in the Repositories settings in Synaptic.

So.. A year ago, I changed every occurance of the word warty in my repos to say hoary.

You and I will soon go in and change the word breezy to the word dapper. As easy as that!!

Then, you "reload" and "mark all upgrades" in Synaptic.  (Make very sure that Synaptic is set to "smart upgrades") And hit "Apply!"

or alternately, for text command fanatics like me... 

```
sudo apt-get update
sudo apt-get dist-upgrade
```

Which is the same thing.  :)

A whoooooooooooole lot of downloading commences.. and some loooong installation time.

It might ask you about some config files during the install.  I simply voted to keep my current configs.

And you'll be set!

-T

---

### Post by Zerocool10482 on 2006-03-18
Well if you want to try Dapper you can but the final will be out in June. If you want to get dappper be warned that there are bugs. But I'm using Breezy and Dapper on another system. I'm just testing things but it looks stable but I'll will wait for the final. That's just me. You can do a dist-upgrade. That's when you change your source list to dapper and then upgrade everything. It's sometimes buggy but again only if you want too. I think Breezy will be stable forever but I like to have new features. That's why I'm waiting for the final.

---

### Post by wdbreen on 2006-03-18
Thanks T
I'll take your advice and print out your suggestions for when the time comes.  Its a great system!
I turned off windows weeks ago and never looked back.

Cheers for the reply

---

