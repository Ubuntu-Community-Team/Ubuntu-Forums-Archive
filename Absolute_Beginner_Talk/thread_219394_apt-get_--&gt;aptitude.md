---
title: "apt-get --&gt;aptitude"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by TheRingmaster on 2006-07-19
Can I download something with synaptic (apt-get) and then remove it aptitude?

---

### Post by aysiu on 2006-07-19
Yes, but the dependencies won't be removed along with it.

---

### Post by TheRingmaster on 2006-07-19
Is there a way to tweak this?

---

### Post by metaltailz on 2006-07-19
The easiest way is just to use aptitude, if you want to search for something using aptitude just use this code

```

sudo aptitude search ____

```

It will pull up a list with any program containing what ever you put.

What I sometimes do is look around in Synaptic to find a program and then use aptitude to download and install it.

---

### Post by mozetti on 2006-07-20
Does Synaptic use aptitude, or apt-get? If it's apt-get, why was that chosen over aptitude?

---

### Post by aysiu on 2006-07-20
> **mozetti said:**
> Does Synaptic use aptitude, or apt-get? If it's apt-get, why was that chosen over aptitude?
Synaptic uses *apt-get*.
I don't know why that was chosen.
I hear that they're working on a smart package manager for Edgy called... Smart.

---

### Post by mozetti on 2006-07-20
> **aysiu said:**
> Synaptic uses *apt-get*.
I don't know why that was chosen.
I hear that they're working on a smart package manager for Edgy called... Smart.

Hmmmm, I see. Very cryptic. :p

---

### Post by lzfy on 2006-07-20
Can someone tell me what the difference is? :rolleyes:

---

### Post by aysiu on 2006-07-20
> **lzfy said:**
> Can someone tell me what the difference is? :rolleyes:
[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

### Post by AirRaven on 2006-07-20
> **aysiu said:**
> Synaptic uses *apt-get*.
I don't know why that was chosen.
I hear that they're working on a smart package manager for Edgy called... Smart.

Apt-get gives you more control over what's installed and removed, I think. Aptitude just removes the whole lot at once, while apt-get only removes what you tell it to.

At least that's what I've observed. I know practically nothing on this subject- so feel free to correct me.

---

### Post by aysiu on 2006-07-20
You're absolutely correct, AirRaven.

The problem is that most people on these forums (the ones I've seen anyway) *want* the whole lot removed.

Personally, I don't care if I have "orphaned" packages. I have plenty of hard drive space (160 GB), so it's no skin off my back.

---

### Post by akniss on 2006-07-20
> **aysiu said:**
> [http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

aysiu: is that your site? its fantastic!  I wish I would have seen it before now!

---

### Post by aysiu on 2006-07-20
> **akniss said:**
> aysiu: is that your site? its fantastic!  I wish I would have seen it before now!
That's my site. I've put a lot of work into that site. Glad you like it.

---

### Post by lzfy on 2006-07-20
Thanks a lot aysiu, great site and very usefull :)

---

