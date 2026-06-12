---
title: "Improving efficiency of a &quot;largest prime factor&quot; problem"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by ConMan318 on 2008-04-10
I just started learning Python, and I have been doing the Euler problems.  I've done six of them, and I am trying to do #3 now.  It is:
```

       The prime factors of 13195 are 5, 7, 13 and 29.
       What is the largest prime factor of the number 600851475143 ?

```

I have written a script that works for smaller numbers (it works for numbers in the millions in .8 seconds) but for a number this big it would take forever.

Essentially I check every odd integer starting from half the original value and work my way down.  If an integer goes into the big number, I check if it is prime.  Since I am counting down, the first prime that goes into it will be the answer, so I break from the loop and print it.

Here is my script:
```

number = 600851475143
currentNumber = number / 2
if currentNumber % 2 == 0:
   currentNumber = currentNumber - 1
prime = 2
while currentNumber > 0:
   flag = 0
   check = 2
   if number % currentNumber == 0:
      while check < currentNumber / 2 and flag == 0:
         if currentNumber % check == 0:
            flag = 1
            break
         check = check + 1
      if flag == 0:
         prime = currentNumber
         break
   currentNumber = currentNumber - 2
print prime
```
I am quite sure I am going about this in a terrible fashion.  I don't need a code, just an idea of a different way to go about this (also, I only know C and BASIC now, so if I have done anything in an odd way in Python, let me know).

Thanks.

---

### Post by tamoneya on 2008-04-10
i think it will be more efficient if you start at the bottom and work your way up.  Say you number is 2*3*7*4723.  (4723 is a prime).  This equals 198366.  If you start at 1/2 this number and work down you wont get anything until you get to 4723.  That is 94460 that you have to check.  Instead if you work from the bottom.  You get that 2 is a factor.  Then you add 2 to a list of factors and then you take the number 198366/2 and find the factors of this. In this example you would have had to check for 2 + 3 +7+4723 = 4735 which is much better than 94460.

Worst case scenario your number is two large primes that are very close to each other. 5233*5237 = 27405221.  If you used your method you would have to check from 13702610 down to 5237 which is 13697372.  With my method you check up to 5233 + 5237 = 10470.  As the numbers get larger the gain of my method will only increase.

---

### Post by ConMan318 on 2008-04-10
So each time your currentNumber went into number, you would divide number by currentNumber, and then continue the process with the new, smaller, number?

In that case, where would you check for the largest **prime** factor?  I assume you would store each of the factors into an array and then check at the end which of them are prime.  Correct?

Also, what if a number was divisible by 2, and then divisible by 2 again, let's say 8 as a very simple example.  So since 2 is a factor, it would divide by 2, so the new number is 4.  Would the counter have to be reset every time a factor is found?  In your example, each factor is larger than the last; what if there is a point where there is another factor, but it is lower that your last factor?  Wouldn't it cause a problem?  Or would that mathematically not ever happen.


EDIT:
Sorry, I get it now, and I got it to work in .031 seconds.  Disregard the above.

And thank you!

---

### Post by tamoneya on 2008-04-10
how is it working on really large numbers.  I would like to see how large a number it can handle

---

### Post by ConMan318 on 2008-04-10
With this code:
```

number = 1000200851465142
currentNumber = 2
while currentNumber <= number / 2:
   if number % currentNumber == 0:
      number = number / currentNumber
      print currentNumber
   currentNumber = currentNumber + 1

```

I got it to run in:
```

$ time python euler3.py
2
3
41
43
409
4703

real    0m0.053s
user    0m0.056s
sys     0m0.000s

```

That number is over 10^15, so I'd say it's pretty good.  Go much higher than that and it gets a little iffy, though.  It depends on the number though; if it finds a few smaller factors quickly it'll cut down the size, and numbers with only a couple factors take a while.  I added a couple more zeroes though and it still runs in under a second...

...Python rocks!  The limited storage capabilities of C always angered me.

Thanks again.

---

