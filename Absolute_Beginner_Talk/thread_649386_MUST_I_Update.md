---
title: "MUST I Update???"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by RVcook on 2007-12-24
I'm running Kubuntu Edgy now and the update manager has informed me that there are 195 updates available.  However, when I go to upgrade, I get an error message telling me that the Update Manager has crashed so no updates are installed.  I've searched and can not find anyway to "fix" this.

Since I use Kubuntu mainly for web surfing and little else, should I be concerned about updates?  My printer works and I can surf with no problems.

Soooooooooooo...***MUST*** I update?

---

### Post by Lvcoyote on 2007-12-24
I think you answered your own question.  If it does what you want it to do, then no... you dont "have" to update.

---

### Post by Sef on 2007-12-24
The best reason for updating is security patches, so your computer is harder to crack.  Otherwise there is no need to update for simply getting a newer version of a program if you are happy with the current one.

---

### Post by p_quarles on 2007-12-24
If you're not running any server software, practice safe web-surfing, and are currently happy with how things are working, there's no pressing reason to upgrade.

If you do feel the need to keep your system up-to-date, though, you can just bypass Adept by running the same function from the command line (much less likely to crash):
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Sef on 2007-12-24
```
If you do feel the need to keep your system up-to-date, though, you can just bypass Adept by running the same function from the command line (much less likely to crash):
Code:

sudo apt-get update && sudo apt-get upgrade


```


That is not quite correct.  The OP is running Kubuntu.  Sudo is for Ubuntu.  

If memory serves me right the correct code would be 

```
kdesu apt-get update && sudo apt-get upgrade
```

---

### Post by HermanAB on 2007-12-24
Simple: Don't fix it if it ain't broke.

Linux is very stable.  I only update desktop systems when I want the latest version, which once every year or two.

---

### Post by p_quarles on 2007-12-24
> **Sef said:**
> ```
If you do feel the need to keep your system up-to-date, though, you can just bypass Adept by running the same function from the command line (much less likely to crash):
Code:

sudo apt-get update && sudo apt-get upgrade


```
That is not quite correct.  The OP is running Kubuntu.  Sudo is for Ubuntu.  

If memory serves me right the correct code would be 

```
kdesu apt-get update && sudo apt-get upgrade
```
Sorry, Sef, but you're wrong. I run Kubuntu as well. "kdesu" is for graphical applications only, and apt-get is not a graphical application. The command I gave the OP is correct.

EDIT: Link: [B][http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

[/B]

---

### Post by Aseld on 2007-12-24
> That is not quite correct.  The OP is running Kubuntu.  Sudo is for Ubuntu.  

If memory serves me right the correct code would be 

```
kdesu apt-get update && sudo apt-get upgrade
```

Are you certain? I'm a newbie, but my understanding is that sudo is not attached to any desktop environment; it's a core GNU/Linux program. Unless my understanding is very flawed, sudo is the correct way to run command line programs as root in any Ubuntu variant.

---

### Post by ~LoKe on 2007-12-24
> **Sef said:**
> That is not quite correct.  The OP is running Kubuntu.  Sudo is for Ubuntu.  

If memory serves me right the correct code would be 

```
kdesu apt-get update && sudo apt-get upgrade
```

sudo is not environment specific, so its use is welcome.  kdesu and gksu are for graphical applications from their respective environments.

---

### Post by RVcook on 2007-12-24
Thank you all for your very prompt answers.  I may manually try to update IF and WHEN I feel the need to.  I haven't had much luck with running the apt-get command in the past, but I might try it again.  Thanks everyone!

---

