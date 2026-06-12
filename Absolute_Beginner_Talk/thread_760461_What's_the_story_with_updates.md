---
title: "What's the story with updates"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by coffeecups on 2008-04-20
Hi there, 
I'm still quite a newbee when it comes to ubuntu although I've been using it now for about 5 months. Everything works great and I'm very pleased to be away from Microsoft and all it's bugs. Updates though are my biggest concern. I live in Ireland and we still, as yet, do not have broadband available outside of major towns. My internet connection is dialup and very slow, every time I go on line there are about 20 updates suggested for my computer and it always takes 3 or more hours to get them. There is always a good number of the updates that fail whenever I do download and I don't really understand why, I get error messages like " Error reading from server - read (104 Connection reset by peer) and Error reading from server. Remote end closed connection" Is it just because dial up is slow? Do I really need to get all the updates suggested? The warning that updates could allow malicious individuals to get in to my computer makes me unsure that I should be downloading anything other than the security updates, although even when I just do the security ones the warning about malicious individuals still comes up!! :confused:

---

### Post by drascus on 2008-04-20
most of the time when I have seen that error message it means that the computer is having trouble connecting to the server. It is usually an internet connection issue on my end of things. So I would say that it is definitely possible that dial up could be the culprit. maybe it is not the best phone line. Their could be all kinds of issues with dial up which is why people try to switch away from it all the time. I use to get booted off line all the time because of my dial up connection. The warning that you get is generally associated with your channels being out of date so it can't varify the updates. This isn't an issue and I wouldn't worry about malicious individuals getting in to your computer through update manager, you should be able to resolve this by opening up a terminal apllications->accessories->Terminal and typing the command "sudo apt-get update" it will ask you for a password. after you type in your password it will connect to the internet and update your software channels (note: this might take a while) then you shouldn't get a warning message when installing updates. if your connection is painfully slow and you don't need a graphical experiance online I suggest trying the Webbrowser called Lynx its text based which means pages will load much quicker. once installed it is run from a terminal window by typing the command "lynx" . I hope this advice prooves useful.

---

### Post by erlyrisa on 2008-04-20
no .... you don't "have to" update...

I personally switched off automatics updates in windows., and there is no reason not to on Ubuntu either.

or...

choose what you want updated.

I am currently using the latest and greatest, and there are always knew package updates - up to 300Mb a day. -I dont update all the time... and usually wait a week to download. (it's KDE4 that is being heavily worked upon at the moment... and there is no piont downloading konqueror everyday.... may aswell wait a bit for a more final version)

---

### Post by coffeecups on 2008-04-21
Many thanks for the help, will have a look at lynx. I ran apt-get update, it seemed to get some updates but then I got this error message:

Fetched 35.6kB in 34s (1029B/s)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/binary-amd64/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
sue@sue-desktop:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

Sorry to be so uninformed but I dont understand what this means ?? What is the public key and what is the lock file?? Appreciate the help very much :)

---

### Post by bodhi.zazen on 2008-04-21
The messages about the key can be ignored. The keys are used to maintain security, establish you are downloading from the official ubuntu repos.

But, it shoulc be fixed if you can.

Try ```
sudo apt-get update
```

If that fails

```
sudo gpg &#8211;-recv-keys 2EBC26B60C5A2783
sudo gpg &#8211;-export &#8211;armor 2EBC26B60C5A2783 | sudo apt-key add -
```

Note the doubble dash - - b4 "recv-keys" and "export"

Ssee here :

[http://www.debuntu.org/how-to-import-export-gpg-key-pair](http://www.debuntu.org/how-to-import-export-gpg-key-pair)

[https://help.ubuntu.com/community/Repositories/Ubuntu#head-589d9639c60888f17e3d660b375340777b436077](https://help.ubuntu.com/community/Repositories/Ubuntu#head-589d9639c60888f17e3d660b375340777b436077)

====

The second error "E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory" is because you did not run apt-get as root.

You need to use sudo

sudo apt-get ....

---

### Post by sdowney717 on 2008-04-21
if you are using hardy beta, I found using 

sudo apt-get update
then 
sudo apt-get dist-upgrade   

from terminal fixed a lot of issues with failure to get etc....
I had been simply clicking the update manager and it just would not work like it should.

---

### Post by SlappyPappy on 2008-04-22
I do that to, pick and choose the updates you want or simply minimize the number of them so you don't have to sweat getting them all at one time. It's less of a hassle then using dialup.

---

### Post by coffeecups on 2008-04-25
Many thanks, seemed to work but still failed to get and ignored a few updates. Maybe they're not important! 

I'ld like to understand the difference between using apt-get and update manager? how come it's so much quicker?:-k

---

