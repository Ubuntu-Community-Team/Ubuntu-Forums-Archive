---
title: "PATH variables"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by hnaamyilkemku on 2007-01-09
Hello,

I'm trying to add /usr/local/texlive/2005/bin/i386-linux to my PATH but don't know where and how to do this. I also don't really know what a PATH is. =/

Thanks in advance!

---

### Post by bodhi.zazen on 2007-01-09
The $PATH is a variable. It is list of directories searched for an executable program.

To see your current path:```
echo $PATH
```

To change you path:

Temporarily (until you close your terminal):```
PATH=/path/to/include:$PATH
```

for long term, make a directory in your home directory (~) "bin"

```
mkdir ~/bin
```

Save your executables in ~/bin

To add ~/bin to your path add this to ~/.bashrc:
> # set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi

---

### Post by hnaamyilkemku on 2007-01-09
/usr/local/texlive/2005/bin/i386-linux contains very many binaries (on the order of 10^2 or so), so I don't want to cp those to my home dir. Is there a way I can add the directory to my path permanently without resorting to this? I read some vague stuff about /etc/profile, but it  didn't help much.

Again, thanks in advance.

---

### Post by taurus on 2007-01-09
Applications -> Accessories -> Terminal
```
gedit ~/.bashrc
```
Then, add these two lines to the end of it.

```
PATH=$PATH:/usr/local/texlive/2005/bin/i386-linux
export PATH
```
Save it.  Log out and back in again.

---

