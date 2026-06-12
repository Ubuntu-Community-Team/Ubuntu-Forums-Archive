---
title: "Where is my dvdauthor"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by Hoom@n on 2008-02-12
Hello!
I installed dvdrip using apt-get. It was great, so I decided to test dvdauthor also. But:
```
hooman@hooman-laptop:~/.Trash$ sudo apt-get install dvdauthor
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dvdauthor is already the newest version.
dvdauthor set to manual installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
There is nothing with the name "dvdauthor" in my applications menu. Where is it?
+++
I have k9copy, is it the reason that I have dvdauthor invisible?
+++
Can I just use k9copy to make dvd from avi file or not?
____
Thanks.

---

### Post by neurostu on 2008-02-12
did you try:
```

$dvdauthor

```

---

### Post by Hoom@n on 2008-02-14
Thanks, please see the result:
```
hooman@hooman-laptop:~$ $dvdauthor
hooman@hooman-laptop:~$ 
```
Nothing oppened. What should I do?
Thanks.

---

### Post by hyper_ch on 2008-02-14
and 

```

man dvdauthor

```

---

### Post by wjston on 2008-02-14
> **Hoom@n said:**
> Hello!
I installed dvdrip using apt-get. It was great, so I decided to test dvdauthor also. But:
```
hooman@hooman-laptop:~/.Trash$ sudo apt-get install dvdauthor
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dvdauthor is already the newest version.
dvdauthor set to manual installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
There is nothing with the name "dvdauthor" in my applications menu. Where is it?
+++
I have k9copy, is it the reason that I have dvdauthor invisible?
+++
Can I just use k9copy to make dvd from avi file or not?
____
Thanks.

Dvdauthor runs in the background. If you want, you can install QDvdAuthor to have a Frontend. This will allow you to insert menus, slideshows, audio, and video that can be processed depending on your needs.

---

### Post by Hoom@n on 2008-02-16
Thanks, but how can I do that?
+++
By "man dvdauthor" I got a lot of things, but not how to run it!
____
Thanks.

---

### Post by vanadium on 2008-02-16
dvdauthor is a command line program. You need to know the command line syntax to work directly with it. There is good accessible documentation on the dvdauthor website for this.

Alternatively, you use it through various graphical frontends. k9copy probably relies on dvdauthor for the DVD video creation part of its functionality. As hinted by wjston, qdvdauthor is a graphical frontend, another one (and somewhat easier for a novice, I find) is dvdstyler.

---

### Post by wjston on 2008-02-19
> **Hoom@n said:**
> Thanks, but how can I do that?
+++
By "man dvdauthor" I got a lot of things, but not how to run it!
____
Thanks.

Either use "sudo apt-get qdvdauthor" or start synaptic package manager>search for qdvdauthor> and install it. Look in Applications>Sound and Video then you should be able to start it from there. Hope this helps.

---

