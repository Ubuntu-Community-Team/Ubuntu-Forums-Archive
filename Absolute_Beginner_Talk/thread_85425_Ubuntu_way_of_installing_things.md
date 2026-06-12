---
title: "Ubuntu way of installing things"
date: 2005-11-02
forum: Absolute Beginner Talk
---

### Post by gt24 on 2005-11-02
In Windows, if you find a program that you want, you grab the exe installer off of the internet, double click it, and you have an installed program in no time, no internet access necessarily required on the Windows box (as long as you have a way of getting that file to the box in question).

In Linux (Ubuntu), you fire up Synaptic (and have the internet on that box), search and mark what you want (and then dependencies are marked), and then you go ahead and watch the install.

The Linux way of doing things has one problem... you NEED the internet to do easy installs.

Why isn't there a website on the internet which allows a person to search through Ubuntu repositories from another machine (Windows perhaps?) for a program that is interesting, select that program, then be allowed to get necessary dependencies (I'll explain below), have the entire ball of wax gzipped or alike for download... and then get that gzip file to a computer for an easy install?

In other words, it would be nice if you could pretty easily get programs for a Linux box from another computer, so that you wouldn't have to get internet to the Linux box.  Also, this sould be an easy affair...

By necessary dependencies above, I mean that you will be suggested to download all dependencies for that program except for ones that you most likely have already (IE, they are on the Ubuntu install CD or alike... or are installed by default).

Either I am missing something (in other words, this idea is already implemented and completely doable) or I am hitting something on the head (this is an idea that needs to be implemented).  Which is it?  Also, does my idea make much sense?

---

### Post by matthew on 2005-11-02
Take a look at this site and see if you can accomplish what you want to do using it. Maybe it will be helpful.

[http://packages.ubuntu.com/]("http://packages.ubuntu.com/")

EDIT: I just played around with the site and noticed you can only download the source from the site, not the deb file. For its original purpose (finding where a package might be or if it exists) that site is very useful...it doesn't look like it will fulfill the original poster's desire.

EDIT #2: Wait. I was wrong. You can download the deb from a link on the page detailing the specific piece of software.

---

### Post by gt24 on 2005-11-02
[QUOTE=matthew]Take a look at this site and see if you can accomplish what you want to do using it. Maybe it will be helpful.

[http://packages.ubuntu.com/]("http://packages.ubuntu.com/")

EDIT: I just played around with the site and noticed you can only download the source from the site, not the deb file. For its original purpose (finding where a package might be or if it exists) that site is very useful...it doesn't look like it will fulfill the original poster's desire.

EDIT #2: Wait. I was wrong. You can download the deb from a link on the page detailing the specific piece of software.[/QUOTE]

Yeah, that could work well.  It would be nice if they marked what packages are instaleld by default with Ubuntu and Kubuntu so that anybody chasing down all the dependencies doesn't end up downloading a couple thousand things potentially.

---

### Post by aysiu on 2005-11-02
Things happen when someone does them.
If someone creates the kind of program you're describing, it exists.
When someone doesn't create it, it doesn't exist.

It's that simple.

Either some company is going to pay someone to do it, or the individual might do it just for fun, but *someone* has to do it. It doesn't just happen because you or I think it's a good idea.

I flat-out would not recommend Ubuntu to anyone who falls into all of the following categories:
1. Has no internet connection
2. Likes to install many programs
3. Doesn't like to figure out how to install programs in a difficult manner.

---

### Post by matthew on 2005-11-02
[quote=gt24]Yeah, that could work well. It would be nice if they marked what packages are instaleld by default with Ubuntu and Kubuntu so that anybody chasing down all the dependencies doesn't end up downloading a couple thousand things potentially.[/quote]
That would be nice, wouldn't it?

I had a thought that *might* be helpful. On a brand-spanking new default installation you could look in /var/cache/apt/archives and list the contents of that directory to see the debs for all the installed software. It seems like a lot of work and there must be an easier way, but maybe this will give you something to use as a starting point as you search further.

---

### Post by wylfing on 2005-11-02
1. Not every piece of software has dependencies. Those that don't can be downloaded and installed more-or-less just like Windows programs.

2. For stuff with dependencies, you should use apt-zip, which will help you fetch all the right stuff from a machine that has better connectivity. You'll have to install apt-zip first, but it's one of those programs for which all the dependencies are probably already installed on your computer, so you can download its deb all by itself.

---

### Post by SilentCacophony on 2005-11-02
Speaking of someone creating such a program, as mentioned, apt-zip is a close match to what you describe, but you may also wish to follow (or help with) the project described in these threads:

[http://www.ubuntuforums.org/showthread.php?t=78364](http://www.ubuntuforums.org/showthread.php?t=78364)

[http://www.ubuntuforums.org/showthread.php?t=84655](http://www.ubuntuforums.org/showthread.php?t=84655)

I spied them in the programming forum here recently, and it sounds similar to what you're looking for.

---

### Post by majikstreet on 2005-11-02
Today, most users have internet connections. So, there is not much demand for this.

-m

---

### Post by wylfing on 2005-11-02
True enough, but many people are still on modems, or there is a requirement to have a particular machine offline for security purposes. So to say "get a pipeline" isn't a solution for some people.

---

