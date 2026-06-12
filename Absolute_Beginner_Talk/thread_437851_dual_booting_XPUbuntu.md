---
title: "dual booting XP/Ubuntu"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by mebuntu on 2007-05-09
Hello Everyone,

am about to jump into the world of LINUX and would appreciate some advice on dual booting XP and Ubuntu.

have a Dell laptop with XP Pro installed. is it possible to install ubuntu desktop and ubuntu server on the same physical drive as XP  ?  Will I need to install the desktop version first or the server ? does it matter ? 

many thanks

---

### Post by Terl on 2007-05-09
It is very easy to set up a dual boot for Ubuntu and xp on the same drive.  I do have a question though, are you thinking of installing ubuntu twice?

---

### Post by Happy_Man on 2007-05-09
The desktop version and the server version are almost exactly the same. The server version doesn't come with a GUI, and comes with some preinstalled server software such as LAMP. The desktop version comes with all the fun stuff you need to have a working home computer such as GIMP, Firefox, etc. Some people who like speed install the server version and then install the essentials. If you don't want to do that, just run the following command:

```
sudo aptitude install ubuntu-desktop
```

or, if you want a custom install, run:

```
sudo apt-get install synaptic firefox
```

to get you started.

---

### Post by Sef on 2007-05-09
Read [Psychocat's installing]("http://www.psychocats.net/ubuntu/installing") to dual boot from the Desktop (Live) CD.

Read the [Illustrated Dual Boot]("http://users.bigpond.net.au/hermanzone/") to dual boot from the alternate (text-based) cd.

---

### Post by mebuntu on 2007-05-09
As you can see i am a total newbie, LOL :) 

i was looking around the ubuntu homepage and saw the desktop/server versions. 

will go with the desktop version. 

are there any "gotchas" during the install or does ubuntu do exactly what it says

---

### Post by Terl on 2007-05-09
Read through the install guides linked above this post.  

No gotchas.  I would defrag your hard drive before you do any partitioning and backup as needed (always a good idea) before you partition and install.

---

### Post by slibuntu on 2007-05-09
I've got a tutorial on my blog for installing Ubuntu, and dual booting it, its for 6.06, but the general gist is the same, link in my sig

---

### Post by mebuntu on 2007-05-09
thanks to all for your replies:popcorn:

---

