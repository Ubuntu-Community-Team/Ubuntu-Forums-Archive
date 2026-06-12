---
title: "Shared directory best practise?"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by Rich78 on 2007-02-01
Hi,

What's the best location to setup shared directories?

/var?

Thanks

---

### Post by dannyboy79 on 2007-02-01
that's the nice thing about linux. you chose!!! i use /usr/share/ but you can pick whatever you want!!!! what do you want to share? network space? share settings/config files, what??

---

### Post by glabouni on 2007-02-01
learn about /var
[http://www.pathname.com/fhs/pub/fhs-2.3.html#THEVARHIERARCHY](http://www.pathname.com/fhs/pub/fhs-2.3.html#THEVARHIERARCHY)

---

### Post by Rich78 on 2007-02-01
Sorry I know it wasn't specific but I thought there might be a best practice to sharing folders?

For instance you wouldn't share /home would you?

I thought /var is a location for directories where by files alter often.

I want it for general file shares, be it either locally between two users or if I was to setup a server, master share directories for various files.

---

### Post by Rich78 on 2007-02-02
Anyone got any more opinions?

---

### Post by hyper_ch on 2007-02-02
I personally like to have as much as possible in /home so I use  /home/exchange to share stuff accross the LAN.

---

### Post by dannyboy79 on 2007-02-02
> **sjau said:**
> I personally like to have as much as possible in /home so I use  /home/exchange to share stuff accross the LAN.

i second this. this way the share folder isn't in your /home/username directory and it's also not under / along with /etc and /var but it's on the same level as your /home/username folder. so it would /home/shared. although linux is really great about permissions and whatnot that it's not a big deal creating a folder within /home/username/shared and just set the owner:group to share or whatever and set the permissions correctly and you'll be fine. this the thing I was trying to point out earlier, when you ask about "best practice" you're gonna get a different answer from 80% of the people. i suppose you could ask the question in the server forum section as they might have a better answer.

---

