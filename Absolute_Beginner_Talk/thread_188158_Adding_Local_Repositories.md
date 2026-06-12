---
title: "Adding Local Repositories?"
date: 2006-06-03
forum: Absolute Beginner Talk
---

### Post by JNowka on 2006-06-03
How would I add a folder on my hard drive that has over 200 .debs in it as a repository in Synaptic?  I downloaded them all and want to keep them seperate from the rest.

---

### Post by aysiu on 2006-06-03
[https://wiki.ubuntu.com/AptMoveHowto](https://wiki.ubuntu.com/AptMoveHowto)

---

### Post by JNowka on 2006-06-03
I want to keep them on my hard drive.  Not burn them on a cd.  I just want to know how to make a apt link in Synaptic so that it reads my /data/LibDebs folder as a repository.

---

### Post by aysiu on 2006-06-03
Skip Step 4, maybe?

---

### Post by CompShrink on 2006-06-03
Difficult but more informative option: Follow the apt-move guide. But, don't burn the CD, because you can mount the *.iso file as if it was a hard drive / CD, and then use it without burning it.

But even easier than that, you can add it in your sources.list like this:

deb file:///PATH/TO/DEBS breezy main

*But *you need to make the debs have the correct directory structure, and correct indexing files first.

Since you don't need all the features of apt-move, you can just use the **apt-ftparchive** command. It should be installed by default, but if not, you can install **apt-utils** to get it.

I'd suggest reading the manual to understand it, but the quick and easy way for now is:

make a folder whereever you keep the debs, call it **dist** , then make a folder inside that one, and call it **breezy** *or whatever version you are using*, make a folder inside **breezy**(or hoary or dapper...) and call it **main**. Put all your debs in there. You can make folders in **main** to keep it organized if you want, or just put them all jumbled up together.

Open the files I attached, change /PATH/TO/DEBS to the path to the folder containing dists, and the /PATH/TO/CONFs to the path to the folder containing the conf files that are attached. This path does _not_ include dists in it!

Make the example-update-archive.sh executable (in nautilus, right click, go to properties, it's under the permissions tab), and then run it in a terminal.

If you need help, feel please post here or PM me. And let me know if you got it working.

**Note, if not using breezy, change both places in the example-apt-custom-release.conf file that say **breezy** to the correct **hoary** or **dapper** etc. and make a folder of the same name as described above.

---

### Post by az on 2006-06-03
[QUOTE=CompShrink]Difficult but more informative option: Follow the apt-move guide. But, don't burn the CD, because you can mount the *.iso file as if it was a hard drive / CD, and then use it without burning it.

But even easier than that, you can add it in your sources.list like this:

deb file:///PATH/TO/DEBS breezy main

*But *you need to make the debs have the correct directory structure, and correct indexing files first.
[/QUOTE]

You don't need to have a directory structure for such an archive.  If they are all in the same directory, just run

dpkg-scanpackages . /dev/null > Packages
and just use the path to that directory.

---

### Post by jeroen2 on 2006-06-11
Thanks for the info so far in this thread, it's been mighty usefull! 

I still run into some problems, after doing the following: 

- Following the apt-move howto to create a local repo. 
- Copying the contents of mirrors/debian to /home/username/local 
- Adding this line to sources.list: 
deb file:///home/username/local breezy main restricted non-free contrib 

Note: I'm running Kubuntu breezy!!! 

The problem: 
The repo seems to mount fine in adept. But I'm missing some packages. Notably those in pool/contrib/. I also don't understand why there is a contrib folder under pool, but not under dists/breezy. I realized putting contrib in the sources.list entry was probably useless, but I tried it anyway: no luck. Even more strange: the packages in pool/non-free don't show up in adept, even though a dists/breezy/non-free exists.... I know I can install these packages by hand. No problem there. I'd just like to have it all at my command from adept.... 

Thanks for your time
 Jeroen

---

