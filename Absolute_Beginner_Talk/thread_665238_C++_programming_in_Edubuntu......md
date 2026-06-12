---
title: "C++ programming in Edubuntu....."
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by abk123 on 2008-01-12
Hi,
I have installed Build essential , Anjuta and Geany.But I find that Anjuta and geany are nothing but text editors(just like notepad!).I can write the programs in it but cant compile or run them.
In Anjuta there is no button which says:"Press me to compile"
In geany these things are greyed out.
Here are some screenshots:
[http://i274.photobucket.com/albums/jj267/abk123_2008/Screenshot-Anjuta.png](http://i274.photobucket.com/albums/jj267/abk123_2008/Screenshot-Anjuta.png)

[http://i274.photobucket.com/albums/jj267/abk123_2008/Screenshot-saved--home-abhishek123-.png](http://i274.photobucket.com/albums/jj267/abk123_2008/Screenshot-saved--home-abhishek123-.png)
Any advice?
Thanks.

---

### Post by finer recliner on 2008-01-12
haven't used either of those editors. but heres how to do it on the command line:

open a terminal and cd to the directory where the C++ file is


```
 g++ filename.cpp
./a.out

```

the first line compiles your filename.cpp. by default, the binary file is called 'a.out' and is created in the same directory you are currently in. to run the file you use the command on the second line.

if the file is just using C code, you can replace 'g++' with 'gcc' (without quotes) to use the GNU C compiler.

---

### Post by RomeReactor on 2008-01-12
Hi. In Geany, did you set the file type (Document->Set Filetype) to C++? Also, the compile option will stay grayed out until you save the file.

---

### Post by abk123 on 2008-01-12
Yeah,that worked!
Thanks!
I am writing down what i did for anyone who has the same prob in future:

Documents>File type........set it to the language you want.

Save the file with proper extensions.(hello.cpp for c++)

---

### Post by kh_naba on 2008-01-12
> **abk123 said:**
> Hi,
I have installed Build essential , Anjuta and Geany.But I find that Anjuta and geany are nothing but text editors(just like notepad!).I can write the programs in it but cant compile or run them.
In Anjuta there is no button which says:"Press me to compile"
In geany these things are greyed out.
Here are some screenshots:
[http://i274.photobucket.com/albums/jj267/abk123_2008/Screenshot-Anjuta.png](http://i274.photobucket.com/albums/jj267/abk123_2008/Screenshot-Anjuta.png)

[http://i274.photobucket.com/albums/jj267/abk123_2008/Screenshot-saved--home-abhishek123-.png](http://i274.photobucket.com/albums/jj267/abk123_2008/Screenshot-saved--home-abhishek123-.png)
Any advice?
Thanks.

And in Anjuta, you need to create a project first before doing anything else. That shold open up all relevent plugins required for the project. Others can be enabled from Edit->preferences on need basis.

---

