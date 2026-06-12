---
title: "Repository security - software installs"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by icedogchi on 2007-02-16
Hello,

I have a general question on ubuntu/linux repositories.  Not how to find them or how to install software, but how to know if a repository is "safe".

I'm still brand spanking new to Ubuntu, and so far it's pretty sweet.  But installing software from a repository that I know little to nothing about makes me nervous.  I've googled for an answer, but most of the results are either about how to add a repository for aptitude, apt-get, etc, or about CVS.  heh.

Anyway, is there a general rule of thumb on what repositories are safe to install software from?  I don't want to accidentally install a trojan horse when I meant to install something else!

-jt

---

### Post by zvacet on 2007-02-16
You are not in the MS movie anymore.Don´t be afreid to install some unofficial rep,cose you will need it.

---

### Post by raffytaffy on 2007-02-16
hi. welcome aboard. one good way is to ask here...i myself use a wide array of dif repos. id post my source list..but i dont want to be blamed for breaking ppls systems.

---

### Post by H.E. Pennypacker on 2007-02-16
I don't pay any attention to who hosts a repository.....I've been using Ubuntu full time for about 6 months now, and haven't had a single problem.  

If you notice that a whole bunch of people are using the same repository (e.g. Automatix), you can be sure its safe.

---

### Post by Tomosaur on 2007-02-16
The repositories are 'signed'. When you manually add a new repository, you will often need to input a key. This key is kind of like a 'contract' between you and the person who manages the repository. If software in that repository is found to be malicious, then you have a record of who put it there. The key provides a kind of guarantee that the software is not malicious, and has not been tampered with to produce unexpected results. The repositories available to you by default are signed too, it's just that they're already set up for use straight away. The default repositories are also managed by the people who develop Ubuntu - so there's no reason not to trust them. After all, you're already using their code to run your computer!

---

### Post by emarkay on 2007-02-16
If it has "Ubuntu.com" in the URL it's prob 100% safe.
The Automatix folks seem to have a real tight ship so they are cool  IMHO.
Other than that, you are on your own!

---

