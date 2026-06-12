---
title: "Repositories going down?"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by MonoMatt304 on 2008-04-13
I'm still pretty new to all this and there's a question that's been bugging me.

I like the way installation via repositories works and all that, but I've been wondering: do repositories ever go down?

This seems like a major downside to this method of software distribution.  With "Windows-like" installations, if a site goes down, you only lose access to that piece of software you want to install (and, chances are, you can find another place to get it, too), versus all software if a repository goes down.  It seems to me that, if a repository goes down, you'd be out of luck until it got back up and running, unless you found the packages for download on a site, or decided to compile the application yourself.

Am I right about this, or are repositories maintained by a variety of sources so that the likelihood of one going down completely is slim?

---

### Post by Saint Angeles on 2008-04-13
well i assume the repos are NOT using windows servers so they prolly won't ever go down.

i've done about 4 apt-get updates a day for the last 6 months with no problems whatsoever.

---

### Post by stuart brogan on 2008-04-13
Hi,

There are so many good books that mention this subject that it is mind boggling. I could start naming them and explaining what I know about repositories (which isn't really a lot) and it would bore you to death.

It is very stable and if the repository went down you can pick from a huge list of others making the system super redundant all over the earth.

If you open Synaptic package manager (system/synaptic...) go to the setting tab and select repositories. On the Ubuntu software tab you will see about halfway down the page download from, opening that select other and then you can see that there are a lot of repositories.

You really started with a good distro to, as you probably know that ubuntu is built off of debian originally, and they still are very much related. Debian has contributed many solid underlying features to the open source community over the years. Ubuntu has improved it and brought deb into the future.

Why I mention this is because all these package managers set on top of dpkg (google is your friend) you can get packages via many ways, I personally use apt if I know what I want, and synaptics to browse. Although you can also use aptitude if you are running on a thin system or just like the cli.

I hope this answered your question and when you get a basic understanding of apt look [here]("http://kitenet.net/~joey/pkg-comp/") for a good comparison of package managers

---

