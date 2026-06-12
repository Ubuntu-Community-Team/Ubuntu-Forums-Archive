---
title: "Gcc"
date: 2006-03-02
forum: Absolute Beginner Talk
---

### Post by linux-beginner on 2006-03-02
Hi,

I've just intalled the gcc 4 on my UBUNTU with Synaptic Package Manager.
But with compiling of my file:
> gcc oef2-2.cpp -g -o oef2-2


I get the next text:
> gcc: installation problem, cannot exec 'cc1plus': No such file or directory

Could you tell me how I can solve this problem?

Thanks,

---

### Post by Sweet on 2006-03-02
It looks like you are trying to compile a C++ program.

Try g++:
```
g++ oef2-2.cpp -o oef2-2
```

Hope this helps :)

---

### Post by daredevil on 2006-03-02
Sweet was right. BTW i think the following command can also be used to install gcc

```
sudo apt-get install build-assential
```

---

### Post by Sweet on 2006-03-02
[QUOTE=daredevil]Sweet was right. BTW i think the following command can also be used to install gcc

```
sudo apt-get install build-assential
```[/QUOTE]

```
sudo apt-get install build-**e**ssential
``` ;)

---

### Post by Copter on 2006-06-22
[QUOTE=daredevil]Sweet was right. BTW i think the following command can also be used to install gcc

```
sudo apt-get install build-assential
```[/QUOTE]
hi!

ive just installed dapper from iso cd. gcc and g++ shoud be deafult installed :)

thnx!
copter :]

---

### Post by Brunellus on 2006-06-22
[QUOTE=Copter]hi!

ive just installed dapper from iso cd. gcc and g++ shoud be deafult installed :)

thnx!
copter :][/QUOTE]
the target audience for Ubuntu tend not to be devs, and tend not to build from source.

There are, apparently, good security reasons for this as well, but I'm goign to let somenoe who knows more about that answer.

---

