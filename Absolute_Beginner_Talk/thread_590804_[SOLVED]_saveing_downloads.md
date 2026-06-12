---
title: "[SOLVED] saveing downloads"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by martin Pen on 2007-10-25
Hi I have limited downloads on my braudband so even though Ubuntu downloads are not large I soon over run my limit. Ive already had to reinstall Ubuntu once losing every thing. 

When I use windows I down load a setup file for any soft ware I use so I always have it if something goes wrong Ubuntu seems to use many different files rather then just one.

I like the software available on Autmatix but it downloads and installs in one operation.

Can I download say a zip file for each new program from Automatix and is it it hard to install from my hard drive once downloaded ie do i need to use a terminal?

Can I back up programs already downloaded and installed and use them say on a different computer or when they install do they become machine specific? 

Hope someone can help?

Martin.

New user

---

### Post by forestpixie on 2007-10-25
have a look at [aptoncd]("http://aptoncd.sourceforge.net/") - it seems like just what you're after

---

### Post by PointyWombat on 2007-10-25
I'm not a fan of automatix at all so I can't speak specifically to that, but you can try to capture the contents of /var/cache/apt/archive to a tar file and then reload that onto a newly created box. This may mitigate having to download these packages again. I haven't tried it but it may be worth testing in your case.

BTW, what is your broadband limit? Seems awful small if you can't simply install a few hundred megs of stuff now and then.

---

### Post by forestpixie on 2007-10-25
that's what aptoncd does - don't think it compresses though, then you can install from the cd - acts like a movable apt/archive, I believe it deals with dependencies as well.

---

### Post by martin Pen on 2007-10-25
thanks for the help guys I'll try this package out.
BTW whats the difference between a deb and a gz ?

My limit is 12 gig but its shared by 6 avid internet users we have a good bundle deal with AAPT but the cost of next jump up cant really be justified.:(

---

### Post by martin Pen on 2007-10-25
yep worked a treat :popcorn:

I wonder if I can add to it seeing as its an image file.

still its all good thanks again.

---

