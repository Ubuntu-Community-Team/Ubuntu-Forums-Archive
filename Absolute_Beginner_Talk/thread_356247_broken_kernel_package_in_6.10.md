---
title: "broken kernel package in 6.10?"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by will m. on 2007-02-08
Hello Everyone,

This morning I discovered my first broken package - the linux kernel itself.  I discovered something was wrong when the update icon came up with an error message.  I clicked on it and went to Synaptic Package Manager where I learned that I had a broken package.  Using the 'broken' filter I search for it to discover that the linux kernel I was using 2.6.17.11 was broken. 

I wasn't sure about updating a broken kernel since, as I understand it, everything else depends upon it.  However, after some consideration of the fact that I have backed up everything elsewhere and have only been using Ubuntu for a few weeks I decided to proceed with a reinstallation of the kernel from Synaptic.

It didn't work and gave me a message similar to what I get when I tried 

```
sudo apt-get update
```

Everything seems to chug along nicely until the last few lines which I pasted below

```
Failed to fetch http://my.favorite.cran.mirror/bin/linux/ubuntu/edgy/Release.gpg  Could not resolve 'my.favorite.cran.mirror'
Failed to fetch http://my.favorite.cran.mirror/bin/linux/ubuntu/edgy/en_US.bz2  Could not resolve 'my.favorite.cran.mirror'
Failed to fetch http://my.favorite.cran.mirror/bin/linux/ubuntu/edgy/Packages.gz  Could not resolve 'my.favorite.cran.mirror'
Failed to fetch http://theli.free.fr/packages/dists/edgy/listen/binary-i386/Packages.gz  404 Not Found
W: GPG error: http://medibuntu.sos-sts.com edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

So my question is is my linux kernel really broken and how can I tell?  If so, what should I do to resolve it?  I'm curious about how this happened in the first place since I would never mess with the kernel at all.  

Also, is this my only problem?  It seems that I have some mirrors that aren't coming up.  Do I need to do anything to resolve that?

One final note, I went to a Linux class yesterday as a means to learn more about the OS and may have made the worst mistake of all.  A TA was talking to me about how to install software (in this case a stats program called LISREL) and I let him take a look at my machine using the terminal.  I can't be sure if the issues I now enjoy originated there but I think I have learned - never let anyone else administrate your machine.

If any souls out there can advise about the kernel and update issues I raise I would appreciate the help.

Will M.

---

### Post by will m. on 2007-02-08
Kernel update issue apparently resolved!

```
sudo apt-get -f install
```

I was unaware of the command above (even though I tried apt-get update) and it seemed to do the trick.  I found it in a forum here [http://ubuntuforums.org/archive/index.php/t-258920.html]("http://ubuntuforums.org/archive/index.php/t-258920.html")
  
However, the mirror problems that I quote above are still present.  Can anyone advise about what might be wrong with the mirrors?

Thanks,

Will M.

---

### Post by raven on 2007-02-08
Failed to fetch [http://my.favorite.cran.mirror/bin/linux/ubuntu/edgy/Release.gpg](http://my.favorite.cran.mirror/bin/linux/ubuntu/edgy/Release.gpg)  Could not resolve 'my.favorite.cran.mirror'
Failed to fetch [http://my.favorite.cran.mirror/bin/linux/ubuntu/edgy/en_US.bz2](http://my.favorite.cran.mirror/bin/linux/ubuntu/edgy/en_US.bz2)  Could not resolve 'my.favorite.cran.mirror'
Failed to fetch [http://my.favorite.cran.mirror/bin/linux/ubuntu/edgy/Packages.gz](http://my.favorite.cran.mirror/bin/linux/ubuntu/edgy/Packages.gz)  Could not resolve 'my.favorite.cran.mirror'
Failed to fetch [http://theli.free.fr/packages/dists/edgy/listen/binary-i386/Packages.gz](http://theli.free.fr/packages/dists/edgy/listen/binary-i386/Packages.gz)  404 Not Found
W: GPG error: [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

the error is very clear, the name "http://my.favorite.cran.mirro" cannot be resolved
try to go to it by your browser and you will see that it does not exist anymore...maybe the site is down/shut who knows...

for this one "http://theli.free.fr/packages/dists/[COLOR="Red"]edgy[/COLOR]/listen/binary-i386/Packages.gz" the site does not have the folder edgy anymore only dapper
so you should change your sources list to "http://theli.free.fr/packages/dists/[COLOR="Red"]dapper[/COLOR]/listen/binary-i386/Packages.gz"
PS:I don't know what version of ubuntu you have, but if you change it to the repository to dapper your package "listen" will try to upgrade it self, you can refuse or upgrade, I don't know what the implications of the upgrade of "listen"...

for this one
W: GPG error: [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy Release: The following signatures couldn't be verified because the public key is not available
again what it says that the public key is not available, could be the owner deleted his public key

more info [http://www.youdzone.com/signature.html](http://www.youdzone.com/signature.html)
and [http://en.wikipedia.org/wiki/Gpg](http://en.wikipedia.org/wiki/Gpg)

I suggest to comment this line "http://medibuntu.sos-sts.com" in you sources list for the time being

---

### Post by will m. on 2007-02-11
Thanks, Raven.

That was very helpful.  I applied all the suggestions and everything appears to be working smoothly.

Will M.

---

