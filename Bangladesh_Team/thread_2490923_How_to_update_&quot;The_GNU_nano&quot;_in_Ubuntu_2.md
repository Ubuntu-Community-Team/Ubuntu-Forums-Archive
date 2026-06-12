---
title: "How to update &quot;The GNU nano&quot; in Ubuntu 22.04.3 LTS (Configure Error Fixed)"
date: 2023-09-20
forum: Bangladesh Team
---

### Post by helloarmaan on 2023-09-20
Usually we don't have many people from [COLOR=#008000]**Bangladesh**[/COLOR] moving here, the situation has become like a desert here. Anyway, I'll try and post one if it helps.
Today, suddenly I wish it would be better if it was possible to keep the works that I have updated in the form of posts. I'm not that super expert at operating Ubuntu although I'm a Student of Computer Technology. So without further ado let's finish today's post. 


The first thing we need to do update **"The GNU nano" **is to open our terminal any type


```
sudo apt-get update
```

You will then need to enter your password so that you can **update** your [COLOR=#006400][B]package list
[/B][/COLOR]

you need to [COLOR=#ff0000]**remove**[/COLOR] the old version of nano with the command


```
sudo apt remove nano
```

It will ask you for a permission to proceed, You just need to press [COLOR=#0000cd]**"The ENTER Button" **[/COLOR]for the default [COLOR=#008080]**"Y"**[/COLOR]  option.


Then, you need to download the source code of the latest version of nano from its official website. You can use the command wget to download it. For example, if you want to install nano version 7.0, you can run 


```
wget https://www.nano-editor.org/dist/v7/nano-7.2.tar.gz
```

Next, you need to extract the downloaded file with the command 


```
tar -xf nano-7.2.tar.gz
```

After that, you need to change your directory to the extracted folder with the command 


```
cd nano-7. 2
```

Then, you need to install the curses header files on your system. The curses library is a text-based user interface library that allows you to create interactive programs that run in a terminal. The header files are the files that contain the declarations and definitions of the functions and variables that are part of the library. You need these files to compile and link your programs that use the curses library.


Fortunately you are using Ubuntu which is a Debian-based OS, you can use the following command to install the [COLOR=#2f4f4f]**libncurses5-dev package**[/COLOR], which contains the header files and other development files for the ncurses library, a modern version of the curses library:


```
sudo apt-get install libncurses5-dev
```

Without this you cannot configure the file. you might face a [COLOR=#ff0000]**configuration error**[/COLOR].
e.g. 
```
[COLOR=#ff0000]configure: error: [/COLOR][COLOR=#ff0000]  
    *** No curses lib was found.  Please install the curses header files[/COLOR]
[COLOR=#ff0000]    *** from libncurses-dev (Debian), ncurses-devel (Fedora), or similar.
[/COLOR][COLOR=#ff0000]    *** (Or install ncurses from https://ftp.gnu.org/gnu/ncurses/.)[/COLOR]

```

Then, you need to run the configuration script with the command 


```
./configure
```

[COLOR=#008080]**Or**[/COLOR], You can also add some options to customize your installation. For example, if you want to enable UTF-8 support, you can run 


```
./configure --enable-utf8
```

Next, you need to compile the source code with the command 


```
make
```


Finally, you need to install the compiled program with the command 


```
sudo make install
```

If you want to check after successful installation the latest version of **"The GNU nano" **by running 


```
nano --version

```

Hope it installed **[COLOR=#2f4f4f]successfully[/COLOR]** on your machine. 
Feel free to let me know if you face any problem.

---

### Post by TheFu on 2023-09-21
There's no accounting for taste.  Why bother with nano at all. There are so many better editors to choose.  "Better" in pretty much any meaning of the word.  
[LIST]
[*]More capable
[*]Smaller
[*]Easier to use
[/LIST]

In short, nano isn't worth our time.  That may sound harsh.

---

### Post by helloarmaan on 2023-09-22
Brother, There're more than 70% people in our country who don't know what is an editor :'( for this reason, this post is only for those who want to learn bash script or want to know something at very basic level. Unfortunately we're from those people who don't know about the root of a tree. I know nano isn't worth time.

I was just trying to Post something for them who don't know even what is an Operating System.

---

### Post by TheFu on 2023-09-22
> **helloarmaan said:**
> Brother, There're more than 70% people in our country who don't know what is an editor :'( for this reason, this post is only for those who want to learn bash script or want to know something at very basic level. Unfortunately we're from those people who don't know about the root of a tree. I know nano isn't worth time.

I was just trying to Post something for them who don't know even what is an Operating System.

I've been around Linux and Unix for decades.  My issue really isn't with nano, though it is pretty limited for the most part, but with suggesting that anyone needs the most up-to-date version of it or that they should go outside the package manager to install anything if they aren't an expert.   

Non-experts should still use the nano software and versions provided from the core Canonical repos.  Getting some source code, compiling it and installing it is a terrible idea. The pre-installed version of nano would be sufficient for quick edits by almost anyone. Getting souce code defeats the purpose of having a package manager and getting curated security updates from professionals, like Canonical.  Package managers and curated repos are one of the top 5 reasons for choosing Linux over other OSes.

Now, if you had suggested some new editor, call it "Gee-Wiz" editor, but not available in the repos and Gee-Wize provided 500 ***useful*** things that other editors didn't do, I could get behind suggesting how to get, compile, and install it. Since you are writing in English, that would be a great tutorial for that part of the forums here.

I honestly didn't notice this was posted in the Bangladesh subforum. I would expect Bengali/Bangla to be posted here. My mistake.  I'll go away now.

---

### Post by ajgreeny on 2023-09-23
I make a lot of use of nano as a simple cli text editor and have never in my 18 years of using Ubuntu needed what TheFu is talking of, ie, an editor, so cli applications such as vi are totally unnecessary to me.

If you want a simple cli text editor there is absolutely no reason to look for or use an alternative to nano.
Why make things more complicated than they need to be?

---

### Post by aljames2 on 2023-09-24
I agree, for basic editing, the default nano should be sufficient for editing non-system config files.  I certainly wouldn't go beyond the version that is already provided in the release repo, and wouldn't encourage someone learning to do so either.  I do actually replace nano with vim in my debian VM that I use for coding practice due to its configurability with colorizations and indentions to make reading code easier.  In learning vim this way, it's become a favorite of mine.  But I certainly use nano for quick reasons, like booting up a Live USB for some utility work, or during the early stages of installing/reinstalling.

---

### Post by Tadaen_Sylvermane on 2023-09-24
I use nano because I'm to lazy to lean vim. Something I need to remedy. May not be ideal but it works for folks. Anything else is to complicated for most.

---

