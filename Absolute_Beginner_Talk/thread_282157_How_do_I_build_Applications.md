---
title: "How do I build Applications?"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by cfsporn on 2006-10-22
Whenever I download an application, I get the source code. How can I make this into an application. For the record I am used to being on a Mac where I just drag and drop an app. Also I am very new to Ubuntu, but not afraid to use the terminal.

---

### Post by Chaos5lw on 2006-10-22
You will probably need gcc and auto-make.

Find the directory where the source data is and (providing its pre-configured) do:
make
sudo make install

I cant remember how to make a config file tho.


There are many apps in the repos so you may be better using them as they auto install. Either use apt-get or synaptic

---

### Post by az on 2006-10-22
> **cfsporn said:**
> Whenever I download an application, I get the source code. How can I make this into an application.

You compile it.

You nee dto install the compiler and the rest of the toolchain first.  

Install build-essential.

Depending on what the application does, you may need additional libraries and header files so that your application can use shared libraries that are installed on your system.  Read the README in the source code.   In Debian/Ubuntu packaging, they are -dev packages.  For example, if you need something that runs with GTK2, you would install libgtk2-dev.

Then configure your application by entering the directory

cd my-source-code-application-1.02

and then configuring it

./configure

the configure script should set all the parameters so that you can compile your app.  If there is something missing, you will be told and the configure will quit.  You will not be able to compile until you can completely finish the configure script.

Then make the application

make


Usually, you have to install it too.  You may need privileges to do that

sudo make install.

What exactly do you want to compile?  It may already be in the repositories...

---

### Post by Klaidas on 2006-10-22
> Also I am very new to Ubuntu, but not afraid to use the terminal.

That's cool, but an application might be available in the reposities, and if it, there no need to compile. And... compiling might get naaasty! :|

---

### Post by TheWizzard on 2006-10-22
> Whenever I download an application, I get the source code. 
do you actually want to build from source or just install the application? 
if you just want to install an application, you shouldn't download it from the web. instead, open your package manager, search for the app, and mark it for installation. 
you can also use the command line. for example, to install firefox, just type:```
sudo apt-get install firefox
```

few notes:
- you may need to add some repo's
- if a package is not in the repo's search for the deb-file
- building from source is only necessary for very weird software

for a more complete story take a look at:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by TheWizzard on 2006-10-22
if you build from source, i would advice you to use checkinstall

---

