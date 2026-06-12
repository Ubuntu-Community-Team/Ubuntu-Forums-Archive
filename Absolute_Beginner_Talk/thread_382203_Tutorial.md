---
title: "Tutorial?"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by carusoswi on 2007-03-11
I downloaded/installed ibuntu.  I know I am a rank beginner, but, where does one go to get simple step by step instructions on how to use it?  I downloaded Ecasound because I am interested in seeing how that ap works?

I don't see any apparent way of making it run.  I know I am coming from XP that I knew fairly well, so I understand that the 'speak' is all different here, but, I am surprised there isn't some sort of instruction on how to do basic (very basic) things like get/install aps (looks like they install automatically) and then invoke them so that I can use them.

Ibuntu can't be this difficult. Am I being impatient?

Thanks for your help.

Caruso

---

### Post by cactaur on 2007-03-11
Well, it depends on what you want to do. If there's something in particular you want to do, I'd recommend [Ubuntu Guide]("http://ubuntuguide.org"). If what you want isn't in there, then check out the [Wiki]("http://wiki.ubuntu.com"). If what you want is in neither of them, ask here. As for Ecasound, did you install from the repositories?

---

### Post by kpkeerthi on 2007-03-11
Check out [http://help.ubuntu.com](http://help.ubuntu.com) and download the ubuntu desktop guide if you are a beginner. It gives you an excellent overview of linux and helps you find your way around in Ubuntu. And then jump onto the wikis and howtos.

---

### Post by carusoswi on 2007-03-11
I installed from repositories.  I've been perusing guides.  I've been at this since 9:00 this morning (first trying to load, and now trying to use ubuntu).

I am certain once someone can show me how to run a program that I have downloaded, it will be easy.

Right now, it is totally foreign.

One thread said to 'cd' to the file location.

I know how to do that in DOS.  How do I do it in linux?

I 'cd', but none of the destinations I type in take me anywhere but to an error message.

Thanks to you all for responding to a frustrated future user.

Caruso

---

### Post by laidback on 2007-03-11
Try this online book:-
[http://www.dsl.org/cookbook/cookbook_toc.html](http://www.dsl.org/cookbook/cookbook_toc.html)

cd means same as in Windows, Change directory
to see what directories you have try ls or ls -l. (I am assuming you're at the command line)
May I suggest that you don't start at the command line, use the package manager Synaptic, you'll find it in System>Adminstration>Synaptic package Manager, the password it asks for is you own.

But even better in my view would be to work your way through the preinstalled software, that'll give you more confidence. Then by all means move on.

---

### Post by carusoswi on 2007-03-11
Thanks for the reply.
It seems that every tip I receive, however, leads me to another dead-end.
I went to that package manager you mentioned.  Clicked on a package - then received a short description of what the package does.  No option obvious to me as to how to get it running.  That seems to be hard to find in this OS.

Can you help me?

Thanks.

Caruso

---

### Post by laidback on 2007-03-12
Some freshly installed software puts a new entry onto your menus, if it's good it will tell you where. Others install themselves but do not give you an icon or menu entry by default. You need to know  it's name first, launch name, for want of a better description. For example when I downloaded Acrobat reader I couldn't get it going, I couldn't even find it to start with. But, either the installation instructions or looking in /usr/bin told me that in fact it's called acroread, not a name I was familiar with. Now this presupposes that I knew to look in /usr/bin . Well this is where some knowledge of the Linux system comes in, it really helps if you have some knowledge of the file structure and the uses each directory is put to. 
In practice once you know it's called acroread your problems are over because you can press Alt F2 , type in its name (acroread) and off you go. After some success with that you can create your own icon for it, since /usr/bin is already searched when you type an instruction you only need to define your icon to run acoread, not some long directory name. Another way I found out what was going on was to look at existing icons, or use right click when on a menu item to create an icon on the desktop, then examine it to find the name etc. How did I know where to start, I read the guides and bought a book. It's unlikely that you'll learn Linux in a few days, A systematic approach worked best for me, I still know very little, but I'm learning and am gaining in confidence. Enough to feel that I can at least offer some advice to other Newbies.
Print off some of the guides mentioned above and have a good read away from the computer.

Good luck

---

### Post by stig on 2007-03-12
> **laidback said:**
> Well this is where some knowledge of the Linux system comes in, it really helps if you have some knowledge of the file structure and the uses each directory is put to. 

File system info:

[http://www.freeos.com/articles/3102/](http://www.freeos.com/articles/3102/)

---

