---
title: "Hello, lots of questions."
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by Baelari on 2007-11-02
I just recently switched to Linux, so I might as well post here, since I don't know where this would actually belong. More about programming languages and CS in general.:confused:

I'm thinking of switching back to CS as a major, (I've changed majors at least 7 times, yuck) I think it was the combination of hating my first college, my intro professor, and just being depressed in general, that made me switch from CS in the first place. I have a while to decide, as I'm doing the Study Abroad thing.

Anyhow, it's been almost 3 years since I've taken my Intro course, and have forgotten a lot of things. First question is, what languages would be a good starting point and would let me work with Japanese characters? (I usually study foreign languages with flashcards... but I've got over 300 to write at the moment, with more each week...  and I'd like them to be 3 sided) Writing a simple program seems the ideal thing to do; refresh what I learned my first semester of college, and save myself from being inundated with flashcards. I already have an idea of how to write it, but no idea what I can write it with. I've used Java before, but didn't really understand it, ergo I'm at square one with all of the languages. I think I learn faster with more in-depth explanation of why things work, as opposed to "it's more complex than the scope of this course, so don't worry about it now."  I suppose that's the long way of saying "what's a good starter language that can work with Unicode?"

Second question: any opinions on what is critical to learn in the first semester? The professor and I didn't match up very well.

Thirdly, does anyone know a good place to review trig and cal?

Also, does anyone know how to delete windows.old from a new installation of windows? It keeps saying it's shared, and I can't figure out how to stop it. I own the folder, and turned off the obnoxious security settings already, but it still says I don't have authorization. This OS tells me that it can't write to that disk.


Lastly, if anyone would take the time to explain public/private/protected/encapsulation and why it's needed, it would be appreciated.

&#12540;&#12424;&#12429;&#12375;&#12367;&#12362;&#39000;&#12356;&#12375;&#12414;&#12377;

---

### Post by gate on 2007-11-02
In my experience Java does well with unicode, I think it is it's default character system. 

Unfortunately I deeply dislike Java.

