---
title: "General Synaptic Package Manager Question"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by chocomoojuice on 2006-12-09
It is to my understanding that most deb based programs will run on Ubuntu, but not all.  If a program or package shows up in the search results of Synaptic Package Manager, is it guaranteed to be completely compatible with Ubuntu?  I ask this because I'm currently looking into an mp3 player, and like the look of XMMS.
Thanks,
James

---

### Post by Famicommie on 2006-12-09
I suggest installing via the Applications->Add/Remove Programs interface.

That particular product manager gives me the message: "Canonical Ltd. provides technical support and security updates for XMMS Audio Player."

While I'm not sure that anything is 'guaranteed', that message is a strong indicator that it's damn likely to work no problem.

---

### Post by chocomoojuice on 2006-12-09
Oh wow, I never knew about this method of installing programs.  There's probably already an answer to this question floating around, but how is this application different from Synaptic?  What about Pros and Cons?

---

### Post by ciscosurfer on 2006-12-09
> **chocomoojuice said:**
> It is to my understanding that most deb based programs will run on Ubuntu, but not all.  If a program or package shows up in the search results of Synaptic Package Manager, is it guaranteed to be completely compatible with Ubuntu?  I ask this because I'm currently looking into an mp3 player, and like the look of XMMS.
Thanks,
JamesIf the sources that you have in your /etc/apt/sources.list (or in Synaptic, go here: System > Administration > Software Sources) contain Ubuntu repos, then they are guaranteed to run on Ubuntu distros.  If you've added different repos to your list, then you need to make sure they are made for Ubuntu and not, for example, strictly for Debian.

Synaptic is a great place to install apps.  If you'd like to know more about Synaptic and other ways of installing software, then you can check here: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Famicommie on 2006-12-09
> **chocomoojuice said:**
> Oh wow, I never knew about this method of installing programs.  There's probably already an answer to this question floating around, but how is this application different from Synaptic?  What about Pros and Cons?

Well, I'm no pro, so I'm sure that my answers are incomplete (and they might be wrong as well :O).

Add/Remove is simple and oriented for doing mundane tasks. I find it to be much easier than Synaptic.

Synaptic is much more comprehensive and much more powerful. It gives you total control over EVERYTHING installed on your computer.

The best comparison I can make is using your terminal as default versus using it as root. While root can do a lot more to the system than the normal user, root also has the ability to break the system if the root user doesn't know exactly what they're doing.

I try to only use Synaptic when I have no other choice.

---

