---
title: "from the desk of a n00b (app install?)"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by jadedcritic on 2006-11-10
Hello.  Short time reader, first time poster.  Suffice it to say I don't see allot of benefit in wasting time lurking.  Won't go into backstory too much;  It's enough to say that a half dozen reasons or so finally provided sufficient incentive for me to try to get involved in that linux thang.  Penguins with greater skillz then my own pointed me towards ubuntu, and here I am

Ultimately, I'd like to get to a level where everything I do with my PC's - I do in linux.  (Except my video games.  Suffice it to say I'll never be able to give those up.) Unfortunately, to get there, certain goals must be accomplished. I've gotten past some of the multimedia codec issues; and found various linux substitutes for the day to day kinds of things I do, but I seem to be encountering similar iterations of the same kinds of problems.

I've been trying to get my head around the standard procedure for compiling one's chosen applications, and I seem to keep hitting similar issues.   As I understand it 1) Find the source file,  2) Download and Unzip   3) Untar   4) run config - which then creates a makefile 5) gcc then uses the makefile to compile and install the app.

4/5 Is where I get lost.  I've probably tried on about a half dozen different apps so far, I get different results, but only one attempt has ever actually successfully generated a makefile.   Also,  I notice there are 3 makefiles in most of the sourcefiles I download,  what's the difference between the 3?  makefile, makefile.am, and makefile.in?

By way of a more concrete example, 

When I try to install WxWidgets (which, from what I can gather, is a GUI prerequisite of what I want, audacity), I get an error that says, "this usually means GTK+ is incorrectly installed"

What's GTK?  Did I grab the wrong installable?

When I try to run ./configure on the Xine library - for exmaple, it shoots a whole lot of information at me and appears to be working; but when I check the contents all I have is the makefile.am and makefile.in.  Not a regular makefile.

Why do I see so many guide/posts that tell me to type ./configure instead of just configure?   I was under the impression the only difference between the two is absolute versus relative paths.  Aren't they really just the same thing?

And I do need use sudo for every step in the process?  Or just the make install?

One last question.  How does one even begin to sort/filter the available apps out there?  I've found softpedia for example.  Can anyone recommend links to the most popular apps?

Before someone points out that it isn't entirely necessary to compile everything yourself - I'm aware that there are simpler approaches, I'm just trying to get my head around the mechanics that make those approaches work.  To metaphor, I'm not content starting the car, I want to peek under the hood. ;) 

Apologies for making this a long post;  Pretty much have no responsibilities at work today, it's left me with allot of forum time :mrgreen:

---

### Post by meng on 2006-11-10
Welcome. The easiest way to install software/applications is from repositories. This means you don't have to find the individual packages and dependencies for a given application. audacity should be in the repositories. Look here for more information:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by jadedcritic on 2006-11-10
Easiest isn't really the goal.  If I wanted easy, I'd use Windows.   Though thank you for the links,  don't think I didn't bookmark them

---

### Post by CatKiller on 2006-11-10
First of all, you could have a look at [this page]("http://monkeyblog.org/ubuntu/installing/#source"). You might find it a bit basic, or you might not.

If you use the methods higher up on that page, all of your dependencies will be sorted out for you. Which is better than having to compile GTK to compile WxWidgets to (hopefully) compile Audacity. Nightmare. Just **sudo aptitude install audacity** is much much simpler. This won't compile it on the fly, which is what you appear to be asking about, but it **is** easier to manage.

