---
title: "Questions about bash"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by rgeddes on 2006-08-27
Installed xubuntu 6.06 and am happy w/ most everything.

Started reading "O'Reilly - Learning Bash" and have a few questions:

1.  In .*ubuntu, where are the original environment variables set?  The book suggested that .bash_profile would be the appropriate place to set them as env vars will propogate into subshells(no need to re-read them in .bashrc), but they are not there.  Most of the postings suggest concatenating to the existing env var or overriding it.  I did a find / -xdev -type f -exec grep -l 'PATH=' {} +, but came up with no file that sets the original (PATH in this case).

2. I prefer the vi command line editing mode, and read that I can change the "readline variable", set editing-mode vi(in ~/.inputrc),which worked.  I further read that bash has "options" that can be set... set -o vi.  Is this two ways to do the same thing or is there a difference between readline vars and bash options? 

richard

---

### Post by TFX360 on 2006-08-27
> **rgeddes said:**
> Installed xubuntu 6.06 and am happy w/ most everything.

Started reading "O'Reilly - Learning Bash" and have a few questions:

1.  In .*ubuntu, where are the original environment variables set?  The book suggested that .bash_profile would be the appropriate place to set them as env vars will propogate into subshells(no need to re-read them in .bashrc), but they are not there.  Most of the postings suggest concatenating to the existing env var or overriding it.  I did a find / -xdev -type f -exec grep -l 'PATH=' {} +, but came up with no file that sets the original (PATH in this case).

2. I prefer the vi command line editing mode, and read that I can change the "readline variable", set editing-mode vi(in ~/.inputrc),which worked.  I further read that bash has "options" that can be set... set -o vi.  Is this two ways to do the same thing or is there a difference between readline vars and bash options? 

richard

Dear Richard,


1. Environment is set in 

```
sudo nano /etc/environment
```

of if you please

```
sudo vi /etc/environment
```

2. I don't have a clue.


Kind regards,


TFX

---

