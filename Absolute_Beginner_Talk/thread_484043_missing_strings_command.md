---
title: "missing strings command"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by ColmOsiris on 2007-06-25
The tutorial I am using is telling me to use the 'strings' command. But when I do, I get this:

> -bash: strings: command not found

Can anyone suggest why this might be, please?

Thanks.

---

### Post by DBStevens on 2007-06-25
Yes, your system doesn't have the binutils package installed.

---

### Post by ColmOsiris on 2007-06-25
That's both helpful and not helpful!

What is it, what is it for, where do I get it, and how do I install it?

---

### Post by Cypher on 2007-06-25
Go to System->Adminstration->Synaptic Package Manager. Search for "binutils" and install that package.

If ever you find you need install a package for some utility and don't know what it's called, check out [http://packages.ubuntu.com](http://packages.ubuntu.com).

---

### Post by ColmOsiris on 2007-06-25
> **Cypher said:**
> Go to System->Adminstration->Synaptic Package Manager. Search for "binutils" and install that package.

Thanks. But I don't know how to do this. I am using only the command line, and have no GUI, as I am networked into my Linux server from my Mac, using the Terminal app.

Can I install this thing, whatever it is, using only the command line?

And do I need to worry about why it isn't there to start with?

On the install disk for Ubuntu Server 6.10, I found the following:

     * binutils_2.17-1ubuntu1_i386.deb
     * binutils-static_2.17-1ubuntu1_i386.deb
     * binutils-static-udeb_2.17-1ubuntu1_i386.udeb

Are any of these of any use to me? If so, how do I install them, please?

---

### Post by DBStevens on 2007-06-25
sudo apt-get install binutils

---

### Post by DBStevens on 2007-06-25
I suspect that if you are playing with a tutorial you'll discover more things "missing".

---

### Post by ColmOsiris on 2007-06-25
Blimey! Are things always that easy to install in Linux?

That was a breeze. Thanks!

---

### Post by DBStevens on 2007-06-25
> **ColmOsiris said:**
> Blimey! Are things always that easy to install in Linux?

That was a breeze. Thanks!

Not always but pretty close.   It like most operating systems can fall apart on new hardware.

---

### Post by ColmOsiris on 2007-06-25
I will bear that in mind while I'm doing the tutorial. I'm surprised there doesn''t appear to be such a thing as a standard install of Ubuntu, but never mind! Or perhaps the writer of the tutorial is making assumptions about my setup?

My only concern now is how do I work out which package contains any particular command I might need. Is there any way I can determine that, apart from asking on here?

---

### Post by DBStevens on 2007-06-25
You can inquire of the packaging system, however I have never used the command line for that and in fact I just changed distros.  So I haven't even looked at a lot of the package manger options yet.

---

### Post by Cypher on 2007-06-25
Man..foiled again..I always provide command line instructions and the one time I resort to the GUI, it doesn't work! :)

---

### Post by DBStevens on 2007-06-25
dpkg -h gives a list of the package manager options.

---

### Post by DBStevens on 2007-06-25
Cypher,

You mean to say that a Mainiac beat one of the from away folk?

---

### Post by jyba on 2007-06-25
> My only concern now is how do I work out which package contains any particular command I might need. Is there any way I can determine that, apart from asking on here?

If you type **any** command at the command line and it's in the repository but not on your hard disc, then you'll get an apt-get suggestion. For instance you type '**cow**' and you get...
```

The program 'cow' is currently not installed.  You can install it by typing:
sudo apt-get install fl-cow
Make sure you have the 'universe' component enabled
bash: cow: command not found
```

So then you just copy/paste the command...
```
sudo apt-get install fl-cow

```...it gets installed and you're good to go.

---

### Post by ColmOsiris on 2007-06-25
jyba

I tried typing 'cow' at the command line, but all I got was this:

> -bash: cow: command not found

Am I doing something wrong? What do I have to do to make it do what you said?

---

### Post by wirelessmonkey on 2007-06-25
It replies if you try to apt-get an application... i.e. 'sudo apt-get install cow'  will get the above reply.  'cow' from the prompt will get the 'command not found' reply.

---

### Post by ColmOsiris on 2007-06-25
I tried that, but I didn't get the reply jyba quoted. I got this:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package cow


---

### Post by jyba on 2007-06-25
Sorry, I was trying to keep it simple and then chose the wrong example. Synaptic only knows about those repositories that you are subscribed to. There are 4 repositories - Main, Restricted, Multiverse, and Universe. I think that Ubuntu only comes with Main, and Restricted available. To add the other repositories you should start up Synaptic, then go to Settings > Repositories, and click on the 'New' button to add these two URLs:

URL: [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/)
Distribution: Feisty
Section(s): Universe

and... 

URL: [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/)
Distribution: Feisty
Section(s): Multiverse

...now 'sudo apt-get install fl-cow' should work. :)

