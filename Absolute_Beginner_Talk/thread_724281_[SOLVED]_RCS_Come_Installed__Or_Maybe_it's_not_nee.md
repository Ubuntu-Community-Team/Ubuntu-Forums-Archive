---
title: "[SOLVED] RCS Come Installed?  Or Maybe it's not needed?"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by Syndacate on 2008-03-14
Hey,

I'm a software engineering student at RIT.

In CS2 (java programming) we have to start utilizing this RCS ********.

Now I'm gonna be completely honest, I think this is a joke and a half, but we need to use it from now on, so BLAH.  Let's just say when I realease revisions they're going to be HUGE, as the check in/out procedure is too damn tedious.

Alright, enough of my bitching.

The way things are set up is we each have usernames on a network - they're solaris machines.

What I did all through CS1 was just SFTP 'em to my computer, finish them, FTP them back - and upload it (it has to be uploaded from their end of the network).  Now I gotta deal with this RCS ********, so I'm a little confused on what to do?

It seems the way it works is **.../working directory/RCS/file.java,v** contains the revision information and past revisions (versions).

So how would I go about working on this from my dorm computer?  I'm not going to walk 20 minutes to the CS building every time I want to work on a Java project - that just isn't happening, so what do I do, I can't SFTP the file.java,v file and just update it locally because it has the username that did the revision (and my username for my dorm computer is different than my one for the RIT network).

Any ideas on what the hell I can do?

Right now my current plan of attack is to just download it - take note of all the changes, then when I FTP it back at the end, just submit one HUGE revision.  Though obviously this might not take kindly to the way we're "supposed" to use it.

Blah - Help?

---

### Post by Syndacate on 2008-03-15
*bump


Anybody

---

### Post by mssever on 2008-03-15
Which RCS are you using? Or is RCS the actual name? Perhaps you should ask your instructor for details.

Most projects use revision control of some sort (Subversion (svn) is the one I'm familiar with). You need to get used to it, because you'll be dealing with it from now on.

---

### Post by supirman on 2008-03-16
RCS certainly does suck... 

There are a few ways:

The easiest would probably be to use sshfs.  sshfs will let you mount a directory (i.e. your home directory) on the solaris machines locally.  Then you can use rcs 'locally'.


Otherwise, you'd likely have to:  ssh into the solaris machine and co each file for your project.  sftp each of them to your local machine if that's where you want to work on them, make changes, sftp them back, then ci each file.

Or, if possible, ssh into the solaris machines and use X forwarding (i have no idea of that's possible, I know nothing about solaris) and then you can just ssh into the solaris machines and treat it as if it's local. 

I hate RCS.

---

### Post by Syndacate on 2008-03-21
> **supirman said:**
> RCS certainly does suck... 

There are a few ways:

The easiest would probably be to use sshfs.  sshfs will let you mount a directory (i.e. your home directory) on the solaris machines locally.  Then you can use rcs 'locally'.


Otherwise, you'd likely have to:  ssh into the solaris machine and co each file for your project.  sftp each of them to your local machine if that's where you want to work on them, make changes, sftp them back, then ci each file.

Or, if possible, ssh into the solaris machines and use X forwarding (i have no idea of that's possible, I know nothing about solaris) and then you can just ssh into the solaris machines and treat it as if it's local. 

I hate RCS.

Thanks, I'll give sshfs a try.  Yeah, it's a tedious (stupid) process.

[quote=mssever]Which RCS are you using? Or is RCS the actual name? Perhaps you should ask your instructor for details.

Most projects use revision control of some sort (Subversion (svn) is the one I'm familiar with). You need to get used to it, because you'll be dealing with it from now on.[/quote]

I don't know anything about it.  My instructor wouldn't tell me jack on it if I asked him - he's against me not using the crappy solaris emacs bull w/ "javac" to make java programs.

I know I'll be dealing with it - but I hate it, and since I hate it, I'm going to deal with it in the easiest way possible, regardless of the outcome.  It's a stupid system - I'm sorry, but if you fu88 up a program so badly that you basically have to hit "exit" without saving first on purpose, then just quit while you're ahead.

---

### Post by Syndacate on 2008-03-25
I think I've found the answer.

The dilemma is simple, I like working on things in eclipse, that's a major problem when you gotta constantly check in and then check out the file again (the sizes will be different and eclipse will throw a **** fit).

I came up with 2 basic ideas.

One:  You can pull the java programs out of the workspace in eclipse, upload them, and DELETE THE PROJECT IN ECLIPSE.  You then check them in, check them out, dl them, and start a new project, and import them.

Two (Which is what I'm going to do):
Open up as many terminal tabs (since I can do tabbed terminals) as *.java programs I'm working on and then use X11 forwarding when I SSH in.  I can then open eclipse locally, and I can forward Gedit via X11 from the solaris machines.  Then when I'm ready to update, I hit <ctrl>+A, <ctrl>+C, <ctrl>+V, <ctrl>+S, <alt>+F4 - and it's saved, on their server, nothing was FTP'ed, and it's still in eclipse.  I can then check it in check it out.

So basically I'm creating it all local side in eclipse, then updating it online.

Things accomplished:
-  RCS system used the way they want you to use it
-  I still get to use eclipse instead of emacs or whatever
-  I don't have to deal with tedious FTP'ing
-  I don't have to use the shitty solaris machines in the lab

Things not figured out:
-  Nothing

I win.

---

### Post by Syndacate on 2008-03-30
I found out how, btw, in case anybody else uses it.

You can just create a folder in your eclipse workspace.

Then open console and type **sudo apt-get install rcs**.

You'll then be able to just leave a terminal window in as you code, and when you want to save a revision, just make sure it's saved in eclipse (so it updates the file), then go to the terminal and type **ci -l <filename>.java** - it's imperative that you use the lock when checking it in so it doesn't disappear, if you don't use the lock it'll move it (oppose to copying it) and eclipse will throw an "*out of sync with file system error*" and you'll have to delete your project and re-import it.

Then when you click on eclipse it'll be like "*This file has been updated, do you wanna re-load newest version?*" - and just hit "yes" and it'll be fine.

And yes, I know about the eclipse backup - but the school wanted us to use RCS (and emacs).

---

