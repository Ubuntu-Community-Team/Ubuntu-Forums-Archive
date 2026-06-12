---
title: "How do you compile software from its source?"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by Kossilar on 2007-01-26
How do you compile software from its source?

---

### Post by mizar001 on 2007-01-26
The source is coded in different languages, so you must have the compiler for this language.
Furthermore you need all the libraries that the source code is calling.

In most of the cases, with linux source code, the language is C and you need a C compiler. The procedure is :
-read the README file that eventually is bundled with the source package, for detailed instruction.
(Probably the README will tell you to configure the building of the source code, with './configure', and so build the code with 'make'. 

gcc is a good compiler, already installed from start in ubuntu, and when you call the configure and make commands, it should start automatically.

---

### Post by hyper_ch on 2007-01-26
You normally don't ^^

But then, download the source, extract it, go to the folder and execute the following commands:
```

./configure

```
```

make

```
```

sudo make install

```

---

### Post by Kossilar on 2007-01-26
Okay, is there like a guide, or a separate piece of software that will handle compiling? Everybody makes it sound so simple, listing 3 commands. But they've never once worked. 

Not once.

---

### Post by fenian on 2007-01-26
Make sure you have the tools to compile type this in a terminal

sudo apt-get install build-essential

---

### Post by deadgobby on 2007-01-26
First off what are you trying to install? Did you look in Synaptic? Synaptic may be the first check to see if the program you want to install. Go to System> Admin> Synaptic. Here is a link to install from source AKA tar ball.
[http://psychocats.net/ubuntu/index](http://psychocats.net/ubuntu/index)
An easy way to unpack a tar is to left click on the  tar ball pack. You have two options. Either open up with Archive manager or scroll down to Unpack Here. After the tar ball or from source is to open up the new foler. There is a read me file or install file. The install file some times will tell you how to install from source.
Gobby

---

### Post by xhaan on 2007-01-26
> **Kossilar said:**
> Okay, is there like a guide, or a separate piece of software that will handle compiling? Everybody makes it sound so simple, listing 3 commands. But they've never once worked. 

Not once.

It can be that simple, in a perfect world...
It's just hard to say how something will compile because it may require certain libraries, a specific kernel, using configure or make options, and there are things that can go wrong such as having libraries or a compiler that are the wrong version or are different builds which cause compile errors... and of course if you don't have *make* and a compiler installed with the correct paths, the commands won't work at all.

---

### Post by Kossilar on 2007-01-26
*sigh* Never mind. Its obvious I'm wasting my time. 

I've read all this stuff already, it just tells you the same things over and over again.

It doesn't work.

---

### Post by xhaan on 2007-01-26
> **Kossilar said:**
> *sigh* Never mind. Its obvious I'm wasting my time. 

I've read all this stuff already, it just tells you the same things over and over again.

It doesn't work.

What are you trying to compile? Some sources won't compile on certain systems no matter how hard you try... so if it's a specific program you're trying to build, it may just simply not work from that source.

---

### Post by mizar001 on 2007-01-26
Don't think it's easy.
Behind the source code is a developer , that does not think like anyone else, so libraries and tools needed may be different, and some aspects like requirements are not ever easy to define properly.

The problem in compiling is that every time the situation (machine, environment, installed libraries and their version) can change, and if you are not an expert, you are not able to do little modifications to get the compilation work.

For most packages anyway, the configure/make way is working well.

---

### Post by lamego on 2007-01-26
If you are not a developer and you don't have the desire for it, you shouldn't care about compiling from the source, software is available on the repositories, or a developer will compile it for your :)

---

### Post by HereInOz on 2007-01-26
You say it doesn't work, but logic would dictate that, given that there are hundreds, or even thousands of people in the Linux community successfully compiling source code every day, that it does actually work, or no binary files would ever be produced for non-compiling luddites like myself to use.

It must work.  Like me, you probably don't know enough to make it work reliably.  Either spend the time learning all there is to know about compiling from source, or just use the packages to install, and accept that it is not your cup of tea.

---

### Post by Kossilar on 2007-01-26
> You say it doesn't work, but logic would dictate that, given that there are hundreds, or even thousands of people in the Linux community successfully compiling source code every day, that it does actually work, or no binary files would ever be produced for non-compiling luddites like myself to use.

It must work. Like me, you probably don't know enough to make it work reliably. Either spend the time learning all there is to know about compiling from source, or just use the packages to install, and accept that it is not your cup of tea.

You're right of course. 

I think the main issue is that developers aren't as clear as they should be about the specific dependencies their software requires. For example, one developer says that you need SDL_Mixer, but the actual file you need to download is something else entirely. I think maybe that's where the main problem lies, miscommunication.

---

### Post by lamego on 2007-01-26
> I think the main issue is that developers aren't as clear as they should be about the specific dependencies their software requires. For example, one developer says that you need SDL_Mixer, but the actual file you need to download is something else entirely. I think maybe that's where the main problem lies, miscommunication.
Reply With Quote
The same library is packed or distributed in different forms (somtimes with different names) across Linux distributions, developers can not and should not care about each linux distribution.
For developers the standard way to install libraries is also from the source...

Just because its common to compile open source software from the source on Linux people tend to believe that compiling from the source is something that an end user must be able to do.

---

### Post by pay on 2007-01-26
Kossilar. You are making it very hard for people to help you. We need to know what errors you are getting and what program you are trying to compile.

---

### Post by onegreenparker on 2008-01-28
I am fairly new to compiling (been using Synaptic for 2 years) and a couple of questions I've never seen asked:

1) When extracting the archive, should it be extracted to a particular location?
2) Is it a good idea to **sudo** ./configure, **sudo** make and/or **sudo** make install?

On a few occasions, **sudo**ing on any or all of these has helped

---

### Post by jpeddicord on 2008-01-28
> **Kossilar said:**
> You're right of course. 

I think the main issue is that developers aren't as clear as they should be about the specific dependencies their software requires. For example, one developer says that you need SDL_Mixer, but the actual file you need to download is something else entirely. I think maybe that's where the main problem lies, miscommunication.
Could you paste the output of ./configure and any errors associated?

---

### Post by hyper_ch on 2008-01-29
> **onegreenparker said:**
> 2) Is it a good idea to **sudo** ./configure, **sudo** make and/or **sudo** make install?

It is not... configuring and compiling shouldn't need root rights... only the installation should.

---

### Post by Deep fried ice-cream on 2008-02-03
I cant seem to get it to work either, it just "command not found"s when I type ./configure

---

