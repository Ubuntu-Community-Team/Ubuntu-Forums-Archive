---
title: "software on wine does not run"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by cmaranhao on 2008-03-15
i need a windows only application to run in Linux (i am with Ubuntu 7.04 - the Feisty Fawn).

firstly i have to say that my knowledge in linux is very small, i was able to configure everything until now but with lots of forum help, how to, etc.

having that said, i already installed WINE but the application does not run. i can already see the application icon in my desktop, however, when i click on it, nothing happens.

a friend of mine was here earlier (but i'm out of luck because he couldn't make it run also).. he also revealed to me that i will probably need Python for windows to be installed before i can use the application.

the problem is he wasn't able to run python from WINE too. having no other options i decided to ask for forum help, maybe someone here can give me some light in this matter.

i really want to run this application. any help is appreciated. 

regards

---

### Post by kamitsukai on 2008-03-15
so whats the application?

---

### Post by forrestcupp on 2008-03-15
1. Wine won't run all Windows apps - it's deceptive for people to entice Windows users by saying that any Windows app will run in Linux.  I hope you weren't deceived in this way.

2. Lots of Windows apps do run correctly, but there are different ways for getting different apps to work.

You need to tell us which app you want to run.

---

### Post by cmaranhao on 2008-03-15
the application is called "BT next evolution".

to give you an idea, that software is from a portuguese torrent site (only with invitation we can be members), i need it to make my downloads. otherwise, the torrents won't start.

---

### Post by kamitsukai on 2008-03-15
well i would advise asking a moderator/creator of the bt site if it works on linux otherwise i would use virtualbox and run windows

---

### Post by cmaranhao on 2008-03-15
no, the application is for windows only. there are already complaints from linux users.. and there is no linux version planned unfortunately.

my friend was also messing with virtualbox. we were able to see the windows logo starting up but then some error happened and no luck with virtual box either (i don't know if there were some configuration problems though). 

virtualbox was also a valid approach for me because each time i turn my PC on, i have the ability to choose between windows or linux. if i could access the windows hard drive from linux and run the application from there it would be fine too. 

i really want to run it from linux, i am done with windows for ever.

vmware isn't viable, i don't have the harddrive space to install it :(

---

### Post by forrestcupp on 2008-03-15
According to this [bug report](http://bugs.winehq.org/show_bug.cgi?id=11865) over at winehq, it looks like it's not going to work no matter what you do because of something called Themida.  It also looks like anything that uses Themida is a security risk.

I think I'd find a different source for torrents if I were you.

---

### Post by cmaranhao on 2008-03-15
i am willing to take the risk, the download speeds are worth it.

so, wine is out of the question because of themida.

what other options do i have? is there a way to access my windows partition through linux? 

that way, i can install the software there and turn it on or off when i am in linux.

---

### Post by forrestcupp on 2008-03-15
Your only options are to dual boot to windows or use a virtual machine, like vmware or virtual box.

Or find a different source.

Or get them to reprogram your software with a newer version of Themida.  It appears that newer versions work better with wine.

---

### Post by cmaranhao on 2008-03-15
ok, thanks for everything. 

i might delete the windows partition and that way i only have single boot.

then, i resize my hard drive so i can install vmware.

one more question: can i drag and drop the files from vmware windows to linux?

regards

---

