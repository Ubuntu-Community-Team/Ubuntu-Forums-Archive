---
title: "Make isn't working."
date: 2006-01-03
forum: Absolute Beginner Talk
---

### Post by doug.barrett on 2006-01-03
This is an extreme newb question, and I have tried searching the forums but I have had no luck.

I am trying to install the ndiswrapper so I can have support on my laptop for my wireless card.

One of the first things it tells me to do is to:

```
make uninstall
```

I did that, but I get the error:

```
bash: make: command not found
```

My friend told me I would have to install the dev packages, and that is fine with me because I can always go into my other room and plug in my computer to our router to get online, I just need to know what I have to download.

I am using Ubuntu 5.10 if that makes any difference

Thank you very much :smile:

---

### Post by gnu2tux on 2006-01-03
[QUOTE=doug.barrett]This is an extreme newb question, and I have tried searching the forums but I have had no luck.

I am trying to install the ndiswrapper so I can have support on my laptop for my wireless card.

One of the first things it tells me to do is to:

```
make uninstall
```

I did that, but I get the error:

```
bash: make: command not found
```

My friend told me I would have to install the dev packages, and that is fine with me because I can always go into my other room and plug in my computer to our router to get online, I just need to know what I have to download.

I am using Ubuntu 5.10 if that makes any difference

Thank you very much :smile:[/QUOTE]

Hi,

 Install the gcc and make packages from Synaptic Package Manager.

Cheers,
Al.

---

### Post by carlosqueso on 2006-01-03
What would be faster is to type: ```
sudo apt-get install build-essential
``` and that should get you all of the developoment packages you need unless you're doing crazy stuff.

---

### Post by bluefrog on 2006-01-03
needs to be installed to work


sudo apt-get install build-essential

james

---

### Post by doug.barrett on 2006-01-03
Thank you very much all! I think i have figured it out :)

---

