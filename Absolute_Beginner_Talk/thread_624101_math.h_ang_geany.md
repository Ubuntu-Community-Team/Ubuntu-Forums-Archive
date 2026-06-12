---
title: "math.h ang geany"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by gryall on 2007-11-26
This might not be an absolute beginners sort of question - but it certainly feels like a noobish sort of one.

I recently started using C for my university course. I wrote a programme in C in xcode (on the departments macs - in there computing lab). Whilst in the lab the programme built and ran fine - so i know the code is Ok.

When i now come to try and build exactly the same code in geany it tells me it doesn't recognise the cos, pwr sqrt etc. operators. I have included the math.h header. I am wondering if the math.h libary is installed, how would i go about checking/installing it?

thanks for your help

---

### Post by mali2297 on 2007-11-26
Have you installed build-essential?
```

sudo apt-get install build-essential

```
The header file math.h is included in the package **libc6-dev** (that comes with  build-essential). The location should be 

**/usr/include/math.h**

---

### Post by gryall on 2007-11-27
I checked both of those had installed before posting. There is a math.h file in the location you've given, so maybe its the geany IDE thats got the problem?

---

### Post by mali2297 on 2007-11-27
What happens if you compile the program from the terminal?
```

gcc -o example example.c

```

---

### Post by gryall on 2007-11-27
```

main.c:(.text+0x256): undefined reference to `cos'
main.c:(.text+0x266): undefined reference to `log'
main.c:(.text+0x290): undefined reference to `sqrt'
main.c:(.text+0x2e8): undefined reference to `pow'

```

Same error as i got in geany so, it mus be the gcc compiler

---

### Post by mali2297 on 2007-11-27
Test
```

gcc -lm -o example example.c

```

I think one has to tell gcc to check for the math library, this is done by adding **-lm**.

---

### Post by gryall on 2007-11-27
that seems to have worked - but how do i get geany to do that?

---

### Post by gryall on 2007-11-27
sorry - have just found out how - I go to the build menu and then set includes and arguments.

Thanks for all your help - turned out it was a nooby qustion

---

