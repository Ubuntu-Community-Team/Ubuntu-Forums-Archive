---
title: "updating ubuntu"
date: 2006-04-02
forum: Absolute Beginner Talk
---

### Post by precinto on 2006-04-02
hello everyone.
i have a question about the update system of ubuntu. i'm going to install ubuntu in my laptop, but i've seen the next version is due within a month. So... if i install ubuntu 5, will i need to reinstall the whole OS again when 6.06 comes out? should i wait until june for the next version or will i be able to update the OS without a new iso, using only my internet connection?

Thanks a lot.

---

### Post by flankker on 2006-04-02
im wondering the same thing myself...

---

### Post by eriefisher on 2006-04-02
From what I've seen so far, it should be just a matter of changing your sources.list to reflect Dapper instead of Breezy and doing a apt-get update and a apt-get dist-upgrade. but I would wait until it goes final first.

eriefisher

---

### Post by precinto on 2006-04-02
why would you wait? is it complicated to do what you said? i don't really know what source.list is...

---

### Post by xXx 0wn3d xXx on 2006-04-02
[QUOTE=precinto]why would you wait? is it complicated to do what you said? i don't really know what source.list is...[/QUOTE]
Dapper is still very unstable and in testing. Your sources.list is links to security updates, program updates, and all that. You would replace Breezy's sources.list with Dappers and then run sudo apt-get update and then sudo apt-get dist-upgrade. Everything will then update.

---

### Post by precinto on 2006-04-02
so, is it easy to do that? you think i, as the beginner i am, should install ubuntu 5 and the update? or isn't it worth the trouble?
thanks.

---

### Post by xXx 0wn3d xXx on 2006-04-02
[QUOTE=precinto]so, is it easy to do that? you think i, as the beginner i am, should install ubuntu 5 and the update? or isn't it worth the trouble?
thanks.[/QUOTE]
Don't update yet ! Install Breezy and then on June 1st you can upgrade to Dapper if you want. On June 1st Dapper will be given an offical release number and become part of the Ubuntu family. :) Yes, it is very easy to do a dist-upgrade, it is automated, keeps all your files, but it takes a fairly long time. About 1-2 hours depending on your internet connection and all that stuff.

---

### Post by precinto on 2006-04-02
ok, that's exactly what i wanted to know. thanks, masteronetwothree.

---