The reason you have to use the keywords "public/private/protected" etc is because java is whats called an objective language. it forces you to use objects, which are bundles of data with functions to act on the data. Public means that anyone interfacing with your code can access that function, private means only YOU can access that function, protected has to do with inheritance which is a really big topic. (all of this is a big topic :( )

 My program begins with C++, what we teach in the first semester is how to build a basic "hello world", then how to do the control structures like for/while/do/if etc. the first semester ends with functions (if you don't know, they are like stored procedures that act on input, etc). Our second semester begins to introduce what Java forces from day one, the Object Orientation, recursion (a function calling itself), pointers (if you don't know, I don't want to explain here) etc.

  My experience in languages: C++, C, C#, Java, Visual Basic, SML/NJ, Prolog. I like C++ mainly because it was my first language and it gives me alot of control that Java/C# abstract away. C++ is also easy to compile for different OSes (Java beats it there, though), it is fast, but it isn't terribly good for a beginner. 

I am a senior in CS btw.

---

### Post by jordanmthomas on 2007-11-02
I can add a little bit here.  When you ask what's important to learn in your first semester of programming is to think in terms of programming.  

You have to think in steps.  If you were the kind of person that has never liked showing their work in math, thinking in terms of programming may be tough.  Start by taking a task and thinking of every step you need to perform it.  If you know exactly what you want to do when programming, it makes the coding MUCH easier.  (I speak from experience...I often just start writing code without knowing exactly how to do what I'm wanting to do.  For what it's worth, I still do it and I'm a Junior studying CSC so I should know better by now.)

As for reviewing Trigonometry and Calculus, you honestly will only need bits of it that you can review as needed.  Here's a good site for Calculus with some easy to follow flash explanations:  [http://calc101.com/](http://calc101.com/)  (not sure on Trig, I've never had to review it...it's just stuck in my head)

> Also, does anyone know how to delete windows.old from a new installation of windows? It keeps saying it's shared, and I can't figure out how to stop it. I own the folder, and turned off the obnoxious security settings already, but it still says I don't have authorization. This OS tells me that it can't write to that disk.
You could mount it in Linux and delete it from there.  (look up ntfs-3g)

---

### Post by Baelari on 2007-11-03
Thanks for the replies

Showing my work, I never minded, writing out the theorems to justify my logic was a pain. I kind of think like that whenever I'm trying to plan anything

> Public means that anyone interfacing with your code can access that function, private means only YOU can access that function

I'm still not really getting it, does it even matter with simple things? Maybe a better question would be how anyone else other than myself would be interfacing with my code?

---

### Post by gate on 2007-11-03
Imagine that you were building an ATM. Your "Public" functions would be ones like enter pin, deposit, withdraw and check balance. Those are the ones that other people need to access. But, what about the neccecary function "Dispense money." When someone uses "withdraw" it checks to make sure they have the money, but "Dispense Money" just activates the cash dispenser for a given amount. You don't want ANYONE but your code to access that vital function, so, you call it "Private" and you have a public one that has security built into it.

  What Public and Private really do is decide how other programmers access your code. You can have fast functions without alot of error or security checking for other functions in the class, but if other people want to access them they have to go through a public function that you built the checks into. This is similar to having a separate function to take user input and check for buffer overflow attacks.

---

### Post by Baelari on 2007-11-04
Ok, that makes a little more sense, maybe. Java still gives me a headache; I never feel like I really know what I'm doing. Is anything anywhere in the program that is 'public' available to every other piece of code, even if it's something 'public' within something bigger that's 'private'? Or does it stop somewhere? Or am I still way off target?

I'm a fan of starting at the bottom and building up, I think. Without knowing, at least generally, how things work, it gets a lot more difficult for me. My course seemed like a lot of topics discussed briefly, and left me with just as many questions as it answered (I ask a lot of questions, too). Even an oversimplified explanation is better than "it will be discussed later/it's too complex for this course, for now, just memorize this." (I'd actually like to know in detail how all the circuits are controlled, and how something goes from electrical current from the wall to a colored dot on the screen, too.) I'm never going to get out of school at this rate, heh. Too much curiosity led me to changing my major 7 times before I decided I shouldn't have left CS in the first place, I suppose. Physics and the rest of the CS classes are the only requirements left for me to take. 

Haha, if I were a teacher, I'd be the type who goes on random tangents every class, wouldn't I?

---

### Post by katch22 on 2007-11-04
I think I am a lot like you Baelari. I changed my college major from music to CS to history, back to music, back to CS and finally graduated with a degree in English! Now I'm working on a master's in education. My point is, take your time, enjoy yourself, learn as much as you can. I took courses in C, Java, Pascal, Fortran, Visual Basic, and even studied 370 Assembly in a class called "Computer Principles and Concepts" (a very informative class that). Another extremely helpful class was actually in the philosophy department. It was called "Logic Theory" and while taking it I remember thinking to myself "This should be a prerequisite for all programming classes!"

   As to what language is best, it is important to remember that the concepts are pretty much the same between all languages. Some are more suited for certain tasks, but once you get the big picture, learning a new programming language is not too difficult. Just stick with good ol' C for now; master it. I am by no means a great programmer, and I have forgotten much of what I used to know. Sometimes, in fact, I look at code I wrote a few years ago and can't believe I was able to do that. When you need to write a little script or program to get something done however, it seems like what you need to know will come back to you.

   About deleting that old windows: Just boot from an old dos disk and "del" it.

---

### Post by wPwLUi3N on 2007-11-04
Hi!!!

Well humbly i say that i am quite above average in programming and if you consider worthy please ponder a little over thing which helped me gain my efficiency in programming.

First is logical puzzles ... it helped a lot, programming is all about algorithms and their realization which in turn is all about developing most efficient solutions. Puzzles help you think out of the grove and will definitely help you become a better programmer. It also improves your mathematics skills which is ultimately what is behind computers.

Also i think best programming language is not an oops one because these languages doesnot help understand the fundamentals which they are built on.

C is the best language to start with.

Cheers!!!

Good luck with your carrier!.

---

### Post by gate on 2007-11-04
well, I am a TA for computer science and yeah, I am one of the random tangent teachers. All a student has to do to distract me is ask a question I am remotely interested in.

   C is a good simple language, but it still requires a few leaps of faith at the beginning, C++ requires even more. My programs professors (at least one of them) are considering/pushing for us to switch our beginning language from C++ to Python, because the language is more abstract and you can focus on the algorithm and not waving hands when students ask about #include and what it really does, the following is one of the reasons he is pushing python explicitly is below.

  consider the following samples, that all they do is print "Hello World" and quit:

  Java: ( *shudder* )
  The following must be in a file named hello.java

  ```

    public class hello
{
	public static void main(String args[])
	{
		System.out.println("Hello World.");
	}
}
  
```

   to run it: 
   javac hello.java
   java hello

  C:
```

 #include <stdio.h>
 int main()
{
   printf("Hello World");
   return 0;
}

```
To Run: 
  gcc code_file.c -o executable_file
  ./executable_file
 
C++
  (Note that you can do the C way in C++, but not vice-versa)

```

#include <iostream>
using namespace std;
int main()
{
	cout << "Hello World" << endl;
	return 0;
}

```
To Run:
   g++ code_file.cpp -o executable_file
   ./executable_file
Python:

 ```

  print "Hello World\n" 

```
  To Run:
   python code_file.py

 All in all, most languages have their specific place.

  If you want to manipulate the bits themselves, C is an awesome way to go. If you want classes and object orientation, but still have most of the bitwise powers of C, then C++ or Objective C (haven't used that one, but I know people who swear by it, of course). If you want syntax like C but don't want to do any bitwise operations and don't want to deal with pointers, and want to be forced to do everything in an object, Java (or C# if you are feeling like being Microsoft Dependant). Then you have fully interpreted languages like Perl or Python. They tend to have rather simple syntax and abstract away a lot of the little stuff and allow you to focus on the algorithms you are implementing, rather than the idiotic gotchas. 
   As said, my favorite language is still C++.

---

### Post by jordanmthomas on 2007-11-04
> Even an oversimplified explanation is better than "it will be discussed later/it's too complex for this course, for now, just memorize this."
Java was the first language we learned in my CSC career and it was full of that too.  We did eventually learn what it all meant but it was not fun when the teacher said, "trust me on this one" without explaining it.  To be fair, he didn't explain it because so much else needed to be explained before we'd understand it.

That's one reason I don't like Java as a first language.  For about half of our first semester we were typing
```
public static void main(String[] args)
```
without having been told what it means other than "this starts your program".  Eventually, though, the pieces fall together and you have a good understanding of how everything works.  It's one of those things where you've just got to hang in there.  Maybe they put Java as a first language to weed out people who aren't willing to be patient and learn, I don't know.   The good thing about learning Java first is that picking up other languages has been very easy.  In c, I basically only had to learn about the concept of pointers and allocating memory (I still fight c whenever I program in it, so I try to avoid it unless it's really the best for the job or it's required for an assignment).

[quote="katch22"]Another extremely helpful class was actually in the philosophy department. It was called "Logic Theory" and while taking it I remember thinking to myself "This should be a prerequisite for all programming classes!"[/quote]
Our school made us take discrete mathematics, which is basically logic.  We also have to take a computer logic course.  I'm surprised yours doesn't since as you said, it should be a prerequesite.

---

### Post by gate on 2007-11-04
Discrete is very geared towards the CS majors here, its even taught by CS faculty and the biggest homework is to implement an RSA encryption algorithm.

    I greatly dislike Java because of its enforcement of object orientation even on something as simple as "Hello World", its half a**ed abstraction of pointers and its sheer verbosity.
    
    Like I was saying, every programming language has its place. For instance the Linux Kernel is in C because of its speed and manipulation of low level memory/processing: exactly what a kernel is supposed to do. Game engines like Quake 3 are also C, for the speed it endows. But, in the instance of a company I know of who is making a web based Medical database, they don't want to worry about where memory allocation is coming from, they need strong object orientation and cross platform power with minimum effort: Java. 

   By the way: you appear to have gotten a reasonable group responding to  you here, but out on internetland language arguments are one of the great holy crusades.

---

