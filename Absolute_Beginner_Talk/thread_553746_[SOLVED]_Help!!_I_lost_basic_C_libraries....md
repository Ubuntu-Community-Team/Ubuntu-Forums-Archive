---
title: "[SOLVED] Help!! I lost basic C libraries..."
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by dalekos on 2007-09-18
Hey guys...

I'm a begginer and i did something wrong last night that has the following effects:

I made a C program today and while trying to compile it the gcc compiler told me:

```
askisi2_3.c:1:19: error: stdio.h: No such file or directory
askisi2_3.c:2:18: error: math.h: No such file or directory

```

how can i regain those libraries :confused: :confused:??? Please...

At synaptic the package: libc6   version:2.6.1-4 seems to be installed....

Thx for ur help!!

---

### Post by Bothered on 2007-09-18
You need the development libraries and headers. The package you need is "libc6-dev" (sudo apt-get install libc6-dev).

---

### Post by dalekos on 2007-09-18
First of all thanks for ur quick answer.

I tried but:

```
libc6-dev: depends on: libc6 (= 2.5-0ubuntu14) but 2.6.1-4 is to be installed.
```

---

### Post by ravenwere on 2007-09-18
This exact error message has now come up in the forums 3 times in the last few days and as yet I am not aware that anyone has found the cause of the problem.

I'm starting to think we have a bug or buggy package somewhere.

The solution in other cases was reinstall but that doesn't identify the cause of the issue.

Any ideas anyone????

---

### Post by dalekos on 2007-09-18
Does anybody have a solution?? 
It is very important for me right now!!!
I need badly to compile some programs...!!! :frown::frown:

---

### Post by Majorix on 2007-09-18
> **dalekos said:**
> Does anybody have a solution?? 

Only if you read the post above you carefully... :)

---

### Post by dalekos on 2007-09-18
reinstall what??

a certain package or the O.S.??

---

### Post by Arwen on 2007-09-18
Start by reinstalling gcc and libc6-dev..

---

### Post by dalekos on 2007-09-18
I reinstalled gcc and the problem still occurs. 
libc6-dev is not even installed and it doesn't let me install it.

---

### Post by LaRoza on 2007-09-18
```

sudo aptitude install build-essential

```

OR

Post your code (only preprocessor directive, please).

---

### Post by Arwen on 2007-09-18
You can't install this one,right?[https://launchpad.net/ubuntu/feisty/i386/libc6-dev/2.5-0ubuntu14](https://launchpad.net/ubuntu/feisty/i386/libc6-dev/2.5-0ubuntu14)

---

### Post by dalekos on 2007-09-18
Hey guyz... Thank you all.

What LaRoza told me worked:
```

sudo aptitude install build-essential
```

I can now work again!!! :guitar: :guitar:

---

### Post by Arwen on 2007-09-18
:shock: How did you install gcc in the first place without that?Whatever,since it's working you're OK:-)

---

### Post by ravenwere on 2007-09-18
This only gets more interesting.

Glad D you found a solution.

........but in one of the other threads the error message that D got appeared when he or she tried to install the build-essential package.

The solution they ended up applying was to reinstall the whole system but that seemed too drastic to me. They said they couldn't install the build-essential or libc6-dev package.

??????????

Maybe this will come up again.

---

### Post by ravenwere on 2007-09-18
PS the only difference I can see at the moment is Laroza used aptitude for the install instead of apt-get????

---

### Post by dalekos on 2007-09-18
i tried to install some webcam drivers last night and i think i messed it up and some packages vanished... Now i run this command and everything is fine again!!! :):)

---

### Post by ravenwere on 2007-09-18
Glad the reinstall worked Dalekos. Still think something else may be going on here but maybe I am looking too hard.

All the best.

---

