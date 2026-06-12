---
title: "How to set PATH environment variable - gcc"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by hotbrainz on 2006-10-09
Hello folks,

I am trying to install a development platform for developing embedded applications. 

[http://www.openclovis.org/downloads]("http://www.openclovis.org/downloads")

Well, i tried installing the software and I get the message:

gcc(1) is required to build ASP/IDE prerequisites
cannot find gcc in your PATH environment variable
Please set your PATH environment variable to the directory where gcc is installed.

how do I set this path variable. Does Ubuntu have gcc to start with . I think it does. Anyways people, any pointers will be most appreciated.

Cheers

---

### Post by ComplexNumber on 2006-10-09
> 
how do I set this path variable
it may be different in unbuntu, but in fedora, i set mine in /home/<your-username>/.bashrc file.

---

### Post by hotbrainz on 2006-10-09
how do you set this...?
I mean is there a command or aomething i gotta add.
This whole "environmental variable" thing is new to me !

Thanks for responding

---

### Post by ComplexNumber on 2006-10-09
> **hotbrainz said:**
> how do you set this...?
I mean is there a command or aomething i gotta add.
This whole "environmental variable" thing is new to me !

Thanks for responding
actually, its the bash_prfile file.....not the .bashrc file.
just open the file with a text editor such as gedit. and add the path to the PATH variable. for example, your file may look like this:
> # .bash_profile

# Get the aliases and functions
if [ -f ~/.bashrc ]; then
    . ~/.bashrc
fi

# User specific environment and startup programs

PATH=$PATH:$HOME/bin:/sbin:/usr/sbin

PKG_CONFIG_PATH=/usr/local/lib/pkgconfig:/usr/lib/pkgconfig


export PKG_CONFIG_PATH
export PATH
unset USERNAME
say, for example, you want to add the path "/usr/local/MyProgs/bin" to your PATH variable, modify the PATH so that it looks like this:
> PATH=$PATH:$HOME/bin:/sbin:/usr/sbin:**/usr/local/MyProgs/bin**the part in bold is what i've added. each path should be separated by a ":"

---

### Post by wirelessmonkey on 2006-10-09
Ubuntu does not install gcc by default, you must add it via your preferred package manager or from source.

sudo apt-get gcc


:)

Path will be set automatically unless you want it in a non-default place.

---

### Post by hotbrainz on 2006-10-10
thanks for all your replies friends

Will try it out tonite and see how it goes

cheers

---

