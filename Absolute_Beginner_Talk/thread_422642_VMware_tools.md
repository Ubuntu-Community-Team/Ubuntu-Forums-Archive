---
title: "VMware tools"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by joejr on 2007-04-25
I am running Edubuntu as a virtual machine on a mac using VMware fusion.  It works pretty well but could work better if i could install the tool set.  When I tell VMware to install VMware tools it places a cd image on my desk top labeled VMware tools.  I can't for the life of me figure out what to do with it or how to get it to run.  
     I will admit I am not sharp when it comes to computers.  If someone can give me the instructions for complete morons I would greatly appreciate it.

                       Joe

---

### Post by Anicka on 2007-04-25
First install a program called alien (sudo aptitude alien). It will ask to install some more packages, but that's normal. There after you do
```
sudo alien --scripts /cdrom/VMwareTools*.rpm
sudo dpkg -i vmwaretools*.deb
sudo vmware-config-tools.pl
```
That worked for me in VMware workstation.

---

### Post by joejr on 2007-04-27
I tried what you said but got an error message it said.

*mkdir: cannot create directory `VMwareTools-7236': File exists*

Thanks though I thought I had it for a minute

                      Joe

---

### Post by Anicka on 2007-04-27
Is there a tar.gz-file on the cd or something simular? In that case you can do like this:
[CODE]cd /tmp
tar -zxf /cdrom/VMwareTools*.tar.gz
cd vmware-tools-distrib
sudo ./vmware-install.pl[\CODE]
I haven't tried this myself, but it should work. but before you run the install-script you have to make sure that you haven't a (partial) install based on the rpm-package. To de-install a deb-package you can use Synaptic or "sudo apt-get purge package".

---

### Post by joejr on 2007-04-27
I appear to be getting somewhere.  But here is what it finally said and got stuck.

[I]None of the pre-built vmmemctl modules for VMware Tools is suitable for your 
running kernel.  Do you want this program to try to build the vmmemctl module 
for your system (you need to have a C compiler installed on your system)? 
[yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] 

The path "/usr/src/linux/include" is not an existing directory.[/I]

Thank you for all the help so far.  We may get through this.

                            Joe

---

### Post by Kilz on 2007-04-27
> **joejr said:**
> I appear to be getting somewhere.  But here is what it finally said and got stuck.

[I]None of the pre-built vmmemctl modules for VMware Tools is suitable for your 
running kernel.  Do you want this program to try to build the vmmemctl module 
for your system (you need to have a C compiler installed on your system)? 
[yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] 

The path "/usr/src/linux/include" is not an existing directory.[/I]

Thank you for all the help so far.  We may get through this.

                            Joe

Try the location 
/usr/src/linux-headers-2.6.20-15-generic/incude

---

### Post by joejr on 2007-05-01
Thanks again, but I am still getting stuck in the same spot.

[I]The path "/usr/src/linux-headers-2.6.20-15-generic/incude" is not an existing 
directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] /usr/src/linux/include
[/I]

Perhaps I don't have the C header files?

                                          Joe

---

### Post by Ziggy72 on 2007-05-01
I don't know if this will help, but do you in fact have a C compiler installed? In any event, and whether you think you have or not, use Synaptic Package Manager to install build-essential and when you've done that, try installing again and see what happens. When installing, accept all the defaults.

---

### Post by joejr on 2007-05-01
Please excuse the stupidity.  Where can I find the synaptic package manager?

---

### Post by joejr on 2007-05-01
Found it, don't need to answer the last question.

---

### Post by joejr on 2007-05-01
Hello again.  I've done all suggested thus far and am still getting.

[I]What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include][/I]

                                Joe

---

### Post by Ziggy72 on 2007-05-01
When you are asked > What is the location of the directory of C header files that match your running kernel? [/usr/src/linux/include]  the [usr/src/linux/include] is what the install program is suggesting as the default location. When you hit Return in response, what message do you get?

---

### Post by ubnewbie2 on 2007-05-01
> **joejr said:**
> Hello again.  I've done all suggested thus far and am still getting.

[I]What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include][/I]

                                Joe

Install the source code for your kernel version.  That will give you the header files it is looking for, and it should symlink /usr/src/linux/include to the right spot I think, so the default it expects will work.

---

### Post by Ziggy72 on 2007-05-01
Ubnewb2 .... > Install the source code for your kernel version. That will give you the header files it is looking for, and it should symlink /usr/src/linux/include to the right spot I think, so the default it expects will work.
What on earth do you mean?
No doubt Ubuntu gurus know but I certainly don't and neither will thousands of other people who are new to Ubuntu. How exactly do you install the source code for your kernel version? Indeed, how do you find what kernel version you have? ... and as for the symlink comment - what does that actually mean? Surely we're talking to people who are new to Ubuntu and very probably new to linux...:confused:

---

### Post by joejr on 2007-05-01
Where do I find the source code?

---

### Post by Anicka on 2007-05-01
Install in synaptic linux-headers-generic (or 386 or 686 if you run one of those) linux-restricted-modules-generic linux-restricted-modules-common linux-image-generic. The source should not be needed.

The c-headers should be found in /lib/modules/2.6.20-15-generic/build/include

---

### Post by jiminycricket on 2007-05-01
> **Ziggy72 said:**
> Ubnewb2 .... 
What on earth do you mean?
No doubt Ubuntu gurus know but I certainly don't and neither will thousands of other people who are new to Ubuntu. How exactly do you install the source code for your kernel version? Indeed, how do you find what kernel version you have? ... and as for the symlink comment - what does that actually mean? Surely we're talking to people who are new to Ubuntu and very probably new to linux...:confused:


Kernel version is found out by typing 'uname -a'.  try ```
sudo aptitude install linux-headers-generic 
``` for the kernel headers.  'linux-source' is another package you may need, so substitute that in for linux-headers-generic if you still have problems.

[Symbolic Links]("http://en.wikipedia.org/wiki/Symbolic_link") are like Windows shortcuts (but better because they can 'mirror' directories), or an alias on a Mac OS X.

In fact, a lot of the command line stuff can be done on both Linux and OS X since they both use similar terminals.

---

### Post by ubnewbie2 on 2007-05-01
> **Ziggy72 said:**
> Ubnewb2 .... 
What on earth do you mean?
No doubt Ubuntu gurus know but I certainly don't and neither will thousands of other people who are new to Ubuntu. How exactly do you install the source code for your kernel version? Indeed, how do you find what kernel version you have? ... and as for the symlink comment - what does that actually mean? Surely we're talking to people who are new to Ubuntu and very probably new to linux...:confused:

I am really sorry.  I am new to unbuntu, but not to linux, and I forgot.

The kernel source is packaged and can be installed just like any or all of the software you'll need. As others have said, you probably only need the headers, I forgot they might be available separately. Last night when I was getting vmware working on a Mandriva machine I just grabbed the whole source, so that was in my mind when I replied (and I was sitting at work on a Windows machine at the time, so I could not check)

The symlink comment was because there are lots of different versions of the linux kernel, and you might have the source for more than one. There seems to be a convention that each version is stored in a subdirectory with the version name, for example, under feisty I see

```
/usr/src/linux-headers-2.6.20-15/include
```

and the generic name

```
usr/src/linux/include 
``` 

instead of being a real directory, may well be a symlink to whichever kernel is currently in use.  Although I don't see that in my default feisty install.  As I said, I am still new to ubuntu :( 

Looking at my mandriva disk, under /usr/src, I see

```
drwxr-xr-x  7 root root 4096 2006-11-03 20:19 .
drwxr-xr-x 15 root root 4096 2006-11-04 04:46 ..
lrwxrwxrwx  1 root root   17 2006-11-03 20:19 linux -> linux-2.6.17-5mdv
drwxr-xr-x  3 root root 4096 2006-06-27 20:28 linux-2.6.12-12mdk
drwxr-xr-x  3 root root 4096 2006-11-03 20:19 linux-2.6.12-22mdk
drwxr-xr-x 22 root root 4096 2006-11-03 20:18 linux-2.6.17-5mdv

