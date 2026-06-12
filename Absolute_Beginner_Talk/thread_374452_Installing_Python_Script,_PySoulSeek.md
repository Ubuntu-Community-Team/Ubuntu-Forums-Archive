---
title: "Installing Python Script, PySoulSeek"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by lateralus23 on 2007-03-02
I am trying to install PySoulSeek on Ubuntu but I can't figure out how to do it. It can be found here ([http://www.sensi.org/~ak/pyslsk/](http://www.sensi.org/~ak/pyslsk/)). I downloaded the tar.gz and read the install instructions, it gave an install command, something like python pyslsk install -- something... I can't remember and unfortunately can't check at the moment since I am at work. Is there some general installation method for python scripts? I can't seem to find anything.

---

### Post by punx45 on 2007-03-02
python scripts are like other scripts in that they do not need to be compiled to binaries in order to be executed.   so if my limited experience with python is correct, the 'install' process merely puts the script in your path so that you can execute it without referring to its precise location.   so it is likely that you can now run the script simply by typing the name of the script (in this case 'pyslsk') in the command line.

of course, all of this assumes that you already have the python environment installed.   if you didn't I'm pretty sure that when you tried 'python pyslsk install' you would have gotten an error message similar to "bash: python: command not found" or something like that.

---

### Post by lateralus23 on 2007-03-02
I am pretty sure Python is installed. If I enter python in the terminal I get
 ```
Python 2.4.3 (#2, Oct  6 2006, 07:49:22)
[GCC 4.0.3 (Ubuntu 4.0.3-1ubuntu5)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>>

```

I am still not sure where I would have to put the file in order to run it. The readme says to do one of the following

```
python setup.py install --prefix=<dir>
```
to launch from the python directory, which I can't seem to locate.

or by running right from the unpackaged .tar.gz by running

```
python ./pyslsk
```

I am really not sure how I am supposed to be executing these in the terminal. I just get all sorts of syntax errors when running after entering "python" and I get no such file or directory errors when trying to run straight from the terminal. I really have no idea what I am doing here :(

---

### Post by po0f on 2007-03-02
lateralus23,

Do you have the dependencies satisfied?  On the website, it says you need Python (which you have), and GTK+ 1.2 and >wxPython-2.6.0.  To install the latter, run this command from the terminal:

```
$ sudo apt-get update
$ sudo apt-get install libgtk1.2 python-wxgtk2.6
```

To run it from the unpacked directory (assuming you downloaded it to your Desktop):

```
$ cd ~/Desktop
$ tar xvzf pyslsk-1.2.7b.tar.gz
$ cd pyslsk-1.2.7b
$ python ./pyslsk
```

---

### Post by gacinalor on 2007-03-17
> **po0f said:**
> lateralus23,

Do you have the dependencies satisfied?  On the website, it says you need Python (which you have), and GTK+ 1.2 and >wxPython-2.6.0.  To install the latter, run this command from the terminal:

```
$ sudo apt-get update
$ sudo apt-get install libgtk1.2 python-wxgtk2.6
```

To run it from the unpacked directory (assuming you downloaded it to your Desktop):

```
$ cd ~/Desktop
$ tar xvzf pyslsk-1.2.7b.tar.gz
$ cd pyslsk-1.2.7b
$ python ./pyslsk
```




i have problems with the last codes,here listed. i have the files on my desktop
it tells me this

gianka@gianka-laptop:~/Desktop$ tar xvzf pylslk-1.2.7b.tar.gz
tar: pylslk-1.2.7b.tar.gz: Impossibile open: Nessun file o directory
tar: Errore irrimediabile: esco
tar: Child returned status 2

(in italian it says)
no file or directory
nonfixable mistake has happened. exit

im new with linux, so im ****, please help
thanks
ciao

---

### Post by FaceLeg on 2007-03-29
I just followed his instructions, and things worked fine.  

I am also rather new to Ubuntu, so I absolutely know how you feel.

I can only guess that you have either missed one of the steps, have copied one of the lines incorrectly, or (The most likely - I know because I did it) downloaded the .tar.gz file to a different directory!

The

pyslsk-1.2.7b.tar.gz

File must be on the Desktop, or copy-pasting the above code will not work.

---

