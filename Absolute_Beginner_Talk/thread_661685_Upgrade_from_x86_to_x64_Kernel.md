---
title: "Upgrade from x86 to x64 Kernel?"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by tigerplug on 2008-01-08
Hey everyone, 


I've searched the forum and Google but I have not been able to find an answer to my question.

I currently have Ubuntu Gutsy 7.10 x86 installed on my Dell Inspiron 1520.
I could not install x64 at the time as I was unable to boot from the x64 CD for some reason.

I've heard other people have had similar problems while booting from the x64 CD.

Is there anyway that I can do an in place upgrade and still preserve all of my files.
I do realize that Maybe its a little too much to ask but its worth a try.

All input appreciated ;) :)

---

### Post by mikeyphi on 2008-01-08
Here's my (small) input!
The 64bit version is generally good but there are reports of unexpected problems and not all 32bit programs are supported.
Unless you have a separate Home partition (i.e. in addition to the standard root and swap partitions) when you install the 64bit version all old info will be lost!!
So - if you decide to go ahead you should backup all your files first!

---

### Post by PmDematagoda on 2008-01-08
I do not think you can do an upgrade from a 32 bit kernel to a 64 bit kernel. You will have to do a clean install in order to use Ubuntu X64.

---

### Post by tigerplug on 2008-01-08
> **mikeyphi said:**
> Here's my (small) input!
The 64bit version is generally good but there are reports of unexpected problems and not all 32bit programs are supported.
Unless you have a separate Home partition (i.e. in addition to the standard root and swap partitions) when you install the 64bit version all old info will be lost!!
So - if you decide to go ahead you should backup all your files first!



Hmm, maybe I should wait for a while.
I mean I don't want to run into any avoidable issues.

---

### Post by tigerplug on 2008-01-08
> **PmDematagoda said:**
> I do not think you can do an upgrade from a 32 bit kernel to a 64 bit kernel. You will have to do a clean install in order to use Ubuntu X64.

Thanks for the input... just as I expected ;)
Aw well I think I will wait for a while.

---

### Post by PmDematagoda on 2008-01-08
> **tigerplug said:**
> Hmm, maybe I should wait for a while.
I mean I don't want to run into any avoidable issues.

I have used Ubuntu X64 and I have not faced a single problem that could not be easily solved, also it is especially easy to use Ubuntu 7.10 X64 as the process of installing Flash and Java(Two rather big problems) have been made very much simpler and reliable.

---

### Post by tigerplug on 2008-01-08
> **PmDematagoda said:**
> I have used Ubuntu X64 and I have not faced a single problem that could not be easily solved, also it is especially easy to use Ubuntu 7.10 X64 as the process of installing Flash and Java(Two rather big problems) have been made very much simpler and reliable.



Hmm, I think its definately something that I will consider over the next few days as I won't have the chance to install until at least Saturday anyway.

---

### Post by dcstar on 2008-01-08
> **tigerplug said:**
> 
..........
Is there anyway that I can do an in place upgrade and still preserve all of my files.
I do realize that Maybe its a little too much to ask but its worth a try.
.........

Create a separate /home partition in your system, and then any upgrade will not touch your personal files and desktop settings.

Do a forum search for detailed instructions on how to do this.

---

