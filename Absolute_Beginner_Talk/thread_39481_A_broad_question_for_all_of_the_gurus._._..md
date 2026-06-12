---
title: "A broad question for all of the gurus. . ."
date: 2005-06-05
forum: Absolute Beginner Talk
---

### Post by K2712 on 2005-06-05
Greetings all,

I switched to linux about a month ago, just out of sheer curiousity, by buying Linux for Dummies w/ FC3.  Up until now, I have only used Windows platforms, and I never really cared about how the OS worked, as I only used computers for www, email, etc.

After tooling around with FC3, which led to reading online documentations, forums, and other various resources, I've become hooked.  I eventually switched to ubuntu, b/c of the great reviews, and I was interested in seeing another distro.  I am extremely happy with ubuntu, and the only problems I've had have been minor, and I've thoroughly enjoyed trying to figure out the solution.

To get to the point, I want to learn as much as possible about linux, and programming in general, with my ultimate goals being to be able to make a useful contribution to the open souce community, and potentially make a career out of programming, system administration, or something similar.  I'm just trying to figure out the most efficient way of making this happen.  The only books I've purchased thus far are Running Linux, 4th Ed., and the Linux pocket guide.  

So any advice, book suggestions, etc you guys could provide would be greatly appreciated, as I would one day like to be the guy answering the questions, rather than posting them.

Thanks in advance for any and all replies.

---

### Post by sas on 2005-06-05
[RUTE](http://www.icon.co.za/~psheer/book/) is a good starting place.

---

### Post by mark on 2005-06-05
[QUOTE=K2712]<snip>So any advice, book suggestions, etc you guys could provide would be greatly appreciated, as I would one day like to be the guy answering the questions, rather than posting them.[/QUOTE]
Wouldn't we all!  I've been fiddlin' with small computers since the late '70s and I still get blown away by how much I don't know...("Now why did it do *that*?")

You're in a good place here.  I've learned a lot since I started frequenting Ubuntu Forum - and I used to think I "knew" Linux.  So keep coming back, hang out, use the Search function (Search is your friend) and I think you'll pick up a lot of useful stuff.

As to books, *I'm* still looking for a good Debian-based book, myself.  For generic, command line-related stuff, I would recommend O'Reilly's *Linux in a Nutshell*.  It's a good desktop reference that should get you through the tough spots ("Now, what's the syntax to blank a CD-RW with *cdrecord*?").

Happy computing!

Mark

---

### Post by az on 2005-06-05
Just get your feet wet.  

Look around and try to figure out how to do all kinds of cools stuff.  If you want to get involved in programming, take a look at all the threads about what programming language is best to learn.  You can do anything with C, but Pythin is easy and a lot of stuff in Ubuntu is in python.

If you want to contribute documentation, the wiki will be used as a grounds for porting information from the forums to the doc team.

[http://test.wiki.ubuntu.com/forum](http://test.wiki.ubuntu.com/forum)

You can get involved in cutting and pasting stuff from the forums onto there.  This is to be a sort of reference for forum users as well as a source of content for the documentatin team to use.

There is plenty to do!

---

### Post by K2712 on 2005-06-05
Thanks for the tips. . .I'm definitely going to check out the wiki forum.

There is just such an incredible amount of information out there, I feel like I'm chasing my tail looking for a good starting place to begin really learning the ins and outs of Linux.  

I've read several of the programming posts, and I think I'm going to start with python, are there any gnome interfaces for python, that I could install in my Applications>Programmng file?

---

### Post by somuchfortheafter on 2005-06-05
the best way to learn linux is (puts on flame jacket) install gentoo, yes it is long, drawn out, tedious, time consuming, and more of a pain in your ass than anything else and you will probably never get it working as smoothly as ubuntu. yet by installing this distro you will gain a butload of knowledge of how linux systems operate, granted not all of that can be ported directy into distributions such as ubuntu, although the general concepts stay the same. (takes off jacket)

---

### Post by K2712 on 2005-06-05
Can I dual boot ubuntu and Gentoo?

---

### Post by somuchfortheafter on 2005-06-05
yes, you will just add another partition to your drive, then when installing gentoo ignore the instructions relating to installing grub or lilo, then add the kernel to the ubuntu install of grub name it like genkernel or somthing, if you can install gentoo the rest is easy lol.

---

### Post by Gtaylor on 2005-06-05
Either that or try [http://linuxfromscratch.org](http://linuxfromscratch.org) for an even more in-depth, nitty-gritty look into the insides of Linux. You won't learn as much from Gentoo by just following some instructions about setting up partitions, hitting a command, waiting 10-24 hours for a compile, and emerging some more.

LFS (Linux From Scratch) starts you with a clean slate. You effectively build your own distribution from a bootstrapped distribution (You could do it from within Ubuntu) and make your own. The time involved in this is substantially greater than Gentoo not only because of compiling, but more so the time you have to spend thinking what you're learning through and acting on it. Of course this is a bit more difficult but infinitely rewarding in the end.

---

### Post by DirtDawg on 2005-06-06
[QUOTE=K2712]
I've read several of the programming posts, and I think I'm going to start with python, are there any gnome interfaces for python, that I could install in my Applications>Programmng file?
[/QUOTE]

I'm not sure I'm responding to the right question. I assume you know you can open your terminal and simply type 'python' and there you go...
Otherwise, I would recommend an editor called 'scite'. Someone recommended it to me when I was P.O.'d at Gedit and you can press the F5 button to run scripts in a little side window. 
Otherwise, there's always IDLE. Though I use scite most, IDLE is pretty neat and probably the most newbie friendly Python application out there. It's all I used while learning Python until I switched to scite a couple months ago. (like you I decided one day out of the blue to try programming and stumbled onto Python.)
I believe both scite and IDLE are available in the repository.
If I read you wrong and I'm answering a question you never asked, well sorry about that.

---

### Post by rjstevens3 on 2005-06-06
yeah, i learned a lot from installing gentoo:) now that i have that badge of honor, i use ubuntu because its easy and fun. i suggest reading online souces like this forum for knowledge. i've found that most books talk about general cases that make some concepts hard to understand. in a forum where someone is rudely complaining about some feature its much easier to remember the answer and implamentation. also, i've noticed that asimilating data can be helpful. when fc3 came out, i learned a ton by getting my wireless card installed. at that time nobody else had my chipset working in fedora, so i just tried a lot of different methods posted for differents distros and chipsets until i got a working wifi setup! after that i posted my results and others though i actually knew something... i think most of us are willing to say that we're still learning linux and thats great because there are so many changes and evolutionary steps in the development of linux. 

good luck

---

### Post by K2712 on 2005-06-06
I'm going through the same process trying to get my wireless card installed in ubuntu, but I'm keeping a detailed log of what i've done(that actually accomplished something), which has proven to be a good learning experience.  I've finally figured out that with the inherent nature of linux, and all the different platforms out there that alot of the howto's and forum posts relate to, there isn't always going to be a simple solution.  But strangely, that's also what keeps me coming back for more.

---

