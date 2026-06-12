---
title: "2 newbie questions"
date: 2006-04-11
forum: Absolute Beginner Talk
---

### Post by jmartrican on 2006-04-11
-  I'm used to chkconfig for editting rc*.  In ubuntu is there a chkconfig like cli based app?

-  Is there a command or file that tells me the version of ubuntu i have running?

thanks a lot

---

### Post by trent dillman on 2006-04-11
rcconf (?)
uname -r  (kernel version, not name e.g., "Breezy")

---

### Post by jmartrican on 2006-04-11
jose@jmart1:/etc$ uname -r
2.6.12-9-386

Did not give me the ubuntu version.

No rcconf installed nor did I find it in aptitude.

---

### Post by trent dillman on 2006-04-11
rcconf is in the Universe repo.

I'm still looking for the 'name' part...you've got me curious....

---

### Post by taurus on 2006-04-11
<Ctrl><Alt>F2

---

### Post by jmartrican on 2006-04-12
cool.  How about from CLI?  I am ssh'd into my box, it does not have a monitor.

By Universe repo, did you just mean that its out there somewhere or were you refering to an actual repo?

On another note, I noticed that on rpmfind.net I do no see any releases for ubuntu distro.  Is this because not a lot of people compiling binaries for ubuntu yet or is everything worth getting obtainable through aptitude and automatix?

---

### Post by trent dillman on 2006-04-12
instead of rcconf, try sysv-rc-conf.

And Ubuntu uses .deb packages, not .rpm. Try packages.ubuntu.com

---

### Post by steve.horsley on 2006-04-12
The multiverse and universe repos are real repositories, not enabled by default install. They contain stuff (lots) not officially supported by Ubuntu.

[http://www.ubuntuguide.org/#repositories](http://www.ubuntuguide.org/#repositories) (Hoary)
[http://www.makuchaku.info/amnesty/#repositories](http://www.makuchaku.info/amnesty/#repositories) (breezy)

---

### Post by jmartrican on 2006-04-12
Dudes,

thanks a lot for all the info!

---

