---
title: "Installed Gnucash 2.0 but I'm running 1.8.12"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by BJinMontreal on 2007-03-09
Over the past few days I have worked my way (with much help from a few ubuntu gurus) through installing Gnucash 2.0.5 (or so I thought) - yet I noticed this evening when I started the program it is version 1.8.12.  I did a quick search through some of the forum topics but didn't see anyone else posting this query, is it a huge ordeal to upgrade from 1.8.12 to 2.0.5?
I am not in a hurry to upgrade as I am still learning the program and what it can do, but if anyone can point me in the right direction I would greatly appreciate it.
BJ

---

### Post by JAPrufrock on 2007-03-09
> **BJinMontreal said:**
> Over the past few days I have worked my way (with much help from a few ubuntu gurus) through installing Gnucash 2.0.5 (or so I thought) - yet I noticed this evening when I started the program it is version 1.8.12.  I did a quick search through some of the forum topics but didn't see anyone else posting this query, is it a huge ordeal to upgrade from 1.8.12 to 2.0.5?
I am not in a hurry to upgrade as I am still learning the program and what it can do, but if anyone can point me in the right direction I would greatly appreciate it.
BJ

Gnucash 1.8.12 is what you can install through Synaptic, apt-get, etc.   Getting Gnucash 2.0.5 installed is a little more difficult.  GnuCash 2.0.5 can be downloaded from sourceforge.net and is available as source code ([http://www.gnucash.org/)](http://www.gnucash.org/)).  Installing binaries is more difficult that installing .deb or rpm files.  There are howto's on installing from source, but it isn't quick and easy (though doable)

I suggest you go to the Gnucash web page and review what kind of extra goodies 2.0.5 will give you to see if it's worth it.

---

### Post by BJinMontreal on 2007-03-09
JAPrufock,
That was the route I had taken .. I used the scripts from the Mint Linux site for downloading and installing 2.0.5 - right through creating the gnucash-2.0.5 directory where I downloaded the 2.0.5 tar.gz.  That is why I was surprised to see the 1.8.12 version on my computer.
BJ

---

### Post by JAPrufrock on 2007-03-09
If you didn't remove 1.8.12, it's still there, even though you installed 2.0.  Unless you set up 2.0 as a desktop entry, if you enter gnucash in the terminal, or by clicking on the icon, 1.8.12 would load.  Find out where the executable file, "gnucash", is for 2.0 and see if you can open it.  Try entering the following command in a terminal:  *sudo find / -name gnucash -type f*     The result of this search should show you where the executable "gnucash" file(s) are located.

---

### Post by BJinMontreal on 2007-03-10
JA,
This is what it's telling me:
brian@brian-compaq:~$ sudo find / -name gnucash -type f
Password:
/usr/bin/gnucash
/usr/lib/gnucash/overrides/gnucash
/usr/share/menu/gnucash

Not sure what that second line means - unless lib is where 1.8.12 is and it's overriding 2.0.5 in bin.
How do I setup Gnucash as a desktop entry? I am starting the program through Terminal.
Thanks
BJ

---

### Post by JAPrufrock on 2007-03-10
> **BJinMontreal said:**
> JA,
This is what it's telling me:
brian@brian-compaq:~$ sudo find / -name gnucash -type f
Password:
/usr/bin/gnucash
/usr/lib/gnucash/overrides/gnucash
/usr/share/menu/gnucash

Not sure what that second line means - unless lib is where 1.8.12 is and it's overriding 2.0.5 in bin.
How do I setup Gnucash as a desktop entry? I am starting the program through Terminal.
Thanks
BJ

Your output using find is exactly what I get from my machine (I have 1.8.12 installed also).  Since /usr/bin/ is in your PATH, whenever you type gnucash, 1.8.12 is loaded.  So the question is, where is 2.0.5?  And why weren't there 2 different "gnucash" executable files in 2 different locations, one for 1.8.12 and another for 2.0.5?  My Gnucash 1.8.12 files are stored in the folder /usr/share/gnucash/ .  Try using the command "locate gnucash" in a terminal.  The output should be a whole lot of files in the directory /usr/share/gnucash/.    Another different directory should pop up with Gnucash 2.0.5 files in it (unless you compiled 2.0.5 in the same directories as 1.8.12).

---

### Post by BJinMontreal on 2007-03-10
OK - it appears as though I have files located in a ../gnucash/gnucash-2.0.5 directory as well as the expected /usr/share/gnucash directory.
The number of lines the "locate" command generated is too many for me to go back to the beginning to check the exact location of 2.0.5 but using the "ls" command within a terminal shows me it is in my home/brian/gnucash/gnucash-2.0.5 folder.
Do I remove the the usr/share/gnucash files and move the 2.0.5 files into it?  If so what would be the proper commands (as I don't want to screw up anything)?
TIA
BJ

---

### Post by JAPrufrock on 2007-03-10
> **BJinMontreal said:**
> OK - it appears as though I have files located in a ../gnucash/gnucash-2.0.5 directory as well as the expected /usr/share/gnucash directory.
The number of lines the "locate" command generated is too many for me to go back to the beginning to check the exact location of 2.0.5 but using the "ls" command within a terminal shows me it is in my home/brian/gnucash/gnucash-2.0.5 folder.
Do I remove the the usr/share/gnucash files and move the 2.0.5 files into it?  If so what would be the proper commands (as I don't want to screw up anything)?
TIA
BJ

Nope, I wouldn't move anything.   Gnucash 2.0.5 should run where it is.  Now what you have to do is find out what the executable file is called, and where it is located.  Most often, it's in /usr/bin so look there.  Since there was already a "gnucash" executable there already (1.8.12), it should have been named something else with gnucash in it's name, like "gnucash-2.0.5" or something like that.  Note: In the terminal all executable files are green.

---

### Post by BJinMontreal on 2007-03-10
JA
My /usr/bin lists the following gnucash executables:
gnopernicus-mag-config   
gnucash
gnucash-config
gnucash-env    
gnucash-make-guids
gnucash-run-script   
goad-browser

only one copy of gnucash.

In the ../gnucash/gnucash-2.0.5 directory there are no gnucash executable files
BJ

---

### Post by JAPrufrock on 2007-03-10
> **BJinMontreal said:**
> JA
My /usr/bin lists the following gnucash executables:
gnopernicus-mag-config   
gnucash
gnucash-config
gnucash-env    
gnucash-make-guids
gnucash-run-script   
goad-browser

only one copy of gnucash.

In the ../gnucash/gnucash-2.0.5 directory there are no gnucash executable files
BJ

Are there any subdirectories in gnucash-2.0.5.?  Any executable files in there?

Run the followng in terminal:
gnucash-config --version

And check /usr/local/bin for a gnucash executable.

If the version is 1.8.12 and there's nothing in /usr/local/bin, I'm starting to think that maybe the installation failed.  Either that, or you installed it, but for some reason the version number never changed.   

To make sure what version you have:  Open Gnucash, go to "Tools", then "Commodity editor", then click "Show National Currencies".  Look for the Russian Ruble symbol.  If it's RUR, you are using Gnucash 1.8.12.  If it's RUB, you are using 2.0.5.

Since I never compiled the 2.0.5 binary, I'm sort of flying in the dark.  Maybe someone else can help here.

---

### Post by freebird54 on 2007-03-11
My first thought from q quick read of this post is that the 2.05 tarball is still balled!  Perhaps have him check the total files list in the 2.05 directory for more clues?  Too new myself to try to direct further myself yet... :)

---

### Post by JAPrufrock on 2007-03-11
> **freebird54 said:**
> My first thought from q quick read of this post is that the 2.05 tarball is still balled!  Perhaps have him check the total files list in the 2.05 directory for more clues?  Too new myself to try to direct further myself yet... :)

Yeah, I was thinking the same.  BJinMontreal, if there are no subdirectories under the 2.05 directory, the install probably never occurred.  You may have thought you installed gnucash, but in fact just downloaded the tarball and unballed it into a directory you created.  In order to compile the binary file you would have had to run *./configure* and *make install*.  If you didn't, you didn't compile/install 2.05.

---

### Post by BJinMontreal on 2007-03-11
The gnucash-2.0.5 directory is loaded with files and sub-directories ,, and the russian Ruble is listed as RUR - it's definitely 1.8.12 that I'm running.
BJ

I remember running the /.configure command because the first time I did it my build-essential was broken and I had to remove and re-install it.  After that I was able to run the /.configure command.  Maybe I'll try running the make install command again.

---

### Post by JAPrufrock on 2007-03-11
> **BJinMontreal said:**
> The gnucash-2.0.5 directory is loaded with files and sub-directories ,, and the russian Ruble is listed as RUR - it's definitely 1.8.12 that I'm running.
BJ

I remember running the /.configure command because the first time I did it my build-essential was broken and I had to remove and re-install it.  After that I was able to run the /.configure command.  Maybe I'll try running the make install command again.

Ok, looks like it was installed.  I looked at the README file included with 1.8.12 (under doc/html). You might want to try to find it in your 2.0.5. subdirectory.   Here's some of it:

> GnuCash supports two types of install, the first is the normal
    /usr or /usr/local/ style, where the files are installed into
    /usr/bin /usr/lib, etc.  This is the default.

It also states the the executive file is named  "gnucash"

You could try the following:
If you ran the make install command after you ran the /. configure command for the second time, that shouldn't be the problem.  If you didn't, by all means run make install again.

I assume you used the default install.  If 2.0.5 uses the same file structure as 1.8.12, it should have overwritten your 1.8.12, _unless_ the default is _not_ to overwrite files.
Even though I didn't read anywhere that you should remove old versions of gnucash before compiling a new one, maybe that's the problem.  If so, you would have to remove 1.8.12 using synaptic, and then re-install 2.0.5.  Since it would be easy to reinstall 1.8.12 if you had to, and since you've already had experience compiling 2.0.5, it might not be that much work.

---

### Post by BJinMontreal on 2007-03-11
Thanks for all the help with this - I think what I will do for now is continue using the 1.8.12 until I am familiar with it, and then, should I decide to upgrade to 2.0.5 uninstall it and re-install the 2.0.5 again.

The one problem I have found is I cannot access the tutorial and help screens in gnucash - I get the error message 
Not Found
The specified URL could not be loaded

---

### Post by JAPrufrock on 2007-03-11
> **BJinMontreal said:**
> Thanks for all the help with this - I think what I will do for now is continue using the 1.8.12 until I am familiar with it, and then, should I decide to upgrade to 2.0.5 uninstall it and re-install the 2.0.5 again.

The one problem I have found is I cannot access the tutorial and help screens in gnucash - I get the error message 
Not Found
The specified URL could not be loaded

Sorry I couldn't help.  I noticed that Gnucash 2.0.1 is available in the repositories for Edgy.  Unfortunately not for Dapper.

---

### Post by BJinMontreal on 2007-03-12
JA,
Actually you were a great help.  I've only being using Ubuntu for a little over a month (if that) and anytime I can go through the processes of finding files, compiling programs, or just reading the steps for doing some of these things, it makes the whole learning process that much clearer.
BJ

---

### Post by JAPrufrock on 2007-03-12
I think you're going about it the right way.  In a few months you'll be helping others.

---

