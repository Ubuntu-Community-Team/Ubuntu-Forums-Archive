---
title: "[SOLVED] Trouble configuring AWN... (glib-2.0)"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by The Catalyst on 2007-09-08
This might be pretty obvious to some, but I can't seem to find any information on it.

I'm installing AWN (Avant WIndow Navigator) and it requires glib-2.0.  I tried to download it though apt-get but it doesn't exist on there - from what I've read it's already on Ubuntu, but it's called something different?  Is this correct?

If so - how do I redirect the ./configure to the other files?

If not - where can I find glib-2.0, it's not in the repositories as far as I know...

Thanks in advance.

---

### Post by coldstatue on 2007-09-09
Do you need to compile for a specific reason? The stacks feature is in the repos now. I have seen several people with compiling issues for the latest source. 

you must delete usr/local/bin/awn-manager before installing a new version, or your prefs manager won't work.

repos are (post back if you don't know how to add these.)

deb [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) feisty avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) feisty avant-window-navigator

then install avant-window-navigator-bzr

install awn-core-applets-bzr (I think it's called - you'll see it in synaptic after you add the sources and refresh.Just search awn. )

Try to (carefully) delete all traces of old versions first. avant-window-navigator folder and the file I mentioned above should be enough.

Hope this helps. I wrote this kind of assuming you have done some installs through various methods. If you need more specific instructions, post back, and I'll reply when I get home to my Feisty box in about 6 hours.

---

### Post by The Catalyst on 2007-09-09
> **coldstatue said:**
> Do you need to compile for a specific reason? The stacks feature is in the repos now.

Hrm, I'm pretty new to Linux so I just read the README and INSTALL files that come with everything, and they've always told me to compile the programs and exactly what to type and stuff, so I usually don't have much of a problem.

Are you saying I can just put the files somewhere in the filesystem and not have to go through this painstaking step of installing things? X_X

I'll try what you said in a little bit and post back, hopefully before you're able to check the post again.

EDIT: I did what you said, but I forgot to delete the old files... and it *still* worked properly!  Thanks a lot my AWN seems to be working fine now :)

---

### Post by coldstatue on 2007-09-09
Awesome!

Yes, for many, many programs, you can get a couple of lines to put in your software sources, and then either install from the command line or synaptic. One HUGE benefit of doing it this way, is that the programs automatically update. This alone will make you fall madly in love with Linux.

Take care.

---

### Post by coldstatue on 2007-09-09
I should mention, before you download files for an install, do a search on google for whatever version of Ubuntu, and the program you want.. i.e., Feisty Avant. You can find a lot of instructions that way. Also, search the forums as best you can. If you're really into customization, you might want to check out  screenlets, gdesklets, and conky. Frozen Bubble is a great game. Messing with this kind of stuff is good practice for getting used to Ubuntu..

---

### Post by The Catalyst on 2007-09-09
> **coldstatue said:**
> I should mention, before you download files for an install, do a search on google for whatever version of Ubuntu, and the program you want.. i.e., Feisty Avant. You can find a lot of instructions that way. Also, search the forums as best you can. If you're really into customization, you might want to check out  screenlets, gdesklets, and conky. Frozen Bubble is a great game. Messing with this kind of stuff is good practice for getting used to Ubuntu..

thanks for the tip guys - but now I've got another fun error.

i set up avant to run on start-up by some very conventional method I google'd up which I can't currently reproduce or remove very easily because it *broke my distro.*

I should mention I had just configured Confiz Fusion *and* AWG with some sweet stuff and restarted.

I'm not sure if there's some kind of conflict there or not, but now when I log in, my system resources are 100% used until I end the process compiz.real and everything speeds back up.

However, ending that process kills Avant, sometimes making my icons invisible, sometimes making the background invisible, and in the process, kills Confiz Fusion, making my window decorations invisible and making it difficult to navigate the OS general.

For the record I'm using a 2.4ghz, 1gb ram, 128mb graphics PC, so I doubt I should be having any kind of problem with speed.

Anyone had a similar issue?

---

### Post by coldstatue on 2007-09-09
I think you should copy and paste this into a new thread with a new title- i.e., compiz.real using 100% of resources. That's what is causing the other problems anyway. I have seen this problem before. I did a quick search but couldn't find the solution. Wish I could do more now, but I have to get my homework done. runnning compiz with a script so that it waits 10 - 15 seconds after login to load solved a bunch of problems for me, and I do that with awn, gdesklets, conky, and maybe even a few other things. If you want to know how to do that, I can post it later.

---

### Post by The Catalyst on 2007-09-09
> **coldstatue said:**
> I think you should copy and paste this into a new thread with a new title- i.e., compiz.real using 100% of resources. That's what is causing the other problems anyway. I have seen this problem before. I did a quick search but couldn't find the solution.

I uninstalled everything and switched repositories to Amaranth's - I followed his instructions and now everything works perfectly.

For anyone else having trouble with Compiz I would recommend to go here:

[http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty](http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty)

It was very helpful for me.

---

### Post by coldstatue on 2007-09-10
awesome blog. Don't forget to use the thread tools link, and mark the issue as solved. That way, people who are searching, and have the same issues, will know that you posted the solution.

Cheers.

---

