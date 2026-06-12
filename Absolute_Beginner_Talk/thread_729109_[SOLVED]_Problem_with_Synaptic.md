---
title: "[SOLVED] Problem with Synaptic"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by expo91 on 2008-03-19
Today I tried to get added programs, but when I click on Synaptic I get the following message, before line 22 came up it was line 34 I rebooted, and now this is what I'm getting.

I have hit reload but still get the message. Went to the repository but cold not get anything working there.

Thanks

E: Type '“deb' is not known on line 22 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

---

### Post by glennric on 2008-03-19
Can you post the output of
```
cat /etc/apt/souces.list
```
here?

---

### Post by neurostu on 2008-03-19
It looks like your sources.list file is messed up.

Did you edit your sources.list file? (If you have one), restore to your backup, it not post your sources.list below

---

### Post by expo91 on 2008-03-19
administrator@administrator:~$ cat /etc/apt/souces.list
cat: /etc/apt/souces.list: No such file or directory
administrator@administrator:

---

### Post by aysiu on 2008-03-19
> **expo91 said:**
> administrator@administrator:~$ cat /etc/apt/souces.list
cat: /etc/apt/souces.list: No such file or directory
administrator@administrator:
Typo. It should be ```
cat /etc/apt/sources.list
``` instead of *cat /etc/apt/souces.list* 

Copy and paste is your friend and is more reliable and faster than retyping.

---

### Post by expo91 on 2008-03-19
That worked better!!!

administrator@administrator:~$ cat /etc/apt/sources.list


## Major bug fix updates produced after the final release of the
## distribution.

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

“deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main”
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted
“deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main”
administrator@administrator:~$

---

### Post by aysiu on 2008-03-19
To get rid of that error, you'd have to remove the quotation marks from those Automatix lines. Frankly, though, you shouldn't need Automatix, and their server's been spotty lately anyway.

---

### Post by expo91 on 2008-03-19
Ok do I just edit whats in the terminal window? and after I do how do I save it, or should I just delete the entire line, then save? Remember I need to know how to save.

Thank
Paul

---

### Post by aysiu on 2008-03-19
> **expo91 said:**
> Ok do I just edit whats in the terminal window? and after I do how do I save it, or should I just delete the entire line, then save? Remember I need to know how to save.

Thank
Paul
Just follow [these instructions](http://www.psychocats.net/ubuntu/sources#key).

---

### Post by expo91 on 2008-03-19
Thanks  that did the trick

Paul:

---

