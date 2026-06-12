---
title: "Arch linux apt-get"
date: 2012-09-08
forum: Any Other OS
---

### Post by eneskuray on 2012-09-08
I will build linux from archlinux but my client wants use apt-get in this linux . i must do this tomorrow how ?

---

### Post by shad0w_walker on 2012-09-08
I believe the answer is in short. You don't. Apt-get is a whole different package management system to to (If memory serves) pac-man which is Archs own package manager. I'm sure there is some way to manage it, but as with most things like that, I wouldn't recommend it if you can't do it yourself as it will likely require a lot of careful management and tinkering and work arounds.

---

### Post by eneskuray on 2012-09-08
> **shad0w_walker said:**
> I believe the answer is in short. You don't. Apt-get is a whole different package management system to to (If memory serves) pac-man which is Archs own package manager. I'm sure there is some way to manage it, but as with most things like that, I wouldn't recommend it if you can't do it yourself as it will likely require a lot of careful management and tinkering and work arounds.

if you show a road , i can remove all package manager . i am only using arch to boot

---

### Post by shad0w_walker on 2012-09-08
I honestly don't have a clue how you'd even start to go about it. You'd basically need to replace the whole OS as far as I can see. The repos you setup with APT would need to have equivilent packages created for the packages installed from pac-man, the local versions would need to be set as installed. 

What are you even trying to do with the system? If you need apt-get that badly, use a debian based system.

---

### Post by eneskuray on 2012-09-08
> **shad0w_walker said:**
> I honestly don't have a clue how you'd even start to go about it. You'd basically need to replace the whole OS as far as I can see. The repos you setup with APT would need to have equivilent packages created for the packages installed from pac-man, the local versions would need to be set as installed. 

What are you even trying to do with the system? If you need apt-get that badly, use a debian based system.

all linux on linux kernel . i am trying kernel 3.5 and i did only format disk , mounting disk , bootload . i have command area only

#root@kuraylinux

---

### Post by shad0w_walker on 2012-09-08
I am well aware that all 'linux is on linux kernel'

What I am trying to say is that EVERYTHING ELSE is built differently from distro to distro. Arch uses a completely different system for managing it's installed programs and libraries to Debian or Ubuntu.

Taking pac-man out and putting apt in is going to be so much work it will be easier to just use something that has apt to start with.

In short

If you can't figure this out on your own. Don't do it. Look at whatever you are trying to do (Still have said so I can't help) and then pick something better for it.

Either switch to a distro that uses apt or use pac-man and stick with arch.

---

### Post by eneskuray on 2012-09-08
> **shad0w_walker said:**
> I am well aware that all 'linux is on linux kernel'

What I am trying to say is that EVERYTHING ELSE is built differently from distro to distro. Arch uses a completely different system for managing it's installed programs and libraries to Debian or Ubuntu.

Taking pac-man out and putting apt in is going to be so much work it will be easier to just use something that has apt to start with.

In short

If you can't figure this out on your own. Don't do it. Look at whatever you are trying to do (Still have said so I can't help) and then pick something better for it.

Either switch to a distro that uses apt or use pac-man and stick with arch.

i want try can you write code to install

---

### Post by MG&amp;TL on 2012-09-08
> **eneskuray said:**
> i want try can you write code to install

You can grab APT source code as shown here: [http://algebraicthunk.net/~dburrows/blog/entry/howto-get-the-apt-source-repository/](http://algebraicthunk.net/~dburrows/blog/entry/howto-get-the-apt-source-repository/)

...you're still doing it the wrong way. And using APT will break everything.

---

### Post by eneskuray on 2012-09-08
> **MG&TL said:**
> You can grab APT source code as shown here: [http://algebraicthunk.net/~dburrows/blog/entry/howto-get-the-apt-source-repository/](http://algebraicthunk.net/~dburrows/blog/entry/howto-get-the-apt-source-repository/)

...you're still doing it the wrong way. And using APT will break everything.

only is this page enough?

---

### Post by MG&amp;TL on 2012-09-08
> **eneskuray said:**
> only is this page enough?

I don't follow. Sorry. :(

---

### Post by shad0w_walker on 2012-09-08
You are clearly either not going to listen to reason on this. I am officially stopping my replies after this post.

[SIZE="4"]WHAT YOU ARE TRYING TO DO IS NOT GOING TO WORK[/SIZE]

---

### Post by MG&amp;TL on 2012-09-08
> **shad0w_walker said:**
> You are clearly either not going to listen to reason on this. I am officially stopping my replies after this post.

[SIZE=4]WHAT YOU ARE TRYING TO DO IS NOT GOING TO WORK[/SIZE]

Seconded.

---

### Post by coffeecat on 2012-09-08
@eneskuray, I have to say that I agree with those who say that what you are trying to do is unlikely to work. The important point is that this is the Ubuntu forums, whose purpose is to provide support for Ubuntu. If anyone knows whether it is possible to run apt-get in Arch and how to achieve this then you will probably find them [here](https://bbs.archlinux.org/).

Thread closed.

---

