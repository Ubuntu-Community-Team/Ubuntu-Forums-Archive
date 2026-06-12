---
title: "Is it at a standstill?"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by sayakb on 2008-02-26
Hello all
I installed Gutsy on my laptop in early December. Since then, I just learned how to customize my OS, create my icons with the Gimp, write elementary scripts for Nautilus, manage to find and edit certain portion of system files... (I know, thats really not much, infact it's nothing, but it's just been 3 months, right?)
 Now at this stage, I can solve minor problems of mine on my own. But I really want to learn more. How do I learn Ubuntu the way I know quite much about Windows? (I agree I am on Windows since 15 years but this time, I really want to know everything Ubuntu has.)

Elucidating: Please tell me where can I start exploring the OS, and some precautions I should take while doing so.

---

### Post by Joeb454 on 2008-02-26
Precautions would be backing everything up (especially /home)

Other than that, just expirement...you will however most likely break it, but it's the only way to learn, if you break it, try and fix it.

If you can't fix it - reinstall it (then restore /home)

This is how I learnt :)

---

### Post by sayakb on 2008-02-26
> **Joeb454 said:**
> Precautions would be backing everything up (especially /home)

Other than that, just expirement...you will however most likely break it, but it's the only way to learn, if you break it, try and fix it.

If you can't fix it - reinstall it (then restore /home)

This is how I learnt :)

Thanks for the quick reply :D
I actually have no data on my internal HDD, so /home doesn't have any relevant data ;)
Btw, any specific area where to start. I am thinking of downloading the sources of apps and studying them. Is that a bad idea?

---

### Post by flick on 2008-02-26
Not a bad idea at all, if you are a programmer/want to learn how a given program is put together. 

Don't even have to be root, just :

1. Make sure there's a line like this in your /etc/apt/sources.list :
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) <ubuntu_version> main restricted universe multiverse

with of course gutsy or feisty or whatever you're using where the <ubuntu_version> is.

2. change to a directory where you feel safe and comfortable messing with source code

3. then apt-get update

4. then apt-get source NAMEOFPACKAGEYOUFEELLIKEPOKINGAROUNDIN

5. then you'll have a source .deb in that directory you're in, ready for you to extract and start looking at all the source code goodness inside.

---

### Post by Joeb454 on 2008-02-26
It can't hurt, though I can't promise you'll understand it :p

Learning to compile programs from source can't hurt either though ;) Try helping out new users too, you'll learn a lot through that as well, I know I have (though it has resulted in a lot of unwanted apps being install on my PC :p)

---

### Post by mali2297 on 2008-02-26
Get involved in the problems that the new users post here, even though you might not know the solution directly.  You can still try to replicate the problem on your own system,  do the searches for them etc.

---

### Post by sayakb on 2008-02-26
> **mali2297 said:**
> Get involved in the problems that the new users post here, even though you might not know the solution directly.  You can still try to replicate the problem on your own system,  do the searches for them etc.
I am trying to stay active here. Though I cannot stay online for more than 6 hrs a day due to network access limitations. :(


> **Joeb454 said:**
> It can't hurt, though I can't promise you'll understand it :p

Learning to compile programs from source can't hurt either though ;) Try helping out new users too, you'll learn a lot through that as well, I know I have (though it has resulted in a lot of unwanted apps being install on my PC :p)
Actually, we just get 50MB daily download limit at our college and that too at a pathetic bandwidth. So you can understand that I cannot afford to lose all the packages I have downloaded (and after the foolishness I have done after cleaning up synaptic packages to save space, though I was never running outta space :( -- yes, my /var/cache/apt/archives folder is empty)

---

### Post by Pelham123 on 2008-02-26
Drop over to the Linux documentation project...

[http://tldp.org/](http://tldp.org/)

Have got some great guides on the filesystem, howto's, guides etc - all of which are downloadable. 

Ubergeekheaven 8)

---

### Post by sayakb on 2008-02-27
> **Pelham123 said:**
> Drop over to the Linux documentation project...

[http://tldp.org/](http://tldp.org/)

Have got some great guides on the filesystem, howto's, guides etc - all of which are downloadable. 

Ubergeekheaven 8)

Thnks for the link :)
I would try it out..

---

### Post by Martje_001 on 2008-02-27
If you really want to know how a Linux system works, install Gentoo.

---