You should **always** use ./configure, as I understand it. It's not so much a difference between absolute and relative paths as **this** file rather than **no** file. To elaborate, when you issue a command, the shell will look for an executable of that name somewhere in your $PATH. The place you've just untarred some random source is unlikely to be in your path. So it won't find it, and won't run it. Or it might find a different executable that **is** in your path, and run that instead. Putting the **./** in front means > this file, that's called "**configure**", in this directory here, the one I'm in, really which is fairly unambiguous.

You should use **sudo** for every command that requires you to change a file outside of your Home folder. So configure and make are OK, since that's just fiddling with the source package you can already write to. But the make install will spread that program throughout your filesystem tree, which requires root priveleges. You might want to consider using **sudo checkinstall** instead, which will make and install a DEB package for you, making it **much** easier to upgrade or uninstall the program you just installed.

Now some more pages you might find helpful:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

EDIT:
> Easiest isn't really the goal. If I wanted easy, I'd use Windows. Though thank you for the links, don't think I didn't bookmark them

You could cheat somewhat, and look at what the dependencies are for the package of the software that you want to install, then hunt down and install all the dependencies from source, then install the software you want. Seems like a bit of unnecessary hassle to me, though. If you don't want to use the package manager - that is IMO the bestest thing about Ubuntu - perhaps a different distro would be more to your tastes. Isn't Gentoo for masochists? :) Or you could use the tools you've got in Ubuntu to get the hang of installing and maintaining a Linux system, and then migrate to something harder once you're up to it.

---

### Post by sethmahoney on 2006-11-10
> **jadedcritic said:**
> One last question.  How does one even begin to sort/filter the available apps out there?  I've found softpedia for example.  Can anyone recommend links to the most popular apps?

This is one of the reasons using synaptic is better than going from source files - all the software available in the repositories is categorized, and can be searched by title and description.  If you're using GNOME, gnomefiles.org can also be useful.  If you're using KDE, I think the site you probably want is kde-apps.org but I could be wrong on that one.

> **jadedcritic said:**
> Before someone points out that it isn't entirely necessary to compile everything yourself - I'm aware that there are simpler approaches, I'm just trying to get my head around the mechanics that make those approaches work.  To metaphor, I'm not content starting the car, I want to peek under the hood. ;) 

Its not just that its not necessary.  Its not recommended.  The apps in the respositories have security and bug fixes, and are meant to work with the other libraries and programs in the distribution.  Moreover, installing from source can (not that it necessarily will, but it can) cause problems when upgrading your distribution.  So, don't install from source unless you have to (with Ubuntu - there are other distributions where its the way to go).

---

### Post by MWAAAHAAA on 2006-11-10
> Easiest isn't really the goal. If I wanted easy, I'd use Windows.

If you want to make it hard on yourself, fine go ahead. I can tell you from my 7+ years of linux experience that there are by far better ways to spend your time, getting to know the system, than compiling everything from source, which is a (almost completely and utterly inconstructive) nightmare anyway. Use the package management system (adept, synaptic, dselect, apt-get, or even dpkg).
I would like to add here, that by searching the web for applications and downloading them is actually the Windows-way of getting your system up and running. In short, time consuming and inefficient, just like windows. To put it in the words we all know so well: "You must unlearn what you have learned."

So, what exactly do you want to learn. What are your goals?

> Ultimately, I'd like to get to a level where everything I do with my PC's - I do in linux. (Except my video games. Suffice it to say I'll never be able to give those up.)

Same here. By now I use linux exclusively for everything but gaming. And as such, I would like to stress again, I learned a lot more about linux, getting everyday jobs done in linux, than by struggling with the ./configure - make process. I would therefore recommend you just try to do the things you want to do.

---

### Post by jadedcritic on 2006-11-10
wups! double posted!  trying to figure out how to delete

---

### Post by jadedcritic on 2006-11-10
> **MWAAAHAAA said:**
> 
Same here. By now I use linux exclusively for everything but gaming. And as such, I would like to stress again, I learned a lot more about linux, getting everyday jobs done in linux, than by struggling with the ./configure - make process. I would therefore recommend you just try to do the things you want to do.

Touche' linux community! I suppose I could always move on the video flickers and save the rest for later. OK, far be it for me to fly in the face of experience.  @#$@# the whole concept centers around community experience.  OK,  I'll get over it for now then. ./configure+make has not seen the last of me! :mrgreen: (glowers at gcc)

Now that I think about it, I should probably figure out the wireless first.  Probably is more important.   DOH!

---

