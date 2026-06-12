---
title: "A Dumb Question?"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by Shibby73 on 2006-11-10
Ok,  well this is probably a stupid question.
But I do think it needs answered.

So if someone installs Dapper and likes other software in Kubuntu or Xubuntu or any other linux kernal based application... can't they just install and basically make their own hybrid version of the operating system interface on their computer.

I understand the idea of having pre-configured packages for installing the user GUI and certain apps, but not seeing why a person can't pick and choose the things they like in each and make their own work environment. 

I was recently reading a post someone wrote about using Edgy and wanting to use a piece of software that is in that edition with Dapper but saying they are limited to different software.  How is this possible?  Can't they just install the programs and dependencies under whatever version of Ubuntu or any other Linux Kernal OS that they please?

I appreciate clarification on this.

Thanks,

-Steve
:evil:

---

### Post by meng on 2006-11-10
You're basically right, in that users can pick and choose which software to install or uninstall once they have the default bundle on their computer. In terms of what can be installed FROM REPOSITORIES, the selection is slightly limited (although still very broad!) depending on which repositories are enabled. Also the repositories contain certain versions of the software, which are not necessarily the most recent, the most featured or even the most stable. If you need a newer OR older version, you may have to do some more tinkering.

If these problems arise, then the solution is to enable other repositories, or else really get your hands dirty with individual .deb files or even (gasp) compiling from source.

---

### Post by fhqwhgads on 2006-11-10
Sure, you can mix and match gnome, kde, and x apps within the same desktop, no problem.

But in the Linux world, progress marches on, and newer apps and builds may not be compatible with older versions of the OS. At least until the app is "backported", then it goes into a special repository, and becomes available through apt.

At least that's how I understand it, but I'm pretty new to this so it might be wrong.

---

### Post by Imsati on 2006-11-10
Well, I think I understand what you're asking, but not 100% sure.

Breezy is Breezy, Dapper is Dapper, Edgy is Edgy. each is a separate upgraded version from the previous. Think WinXp vs. Win98--both do the same things (poorly) with different looks and feels to them.

However, if you like some aspects of Ubuntu, and other aspects of K/Xubuntu, you can install each of them at the same time. In simplest terms, think of it as a dual/triple boot running off the same kernel. Everything will load normally, then at your Login screen, you'll have the option to change your Session type. When you click on it, you can choose to proceed with any desktop environment you have installed. They will, however, all be the same version kernel (Breezy OR Dapper OR Edgy, not a combo).

Did that make sense? Did I understand the question correctly?

---

### Post by bulldog on 2006-11-10
Well yes and no.

In some cases you can use software from another distribution if they don't need special dependency's.

But if Edgy uses a lib version 1.2.4.5 and the program you want to install needs 1.2.3.4 it can't install because of a dependency problem.
You should downgrade and if the lib is used by more programs you can't downgrade without removing all the apps which depends on this lib.

This is a very summary and it's much more complicated I guess but I think you know what I mean.

---

### Post by kinematic on 2006-11-10
the problem is the way linux distro's package apps.
each distro has their own naming convention and uses a different version of the gnu c compiler and glibc(glibc is the core library against wich every program is compiled).
if you want to install an app from let's say debian on edgy it has to be compiled against the same gnu c compiler(in some cases even the gnu c++ compiler)and glibc and it also has to have the same dependencies.
in order to satisfy these requirements each distro has their own repository and the only way to be sure a program that's not in the repository will work on ubuntu is to compile ot yourself from the source code and even then you could end up satisfying the dependencies manually before it builds properly.

---

### Post by Shibby73 on 2006-11-11
:twisted: 

Ahhh now I see a little better in this forest.

So, here is an idea:  Perhaps you can help me with it?

How can I make my machine run all of these distros at the same time?

I want to hop back and forth at will between them and see what things I like and don't like with little hassle.

I am noticing a neat feature of Ubuntu the "workspaces" but imagine this is not sufficient to use for say Workspace 2 being Kubuntu and Workspace 3 Being Xubuntu?

Any tips, I don't want to compile code and really don't have time to learn that just yet (eventually sure I would love to learn how to reprogram the whole matrix etc... but I got other stuff to do in real life ATM).

Power to you programmers!!!

Oh, another couple things I wanted to work on... 
1. Privoxy and Torr use for total anonymous browsing etc... (as needed)
2. Where do I get good free music or other streaming vids etc to enjoy on this box (on my win box when I felt like it I used limewire)

Thanks,

-Steve
:evil:

---

### Post by Shibby73 on 2006-11-11
Sorry I used the "dumb question" as the thread header, I was being stupid.

I am going to repost as new thread the topic:
"Multi-distro start-up?"

Maybe that der will be of guidance?

---

### Post by junglepeanut on 2006-11-11
I read a post on here where someone set it up where all they had to do was hit f7 ,f8 or f9 to switch between DE's. They did not run gdm, so it started like a server then he would start all three using either screen or something like it so that his family who all shared the computer could switch between them quickly whenever they walked up to the shared computer.

I can't remember the exact things but I will look for the post...

---

### Post by junglepeanut on 2006-11-11
WOW, turns out there is like a gazillion posts like this, not interested in searching through all of them, seems some people do a nested version but I dont think that is what you want, but it may be good enough.

It will probably pop up for me later somewhere and I will post it as I know I bookmarked it...it just that I think it is bookmarked on my mac at school.

---

### Post by dweez on 2006-11-16
I was under the impression (could easily be wrong) that some applications are specific to certain DE's.  Say Nautilus is Gnome specific.  It uses libs and packages from the Gnome environment and thus wouldn't run on KDE.  Junglepeanut's comments sounds like it would work, by opening 3 different sessions, each with a different DE, but seems convoluted and overkill.

---

