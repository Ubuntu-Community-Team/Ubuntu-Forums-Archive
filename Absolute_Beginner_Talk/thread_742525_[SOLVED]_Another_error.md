---
title: "[SOLVED] Another error"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by Not so Superdave on 2008-04-01
I was given a source file to copy and paste. Once I was done with that, I did the sudo apt-get update. Very next line I got was this error

```
E: Type 'restricted' is not known on line 9 in source list /etc/apt/sources.list
```

Any ideas what this is? 

Any help is appreciated.

---

### Post by mick8985 on 2008-04-01
please paste line 9 of your sources.list

---

### Post by Not so Superdave on 2008-04-01
```
deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.

deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main
 restricted

##Universe

deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## Multiverse

deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Backports

deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main
 restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main
 restricted universe multiverse

## Canonical Partner Repository 

deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main
 restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at
 own risk.)
deb http://packages.medibuntu.org/ gutsy free non-free
```

Posting the entire thing to make sure I don't wind up with another error.

---

### Post by mick8985 on 2008-04-01
Yeah all that has happened is you see this line?
```
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main
 restricted
```

It should be like this

```
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
```

A nice way to add lines to you sources.list is just to use System > Administration > Software Sources

---

### Post by Not so Superdave on 2008-04-01
ok, will correct it and thank you very much! :)

---

### Post by mick8985 on 2008-04-01
You're welcome, Please mark the topic as solved in thread tools (forum etiquette).

---

### Post by Not so Superdave on 2008-04-01
Looks like it's solved. I do have one question though. While counting to get the source list line number you would only count the debs right? I'm asking because I'm a little confused about the error telling me to look at line 9. Yet when I did as was suggested the errors were all fixed.  What was line 9?

---

### Post by mick8985 on 2008-04-01
Line 9 is the actual phyical line including comments and whitespace, if you open the file in gedit click on the menu edit > preferences and then "display line numbers" it will show you the line, as it happened the error was on 2 lines so it was better you did just paste the entire file

---

### Post by Not so Superdave on 2008-04-01
Ok, thanks a bunch!!! Marking this as solved.

---

