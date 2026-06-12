---
title: "Source a file in bash permanently"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by GoPool on 2007-08-11
two quick questions.

1. I just installed a couple of programs that have to be sources for them to work in bash. That i do by running "*source filename*" in a terminal. The thing is I have to do that everytime I open the terminal. Is there is way I can permanently source these files in .bashrc, .bash_profiles, or another system file, so that I do not have to run the source command in t every time?

2. Normally when I install a program, eg. pymol, I could launch that program by running  "*pymol*" in a terminal or application launcher. However, I just install a program called coot, and in order for me to run that program I have to run "*/usr/local/xtal/coot-0.3.1/bin/coot*" I cannot always remeber that path, and it takes a while to launch the program because I have to actually cd to the directory and then launch the program. Is there an easier way for me to launch this program in terminal or application launcher by just running "*coot*"? Thanks you in advance. Any help would be greatly appreciated.

---

### Post by morgan_greywolf on 2007-08-11
> 1. I just installed a couple of programs that have to be sources for them to work in bash. That i do by running "source filename" in a terminal. The thing is I have to do that everytime I open the terminal. Is there is way I can permanently source these files in .bashrc, .bash_profiles, or another system file, so that I do not have to run the source command in t every time?

Just add ```
source filename
``` or ```
. filename
``` to your .bashrc, at the end of the file with your favorite text editor.

> 2. Normally when I install a program, eg. pymol, I could launch that program by running "pymol" in a terminal or application launcher. However, I just install a program called coot, and in order for me to run that program I have to run "/usr/local/xtal/coot-0.3.1/bin/coot" I cannot always remeber that path, and it takes a while to launch the program because I have to actually cd to the directory and then launch the program. Is there an easier way for me to launch this program in terminal or application launcher by just running "coot"? Thanks you in advance. Any help would be greatly appreciated.

Just add a symbolic link to the file in /usr/local/bin:

```
sudo ln -s /usr/local/xtral/coot-0.3.1/bin/coot /usr/local/bin
```

---

### Post by GoPool on 2007-08-11
thanks a lot for the quick response. That works great; running coot in terminal launchers the coot program now, but how can I get it to run by running coot in the application launcher (Atl+F2)?

Never mind I figured it out. "sudo ln - s /file-path /usr/bin"

---

