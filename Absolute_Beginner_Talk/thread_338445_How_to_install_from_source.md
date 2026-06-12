---
title: "How to install from source?"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by tbasherizer on 2007-01-14
Hey, I've got a problem with installing a program. I went to psychocats.net and read their tutorials on how to do stuff in Ubuntu. I followed their directions to install the program I needed, but when I went to enter into the Konsole "tar -xvzf VMware-server-1.0.1-29996.tar.gz" Konsole replied by saying that such a directory didn't exist, but I followed everything the tutorial said for me to do.](*,)  Gach! I'm frustrated.

---

### Post by meng on 2007-01-14
You're obviously not in the correct directory when you ran that command. Where did you save the file?

---

### Post by tbasherizer on 2007-01-14
The desktop, like the tutorial said. That's why I was wondering why it didn't work.

---

### Post by meng on 2007-01-14
Well did you try:
cd ~/Desktop
before the tar command?

---

### Post by tbasherizer on 2007-01-14
It wasn't in the tutorial, but I got Ubuntu to figure out Linux, so I'll try that.

Thanks.

---

### Post by tbasherizer on 2007-01-14
Thank you! It's working now.

---

### Post by tbasherizer on 2007-01-14
Oh! I have a new problem. When I type in the next set of directions in the Konsole, cd VMware-server-1.0.1-29996.tar.gz, it says there is no such directory. How should I type it differently?

---

### Post by Pobega on 2007-01-14
> **tbasherizer said:**
> Oh! I have a new problem. When I type in the next set of directions in the Konsole, cd VMware-server-1.0.1-29996.tar.gz, it says there is no such directory. How should I type it differently?

user@linux~$: cd VMware-server-1.0.1-29996

**Edit:** I'll explain installing from source for you, so that you can figure it out in future ventures.

When you get a tarball, you have to extract it (I usually use the GUI to do this, but depending upon the extension you can use multiple terminal commands).

Now that tarball creates a directory, usually the name of the file without the extension (So if the name is program.tar.gz the folder will be called program).

So you can cd into that directory (cd stands for change directory), and the usually install is as follows:

./configure *(Creates the make file)*
make *(This usually takes the longest)*
sudo make install *(This is the actual installation into your filesystem)*

---

### Post by tbasherizer on 2007-01-14
Ol, I'll try that out.

---

### Post by tbasherizer on 2007-01-14
I used ./configure, but it says no directory found when I am in fact trying to execute  a command.

---

### Post by rabid9797 on 2007-01-14
> **tbasherizer said:**
> I used ./configure, but it says no directory found when I am in fact trying to execute  a command.

your got to extract the tarball(tar.gz file), than cd to the new folder it made, so:

1. after you extract the tarball, do this:
```

cd VMware-server-1.0.1-29996

```

2. then do ./configure and follow the rest of the directions

---

### Post by Linux&amp;Lizards on 2007-01-14
I think he is doing it right..........

I have also had the exact same problem, I just try not to install anyhting from source and then wait till I can go to my local lug for support.

---

### Post by tbasherizer on 2007-01-14
> **rabid9797 said:**
> your got to extract the tarball(tar.gz file), than cd to the new folder it made, so:

1. after you extract the tarball, do this:
```

cd VMware-server-1.0.1-29996

```

2. then do ./configure and follow the rest of the directions


That's what I'm doing, but ./configure is not working.

---

### Post by tbasherizer on 2007-01-14
> **Linux&Lizards said:**
> I think he is doing it right..........

I have also had the exact same problem, I just try not to install anyhting from source and then wait till I can go to my local lug for support.

Lug? What is that?

---

### Post by qamelian on 2007-01-14
> **tbasherizer said:**
> Lug? What is that?

LUG = Linux Users Group

---

### Post by tbasherizer on 2007-01-14
Does anyone know why my ./configure is not working?

---

### Post by jonny on 2007-01-14
The command ./configure actually tries to run a program called configure in the present working directory - the ./ at the beginning is a security measure to help prevent accidental execution of program files.

You need to look in the directory that you're working in (the command pwd will tell you where you are) and make sure that you have a configure file.  If you don't, you need to find it - look in all the subdirectories - or use some different compilation instructions - not all programs install in the same way, so try looking for a file called README or INSTALL.  Another thing you should do is check that you've installed the build-essential software package.

But - and this is a friendly warning, so don't take it the wrong way - you should be aware that rolling your own code isn't really recommended on Ubuntu.  You can do it, but it's quite possible that a badly behave application could destroy your whole system.  You should never compile and install programs on a system that's important to you unless you're confident that you can unravel any problems or rebuild it from scratch should the worst happen.

---

### Post by confused57 on 2007-01-14
> **tbasherizer said:**
> Does anyone know why my ./configure is not working?
After you've changed directories as mentioned(cd VMware-server-1.0.1-29996)...at the prompt, enter:
```
ls
```

If there is a "configure" or "CONFIGURE" file there, make sure you're typing it exactly as it's listed...if it still doesn't work, you probably need to install "build-essential", using Synaptic Package Manager.

---

### Post by tbasherizer on 2007-01-14
I found a config file, but when I type in ./config, it says access denied. Any ideas?

---

### Post by po0f on 2007-01-14
tbasherizer,

Post the output of:
```
[FONT="Courier New"]$ ls -l ~/Desktop/VMware-server-1.0.1-29996[/FONT]
```

---

### Post by riven0 on 2007-01-14
Can you paste the output of this command while in the Vmware directory?:
> 
ls -a

---

### Post by tbasherizer on 2007-01-14
bash: Is: command not found

There you go

---

### Post by meng on 2007-01-14
that's l as in Larry, a lower-case L.
ls

