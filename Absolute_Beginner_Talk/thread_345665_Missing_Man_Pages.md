---
title: "Missing Man Pages"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by robobart on 2007-01-24
I can't find my man pages.

Here is an example:

$ man man
No manual entry for man
See 'man 7 undocumented' for help when manual pages are not available
$ man nano
No manual entry for nano
See 'man 7 undocumented' for help when manual pages are not available.

etc

I've tried:
# aptitude install man-db
# aptitude reinstall man-db
# aptitude install manpages-dev
# aptitude reinstall manpages-dev

no dice. Suggestions? Others with the same problem? 

I'm running edgy ubuntu

Thanks!!!

---

### Post by taurus on 2007-01-24
Maybe

```
sudo aptitude update
sudo aptitude install manpages
```

---

### Post by robobart on 2007-01-24
Ok tried that, also tried

# aptitude reinstall manpages

still no dice. Also, I know this is not an isolated occurence.

---

### Post by robobart on 2007-01-29
OK people. This is a real problem.

If you google "Ubuntu missing man pages" you can find all sorts of isolated "Ubuntu doesn't have man pages for application X"

I think this is part of a bigger problem. Could you guys open a terminal and type

man man

you should get something other than:

No manual entry for man
See 'man 7 undocumented' for help when manual pages are not available.

I *know* there are others with this problem. If you read this post please double check that you can read you man pages.

---

### Post by yabbadabbadont on 2007-01-29
From past experience, I know that I have some missing man pages, but not the same ones as you.  However, I'm running Dapper so that is probably why.

---

### Post by robobart on 2007-02-01
Ok could I be missing man pages because I skipped the "multi-language" (what ever it is called) during the installation?

Even if this is true, why can't I somehow aptitude them?

-Bart

---

### Post by cbhargava on 2007-02-09
I'm running into the same problem. I have reinstalled manpages and I see man files in /usr/share/man/man1 (plus others like man?) even then it is not working.

For example I see the followin file in /usr/share/man/man1
-rw-r--r-- 1 root root   4645 2005-12-16 00:11 a2p.1.gz

when I do 
man 1 a2p
I get 

No manual entry for a2p in section 1
See 'man 7 undocumented' for help when manual pages are not available.

I'm running 6.06LTS Desktop.

Would appreciate some help.

Regards

---

### Post by robobart on 2007-02-10
Ok try this:


echo $MANPATH

I think you should get *nothing* back. However, if you actually get a path back, then you have a problem. 

My problem (which I still don't know how to fix) was caused by the fact that I installed a program locally that clobbered my manpath. 

apparently, if no manpath is specified, then some "default" path is used, otherwise the specified one is used. Thus, if one is specified, your default one will not be accessed.

Ok now I admit, I don't really understand this. If I have spoken incorrectly, please someone correct this!  :)

---

### Post by cbhargava on 2007-02-12
Thanks Robobart,

Looks like the problem was similar to what you had. I installed a asem51 (an 8051 assembler) program locally and that caused my .bashrc to set $MANPATH. I commented it and restarted the shell and it was okay. I did  echo $MANPATH I did not get anything but man worked okay.

Looks like by default the MANPATH variable is unset.

Thanks for your help.

Regards. :)

---

### Post by robobart on 2007-02-12
Great!

Does anybody know what we can append to our MANPATH in the .bashrc file to get the man pages to be found?

Thanks,

-Bart

---

### Post by leafyoung on 2007-04-09
Different from other distribution, you shall refrain from added additional manpath to environmental variable MANPATH. Keep it unset and add your own software's to /etc/manpath.

---

### Post by equinox_child on 2007-06-17
I'm having a similar problem...for me my man pages relating to some C library functions are missing...
man man still works and the pages im talking about used to work...stuff like man fprintf doesn't work anymore...
any ideas?

---

### Post by tblancher on 2007-07-27
I was having the same problem with ping and fsck.  And $MANPATH was empty.  Reinstalling the packages containing those two files (iputils-ping and e2fsprogs, respectively) fixed those man pages.  I also reinstalled manpages before having success.  YMMV.

---

