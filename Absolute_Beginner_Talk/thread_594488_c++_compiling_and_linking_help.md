---
title: "c++ compiling and linking help"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by omkarwagh on 2007-10-28
i am quite a beginner to programming so you'll probably find this a stupid question.

i have a project that involves a number of header files .h (that contain the declarations of a number of classes and functions) while some other people have made a number of .cpp files that implement these functions.

i also have a main.cpp file that uses all these header contained stuff. however i am not able to link all these things properly.
in windows at least simply including the header files in the main.cpp would automatically compile all the header files along with the implementations and include them. however in ubuntu i am getting a number of
"Undefined reference to ****" if i use g++.
i also need to include mesa(glut) header files. even they are not being included using the simple
#include<GL/glut.h> giving the same "Undefined reference to ****"

My other problem was the follows:-
also, i tried to use gcc but it gives a huge number of errors involving maybe iostream or stl_vector or god only knows what. ive been using g++ since. any ideas on how to use iostream or vectors in gcc? (because gcc is linking these automatically not g++).

hope i dont have to go back to windows. :P

---

### Post by taurus on 2007-10-28
You need the build-essential package if you want to use gcc or g++.

```
sudo aptitude update
sudo aptitude install build-essential
gcc -v
```

---

### Post by omkarwagh on 2007-10-28
i

---

### Post by omkarwagh on 2007-10-28
i tried doing that too. doesnt work.

i have gcc and g++. im just not able to make g++ realise that my main.cpp file includes a xyz.h file that has all the funcitons that it needs. (and there are a lot of these header files.)

an easy way out would be to copy-paste everything into one big unweildy main.cpp(it works that way). however, im not too keen on doing that. it becomes very hard to debug. 

the problem with gcc is that it doesnt seem to be able to use the iotream and the stl packages. no idea why. gives a long list of unintelligible errors.

---

### Post by omkarwagh on 2007-10-28
ok got it to work finally.

used the -c option to individually compile the header files as .o files and then included all the .o files at the command prompt when compiling the main file.

---

