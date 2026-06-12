---
title: "Poor audio quality?"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by Kanark on 2006-08-30
alright, im a long time user of windows, and ive just recently started using ubuntu.

ive gotten used to the luxery of better audio drivers and ease of installations.

alright, thats somewhat beside the point. ive tried using the many media players built into ubuntu, and through all of them I have the same problem: poor sound quality.

so im thinking its a drivers problem. so, i have 2 questions.

1. Is there a way i can better customize audio options (ive tried volume control already)

or

2. I have a disc that came with my motherboard, my ASUS disc that comes with the realtek audio drivers. So how can i install my (probably better?) audio drivers? (it does come with a linux driver file).

---

### Post by TFX360 on 2006-08-30
> **Kanark said:**
> alright, im a long time user of windows, and ive just recently started using ubuntu.

ive gotten used to the luxery of better audio drivers and ease of installations.

alright, thats somewhat beside the point. ive tried using the many media players built into ubuntu, and through all of them I have the same problem: poor sound quality.

so im thinking its a drivers problem. so, i have 2 questions.

1. Is there a way i can better customize audio options (ive tried volume control already)

or

2. I have a disc that came with my motherboard, my ASUS disc that comes with the realtek audio drivers. So how can i install my (probably better?) audio drivers? (it does come with a linux driver file).


Dear Kanark,


Can you give us the name of the driver on the disc?

---

### Post by Kanark on 2006-08-30
it comes in a archive file, named alc-082604.tar.bz2

---

### Post by TFX360 on 2006-08-30
> **Kanark said:**
> it comes in a archive file, named alc-082604.tar.bz2

Copy the file to you home dir.

```
tar -xvjf alc-082604.tar.bz2
```

```
cd alc-082604
```

and then probably

```
./install
```

Or look for a green (executable) install file and ./ that.

---

### Post by Kanark on 2006-08-30
hmm, the first command thing worked, the second 2 didnt.

i got this error.

```
kanark@kanark-desktop:~$ cd alc-082604
bash: cd: alc-082604: No such file or directory

```

---

### Post by TFX360 on 2006-08-30
Could you paste the response of the command

```
ls -hs
```

---

### Post by Kanark on 2006-08-30
```
kanark@kanark-desktop:~$ ls -hs
total 2.0M
2.0M alc-082604.tar.bz2  4.0K Desktop
4.0K alsa-driver-1.0.4   4.0K Journey-Greatest Hits-[1992-mp3-320vbr]
4.0K Audio

```

---

### Post by TFX360 on 2006-08-30
> **Kanark said:**
> ```
kanark@kanark-desktop:~$ ls -hs
total 2.0M
2.0M alc-082604.tar.bz2  4.0K Desktop
4.0K alsa-driver-1.0.4   4.0K Journey-Greatest Hits-[1992-mp3-320vbr]
4.0K Audio

```

Stupid driver makers

It should be:

```
cd alsa-driver-1.0.4
```

---

