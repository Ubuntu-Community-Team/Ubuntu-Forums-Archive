---
title: "Installing from tar.gz"
date: 2006-06-23
forum: Absolute Beginner Talk
---

### Post by FuzZy2006 on 2006-06-23
After i decompress the tar.gz, i run the ./configure in the terminal and then it says make and make install. How can i use these commands, cos' they can't be just typed in the trminal like ./configure.

---

### Post by x64Jimbo on 2006-06-23
Why do you say that? make and make install are terminal commands just like ./configure. 
You're installing from source, which means you're actually compiling the source code and using a pre-made install script written by the program's author to install the application on your system. 
The complete steps for installing from source are as follows:
$./configure
$make
$sudo make install

---

### Post by Perfect Storm on 2006-06-23
Make sure you have 

```
sudo apt-get install build-essential
```

It install the basic compiling tools.

Extract the tar.gz and **cd** to the folder.
type then
./configure
If you want to fine tune some stuff type first ./configure --help which display all its options.
Pay close intention on the output of the ./configure it tells what you're missing of libs and other stuff.

Of cause not all sources are compilie this way. You might want to read the README or read installation help/guide from its homepage.

---

### Post by richbarna on 2006-06-23
[QUOTE=FuzZy2006]After i decompress the tar.gz, i run the ./configure in the terminal and then it says make and make install. How can i use these commands, cos' they can't be just typed in the trminal like ./configure.[/QUOTE]

Yep, go with what x64Jimbo said.
Also before you do this, make sure that you install "build essential" first this will give you the necessary tools to make/make install.

> sudo apt-get update && upgrade

then :-

> sudo apt-get install build-essential

Good Luck !

EDIT: AI beat me to it :) "that was some quick posting"

---

### Post by Apple 101 on 2006-06-23
Can anyone tell me how to invoke portaudio, or add it to the compile flags?  Installing the build-essential package solved my weird error problem.

---

### Post by Perfect Storm on 2006-06-23
```
sudo apt-get install libportaudio-dev
```

If it doesn't find it when you running ./configure then run ./configure --help to see how to enable it if it's disable by default.

---

### Post by Apple 101 on 2006-06-23
Okay, I'll try it later.

---

### Post by mister_p_1998 on 2006-06-23
[QUOTE=Artificial Intelligence]Make sure you have 

```
sudo apt-get install build-essential
```

It install the basic compiling tools.

Extract the tar.gz and **cd** to the folder.
type then
./configure
If you want to fine tune some stuff type first ./configure --help which display all its options.
Pay close intention on the output of the ./configure it tells what you're missing of libs and other stuff.

Of cause not all sources are compilie this way. You might want to read the README or read installation help/guide from its homepage.[/QUOTE]

Thats a gorgeous desktop! what are the apps running on the right showing your HD's etc?
Steve

---

### Post by Perfect Storm on 2006-06-23
It gdesklets. It's in the repo if you enable universe.

---

