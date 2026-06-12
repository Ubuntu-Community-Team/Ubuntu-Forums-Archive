---
title: "[SOLVED] Need help with OpenGL"
date: 2009-01-05
forum: Apple Hardware Users
---

### Post by stone915 on 2009-01-05
So, I'm trying to install the GHC for my computer science class, and I'm working on installing GLFW so I can use the SOE library, but I keep getting an error message that I'm missing a version of OpenGL newer than 2.1. Anyone know how to fix this?

---

### Post by cyberdork33 on 2009-01-05
> **stone915 said:**
> So, I'm trying to install the GHC for my computer science class, and I'm working on installing GLFW so I can use the SOE library, but I keep getting an error message that I'm missing a version of OpenGL newer than 2.1. Anyone know how to fix this?
Are you on Apple Hardware?

---

### Post by stone915 on 2009-01-05
Yes, I'm using a Macbook 4,1.

---

### Post by bryonak on 2009-01-05
Could you post the outputs of the following terminal commands:
```
aptitude search opengl
```
```
aptitude search ghc | grep -v libghc6-
```
```
aptitude search glfw
```

The *i* means installed, *p* means not installed, *v* is a metapackage. If you installed those via Synaptic/aptitude, the dependencies should have been resolved automatically.

Let us know which Ubuntu version you use. (You should always include this together with your Mac model in your first posting when asking for help)

---

### Post by stone915 on 2009-01-05
> **bryonak said:**
> Could you post the outputs of the following terminal commands:
```
mattstone@intrepidmac:~$ aptitude search opengl
p   cl-sdl-opengl                   - Support for OpenGL in Common Lisp, via CL-
p   gambas2-gb-opengl               - The OpenGL component for Gambas           
p   gambas2-gb-qt-opengl            - OpenGL with QT toolkit Gambas component   
p   libghc6-opengl-dev              - Haskell OpenGL binding for GHC            
p   libghc6-opengl-doc              - Haskell OpenGL binding for GHC; documentat
p   libghc6-opengl-prof             - Haskell OpenGL binding for GHC; profiling 
p   libguichan-opengl-0.8.1-1       - small, efficient C++ GUI library (OpenGL i
v   libhugs-opengl                  -                                           
p   libhugs-opengl-bundled          - A binding for the OpenGL graphics system  
p   libopengl-perl                  - Perl module to display 3D data using OpenG
p   libopengl-ruby                  - OpenGL binding for Ruby                   
p   libopengl-ruby1.8               - OpenGL binding for Ruby                   
p   libopengl-ruby1.9               - OpenGL binding for Ruby                   
p   libqt4-opengl                   - Qt 4 OpenGL module                        
p   libqt4-opengl-dev               - Qt 4 OpenGL library development files     
p   libtiff-opengl                  - TIFF manipulation and conversion tools    
p   openglad                        - Top-down guantlet-style RPG               
p   python-opengl                   - Python bindings to OpenGL                 
p   python-opengl-doc               - Documentation for PyOpenGL                
p   spl-opengl                      - SPL Programming Language -- OpenGL adapter
mattstone@intrepidmac:~$ 

```
```
mattstone@intrepidmac:~$ aptitude search ghc | grep -v libghc6-
v   ghc                             -                                           
v   ghc-prof                        -                                           
i   ghc6                            - GHC - the Glasgow Haskell Compilation syst
p   ghc6-doc                        - Documentation for the Glasgow Haskell Comp
p   ghc6-prof                       - Profiling libraries for the Glasgow Haskel
v   gtk2-engines-highcontrast       -                                           
v   hat-ghc6                        -                                           
mattstone@intrepidmac:~$ 

```
```
mattstone@intrepidmac:~$ aptitude search glfw
p   libglfw-dev                     - portable framework for OpenGL application 
p   libglfw2                        - portable framework for OpenGL application 
mattstone@intrepidmac:~$ 

```

The *i* means installed, *p* means not installed, *v* is a metapackage. If you installed those via Synaptic/aptitude, the dependencies should have been resolved automatically.

Let us know which Ubuntu version you use. (You should always include this together with your Mac model in your first posting when asking for help)

And I'm running Ubuntu 8.10. Sorry for not putting it in, I'm kind of new at this.

