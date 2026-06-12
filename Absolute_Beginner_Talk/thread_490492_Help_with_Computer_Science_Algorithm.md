---
title: "Help with Computer Science Algorithm"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by dj44fan on 2007-07-02
Hello all -

I am taking computer science 111 and I am having a really hard time with this question - can somebody help please?  

"Design an algorithm for finding all the factors of a positive integer"  

Thanks for any guidance - maybe I am just making the question harder than it is.

Sandra:?:

---

### Post by LaRoza on 2007-07-02
You might find the modulus operater handy.

---

### Post by Praill on 2007-07-02
I probably shouldnt do your homework for you, but Im bored so youre lucky.
Here's a C example that should do just that. I havent tested it (im not going to do all the work) but it should give the general idea of what's required.

```

#include <iostream>

int main(int argc, char * argv[])
{
int num=argv[0];
cout << "Factors of " << num << ":" << endl;
for( int i=1 ; i<=num ; i++ )
{
if( num%i==0 ) cout << i << endl;
}
}

```

---

### Post by jordanmthomas on 2007-07-02
...and since you may not know c or what mod is because you're in an early CS class I'll explain it in English.
for all integers x from 1 up to the number, check to see if the remainder of (number / x ) is 0.
If it is, then x is a factor of your number.

Hopefully you should be able to follow this if you can't follow the c example above (which should work as advertised).

Of course, there's plenty more ways to do it if you're willing to read through them:
[http://en.wikipedia.org/wiki/Integer_factorization](http://en.wikipedia.org/wiki/Integer_factorization)

---

### Post by hill0093 on 2007-07-02
Try this too.
  protected int allFactors(int numb) { 
    int number=numb,factCnt=0; System.out.print(numb+"="); print(prFilStrm,": 1",prFilNam); 
    for(int curDivisor=2;curDivisor<=number;curDivisor++) { 
      if((number%curDivisor==0)) { 
        factCnt++; System.out.print(","+curDivisor); print(prFilStrm,","+curDivisor,prFilNam); 
    } } System.out.println(); println(prFilStrm,prFilNam); return(factCnt); 
  }

---

### Post by dj44fan on 2007-07-02
Thanks sooo much!  It makes sense now that I see how to do you - you rock and I'm glad you were bored.

---

### Post by bodhi.zazen on 2007-07-02
This type of thread is discouraged on the Ubuntu forums for obvious reasons.

Thread closed.

---

