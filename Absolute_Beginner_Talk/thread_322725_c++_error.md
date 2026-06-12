---
title: "c++ error"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by zetsumei on 2006-12-20
im trying to learn c++ and i get this error when compling it

> bryce@bryce:~/c++$ g++ helloworld2.cc -o helloworld2
helloworld2.cc: In function ‘int main(int, char**)’:
helloworld2.cc:6: error: ‘cout’ was not declared in this scope
helloworld2.cc:6: error: ‘endl’ was not declared in this scope


here is my code in helloworld2.cc

> #include <iostream>

int
main(int argc, char* argv[])
{
        cout << "hello world" >> endl;

        return 0;
}


---

### Post by po0f on 2006-12-20
zetsumei,

After you include iostream, insert the following line:
```
[FONT="Courier New"]using namespace std;[/FONT]
```
All of C++'s functions and classes reside in what's called the std namespace.  Namespaces help keep global pollution down, and are a good thing.  For such a small program, it's OK to globally expose the std namespace though.

For future reference, this question should actually have been posted in [Programming Talk](http://www.ubuntuforums.org/forumdisplay.php?f=39).

[EDIT]

Line 6 should read:
```
[FONT="Courier New"]cout << "hello world" **<<** endl;[/FONT]
```

---

### Post by zetsumei on 2006-12-20
oh and is it g++ to compile c++

---

### Post by po0f on 2006-12-20
zetsumei,

Yes, use g++ to compile your C++ programs.

Try to make it a habit to add '-Wall' to your compile commands.  This will let you know about all of the errors in your programs.

```
[FONT="Courier New"]$ g++ -Wall -o helloworld2 helloworld2.cc[/FONT]
```

---

### Post by zetsumei on 2006-12-20
ok, and the tutorial i am following shows the command like

> g++ helloworld2.cc -o helloworld2

is there any difference between the way i did that and the way you did it?

EDIT: nevermind theres no difference XD

---

### Post by po0f on 2006-12-20
zetsumei,

[quote=po0f]**Try to make it a habit to add '-Wall' to your compile commands. This will let you know about all of the errors in your programs.**[/quote]

---

### Post by zetsumei on 2006-12-20
i did add -Wall in the terminal window but you're right I do need to add -Wall everywhere =)

---

