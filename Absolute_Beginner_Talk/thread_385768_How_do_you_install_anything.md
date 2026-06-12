---
title: "How do you install anything"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by jtx472 on 2007-03-16
How do I install after download?  I downloaded F-Prot for linux.  I see it on my desktop but what do I do now?  I also have stuff in Archive Manager but can't figure out how to install.  Thank you

---

### Post by petersjm on 2007-03-16
These links might be of help...
[How to Install Anything in Ubuntu](http://monkeyblog.org/ubuntu/installing/)

and

[How to install software on Linux](http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/64958-how-install-software-linux.html).

---

### Post by Quillz on 2007-03-16
Almost anything you could ever need is in your package manager. If you want to work in a GUI, that'd be Synaptic (Ubuntu) or Adept (Kubuntu.) If you prefer a CLI, then you run "apt-get install" commands in the Terminal.

---

### Post by hyper_ch on 2007-03-16
Just a question: What do you need F-Prot for?

---

### Post by jtx472 on 2007-03-16
Thank you for your replies.  I did as suggested and installed by using "sudo apt-get install aegis" and watched it install.  So now, how do I access the aegis scanner?  I still can't find it.  Thanks again

---

### Post by hyper_ch on 2007-03-16
Open a command terminal and enter the following command:

> 
ps aux | grep aegis


Plz post the output here :)

---

### Post by jtx472 on 2007-03-16
Dumb question...but how do I type that line in between "aux" and "grep"?  Thanks

---

### Post by hyper_ch on 2007-03-16
That depends on your keyboard. On my Swiss German keyboard I have to type AltGr + 7 but you have to be careful as there is a  | and ¦... you have to use the first one :)
For example @ is for me AltGr + 2

---

### Post by 23meg on 2007-03-16
The package you need to install if you want aegis isn't "aegis", but "aegis-virus-scanner". ```
sudo apt-get install aegis-virus-scanner
```

---

### Post by jtx472 on 2007-03-16
When I type that in "sudo apt-get install aegis-virus scanner" it says it' already installed with the newest version.  But I'd still like to know how to access it.  Thanks

---

### Post by 23meg on 2007-03-16
Hit Alt + F2 and type "aegis-virus-scanner" if it's not in your Applications menu.

---

