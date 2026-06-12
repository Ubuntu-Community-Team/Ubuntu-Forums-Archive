---
title: "how to install pidgin from source code ??"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by Aamir Aziz on 2007-08-19
i'm trying install pidgin from source code but when i write **./configure** it gives the error:
i.e.


configure: error:

You must have the GLib 2.0 development headers installed to build.


how should i install GLib 2.0 ???

---

### Post by nemequ on 2007-08-19
I would advise against installing it from source without good reason, but...

```
sudo apt-get build-dep gaim
```

Should install all the dependencies you'll need.

---

### Post by Ek0nomik on 2007-08-19
> **Aamir Aziz said:**
> i'm trying install pidgin from source code but when i write **./configure** it gives the error:
i.e.


configure: error:

You must have the GLib 2.0 development headers installed to build.


how should i install GLib 2.0 ???

```
sudo apt-get install libglib2.0-dev
```

---

### Post by Raptor45 on 2007-08-19
I have to ask... why are you doing this?

Especially for something like Pidgin which is available pre-built from lots of places...

I feel I have to say that this is a case where if you don't know how to find build dependencies, you probably shouldn't be compiling software.

---

### Post by Ek0nomik on 2007-08-19
> **Raptor45 said:**
> I have to ask... why are you doing this?

Especially for something like Pidgin which is available pre-built from lots of places...

I feel I have to say that this is a case where if you don't know how to find build dependencies, you probably shouldn't be compiling software.

He wants to compile it from source, so let him do it.  Just because he doesn't know exactly how to do it doesn't mean he can't have an urge to learn how.

It's a good thing to learn when certain software doesn't come in *.deb form.

---

### Post by Raptor45 on 2007-08-19
> **Ek0nomik said:**
> He wants to compile it from source, so let him do it.  Just because he doesn't know exactly how to do it doesn't mean he can't have an urge to learn how.

It's a good thing to learn when certain software doesn't come in *.deb form.

Ah, but he never specified he was doing it just for the experience.

If thats the case, then thats just fine and dandy and I'd be happy to help learn. However, its worth pointing out that theres a chance that unusual troubles might arise.

If on the other hand, the goal is just to install a newer version, a much simpler solution is to go to getdeb and download.

---

### Post by happy-and-lost on 2007-08-19
As a quick warning, MSN won't work on a hand-compiled Pidgin unless you include SSL support whilst doing so.

---

### Post by walkerk on 2007-08-19
> **Raptor45 said:**
> Ah, but he never specified he was doing it just for the experience.

If thats the case, then thats just fine and dandy and I'd be happy to help learn. However, its worth pointing out that theres a chance that unusual troubles might arise.

If on the other hand, the goal is just to install a newer version, a much simpler solution is to go to getdeb and download.

I prefer to compile from source so that I can configure the software before compiling it. Another reason is to be able to upgrade as soon as new versions are released. It's not hard and there is no reason to wait for someone else to do the work before you can benefit from new software.

---

### Post by Arthur Archnix on 2007-08-19
I think he's got his answer from above. But I agree with some of the above, I think if you're the kind of person who likes to compile from source to keep up to date with the latest apps... well, why are you using ubuntu? You'd be much happier with Gentoo or Arch, no? When using Ubuntu you should only compile from source to achieve specific goals, and it's really not clear from the OP that that is the intent.

/2cents.

---

### Post by RomeReactor on 2007-08-19
> **Arthur Archnix said:**
> I think he's got his answer from above. But I agree with some of the above, I think if you're the kind of person who likes to compile from source to keep up to date with the latest apps... well, why are you using ubuntu? You'd be much happier with Gentoo or Arch, no? When using Ubuntu you should only compile from source to achieve specific goals, and it's really not clear from the OP that that is the intent.

/2cents.

I think compiling is a great way to learn about programs. Granted that many people won't know they can get the program in a deb package, and get themselves in a problem that may very well frustrate them; however, that doesn't mean that if a person is aware of the precompiled alternatives and still they want to compile (for whatever reason), we should deter them. On the contrary: we should encourage them and provide as much help as possible.

I completely agree with Ek0nomik.

> **Raptor45 said:**
> Ah, but he never specified he was doing it just for the experience.

If thats the case, then thats just fine and dandy and I'd be happy to help learn. However, its worth pointing out that theres a chance that unusual troubles might arise. (*SNIP*)

Why should we question their motivation? as long as there is an awareness of the process and that there are alternatives, as you yourself said, they will gain from the experience.

---

### Post by walkerk on 2007-08-19
> **Arthur Archnix said:**
> I think he's got his answer from above. But I agree with some of the above, I think if you're the kind of person who likes to compile from source to keep up to date with the latest apps... well, why are you using ubuntu? You'd be much happier with Gentoo or Arch, no? When using Ubuntu you should only compile from source to achieve specific goals, and it's really not clear from the OP that that is the intent.

/2cents.

LOL. So you're saying because I like to compile I shouldn't use Ubuntu? I use Ubuntu because I like the community. I've been through fedora, opensuse, and arch linux and liked them all. Ubuntu was the last I tried with the intent of moving to debian.. but got comfortable.. :)

---

### Post by Arthur Archnix on 2007-08-19
> **RomeReactor said:**
> I think compiling is a great way to learn about programs. Granted that many people won't know they can get the program in a deb package, and get themselves in a problem that may very well lead them back to windows; however, that doesn't mean that if a person is aware of the precompiled alternatives and still they want to compile (for whatever reason), we should deter them. On the contrary: we should encourage them and provide as much help as possible.

I completely agree with Ek0nomik.

Sure Rome, I agree with your comments about compiling and learning. But I'm also mindful of the ubuntu forum guidelines, as well as the intent of ubuntu in general. For instance, one of the ubuntu recommendations on how to respond to help requests states:
> Please remember to do things the Ubuntu way. There are always more than one solution to a problem, choose the one you think will be the easiest for the user. Automatic package installation (using Synaptic, Aptitude, or apt) over manual installation. DEB over source. Please never instruct users to do anything that might break their system, this includes using --force and -ignore-depends when installing a DEB. Try to think as a green user and choose the simplest solution.
Now, I realize that helping this user compile pidgeon doesn't in any way violate that guideline, but at the same time, if their goal is to gain a deep understanding of linux and maintain the most up to date systems, advising them that there are other distros more in line with those aims isn't out of line. 

And remember that when I suggested that arch or gentoo might better suit someone who wanted to compile programs and stay very current,  I also noted that someone had already provided them with the answer they sought. My comments about seeking out a different distro that would be more in their with their goals was made after someone had already provided them with the information they sought, and if they hadn't gotten that information already i would have tried to point them in the right direction of doing it in Ubuntu, before suggesting that another distro might be a better choice.

> LOL. So you're saying because I like to compile I shouldn't use Ubuntu? 

No, not at all. But frankly, if you like to compile and stay current then you should certainly take a look at other distros, as you have done, before deciding that Ubuntu is the only one for you.

---

### Post by oldHat on 2008-01-13
Sorry, I didn't read the whole thread, so I might have missed another solution.

The following link (where it tells which libraries to add) helped me to solve the GTK issue.

[http://jhcore.com/2007/06/04/install-pidgin-in-ubuntu/](http://jhcore.com/2007/06/04/install-pidgin-in-ubuntu/)

---

### Post by kevdog on 2008-01-14
Here's the best link I know of telling you how to compile pidgin.  Its a lot of steps, but very straightforward.  You will like the results:

[http://ubuntuforums.org/showthread.php?t=658244&highlight=pidgin](http://ubuntuforums.org/showthread.php?t=658244&highlight=pidgin)

---

