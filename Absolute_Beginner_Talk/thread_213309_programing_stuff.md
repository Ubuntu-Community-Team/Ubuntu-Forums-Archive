---
title: "programing stuff"
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by MaximB on 2006-07-11
I know nothing about programing...I'm a graphic man  :)
but I'm very intersted in knowing basic things :
1.what excactly is closed source programs ?
2.if it's a closed program how then is possible to add paches and fix bugs ?
3.what is an open source program ?
4.what are binaries ?
5.what are source files ???
please explain more then just : "closed program you cannot change...".

thanx ahead !!!

---

### Post by Gustav on 2006-07-11
1. Closed programs are programs that have a license that forbids the user to change the source code and therefore the program.

2. The creater of the closed source program can still fix bugs and give you (or sell you) updated versions where the bugs are fixed.

3. Open source programs are programs that are not closed source.

4. A binary is a file that have a computer readable format. It is not readdable for humans since there are not regular 'words', just data (1's and 0's)

5. A source file is a file that have the format in wich it is programmed. It is readable for humans but the computer can't read it (unless it's an interpreted language lika python). If you compile the file you get a binary.

For a better explanation on open/closed source look at [http://www.gnu.org/philosophy/free-sw.html](http://www.gnu.org/philosophy/free-sw.html) or [http://www.opensource.org/docs/definition.php](http://www.opensource.org/docs/definition.php)

---

### Post by MaximB on 2006-07-11
so why is it much easier to fix ubuntu/linux/open source bugs then windows/closed source bugs ?

---

### Post by carlosqueso on 2006-07-11
> **MAXDDARK said:**
> so why is it much easier to fix ubuntu/linux/open source bugs then windows/closed source bugs ?

Since anyone can see and change the source in open source software, anyone with the technical know-how can submit a patch to fix it.  In closed source software, only people that work for the owner of the copyright are allowed to see the source and fix it.  It's merely a question of numbers.

---

### Post by Brunellus on 2006-07-11
> **MAXDDARK said:**
> so why is it much easier to fix ubuntu/linux/open source bugs then windows/closed source bugs ?
In closed-source situations, only the original author of the program can fix the bug.  If, for instance, he does not detect it, those people reporting it can do nothing but wait until he devotes the time/energy to fixing it.

Open-source programs can be fixed by anyone who has access to the source code.  Those users who can fix problems by themselves can use the newly-fixed program themselves.  Fixes can also be submitted to the original author/architect for eventual inclusion in a subsequent release.  Occasionally, "fixes" may become redistributed as wholly new branches of an existing program.

---

### Post by mmcmonster on 2006-07-11
**Source code **is the actual language used by computer programmers to tell the computer what to do.

This source code is translated to **binary** **code **by a compiler or interpreter on the machine.  The binary code is a language that the computer can understand.

Closed source applications will typically only distribute the binary code.  This is not easy to read by another programmer, making it much harder for the programmer to make changes/patches.

Open source applications will distribute source code as well as binary code.  Other programmers can find a bug in the source code and fix it and create a new binary version that they can use.  If the programmer is nice, he can send in the change he made in the file to the original distributers of the application, so that it becomes part of the next version of the program.

Certain open source liscenses state that anyone that distributes a modified version of a program must also make available the source code to the program.

---

