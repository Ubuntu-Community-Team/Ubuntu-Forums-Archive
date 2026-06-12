---
title: "how to run a C program in anjuta?"
date: 2006-04-22
forum: Absolute Beginner Talk
---

### Post by medya on 2006-04-22
hello I am learning C language , i used to use Turbo C in windows, I was told that I would need Anjuta in ubuntu so I installed it , now I want to test a simple C program that Adds two number . I type the source in a new file of Anjuta .

```
#include <stdio.h>
main ()
{
int a,b,sum;
scanf("%d %d",a,b);
sum=a+b;
printf("%d",sum);
getch();

}

```
now I want to test the program , how can I do that ? I want to give 4 and 3 to the program and recive 7 .

---

### Post by ComplexNumber on 2006-04-22
first you need to compile it. then you can run it.

---

### Post by medya on 2006-04-22
I did complie it using f9 ... and it was compiled succefully, how I can run it ?

---

### Post by mostwanted on 2006-04-22
Open it in a terminal. Might wanna check this out:

[http://www.ubuntuforums.org/showpost.php?p=945432&postcount=5](http://www.ubuntuforums.org/showpost.php?p=945432&postcount=5)

---

### Post by medya on 2006-04-22
ok I found it, I had to build it first then excute it .

I did it but running the program I got error : 
here is a copy of my Runned Program Output.

> EXECUTING:
/home/fred/MyDocuments/test
----------------------------------------------
enter two numbers please4
5

----------------------------------------------
Program has been terminated receiving signal 11 (Segmentation fault)
Press the Enter key to close this terminal ...


whats the problem ? why it is not working ?

---

### Post by mostwanted on 2006-04-22
[QUOTE=medya]ok I found it, I had to build it first then excute it .

I did it but running the program I got error : 
here is a copy of my Runned Program Output.



whats the problem ? why it is not working ?[/QUOTE]

You haven't assigned anything to the variables you're trying to print. You need to make a reference to the variables you're filling up, otherwise you just get their contents, no assigning is ever done and printing out their values will be - to put it in Windows terms - an illegal action. Replace this line

```
scanf("%d %d",a,b);
```

with 

```
scanf("%d %d", &a, &b);
```

and remove that getch() thing at the end, that's just so Windowsy.

Edit: Maybe you should get a better resource for learning C? If what you're using now is teaching you this, then it's not a very high quality book/website.

---

### Post by medya on 2006-04-22
thanks a lot, can you advise me to some good books ?

by the way , which one should I start to learn, C or C++ ? which one is better?

---

### Post by mostwanted on 2006-04-22
[QUOTE=medya]thanks a lot, can you advise me to some good books ?

by the way , which one should I start to learn, C or C++ ? which one is better?[/QUOTE]

Well, both are archaic and overly complex languages in my opinion, but if you need to learn one of them, C will be the most simple language, but C++ will be the better one in the long run (it has a lot of object oriented features, but can still use old C APIs).

If you want to learn a really cool language, then I suggest that you learn Ruby, even though it's a scripting language.

If you want a language that's more like C/C++ then C# is there. C# looks and acts a lot like Java, but has some really nice improvements over it. You don't need to do any memory management like in C/C++ because there's a garbage collector.

But you shouldn't settle on a single language. All those languages are there to be explored by you :)

If you want a good book then I suggest "Beginning Linux Programming" by Richard Stones and David Matthew. It starts off teaching you BASH shell, scripting then evolves into C, Perl, Tcl, GUI programming with Gtk+ and Tk and teaches a lot of Linux specific techniques such as creating makefiles and so on. Doesn't really matter that's it not my favourite languages it teaches, because it's a great book for an overview.

If you want a C or C++ book, I can't help you there. Might wanna try asking for help with choosing one in the programming forum.

---

### Post by malavar on 2006-04-22
hey a decent book thats cheap, is practical c programming by steve Oualline. maybe check it out on amazon.com or a local library.

---

### Post by medya on 2006-04-22
thanks I love to learn Programming for Linux, one of my ambitions is to make programs for linux.
I already know pascal / html and a bit php .
do you think I can be a linux programmer in a few week ?
which programming language is being teached in "Beginning Linux Programming" book ? is it a special lanugage for linux ?

+ rudy ? never heared about it ...

---

### Post by mostwanted on 2006-04-22
[QUOTE=medya]thanks I love to learn Programming for Linux, one of my ambitions is to make programs for linux.
I already know pascal / html and a bit php .
do you think I can be a linux programmer in a few week ?
which programming language is being teached in "Beginning Linux Programming" book ? is it a special lanugage for linux ?

+ rudy ? never heared about it ...[/QUOTE]

As I said, it was a variety of languages. If you re-read my post you'll see I've already mentioned what languages it goes through.

And it's Ruby, not Rudy :p

[http://poignantguide.net/ruby/](http://poignantguide.net/ruby/)

---

