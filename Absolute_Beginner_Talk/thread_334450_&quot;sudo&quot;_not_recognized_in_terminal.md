---
title: "&quot;sudo&quot; not recognized in terminal"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by jerrynewt on 2007-01-08
I can't seem to use the sudo command in terminal anymore-When I tried "gksudo network-manager" I get "sudo: unable to lookup (none) via gethostbyname ()" as a response.  Any ideas as to what I might have done wrong? I am running Ubuntu 6.06.1 on a Toshiba Satellite Pro--768 M RAM--40 Gig HD--dual boot with windowz. Also I can't run any admin apps such as synaptic or network from the menu.

---

### Post by Voxxi on 2007-01-08
Sounds like your /etc/hosts or /etc/hostname are screwed up, have you modified them recently?

Post the output of:

```
cat /etc/hosts
```

and

```
cat /etc/hostname
```

---

### Post by c-ron on 2007-01-08
Is your hostname set?

You can try resetting it with:
sudo hostname <yourhostname>

---

### Post by Voxxi on 2007-01-08
> **c-ron said:**
> Is your hostname set?

You can try resetting it with:
sudo hostname <yourhostname>

But, he can't sudo. ;) 

I looked it up some more and [this post]("http://www.ubuntuforums.org/showpost.php?p=1549563&postcount=3") might be helpful.

---

### Post by jerrynewt on 2007-01-08
Thanks for quick replies. I will post the results of the commands and try the link out and let you know. Since I am on windoz now, I will be back in a few.

---