---

### Post by stone915 on 2009-01-05
Is there a quicker way to install everything I need than manually installing each file with 
```
$ sudo apt-get install *file*
```
?

---

### Post by bryonak on 2009-01-05
Since I have no idea about Haskell and my OpenGL experience is limited to a bit of meddling-for-fun (not even on my own code), that'll be a bit of blind help now...


The main GHC package is installed, so what happens if you simply try to install GLFW:
```
sudo aptitude install libglfw2
```(you can of course go the long way with Synaptic: Search -> glfw -> right click -> mark -> apply)

Feel free to install the other GHC packages as you see fit. *aptitude show PACKAGE_NAME* will show you more info about it.
The *-dev* suffix is the source code, if you want to compile the library yourself. It never hurts to install it aswell.


Oh I see you just posted again... Synaptic/aptitude are based on the APT system, which takes care of all dependencies. This means that if you install one package, all the other ones needed for it to work correctly will be downloaded and installed.
apt-get is an "older" version of aptitude, the main difference being that you can do everything (install, remove, purge, search, show, ...) with aptitude while apt-get can only install and remove. For search/show there is apt-cache, then there is apt-mark and some others. It's best to use aptitude for everything (or Synaptic if you prefer a GUI).

---

### Post by stone915 on 2009-01-05
Awesome, thank you so much. I got what I needed and got the GHC installed.

---

### Post by bryonak on 2009-01-05
You're welcome.

A protip: if you keep meddling with the terminal, you should get used to the autocompletion feature: if you type *a* and hit the tab key, it will autocomplete to a program that begins with a. Now if it does nothing, this means that there is more than one program starting with a. Just hit the tab again and it will list you all the a-programs.
Try typing *apti* and hitting tab. Since aptitude is the only program that starts with apti, it will get completed. You can then press space, hit *i*, which will get completed to *install*, since it's the only of aptitude's functions starting with i. Proceed to type *libglf* and hit tab here. I think it's obvious now.
One more: *fire* and tab.

This also works on directories and filenames. Try the *ls* (=list) command, a *D* and tab. It should complete to *Desktop*.

It's turned off with search expressions (such as "aptitude search ...")

I hope that's a hint at what people mean by "the terminal is much more powerful than the GUI"... well, aptitude sure beats opening Firefox, Google, searching for a program, hunting down the right page, downloading and then installing.


Just out of curiosity: how did you install GHC in the first place?


One more thing: Mark threads as solved if the main question has been answered, so other people using the search function may see that it's useful. Do so by clicking on "Thread Tools" at the very right top of the page.

---

### Post by stone915 on 2009-01-07
> **bryonak said:**
> You're welcome.

A protip: if you keep meddling with the terminal, you should get used to the autocompletion feature: if you type *a* and hit the tab key, it will autocomplete to a program that begins with a. Now if it does nothing, this means that there is more than one program starting with a. Just hit the tab again and it will list you all the a-programs.
Try typing *apti* and hitting tab. Since aptitude is the only program that starts with apti, it will get completed. You can then press space, hit *i*, which will get completed to *install*, since it's the only of aptitude's functions starting with i. Proceed to type *libglf* and hit tab here. I think it's obvious now.
One more: *fire* and tab.

This also works on directories and filenames. Try the *ls* (=list) command, a *D* and tab. It should complete to *Desktop*.

It's turned off with search expressions (such as "aptitude search ...")

I hope that's a hint at what people mean by "the terminal is much more powerful than the GUI"... well, aptitude sure beats opening Firefox, Google, searching for a program, hunting down the right page, downloading and then installing.


Just out of curiosity: how did you install GHC in the first place?


One more thing: Mark threads as solved if the main question has been answered, so other people using the search function may see that it's useful. Do so by clicking on "Thread Tools" at the very right top of the page.

Awesome, thank you, the tab completion should make my life easier. And yeah, aptitude/apt-get make programs incredibly easy to install, as long as I make sure I get all the right dependencies.

I installed GHC with
```
sudo apt-get install ghc
```

Thanks for the tip about marking it as solved; I was wondering how to do that. Thanks so much for all the advice, it's really helped me out.

---

