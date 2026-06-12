---
title: "Fresh install of Ubuntu......have a couple of questions."
date: 2005-12-13
forum: Absolute Beginner Talk
---

### Post by Il_Tuo_Nome on 2005-12-13
I've been using Ubuntu for several weeks now and have to say I love it. It's been so good installing apps, experimenting, learning knew things with CLI (although I still need to learn more). Now that I feel comfortable using apt-get, and seeing what does what, I went ahead and installed fresh, now that I know what I need and how to get it, config and so on. My main question is though, if I try to remove a package, for example, a game I'll never play, it tells me that package is needed for others to work. I know I can hide those and they won't cause problems, but for some reason knowing they're there bothers me. Especially knowing I'll never use them. So is that absolutely correct, they shouldn't be removed? Before I re-installed, I removed a few icons (the help 'lifebuoy' & add applications from the applications drop down) to see if I could find the correct paths and recreat them. We'll I couldn't, so how could I find the paths for something like that, if that were to happen?

Thanks for any help in advance :)

---

### Post by kairu0 on 2005-12-13
Usually there is a good reason behind those annoying dependencies. If you remove A, then B will not work. Why? Because A includes a library that B uses.

As it's not a good idea to force uninstalls (leaving yourself with broken dependencies) and, worse still, delete a package's files on your own from the filesystem, you might just have to put up with having a few extra things that you don't use.

Maybe you would like Debian Orphan. If you set it up to work with Synaptic, then you can delete straggling packages that aren't needed for anything else to work. Read "Scenario 2" of the first post of [http://ubuntuforums.org/showthread.php?t=24403](http://ubuntuforums.org/showthread.php?t=24403) if you're interested.

---