```

as you can see 3 versions, and one symlink, linux, pointing to the latest.


Again apologies for not explaining the first time.

---

### Post by Ziggy72 on 2007-05-01
joejr...

A while ago I asked you a question: >  When you are asked
Quote:
What is the location of the directory of C header files that match your running kernel? [/usr/src/linux/include]
the [usr/src/linux/include] is what the install program is suggesting as the default location. When you hit Return in response, what message do you get? 
Will you please let me have an answer. Thanks.

---

### Post by ubnewbie2 on 2007-05-01
From memory, what he is probably seeing is just a repeat of the same question/prompt.  I think that's what it does when it can't find what it is looking for.

---

### Post by Ziggy72 on 2007-05-01
ubnewb2...

You say > From memory, what he is probably seeing is just a repeat of the same question/prompt. I think that's what it does when it can't find what it is looking for

Actually I don't think you are correct.  I think I remember that when installing VMWare tools, the prompt > What is the location of the directory of C header files that match your running kernel? [/usr/src/linux/include]  is exactly what would be expected if everything is proceeding normally. When installing and I see that prompt, I simply press "return" and then I get another question with a different default suggested location and so the whole install process continues with me hitting "enter" for each question until the install completes. That is why I asked the question "What happens after you press 'Enter' at that prompt?" 

It may simply be that when joejr asked the original question he never thought to press "return" to continue the installation normally. After all, that is a likely scenario if he needs to ask "Where do I find Synaptic Package Manager?" My question was merely trying to eliminate the simplest and most likely reason for 'failure' before moving to more esoteric solutions.

---

### Post by ubnewbie2 on 2007-05-01
I see, sorry, but I didn't realise it came back with different suggested locations each time you pressed enter.

---

### Post by joejr on 2007-05-02
I'm back at it.  I'll try everything people said and get back to you.

                      Joe

---

### Post by joejr on 2007-05-02
OK,

     It says...
*The path "usr/src/linux/include" is not an existing directory.*

Then it repeats the question.  

I've installed source headers and source code.  Every one suggested in this conversation.

                                  Joe

---

### Post by ubnewbie2 on 2007-05-02
> **joejr said:**
> OK,

     It says...
*The path "usr/src/linux/include" is not an existing directory.*

Then it repeats the question.  

I've installed source headers and source code.  Every one suggested in this conversation.

                                  Joe


So it does repeat the same question with the same default directory?  That's what I initially thought it did too, but someone else suggested it would try different defaults.

Anyway, if the usr/src/linux/include directory does not exist, you can point it to the equivalent directory where your headers were installed,

say

```
usr/src/linux-headers-2.6.20-15/include 
```

 or create a symlink for usr/src/linux/include that points to it (a better option)

something like

```
ln -sT usr/src/linux-headers-2.6.20-15/include usr/src/linux/include
```

then it should be happy

---

### Post by joejr on 2007-05-07
Same reply still.  It won't let me configure the files.  It just can't seem to find the files.  I gave up for a few days in frustration but willing to try and give it another go.  Can someone help me find the location of the files necessary to complete this job?

                  Joe

---

### Post by willowdan on 2007-05-09
Hi,

Actually I'm having the same problem, but not when using VMWare 6.0.0 where I smoothly installed vmware-tools. Why was that? Still experiencing it with with version 5.5.1.

Please, anyone help us.

Many thanks,

---

### Post by gng4life on 2007-05-11
Hi All!

I'm having the same problem.  I have:

WinXP Host PC
VMWare Workstation 5.5
Ubuntu 7.04 loaded in VMWare

I'm trying to install the VMWare Tools but I get to that same line:

What is the location of the directory of C header files that match your running 
kernel? [/usr/src/linux/include] 

I can't get past it.  I have put every directory that has been suggested but no luck.  I installed the source/header  information also.  

Please, if anyone has a solution or even a suggestion, it would be greatly appreciated.  I'll keep researching it also and will post any information I find here...Thanks!

---

### Post by Anicka on 2007-05-11
> **gng4life said:**
> Hi All!

I'm having the same problem.  I have:

WinXP Host PC
VMWare Workstation 5.5
Ubuntu 7.04 loaded in VMWare

I'm trying to install the VMWare Tools but I get to that same line:

What is the location of the directory of C header files that match your running 
kernel? [/usr/src/linux/include] 

I can't get past it.  I have put every directory that has been suggested but no luck.  I installed the source/header  information also.  

Please, if anyone has a solution or even a suggestion, it would be greatly appreciated.  I'll keep researching it also and will post any information I find here...Thanks!

When I installed ubuntu (dapper) in VMware 5.5.0 I had to manually put in the path, but after that it was ok. I updated to 5.5.3 and the path was found directly. After that I have updated ubuntu to edgy and further to feisty without having to touch vmware-tools too much, so maybe the 5.5.x just doesn't like feisty being freshly installed. I do have problems with the the network interface, but I can live with it. Hopefully the official version of 6.0 will be released soon and distributed by my employer for use at work.

---

### Post by joejr on 2007-06-04
I figured it out and it works great.  I had to not only install the c header files but configure them as well.  Then after that the vmware tools selects the correct files.  Perhaps I didn't state that right.  I typed this.

*sudo apt-get install linux-kernal-headers*
*sudo apt-get install build-essential* 
*sudo apt-get install linux-headers-`uname -r`*

After that I was able to run *vmware-config-tools.pl*


I got it off of the "How to Geek" website.  Thanks for all your help those of you who took the time to assist me.

---

