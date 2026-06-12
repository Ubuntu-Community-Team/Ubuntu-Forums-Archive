---
title: "How stable is using universe, multiverse and so on?"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by lordsteff on 2006-08-06
Hello

I activated the extra repositories like multiverse and the plf resository as described here: [http://linux.wordpress.com/2006/06/25/tips-adding-extra-repositories-on-ubuntu/](http://linux.wordpress.com/2006/06/25/tips-adding-extra-repositories-on-ubuntu/)

And I installed easyubuntu to get the additional codecs, browser plugins etc.

So now my question: If I keep using universe, multiverse and the plf repository, how stable will my system be? Will I get a broken system every week, or get in apt hell (like rpm hell)?. I think many of you use the extra repositories, so I would appreciate it if you tell me your experiences.

BTW: It would also be nice to be able to upgrade to the next ubuntu versions without reinstalling it. Has someone done this successfully even when using multiverse etc?

---

### Post by MaximB on 2006-08-06
it is completly safe to use the extra repositories
and you MUST use it to get the codecs - if you want to be able to play mp3's and other media
 
but don't mess with the .rpm files
you can convert it to .deb with alien but it's not always work well
get the .deb packages instead

---

### Post by Kurt` on 2006-08-06
For general Ubuntu questions, check out [www.ubuntuguide.org](www.ubuntuguide.org) . It has guides on how to do most basic things.

To upgrade your install to the current version, run the following command:

# sudo apt-get dist-upgrade

---

### Post by 23meg on 2006-08-06
If you just use multimedia codecs and the like it's unlikely that there will be a stability issue.

As a sidenote, the term "extra repositories" may be a bit too rough here; PLF is a third party repository whereas Universe and Multiverse are official repositories, even though support isn't guaranteed for them.

---

### Post by lordsteff on 2006-08-06
Hello, thanks for the replies. Yeah I know how to upgrade the system with dist-upgrade, and I don't plan to use rpms. 

I'm just not sure whether I will get into trouble when using the extra repositories. I'm the kind of user who always wants to be up to date with the system, so I update regularly. And from time to time I try new apps. But of course I don't want to break my system.

---

### Post by steve.horsley on 2006-08-06
Well, I have never had any problem with the extra repositories. I'd say you can trust them.

---

