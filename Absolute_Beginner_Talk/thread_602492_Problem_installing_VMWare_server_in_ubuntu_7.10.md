---
title: "Problem installing VMWare server in ubuntu 7.10"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by nittanylionfan88 on 2007-11-04
I am trying to install VMWare server on ubuntu 7.10 server.  I have used many of the forum posts to help me make progress, but now I have a problem I can't find an answer for.

The installation is complete and I am now trying to run the configuration:
sudo /usr/bin/vmware-config.pl

I keep selecting defaults and I get to this:
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)?

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] 

The path "/usr/src/linux/include" is not an existing directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] 

I have no idea how to proceed, anyone's help is much appreciated.

---

### Post by docshawnc on 2007-11-04
First, make sure your are doing this as super user (through sudo).  If you haven't already done so, grab build essential and the headers you need via synaptic.  Once you've done this, just hitting the return to accept the defaults should work.

To compile anything or work with the kernel you need:

Build-essential

linux-headers (for your version of the kernel)

Both can be found in package manager

or type:

sudo apt-get install build-essential linux-headers-`uname -r`

---

### Post by mdpalow on 2007-11-04
Did you download the 'build-essential' as stated in step 1 of the tutorial for setting up VMware? I assume you're following that, right?

When asked that question, you should only have to type in 'yes' and it should move on by itself...

During this installation, you will see it stop and ask you a question about a path/directory. It looks like: 

[/usr/src/linux/include]

All you have to do is type what you see in the brackets and hit return.

So, it would look like this:

[/usr/src/linux/include]  /usr/src/linux/include


if you see something in brackets and don't know the answer, copy what's in the brackets. It's the default and what you want to use.

good luck...

---

### Post by nittanylionfan88 on 2007-11-04
Thank you, that helped.
I didn't have the server headers downloaded.  Using the synaptic package manager I was able to get them.
I did have to change the path to match the package, but then everything went through from there.
Again, Thanks!

---

