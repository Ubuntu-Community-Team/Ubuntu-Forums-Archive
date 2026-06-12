---
title: "Compiling"
date: 2006-04-01
forum: Absolute Beginner Talk
---

### Post by amitroy5 on 2006-04-01
I just downloaded PHP ming. What is the proper way to compile it by using python? Thanks!

---

### Post by chuckyp on 2006-04-01
Make sure you have build-essential installed to take care of most common build environments.  Then look in the directory where you un tarred the package there should be a readme with directions.

---

### Post by amitroy5 on 2006-04-01
How do I use build-essential?

---

### Post by Sef on 2006-04-01
To download build-essential, so you can compile, do this:

sudo apt-get update

sudo apt-get install build-essential

---

### Post by amitroy5 on 2006-04-01
I already downloaded it. However, I am still not sure how to use it. Thanks!

---

### Post by taurus on 2006-04-01
You have downloaded what and not sure how to use what!!!  Open a terminal and from it, type
```

sudo apt-get update
sudo apt-get install build-essential

```
Then unpack whatever you have downloaded and read either README or INSTALL  for further instructions on how to build it...  If not sure, give me the exact name of the file that you've downloaded or where and I can tell you exactly how to build it!!!

---

### Post by amitroy5 on 2006-04-01
How do I find out where it was installed? Thanks!

---

### Post by taurus on 2006-04-01
Where what was installed?  Are you talking about the build-essential package?  Most of the programs that you install by using either apt-get (from command prompt) or synaptic (GUI) are usually in /usr/bin...

---

### Post by amitroy5 on 2006-04-01
I looked though every file and for some reason, I cannot locate it. However, I am able to confirm that it is installed.

---

### Post by taurus on 2006-04-01
What is installed???  You need to be a little more specific in what you are looking for!  Then, I can tell you exactly where it is or how to find it.  Otherwise, I have no idea what you are looking for and we will be going around in circle...

---

### Post by amitroy5 on 2006-04-01
I'm sorry. :( I am looking for the exact place where build-essential has installed.

---

### Post by Mustard on 2006-04-01
I agree with the confusion here. :)  What is 'it'?  Try substituting the actual program name you are looking for instead of saying 'it.

---

### Post by Mustard on 2006-04-01
[QUOTE=amitroy5]I'm sorry. :( I am looking for the exact place where build-essential has installed.[/QUOTE]

You don't run build-essential to compile stuff.  It just installs the necessary tools to make compiling work.  Use the instructions that came with the phg ming to compile.  What type of file did this php ming come in?  Was it a tar.gz file?

It might be helpful if you show where you downloaded it from too, so we can see that we can all be on the same page with this problem you are having.

---

### Post by taurus on 2006-04-01
[QUOTE=amitroy5]I'm sorry. :( I am looking for the exact place where build-essential has installed.[/QUOTE]
Actually, it didn't install build-essential as a program name.  Instead, build-essential installed a bunch of programs and their libraries like gcc, make, etc. so you can build stuff from sources.  Now, just unpack your source and follow the instructions in either README and/or INSTALL to build or install it...  Don't worry about build-essential anymore!

---

### Post by amitroy5 on 2006-04-01
Thank you for the clarification. :) Here are what the instructions say:

  PYTHON
  ******

  (You may need python 1.5.2 or higher)

      $ ./configure
      $ make static
      $ cd py_ext
      $ make mingcmodule.so

  Then fix the install path in the Makefile

  Then install

      $ make install

How should I follow these? I think it has something to do with the Terminal.

---

### Post by taurus on 2006-04-01
Yes, open a terminal, Applications -> Accessories -> Terminal, and do all that except the last command, you need to use sudo if you want to install it on your system since you need root's permission to write to it,
```

sudo make install

```

---

### Post by amitroy5 on 2006-04-01
Reguarding these steps:

 $ ./configure
$ make static
$ cd py_ext
$ make mingcmodule.so

Is each line usually a separate command?

---

### Post by BoneKracker on 2006-04-01
"I think it has something to do with the terminal" suggests to me that you might benefit from doing a bit of research on your own regarding how one compiles software in Linux.

Just try some general searches in these forums or more broadly on the internet.  Then, when you have taken advantage of that readily-available information, you might use the forum to get help with unresolved questions.

:D

---

### Post by amitroy5 on 2006-04-01
Is there a guide to compile on Ubuntu? I failed to find anything, even on Google. :( Thanks!

---

### Post by Mustard on 2006-04-01
[QUOTE=amitroy5]Is there a guide to compile on Ubuntu? I failed to find anything, even on Google. :( Thanks![/QUOTE]

A guide is not going to tell you much more than the instructions given above by the maker of the program.  Basically you would do each of those commands, one at a time.  The only change being the use of 'sudo make install' instead of 'make install' at the end.

If you try to 'make mingcmodule.so' and it gives you errors, you would need to study the errors to see what 'dependencies' it wants you to install to fix the errors.  It's probably best if you paste the errors in here so we can decipher them for you.  Compiling from source is sort of jumping into the deep end with regards to using linux, but I take it you have some pressing reason to compile this. :)


I would even go one step further and not use 'make install' at all.  I would download and install the checkinstall program using this command..

```
sudo apt-get install checkinstall
```

Then when it comes to the stage to use the 'sudo make install' command, I would use this instead..

```
sudo checkinstall
```

Using 'sudo checkinstall', its going to do the 'sudo make install' part, but it will also create a .deb package that you can use to uninstall, should you wish to do so in the future.  If you skip using 'checkinstall' and just use 'make install' then uninstalling the compiled program is going to be a somewhat difficult process at times.

---

### Post by Mustard on 2006-04-01
I'd mention that in terms of guides for compiling on Ubuntu, there is a brief mention of it in the sticky thread entitled 'How to Help Yourself' at the top of the Absolute Beginners forum.  The sticky threads are often overlooked by people when they read forums, but people might do well to realise that they are 'sticky threads' for a reason. They have good information in them. :)

How to Help Yourself is here..

[http://www.ubuntuforums.org/showthread.php?t=142716](http://www.ubuntuforums.org/showthread.php?t=142716)

This is another recently authored thread to help with basic stuff..

[http://ubuntuforums.org/showthread.php?t=153118](http://ubuntuforums.org/showthread.php?t=153118)

---

### Post by amitroy5 on 2006-04-01
Sorry about asking about this. This is the first thing I ever compiled on linux. I was able to get though the first step:

$ ./configure

After that finished, I entered:

$ make static

However, after I do this command, I get the following error:
make: *** No rule to make target `static'.  Stop.

How should I proceed?

---

### Post by Mustard on 2006-04-01
[QUOTE=amitroy5]Sorry about asking about this. This is the first thing I ever compiled on linux. I was able to get though the first step:

$ ./configure

After that finished, I entered:

$ make static

However, after I do this command, I get the following error:
make: *** No rule to make target `static'.  Stop.

How should I proceed?[/QUOTE]

It's quite fine to ask questions. :)  You don't have to apologise.

I have to say though that I am stumped on this one too.  I've never seen 'make static' before, so I guess you will have to see if anyone else comes along that knows what this error means.

---

