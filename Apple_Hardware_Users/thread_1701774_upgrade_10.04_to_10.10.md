---
title: "upgrade 10.04 to 10.10"
date: 2011-03-06
forum: Apple Hardware Users
---

### Post by yahway666 on 2011-03-06
I am currently running 10.04 on my ibook g4 and I want to ugrade to 10.10 but i keep getting this error message:
"W:Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/maverick/Release](http://ports.ubuntu.com/ubuntu-ports/dists/maverick/Release)  Unable to find expected entry  partner/binary-powerpc/Packages in Meta-index file (malformed Release file?)
, E:Some index files failed to download, they have been ignored, or old ones used instead."

Help please.

---

### Post by mikewhatever on 2011-03-06
I didn't know upgrading was supported on ppc architecture.

---

### Post by yahway666 on 2011-03-07
Well I know for a fact that 10.10 is compatible with PPC architecture so I just assumed that upgrading would be as well. For all i know that error could be ubuntu's way of saying 'lawl jk, I'm not gonna do that with this architecture'.

---

### Post by Sef on 2011-03-07
From the [Ubuntu Wiki]("https://wiki.ubuntu.com/PowerPC"):


> PowerPC was an officially supported architecture for Ubuntu between versions 4.10 and 6.10. From 7.04 onwards it is a community supported port.

---

### Post by yahway666 on 2011-03-07
Well that doesn't help much... Does anyone know how I can fix this? I know for a fact that 10.10 exists for PPC architecture, the only reason I simply didn't install that from the start was because it is slightly too big for a cd and this laptop doesn't have a dvd drive.

---

### Post by yahway666 on 2011-03-07
Ok, I just tried updating through terminal instead of through the update manager and I got the same error. Except this time I got to see exactly where it screwed up. Apparently it got to 94% complete and then had issues reading the mirror file. Is there a fix for this?

---

### Post by Bucky Ball on 2011-03-07
One question: Why do you want to upgrade exactly? 10.04 LTS is more stable and has a longer support life. If it ain't broke ...

10.10 is a rolling release so expect some surprises from time to time. If there is a specific reason to upgrade I would say go for it (paticular app, other tweak in a newer kernel). If not I wouldn't bother, but that is me. ;)

---

### Post by yahway666 on 2011-03-07
I guess it can wait, I mostly just wanted to have the most updated version and most of my friends said it was amazing.

---

### Post by Bucky Ball on 2011-03-07
It's not that different and latest is not always the greatest, in Linux as it is in Windows world. ;)

---

### Post by yahway666 on 2011-03-07
I'm a mac guy so I wouldn't know much about the windows world, aside from viruses and crashing, and everyone I know that uses it all said it was a vast improvement. Also, at this point I would just feel like a bad *** for getting it to work :)

---

### Post by linuxopjemac on 2011-03-07
You can adapt your /etc/apt/sources.list file according to this one:
[http://mac.linux.be/content/sourceslist-ubuntu-derivatives-ppc](http://mac.linux.be/content/sourceslist-ubuntu-derivatives-ppc)
(replace lucid with maverick)

---

### Post by rsavage on 2011-03-07
I upgraded from 10.04 to 10.10 on ppc from Update Manager I think.  After a while though I kept getting your error message in Synaptic.  Things still seemed to install correctly using the Software Centre so I wasn't sure if this was a critical error message or not?

After I screwed up my system with macbuntu I had to reinstall, but went back to 10.04 because of the error message.  10.10 can definitely do things that 10.04 can't though so I'm kinda of thinking I may upgrade again.  Couldn't understand why nobody else was reporting a 404 error.

---

### Post by rsavage on 2011-03-07
[linuxopjemac]("http://ubuntuforums.org/member.php?u=468914"), have you tried this with Maverick?

Why are you pointing to [http://ftp.usf.edu/pub/ubuntu/?]("http://ftp.usf.edu/pub/ubuntu/")

---

### Post by linuxopjemac on 2011-03-07
I am not using Ubuntu at all on PPC but the sources.list has worked all the time for other people.

---

