---
title: "Restricted formats issue"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by DeadEagle on 2008-01-26
Hi all, please forgive me if this has been covered...

Okay, I just tried to install the restricted format package in an attempt to get MP3's working in Amarok. Well, I let terminal do it's job, until it comes to a screen that says something about java installation, and it won't move on beyond this screen. Have I done something wrong?

---

### Post by LaRoza on 2008-01-26
You have to accept the agreement.

---

### Post by bumanie on 2008-01-26
It is most likely that you have not installed jre 6. In terminal type
sudo apt-get install sun-java6-plugin and hit enter
follow the instructions, including accepting the agreement.

---

### Post by LaRoza on 2008-01-26
> **bumanie said:**
> It is most likely that you have not installed jre 6. In terminal type
sudo apt-get install sun-java6-plugin and hit enter
follow the instructions, including accepting the agreement.

I think the poster is at the accepting agreement screen in the restricted-formats meta package.

---

### Post by DeadEagle on 2008-01-26
I got past one screen where I had to press "okay", and this screen looks very similar, though it's much longer, and it wouldn't let me accept....:confused:

*edit* I made the mistake of exiting Terminal, and I'm now getting this message : dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

---

### Post by schiznik on 2008-01-26
you need to run 'dpkg --configure -a' as it says, either as root or with sudo - this will finish off the last jobs that apt/dpkg were doing.

you might need to re-run 'aptitude install sun-java6-plugin' afterwards, depending on where it got to before.

---

### Post by chewearn on 2008-01-26
One thing to remember when getting stuck in the terminal with a long EULA page, and can't find a way to exit/accept the EULA: hit the TAB key.

---

### Post by DeadEagle on 2008-01-26
> **AstalaVista said:**
> One thing to remember when getting stuck in the terminal with a long EULA page, and can't find a way to exit/accept the EULA: hit the TAB key.

Oh... wow now I feel stupid.

How can I get terminal back to normal?

*edit* just so you guys know what I'm seeing: 

```
sean@SeanLinux-desktop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
```

---

### Post by chewearn on 2008-01-26
```

sudo dpkg --configure -a
```

---

### Post by DeadEagle on 2008-01-26
> **AstalaVista said:**
> ```

sudo dpkg --configure -a
```
And again, I feel stupid.

Thank you sir, terminal is doing *something* now.

---

### Post by chewearn on 2008-01-26
> **DeadEagle said:**
> And again, I feel stupid.

Thank you sir, terminal is doing *something* now.
No need to feel stupid; almost everyone is in the same boat at one time or another.):P

---

### Post by DeadEagle on 2008-01-26
okay... it appears that this issue is resolved

---

### Post by DeadEagle on 2008-01-26
Blargh. Amarok still won't compile a collection.

---

