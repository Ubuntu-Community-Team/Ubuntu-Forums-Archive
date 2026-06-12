---
title: "What to do when &quot;Some index files failed to download&quot;?"
date: 2014-06-27
forum: Any Other OS
---

### Post by fernandojosecabral on 2014-06-27
I have been getting the error message displayed bellow. What can I do to solve the problem OR, at least, get rid of the message?

```
###ERROR###ERROR###ERROR###ERROR###ERROR###ERROR
W:Failed to fetch http://archive.canonical.com/dists/petra/partner/binary-amd64/Packages  404  Not Found [IP: 91.189.92.191 80]
, W:Failed to fetch http://archive.canonical.com/dists/petra/partner/binary-i386/Packages  404  Not Found [IP: 91.189.92.191 80]
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by plucky on 2014-06-27
> **fernandojosecabral said:**
> I have been getting the error message displayed bellow. What can I do to solve the problem OR, at least, get rid of the message?

```
###ERROR###ERROR###ERROR###ERROR###ERROR###ERROR
W:Failed to fetch http://archive.canonical.com/dists/petra/partner/binary-amd64/Packages  404  Not Found [IP: 91.189.92.191 80]
, W:Failed to fetch http://archive.canonical.com/dists/petra/partner/binary-i386/Packages  404  Not Found [IP: 91.189.92.191 80]
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```

Post your sources.list ```
cat /etc/apt/sources.list
```

> [http://archive.canonical.com/dists/petra/partner/binary-amd64/Packages](http://archive.canonical.com/dists/petra/partner/binary-amd64/Packages)

What version of Ubuntu are you running?

There is no version called petra.

---

### Post by grahammechanical on 2014-06-27
What is "petra?" It is the code name for Linux Mint 16. Are you running Lint Mint 16? Or is this referring to some other "petra?"

You can a do two things. You can do what apt-get is doing an ignore. Can you still update/upgrade. You can disable the partner repositories in the Other Software tab of software and Updates.

Regards.

---

### Post by fernandojosecabral on 2014-06-27
> **plucky said:**
> Post your sources.list ```
cat /etc/apt/sources.list
```



What version of Ubuntu are you running?

There is no version called petra.
I am using linux mint petra. Since it is ubuntu-based and uses apt, I presume it must be the same as ubuntu on this particular aspect.

Anyway, I deleted the offending file and the message disapeared. Since it was not doing any good, there will be no harm, I'd guess.
(Perhaps some packge I have installed will not get updated...)

Thanks everyone who hinted or asked.

---

### Post by oldos2er on 2014-06-27
Moved to Other OS/Distro Support.

---

### Post by buzzingrobot on 2014-06-28
What was happening was that the updater was trying to find a "petra" directory at archive.canonical.com, and there is no such directory. The "404" is webspeak for "it's not here"

Mint, like Ubuntu, has a tool that tests mirror speed, identifies the fastest, and allows you to permanently select it.

---