NOT
I as in the first person singular pronoun, upper case i.

---

### Post by tbasherizer on 2007-01-14
Forgive my being a newb, here it is

.   bin  etc    installer  man   vmware-install.pl
..  doc  FILES  lib        sbin  vmware-vix

---

### Post by riven0 on 2007-01-14
> **tbasherizer said:**
> Forgive my being a newb, here it is

.   bin  etc    installer  man   vmware-install.pl
..  doc  FILES  lib        sbin  vmware-vix

Okay, so in the terminal, can you try this?:
> 
sudo vmware-install.pl

what does that do?

---

### Post by marx2k on 2007-01-14
Just seeing if I can figure this out as I'm reading this thread.  Would this be a precompiled (by VMWare) binary install?

---

### Post by tbasherizer on 2007-01-14
> **riven0 said:**
> Okay, so in the terminal, can you try this?:


what does that do?

it returns negatively.

---

### Post by po0f on 2007-01-14
tbasherizer,

An error message would be nice.

[EDIT]

If it's a "command not found" message, try `sudo perl ./vmware-install.pl`.

---

### Post by riven0 on 2007-01-14
> **po0f said:**
> If it's a "command not found" message, try `sudo perl ./vmware-install.pl`.

*smacks forhead* That's correct, though you may not need the **perl**. At least I didn't on my side.

---

### Post by misha680 on 2007-01-15
I think the problem might be he needs to type:
```
sudo ./vmware-install.pl
```
as the command is in the current directory and not known system wide.

Misha

---

### Post by tbasherizer on 2007-01-15
Thanks guys, but I discovered Wine. I do have the means to make a Windows XP virtual machine and I will, once I use your wonderful advice.

I'll post more of my n00bidities later. I am currently on my school system, using Windows, but fortunately enough I at least have Firefox portable to sustain me.

---

### Post by tbasherizer on 2007-01-16
Ok, I've got that far. now can someone walk me through what to do next?

---

### Post by riven0 on 2007-01-16
> **tbasherizer said:**
> Ok, I've got that far. now can someone walk me through what to do next?

Got *what* far? Where exactly are you?

---

### Post by tbasherizer on 2007-01-16
Installing the content of the package.

In which directory do you want to install the binary files?
[/bin] /bin

What is the directory that contains the init directories (rc0.d/ to rc6.d/)?
[/etc]   

That far. 'Scuse my n00bidity once again.

---

### Post by riven0 on 2007-01-16
No problem. Just keep hitting enter. 

When you get to the networking setup, though, you may want to choose NAT. It's really up to you, but that's what I recommend. Other than that, though, just go with the defaults until the installation completes.

---

### Post by tbasherizer on 2007-01-16
Uh oh.

Here is what it says when it starts to install

"The file /etc/vmware that this program was about to install already exists.
Overwrite? [yes]

Unable to copy the source file ./installer/services.sh to the destination file
/etc/vmware.

Execution aborted."

Can you explain?

---

### Post by riven0 on 2007-01-16
Alright, try deleting that directory and then do a re-installation. So, open the terminal and copy and paste this command:

> sudo rm -r /etc/vmware

Now cd back to wherever your vmware folder is again and re-start the installation:

> sudo ./vmware-install.pl

---

### Post by tbasherizer on 2007-01-16
So I take it that Konsole is the super user?

---

### Post by tbasherizer on 2007-01-16
Oh crap, scratch that last one there, I have a new problem. here it is.

"None of the pre-built vmmon modules for VMware Server is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is not an existing directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]"

Could you explain how what you will suggest works?

---

### Post by riven0 on 2007-01-16
Does it give you any error message at all? It should compile the headers, and then throw an error if it doesn't work correctly. So go ahead and hit Enter and then see what it does.

---

### Post by tbasherizer on 2007-01-16
It says that it;s going to make something for me, and that I need a C compiler installed to do that, so I guess it's back to Synaptic to get it then.

---

### Post by tbasherizer on 2007-01-16
I installed a copmiler from Synaptic, but it seems to require a compiler hat is in the usr/src/linux subdirectory, but in the /src subdirectory, there is no linux folder, so wth?

---

### Post by riven0 on 2007-01-16
Try installing this and then re-doing the VMWare installation:

> sudo apt-get install linux-headers-`uname -r` build-essential xinetd

See if that'll work.

---

### Post by tbasherizer on 2007-01-16
I got it, thanks. IT finally works!

---

### Post by Pobega on 2007-01-16
> **tbasherizer said:**
> So I take it that Konsole is the super user?

Also just for note, Konsole isn't superuser. Konsole is the KDE equivalent to a terminal, and it's just the name of the program.

The superuser is named root, root can do anything it wants on your filesystem; Which is why logins are disabled by default (Instead of logging into root to ensure you don't break anything, you use sudo before root commands).

---

### Post by lexrexus on 2007-01-17
> **tbasherizer said:**
> I used ./configure, but it says no directory found when I am in fact trying to execute  a command.

Hey!  Maybe I, too, have missed something above, but I'm a Uby Newbie, and am waiting for this to be continued/answered - too, I assume!   Yo?](*,)

---

### Post by riven0 on 2007-01-17
> **lexrexus said:**
> Hey!  Maybe I, too, have missed something above, but I'm a Uby Newbie, and am waiting for this to be continued/answered - too, I assume!   Yo?](*,)

Lexrexus, go to the terminal and copy and paste this:
> 
sudo apt-get install linux-headers-`uname -r` build-essential xinetd

After that's installed,  cd to your VMWare directory, and do this:

> sudo ./vmware-install.pl

Then continue with the installation as normal.

---