---

### Post by kevdog on 2007-06-25
To search for packages that you may know one part of the package name (for example ndiswrapper), do the following at the command line:

sudo apt-cache search ndis  <---Can give part or the whole package name.

Once you find the name of the package from the output, just install as normal
sudo aptitude install ndiswrapper

---

### Post by ColmOsiris on 2007-06-25
Thanks. But I only have access to the command line, first because the Ubuntu Server installer doesn't install a GUI, and second because I am accessing it through the Terminal app on my Mac, which is networked to the Ubuntu Server box.

---

### Post by ColmOsiris on 2007-06-25
> **kevdog said:**
> To search for packages that you may know one part of the package name (for example ndiswrapper), do the following at the command line:

sudo apt-cache search ndis  <---Can give part or the whole package name.

Once you find the name of the package from the output, just install as normal
sudo aptitude install ndiswrapper

Thanks. But first, I'd need to know that strings was part of the package binutils. Is there any way I could determine that?

---

### Post by kevdog on 2007-06-25
Not sitting at my Ubuntu machine right now, I cant say for certain.  Type

dpkg --help

and look for an option that might suit want you want.  I seem to remember something like -i or --info.

---

### Post by DBStevens on 2007-06-25
dpkg -S|--search <pattern> ...        Find package(s) owning file(s).

---

### Post by ColmOsiris on 2007-06-26
Thanks. I tried this:

```
dpkg -S|--search strings
```

and I got this:

> -bash: --search: command not found
dpkg-query: --search needs at least one file name pattern argument

Use --help for help about querying packages;
Use --license for copyright license and lack of warranty (GNU GPL).


Then I tried this:

```
dpkg -S|--search <strings>

```

and I got this:

> -bash: syntax error near unexpected token `newline'


I also tried 'dpkg --help', but I'm afraid I didn't understand the response!

What did I do wrong, please?

---

### Post by mattg89 on 2007-06-26
either use --search OR -S
That should work.

---

### Post by ColmOsiris on 2007-06-26
Oh yeah, so it does! Thanks.

---

### Post by DBStevens on 2007-06-26
You will find that the form one thing|another thing <pattern> is a very common way to say pick only one of the things seperated by the | and that <pattern> means: sort of looks like or fits a regular expression.

You will run into these shorthand notations all over the place.

How's that tutorial going?

---

### Post by ColmOsiris on 2007-06-26
> **DBStevens said:**
> You will find that the form one thing|another thing <pattern> is a very common way to say pick only one of the things seperated by the | and that <pattern> means: sort of looks like or fits a regular expression.

You will run into these shorthand notations all over the place.

How's that tutorial going?

Thanks very much. I understand the pipe idea, but I thought it was being used in a Unix command way, ie. directing output to something! I am familiar with old IBM manuals, and they used the [either|or] concept all the time. As well as pages whose only content was "This page intentionally left blank"!

I don't really understand the <pattern> thing, though. Can you possibly give me an example?

The tutorial's going well, I think, thanks. I'm getting used to the commands and stuff. I'm quite glad to see that the syntax of Unix functions is pretty similar to PHP, which is where I'm headed - to make an online PHP/MySQL database for a non-profit organisation I'm part of. (I've worked with databases for nearly thirty years, first IBM ISAM ones, and then FileMaker, but only briefly so far with MySQL.)

---

### Post by DBStevens on 2007-06-27
I'd suggest that you find a book or web site that goes into regular expressions in detail.

A real good Perl or PHP book would spend several pages on regular expressions as a number of functions use them.  In addition grep is a command that revolves around regular expressions that is the rep part the g stands for generalized.

A pattern of strings will return all things that contain strings.

---

### Post by ColmOsiris on 2007-06-28
Ah! Having looked up 'regular expressions' I can see that what you're talking about is pattern matching, which is a concept I am familiar with. As is often the case, I find, I do know the concepts people talk about, but not necessarily the terminology! On learning the new (to me) names for old things, all becomes clear!

---

