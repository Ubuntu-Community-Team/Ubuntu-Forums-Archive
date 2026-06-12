---
title: "Burning Programs"
date: 2005-08-22
forum: Absolute Beginner Talk
---

### Post by Irony on 2005-08-22
I have a friend who is on dial-up, I would like to burn a cd-r to give him some programs.

For example I have gftp installed, is it possible to burn this to a cd as a program or somehow create gftp as a folder to burn to cd - how would I do this and how would he install it on his ubuntu?

---

### Post by xmastree on 2005-08-22
I thought gftp was on the installer CD? I have it installed here, and I'm sure I didn't apt-get it.

If your friend has installed ubuntu from CD, he may already have it.

Any other programs he needs can be found [here](http://archive.ubuntu.com/ubuntu/pool/) although it's rather messy doing it that way. Select a package and look at the .DSC file to see what else it needs (depends on...). If those dependencies aren't installed, and aren't available it'll fail.

Vrey frustrating. ](*,)

---

### Post by chiefofthejojos on 2005-08-22
[QUOTE=xmastree]
Any other programs he needs can be found [here](http://archive.ubuntu.com/ubuntu/pool/) although it's rather messy doing it that way. Select a package and look at the .DSC file to see what else it needs (depends on...). If those dependencies aren't installed, and aren't available it'll fail.

Vrey frustrating. ](*,)[/QUOTE]

Yes.  imho, you shouldn't try giving him programs this way, considering he may not have all the dependancies.  
And I agree with xmastree that there is a good chance gftp is on the install cd.  If that's the case he should be able to install it the regular way (through synaptic) and it will automatically take the file from cd instead of downloading it (unless he has changed his repositories).

---

### Post by Irony on 2005-08-23
Gftp was perhaps a bad example. What I meant was can I download programs to give to him given that he's on dial-up. If so how would I do this, or is it not really practical?

---

### Post by h4rdc0d3 on 2005-08-23
Just a guess... but perhaps a tool like apt-mirror could help. Since, Ubuntu mirrors (aka package repositories) are set up the same way as Debian's, maybe you could create a local mirror of the packages you want, burn it to CD-R/DVD-R and add a "deb file..." line to your dial-up friend's /etc/apt/sources.list file.

If you try it, let me know how it goes.

Oh... here's the URL: [http://apt-mirror.sourceforge.net/]("http://apt-mirror.sourceforge.net/")

---

### Post by Irony on 2005-08-25
Thanks for that. I'll look into it.

---

