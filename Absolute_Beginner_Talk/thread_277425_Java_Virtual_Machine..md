---
title: "Java Virtual Machine."
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by sanderella on 2006-10-14
Is it possible to install this in Ubuntu? Any help appreciated.:)

---

### Post by meng on 2006-10-14
Yes check the wiki, it's a great resource for all manner of questions.
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by Delkster on 2006-10-14
Sure, the Sun Java VM is available in the Ubuntu software repositories. A free, open source implementation of Java is also installed by default but it's not complete yet and doesn't run all applications.

1. Open **Applications > Add/Remove** in the menu.
2. Make sure that "**Show unsupported applications**" and "**Show commercial applications**" are selected.
3. Enter `**java**' in the search box and browse the list down to "**Sun Java 5.0 Runtime**". Select the checkbox next to it to install, and click on "**Apply**" or "**Ok**".

Since there's the open source JVM also installed, you'll probably want to set the Sun package you just installed as the default one as instructed on the [Ubuntu Community help page for Java](https://help.ubuntu.com/community/Java#head-fef9352fb26820bb774df978180c9dd3a60e777b). That page is also a good resource for other things regarding Java on Ubuntu and also includes installation instructions but I still decided to write up my own here because not everything on that page goes to the very specifics.

---

### Post by TooRight on 2006-10-14
I was finally able to get it installed on my comp, but then had difficulties installing it on a friend's computer... however, after finding out about Automatix in another thread I talked him through the installation of that over the phone and then with it he was able to flawlessly and easily install sun java. It also has auto installs of loadsssss of other stuff; you should check it out!!

---

### Post by sanderella on 2006-10-15
Thanks guys, but when I did this I got the message

"Sun Java 5 Runtime is not available in any channel.The application might not support your system architecture"

](*,) 

Help please?

---

### Post by Delkster on 2006-10-15
> **sanderella said:**
> Thanks guys, but when I did this I got the message

"Sun Java 5 Runtime is not available in any channel.The application might not support your system architecture"

What kind of a computer do you have? Is it a 64-bit one, or a 32-bit Intel/AMD (a.k.a. x86), or a PPC (such as older Macs)?

You could try entering this in the terminal to find out:
```
uname -m
```

---

### Post by sanderella on 2006-10-16
What kind of a computer do you have? Is it a 64-bit one, or a 32-bit Intel/AMD (a.k.a. x86), or a PPC (such as older Macs)?

You could try entering this in the terminal to find out:
Code: uname -m

The answer was i686

Sanderella

---

### Post by Delkster on 2006-10-20
The Sun Java Runtime Environment is in the `multiverse' software repository due to its non-free (closed source) license. I thought Add/Remove Applications automatically enables the repository for you if you try to install an application that's only available in that repository, but I'm not sure about that after all. Thus, if you haven't enabled multiverse yet, you may need to do it as instructed in the wiki:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

I hope this information is still useful despite the few days' delay. (Okay, actually I hope you've got the problem solved already so, maybe it's better if it's no longer useful.)

---

### Post by sanderella on 2006-10-24
Thanks for your help, very kind of you. I've got java installed now.

---

