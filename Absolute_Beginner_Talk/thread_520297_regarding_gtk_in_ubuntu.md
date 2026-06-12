---
title: "regarding gtk in ubuntu"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by cnu_sree on 2007-08-08
is GTK and Glibs  are installed manually or they came with ubuntu
i tried whereis Glibs  command but no use
thank u,in advance
sree

---

### Post by PaulFr on 2007-08-08
```
aptitude search glib | grep 'libglib[0-9]'
aptitude search gtk|grep 'libgtk[0-9]'
```Any lines that have **i** in the left hand column mean that package is installed. Please see **man aptitude** and look for explanation of **search** action for explanation of possible values. If you want more details on any one package, say libglib2.0-0, then you can run ```
aptitude show libglib2.0-0
``` to get such details. Also, try **whereis glib** or **whereis gtk**. Hope this helps.

---

### Post by aquavitae on 2007-08-08
gtk and glibs are base libraries from gnome, so provided you have gnome installed you'll have gtk and glibs.  Why do you need them?  The development libraries are not usually installed by default, so if you want to program with them you'll have to install the dev versions.

---

### Post by cnu_sree on 2007-08-08
i done a project in gtk+c in fedora6
now i want  to implement in ubuntu.
so iam trying to do that.
my question is am i directly start programming as i did in fedora6 or i should install gtk  manually.
thank u ,inadvance
sree.

---

### Post by aquavitae on 2007-08-08
Do you know the name of the library you used in Fedora?  e.g. wxGtk, libgtk2.0-dev, etc.  You probably need to install it using synaptic if you want to compile your program.

---

### Post by cnu_sree on 2007-08-08
i tried this command
 aptitude show libgtk2.0-0
 aptitude show libglib2.0-0
 it's showing tht packages or installed but i din't found any include files of gtk and glibs.
and iam unable to link the libs to my program
thank u,in advance

---

### Post by PaulFr on 2007-08-08
Those are the runtime libraries, please install the -dev versions.

---

### Post by aquavitae on 2007-08-08
The packages include the include files. They are not shown separately.  To check that thy are there, look in /usr/include, /usr/share/include /usr/local/include and /usr/share/local/include (various distro's use different ones of these and I can never remember which one uses which, but it should be somewhere there).  But you shouldn't need to specify the path of the include files - they should be in your PATH.

---

### Post by tuxcantfly on 2007-08-08
> i done a project in gtk+c in fedora6

if it's c++ you'll need the gtkmm libraries and include files, try installing libgtkmm2.0-dev

---

### Post by cnu_sree on 2007-08-08
ok thank u for ur respone
if u install gtk-dev and i compile my application  after tht if i exe in another ubuntu system.
is this exe work's or fails.
thank u inadvance
sree

---

### Post by bluezapper on 2007-08-08
Hi,

If you install the following gnome library all the required gtk packages for development will be installed:

Goto Synaptic package manager and install

**libgnomeui-2.0**

regards,

bluezapper

---

### Post by 3rdalbum on 2007-08-08
I'm not sure exactly what you're asking here, but if you install the development libraries for GTK, compile and then put the compiled program onto another Ubuntu system, it will work. The development libraries are only necessary for compiling.

---

### Post by cnu_sree on 2007-08-08
thank u very much
sorry for disturbing u 
iam new to ubuntu
where should i find "Synaptic package manager" in ubuntu.
thank u
sree

---

### Post by BaffledMollusc on 2007-08-08
> **cnu_sree said:**
> thank u very much
sorry for disturbing u 
iam new to ubuntu

No problem - welcome to the community!
> 
where should i find "Synaptic package manager" in ubuntu.
thank u
sree
System->Administration->Synaptic Package Manager

---

### Post by cnu_sree on 2007-08-08
thank u
i didnot find libgnomeui-2.0.
i found libgnomeui2 when i click on tht it's showing tht it's already installed
so wht lib should i instal for gtk and glibs

---

### Post by BaffledMollusc on 2007-08-08
> **cnu_sree said:**
> thank u
i didnot find libgnomeui-2.0.
i found libgnomeui2 when i click on tht it's showing tht it's already installed
so wht lib should i instal for gtk and glibs
I think the package you need is libgnomeui-dev. 

Usually if a package name ends in -dev it is the development version, and contains all the headers and suchlike you need to compile programs based on that library.

---

### Post by BaffledMollusc on 2007-08-08
Oh, and if you want the C++ bindings, you might also need to install libgnomeuimm-2.6-dev.

---

