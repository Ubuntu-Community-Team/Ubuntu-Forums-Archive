---
title: "how do i compile c++?"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by smurf killer on 2007-03-27
hi how can i compile a c++ program? i use the anjuta IDE. i have tried with the g++ command but it didn't recognise it.

---

### Post by Lord Illidan on 2007-03-27
First you must install the compiler with the following command:

```
sudo apt-get install build-essential
```

---

### Post by smurf killer on 2007-03-27
thanks now i can compile with g++ test.cpp but where does it put the compiled program at? and isn't there a /test function or something?

---

### Post by monkeyking on 2007-03-27
It depends on how you have set it up.

if your compile command was 
```

g++ test.cpp

```

then your program is called a.out and you can run it from the promt with
```

./a.out

```

If you compiled with 
```

g++ -o test test.cpp

```

then your program is called test and you can run it with
```

./test

```

---

