---
title: "what is a super user?  First post"
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by Bdubbya on 2006-07-30
This is my first post on the ubuntu forums.

Today i felt the need to install linux. So I donloaded the ISO from the Ubuntu website, bunred the CD and now I'm on my way.

Until today I'v only used Windows, I'm an IT consulant for small and Medium business in the Detroit area.

Anyways, down to business...
I installed all of the updates. but my graphics card (ATI mobility Radeon 9600) needs drivers installed manually. the Ati website has a section for linux drivers, I downloaded the files and falloed the instrustions till i had to run "sh ./ati-driver-installer-8.27.10-i386.run" in the terminal. then i had an error message pop up telling me i need to be a Super user to do that.

How do i log in as a super user? is it the same thing as the root? the user name I'm useing is the one i defined on install.

Please help.

I also need help with my Wlan card, but thats another post.

---

### Post by Jagot on 2006-07-30
You just have to use sudo before all of your commands, so:

```
sudo sh ./ati-driver-installer-8.27.10-i386.run
```

You can read more here:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Bdubbya on 2006-07-30
Thanks so much!

---

### Post by Jagot on 2006-07-30
Just came across this:

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

It's Ubuntu specific instructions to install ATI drivers - may be of use to you.

---

