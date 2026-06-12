---
title: "audacity works for one user, not for another."
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by beanco on 2008-01-22
so user aron cannot get audacity to run/work

user robi gets it open and running no worries.

i thougth I would 

```
sudo get-apt purge audacity
```

and then reinstall but I get the

```
Invalid purge operation
``` error

so what is wrong?

robi

---

### Post by django0909 on 2008-01-22
I'm not going to pretend I know what I'm talking about, but isn't it 

sudo apt-get

not

sudo get-apt?

---

### Post by sisco311 on 2008-01-22
add the user to the audio group:
```
sudo usermod -a -G audio <username>
```

---

### Post by beanco on 2008-01-22
that was a typo, sorry.

I just tried it again

rob@rob-desktop:~$ sudo apt-get purge audacity

E: Invalid operation purge

---

### Post by beanco on 2008-01-22
> **sisco311 said:**
> add the user to the audio group:
```
sudo usermod -a -G audio <username>
```


a n00b question ,but what will this do?

robi

---

### Post by sisco311 on 2008-01-22
the command will add <username> user to the audio group. to use audio devices the user must be member of this group.

---

### Post by beanco on 2008-01-22
> **sisco311 said:**
> the command will add <username> user to the audio group. to use audio devices the user must be member of this group.

will give it a try

robi

---

### Post by beanco on 2008-01-22
ok so it runs, opens, whatever, but there is no sound!!!!

I played an mp3 file under my account, no problems,

under aron's account there is no sound

robi

---

