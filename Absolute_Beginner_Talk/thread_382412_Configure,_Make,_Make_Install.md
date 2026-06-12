---
title: "Configure, Make, Make Install"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by avgjoe22 on 2007-03-12
Not so simple.

I can get through "Configure" but at make I get a whole shitload of errors when installing "Foobilliard" (a virtual version of a game very close to my heart) when doing Make.

Here are the errors that would fit in the message...
```

billard3d.c:4877: warning: data definition has no type or storage class
billard3d.c:4878: warning: type defaults to ‘int’ in declaration of ‘glTexParameteri’
billard3d.c:4878: warning: parameter names (without types) in function declaration
billard3d.c:4878: warning: data definition has no type or storage class
billard3d.c:4879: warning: type defaults to ‘int’ in declaration of ‘glTexParameteri’
billard3d.c:4879: warning: parameter names (without types) in function declaration
billard3d.c:4879: warning: data definition has no type or storage class
billard3d.c:4880: warning: type defaults to ‘int’ in declaration of ‘glTexEnvi’
billard3d.c:4880: warning: parameter names (without types) in function declaration
billard3d.c:4880: warning: data definition has no type or storage class
billard3d.c:4882: warning: type defaults to ‘int’ in declaration of ‘free’
billard3d.c:4882: warning: parameter names (without types) in function declaration
billard3d.c:4882: error: conflicting types for ‘free’
/usr/include/stdlib.h:597: error: previous declaration of ‘free’ was here
billard3d.c:4882: warning: data definition has no type or storage class
billard3d.c:4885: warning: type defaults to ‘int’ in declaration of ‘glEnable’
billard3d.c:4885: warning: parameter names (without types) in function declaration
billard3d.c:4885: warning: data definition has no type or storage class
billard3d.c:4886: warning: type defaults to ‘int’ in declaration of ‘glFogi’
billard3d.c:4886: warning: parameter names (without types) in function declaration
billard3d.c:4886: warning: data definition has no type or storage class
billard3d.c:4887: warning: type defaults to ‘int’ in declaration of ‘glHint’
billard3d.c:4887: warning: parameter names (without types) in function declaration
billard3d.c:4887: warning: data definition has no type or storage class
billard3d.c:4888: error: syntax error before numeric constant
billard3d.c:4888: warning: type defaults to ‘int’ in declaration of ‘glFogf’
billard3d.c:4888: warning: data definition has no type or storage class
billard3d.c:4889: error: syntax error before numeric constant
billard3d.c:4889: warning: type defaults to ‘int’ in declaration of ‘glFogf’
billard3d.c:4889: warning: data definition has no type or storage class
billard3d.c:4890: warning: type defaults to ‘int’ in declaration of ‘glFogfv’
billard3d.c:4890: warning: parameter names (without types) in function declaration
billard3d.c:4890: warning: data definition has no type or storage class
billard3d.c:4893: warning: type defaults to ‘int’ in declaration of ‘glHint’
billard3d.c:4893: warning: parameter names (without types) in function declaration
billard3d.c:4893: warning: data definition has no type or storage class
billard3d.c:4908: error: syntax error before ‘.’ token
billard3d.c:4910: error: syntax error before ‘&’ token
billard3d.c:4910: warning: type defaults to ‘int’ in declaration of ‘create_walls’
billard3d.c:4910: error: ‘create_walls’ redeclared as different kind of symbol
billard.h:81: error: previous declaration of ‘create_walls’ was here
billard3d.c:4910: warning: data definition has no type or storage class
billard3d.c:4911: error: syntax error before ‘.’ token
billard3d.c:4913: error: syntax error before ‘&’ token
billard3d.c:4913: warning: type defaults to ‘int’ in declaration of ‘create_scene’
billard3d.c:4913: error: ‘create_scene’ redeclared as different kind of symbol
billard.h:80: error: previous declaration of ‘create_scene’ was here
billard3d.c:4913: warning: data definition has no type or storage class
billard3d.c:4923: warning: type defaults to ‘int’ in declaration of ‘table_obj’
billard3d.c:4923: error: redefinition of ‘table_obj’
billard3d.c:135: error: previous definition of ‘table_obj’ was here
billard3d.c:4923: error: initializer element is not constant
billard3d.c:4923: warning: data definition has no type or storage class
billard3d.c:4929: warning: type defaults to ‘int’ in declaration of ‘glEnable’
billard3d.c:4929: warning: parameter names (without types) in function declaration
billard3d.c:4929: warning: data definition has no type or storage class
billard3d.c:4930: warning: type defaults to ‘int’ in declaration of ‘glEnable’
billard3d.c:4930: warning: parameter names (without types) in function declaration
billard3d.c:4930: warning: data definition has no type or storage class
billard3d.c:4931: warning: type defaults to ‘int’ in declaration of ‘glEnable’
billard3d.c:4931: warning: parameter names (without types) in function declaration
billard3d.c:4931: warning: data definition has no type or storage class
billard3d.c:4935: warning: type defaults to ‘int’ in declaration of ‘glEnable’
billard3d.c:4935: warning: parameter names (without types) in function declaration
billard3d.c:4935: warning: data definition has no type or storage class
billard3d.c:4936: warning: type defaults to ‘int’ in declaration of ‘glFrontFace’
billard3d.c:4936: warning: parameter names (without types) in function declaration
billard3d.c:4936: warning: data definition has no type or storage class
billard3d.c:4938: warning: type defaults to ‘int’ in declaration of ‘glEnable’
billard3d.c:4938: warning: parameter names (without types) in function declaration
billard3d.c:4938: warning: data definition has no type or storage class
billard3d.c:4939: warning: type defaults to ‘int’ in declaration of ‘glDepthMask’
billard3d.c:4939: warning: parameter names (without types) in function declaration
billard3d.c:4939: warning: data definition has no type or storage class
billard3d.c:4942: warning: type defaults to ‘int’ in declaration of ‘glDepthFunc’
billard3d.c:4942: warning: parameter names (without types) in function declaration
billard3d.c:4942: warning: data definition has no type or storage class
billard3d.c:4946: error: syntax error before ‘if’
billard3d.c:4950: error: syntax error before numeric constant
billard3d.c:4950: warning: type defaults to ‘int’ in declaration of ‘SetMode’
billard3d.c:4950: error: conflicting types for ‘SetMode’
billard3d.c:3569: error: previous definition of ‘SetMode’ was here
billard3d.c:4950: warning: data definition has no type or storage class
billard3d.c: In function ‘main’:
billard3d.c:5043: warning: implicit declaration of function ‘glGetIntegerv’
billard3d.c:5043: error: ‘GL_AUX_BUFFERS’ undeclared (first use in this function)
billard3d.c:5046: error: ‘GL_LIGHTING’ undeclared (first use in this function)
make[1]: *** [billard3d.o] Error 1
make[1]: Leaving directory `/home/joey/Desktop/foobillard-3.0a/src'
make: *** [install-recursive] Error 1
billard3d.c:4877: warning: type defaults to ‘int’ in declaration of ‘gluBuild2DMipmaps’
billard3d.c:4877: warning: data definition has no type or storage class
billard3d.c:4878: warning: type defaults to ‘int’ in declaration of ‘glTexParameteri’
billard3d.c:4878: warning: parameter names (without types) in function declaration
billard3d.c:4878: warning: data definition has no type or storage class
billard3d.c:4879: warning: type defaults to ‘int’ in declaration of ‘glTexParameteri’
billard3d.c:4879: warning: parameter names (without types) in function declaration
billard3d.c:4879: warning: data definition has no type or storage class
billard3d.c:4880: warning: type defaults to ‘int’ in declaration of ‘glTexEnvi’
billard3d.c:4880: warning: parameter names (without types) in function declaration
billard3d.c:4880: warning: data definition has no type or storage class
billard3d.c:4882: warning: type defaults to ‘int’ in declaration of ‘free’
billard3d.c:4882: warning: parameter names (without types) in function declaration
billard3d.c:4882: error: conflicting types for ‘free’
/usr/include/stdlib.h:597: error: previous declaration of ‘free’ was here
billard3d.c:4882: warning: data definition has no type or storage class
billard3d.c:4885: warning: type defaults to ‘int’ in declaration of ‘glEnable’
billard3d.c:4885: warning: parameter names (without types) in function declaration
billard3d.c:4885: warning: data definition has no type or storage class
billard3d.c:4886: warning: type defaults to ‘int’ in declaration of ‘glFogi’
billard3d.c:4886: warning: parameter names (without types) in function declaration
billard3d.c:4886: warning: data definition has no type or storage class
billard3d.c:4887: warning: type defaults to ‘int’ in declaration of ‘glHint’
billard3d.c:4887: warning: parameter names (without types) in function declaration
billard3d.c:4887: warning: data definition has no type or storage class
billard3d.c:4888: error: syntax error before numeric constant
billard3d.c:4888: warning: type defaults to ‘int’ in declaration of ‘glFogf’
billard3d.c:4888: warning: data definition has no type or storage class
billard3d.c:4889: error: syntax error before numeric constant
billard3d.c:4889: warning: type defaults to ‘int’ in declaration of ‘glFogf’
billard3d.c:4889: warning: data definition has no type or storage class
billard3d.c:4890: warning: type defaults to ‘int’ in declaration of ‘glFogfv’
billard3d.c:4890: warning: parameter names (without types) in function declaration
billard3d.c:4890: warning: data definition has no type or storage class
billard3d.c:4893: warning: type defaults to ‘int’ in declaration of ‘glHint’
billard3d.c:4893: warning: parameter names (without types) in function declaration
billard3d.c:4893: warning: data definition has no type or storage class
billard3d.c:4908: error: syntax error before ‘.’ token
billard3d.c:4910: error: syntax error before ‘&’ token
billard3d.c:4910: warning: type defaults to ‘int’ in declaration of ‘create_walls’
billard3d.c:4910: error: ‘create_walls’ redeclared as different kind of symbol
billard.h:81: error: previous declaration of ‘create_walls’ was here
billard3d.c:4910: warning: data definition has no type or storage class
billard3d.c:4911: error: syntax error before ‘.’ token
billard3d.c:4913: error: syntax error before ‘&’ token
billard3d.c:4913: warning: type defaults to ‘int’ in declaration of ‘create_scene’
billard3d.c:4913: error: ‘create_scene’ redeclared as different kind of symbol
billard.h:80: error: previous declaration of ‘create_scene’ was here
billard3d.c:4913: warning: data definition has no type or storage class
billard3d.c:4923: warning: type defaults to ‘int’ in declaration of ‘table_obj’
billard3d.c:4923: error: redefinition of ‘table_obj’
billard3d.c:135: error: previous definition of ‘table_obj’ was here
billard3d.c:4923: error: initializer element is not constant
billard3d.c:4923: warning: data definition has no type or storage class
billard3d.c:4929: warning: type defaults to ‘int’ in declaration of ‘glEnable’
billard3d.c:4929: warning: parameter names (without types) in function declaration
billard3d.c:4929: warning: data definition has no type or storage class
billard3d.c:4930: warning: type defaults to ‘int’ in declaration of ‘glEnable’
billard3d.c:4930: warning: parameter names (without types) in function declaration
billard3d.c:4930: warning: data definition has no type or storage class
billard3d.c:4931: warning: type defaults to ‘int’ in declaration of ‘glEnable’
billard3d.c:4931: warning: parameter names (without types) in function declaration
billard3d.c:4931: warning: data definition has no type or storage class
billard3d.c:4935: warning: type defaults to ‘int’ in declaration of ‘glEnable’
billard3d.c:4935: warning: parameter names (without types) in function declaration
billard3d.c:4935: warning: data definition has no type or storage class
billard3d.c:4936: warning: type defaults to ‘int’ in declaration of ‘glFrontFace’
billard3d.c:4936: warning: parameter names (without types) in function declaration
billard3d.c:4936: warning: data definition has no type or storage class
billard3d.c:4938: warning: type defaults to ‘int’ in declaration of ‘glEnable’
billard3d.c:4938: warning: parameter names (without types) in function declaration
billard3d.c:4938: warning: data definition has no type or storage class
billard3d.c:4939: warning: type defaults to ‘int’ in declaration of ‘glDepthMask’
billard3d.c:4939: warning: parameter names (without types) in function declaration
billard3d.c:4939: warning: data definition has no type or storage class
billard3d.c:4942: warning: type defaults to ‘int’ in declaration of ‘glDepthFunc’
billard3d.c:4942: warning: parameter names (without types) in function declaration
billard3d.c:4942: warning: data definition has no type or storage class
billard3d.c:4946: error: syntax error before ‘if’
billard3d.c:4950: error: syntax error before numeric constant
billard3d.c:4950: warning: type defaults to ‘int’ in declaration of ‘SetMode’
billard3d.c:4950: error: conflicting types for ‘SetMode’
billard3d.c:3569: error: previous definition of ‘SetMode’ was here
billard3d.c:4950: warning: data definition has no type or storage class
billard3d.c: In function ‘main’:
billard3d.c:5043: warning: implicit declaration of function ‘glGetIntegerv’
billard3d.c:5043: error: ‘GL_AUX_BUFFERS’ undeclared (first use in this function)
billard3d.c:5046: error: ‘GL_LIGHTING’ undeclared (first use in this function)
make[1]: *** [billard3d.o] Error 1
make[1]: Leaving directory `/home/joey/Desktop/foobillard-3.0a/src'
make: *** [install-recursive] Error 1
```

Any ideas?

---

### Post by HereInOz on 2007-03-12
I reckon you might need the build-essential packages and perhaps xinetd to do this.

try:
sudo apt-get install build-essential xinetd

That might allow things to progess.

---

### Post by K.Mandla on 2007-03-12
Could I ask why you're not using the version in the repositories?

[http://packages.ubuntu.com/edgy/games/foobillard](http://packages.ubuntu.com/edgy/games/foobillard)

---

### Post by avgjoe22 on 2007-03-12
honestly, i didn't even know what a repository was until just now...

---

### Post by K.Mandla on 2007-03-12
:D It's okay. If you use Synaptic, you should be able to search for "foobillard" and install it that way, or if you are already in a terminal. ...

```
sudo aptitude install foobillard
```

Have fun! It's a great game; there's also [billard-gl]("http://packages.ubuntu.com/edgy/games/billard-gl") which is pretty good too.

---

### Post by aysiu on 2007-03-12
Read more about installing from the repositories:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

