---
title: "How do you turn off echo in a bash shell and/or c++"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by Smatt454 on 2008-02-07
hello. i have been trying for a while to find out how to turn echo off in a bash shell or in c++

say i am writing a program and i want them to create a username and password (for like a game, i aksed them to choose a username and password) and i want when the enter the password for them not to see what they type in.

for example in c++
```

#include <iostream>
using namespace std;
int main ()
{
	char password,username;
	cout << "Please choose a username: ";
	cin >>username;
	cout<<"Please choose a password: ";
        [turn echo off]
        cin>>password;
 }


```
 
like i said, i would like to know how to do this in both c++ and in bash

thanks! :guitar:

---

### Post by Bodsda on 2008-02-07
It is not possible to my knowledge to remove a command from a language, however there are simple solutions to your problem

1) Use the same font colour as the background colour for the input box, 

2) When entering a password at login, it shows up as * ,. meaning you can change which charcters are shown when typing something.

perhaps research the way sudo does it from the terminal, or check the GDM login scripts for the password input box

---

### Post by Smatt454 on 2008-02-07
i am not trying to remove a command from a language. i just want to turn echo off. (not removing echo from the language, for example if u run "@Echo off" in linux, it wont show u the output

---

### Post by ghostdog74 on 2008-02-07
in bash
```

# stty -echo

```
man stty

in C, man getch

---

### Post by Smatt454 on 2008-02-07
THANKS! I am not in a position to try this (i am at schoo on a windows computer :( ) but this seems to be EXACTLY what i was looking for!

---

