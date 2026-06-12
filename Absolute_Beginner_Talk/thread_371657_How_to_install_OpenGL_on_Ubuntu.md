---
title: "How to install OpenGL on Ubuntu?"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by smith.norton on 2007-02-27
I want to get started with some OpenGL programming. But I don't find the following header files in my system.
```

#include <GL/glut.h>    // Header File For The GLUT Library 
#include <GL/gl.h>	// Header File For The OpenGL32 Library
#include <GL/glu.h>	// Header File For The GLu32 Library
```

How can I install this library and corresponding header files into my system and get started. Please suggest.

---

### Post by dubrict on 2007-03-01
in a terminal, type in:

sudo apt-get update
sudo apt-get install libglu1-mesa-dev freeglut3-dev mesa-common-dev

---

